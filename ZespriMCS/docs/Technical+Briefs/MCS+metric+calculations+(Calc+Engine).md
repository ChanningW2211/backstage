# **MCS metric calculations (Calc Engine)**
## **Summary:**
“MCS metric calculations“ or the “calc engine” is responsible for setting up all the reporting schema tables in the MCS database. These tables are used to review the results each sample request received during its testing and what the overall clearance the sample request achieved.

The Calc engine is fired off every 15 minutes from ADF ([Link Prod](https://adf.azure.com/en-us/authoring/pipeline/pl_metric_calculation_orchestration?factory=%2Fsubscriptions%2F4ae35c85-3190-4987-bc9f-c7b05ab5174c%2FresourceGroups%2Frg-maturityclearances%2Fproviders%2FMicrosoft.DataFactory%2Ffactories%2Fadf-zes-prd-wu2-mcs)) (Azure: (adf-zes-prd-wu2-mcs/pl\_metric\_calculation\_orchestration). Stored procedures are executed in order from the staging of all sample requests that need to go through the calc engine, to calculating different metrics, inserting into staging tables and finally to update the front facing reporting tables and most importantly setting the clearance status\criteria achieved at a sample level. Clearance Status is a business term used to say whether or not a sample request has achieved a clearance status of “Cleared” or “Failed”, this pass relates to a specific criteria which is also present on the main clearance table. Please see below for more details.
## **Future Development plans for the MCS calc engine:**
1. Changing the orchestration of the MCS metric system. Zespri want to change the orchestration from a batch model (multiple at a time every 15 mins) to run automatically as a sample request has its status changed to “testsCompleted”. In order to achieve this we would need to review the current calc engine and remodel it to work better for individual sample requests instead of batching them (performance). 
2. Reviewing, Fixing and enabling the “Combined” metric tables. Located ([Stg].[UspMetricCalcCombinedSamplesGADMAllSamples], [Stg].[UspMetricCalcCombinedSamplesHWDMAllSamples]). Zespri are currently not reporting on Combined samples, however they do want these fixed and working for next season
## **MCS Calculation Breakdown:**
Stored procedures Sequence:

1. [Stg].[UspMetricCalcSampleMaster]
2. [Stg].[UspMetricCalcDryMatterTestAllSamples]
3. [Stg].[UspMetricCalcDryMatterBySizeTestAllSamples]
4. [Stg].[UspMetricCalcColourTestAllSamples]
5. [Stg].[UspMetricCalcColourBySizeTestAllSamples]
6. [Stg].[UspMetricCalcFreshWeightTestAllSamples]
7. [Stg].[UspMetricCalcPressureTestAllSamples]
8. [Stg].[UspMetricCalcBrixTestAllSamples]
9. [Stg].[UspMetricCalcSeedColourTestAllSamples]
10. [Stg].[UspMetricCalcFruitResults]
11. [Stg].[UspMetricCalcClearanceOutput]
12. [Stg].[UspMetricCalcInheritance]

## **1. [Stg].[UspMetricCalcSampleMaster]**
Stages all sample requests in the ‘TestsCompleted’ state that also have a maturity type code of ‘C' or 'M’ in a staging table for bulk metric calculation. 

## **2. [Stg].[UspMetricCalcDryMatterTestAllSamples]**
Calculates metrics for samples for dry matter at a sample level and inserts output into the table [Rep].[RepMetricCalcDryMatterTestOutput] which acts as the “sample level” dry matter metric table. If the sample request contains not valid (null) dry matter in the results table this will not run for that sample request. Only one row for a sample request can be “active = 1“ at one time.

## **3. [Stg].[UspMetricCalcDryMatterBySizeTestAllSamples]**
Calculates dry matter for each sample at a size level. This only applies to samples that have been staged in the USPMetricCalcSampleMaster that are of a variety ‘GA’ and have a valid dry matter\fresh weight in the sample results table. This output is inserted into the reporting table [Rep].[RepMetricCalcDryMatterSizeBandTestOutput]. Only one row for a sample request/size can be “active = 1“ at one time.

## **4. [Stg].[UspMetricCalcColourTestAllSamples]**
Calculates colour metrics at a sample level. Samples must have either a valid (not null) Hue1 or a valid Hue2 in the sample results table for the result to sync through to this calc. The calculation output is inserted into the reporting table [Rep].[RepMetricCalcColourTestOutput]. Only one row for a sample request can be “active = 1“ at one time.

## **5. [Stg].[UspMetricCalcColourBySizeTestAllSamples]**
Calculates colour metrics for samples at a size level. This is only valid for sample requests staged that have a ‘GA’ variety a Valid Fresh weight and a valid Hue1 or Hue 2. This calculation output is inserted into the reporting table [Rep].[RepMetricCalcColourSizeBandTestOutput].Only one row for a sample request/size can be “active = 1“ at one time.

## **6. [Stg].[UspMetricCalcFreshWeightTestAllSamples]**
Calculates fresh weight metrics at a sample level. This is only valid for sample requests staged that have a valid fresh weight. This calculation output is inserted into the reporting table [Rep].[RepMetricCalcFreshWeightTestOutput]. Only one row for a sample request can be “active = 1“ at one time.

## **7. [Stg].[UspMetricCalcPressureTestAllSamples]**
Calculates Pressure metrics at a sample level. This is only valid for sample results that have a valid ‘Pressure1’ from the sample results table. This calculation output is inserted into the reporting table [Rep].[RepMetricCalcPressureTestOutput]. Only one row for a sample request can be “active = 1“ at one time.

## **8. [Stg].[UspMetricCalcBrixTestAllSamples]**
Calculates brix (sugar) metrics at a sample level. This is only valid for sample results that have a valid ‘BrixEquitorial’ from the sample results table. This calculation output is inserted into the reporting table [Rep].[RepMetricCalcBrixTestOutput]. Only one row for a sample request can be “active = 1“ at one time.

## **9. [Stg].[UspMetricCalcSeedColourTestAllSamples]**
Calculates seed metrics at a sample level. This is only valid for sample results that have a valid ‘BlackSeeds’ from the sample results table. This calculation output is inserted into the reporting table [Rep].[RepMetricCalcSeedColourTestOutput]. Only one row for a sample request can be “active = 1“ at one time.

## **10. [Stg].[UspMetricCalcFruitResults]**
Step 1 stages the basic skeleton of the staging table “[stg].[StgMetricCalcFruitOutput]”. This is then updated through steps 2-9 with outlier data. Once we get to step 10 we use this staging table to insert fruit level metrics into the [rep].[RepMetricCalcFruitOutput] table. Only one row for a sample request can be “active = 1“ at one time. 

## **11. [Stg].[UspMetricCalcClearanceOutput]**
This stored procedure is responsible for calculating the sample level clearance output for each sample. We fetch all of the metrics calculated in steps 2-9, and join the sample request to the criteria table based on the sample requests variety, grow method and country ID. Based on this join we will normally get a few criteria we can use to compare our metrics against. We use the criteria versioning table and join it to the criteria rule table in order to fetch the “CriteriaSort” column which is used as a way to rank criteria and all the rules like “Brix Threshold”. We compare metric rule\threshold data in the Criteria rule table against the metrics above and if the sample has passed multiple criteria (meet all thresholds) then we use the Sort order table to find out what criteria is best. Based on this criteria and clearance the sample request will get a row in the [rep].[repmetriccalcclearanceoutput] table which contains a Clear status of “Cleared” or “Failed” which relates to a criteria Id column that can be linked back the criteria the sample was tested against. All Monitoring SRs gets a “Completed” status in repmetric calc.

Please note, this procedure also looks at inheritance when calculating the sample level pass but only when testing for Dry Matter threshold. Only one row for a sample request can be “active = 1“ at one time.

## **12. [Stg].[UspMetricCalcInheritance]**
This stored procedure is responsible for inheritance. Each sample request in step 11 will have a cleared Status of failed or cleared. Regardless of status we will also check to see if inheritance can be used to fetch a better overall pass from a historic sample clearance tests. We use the sample requests block key to match to historic sample requests that have a sample level clear status of “Cleared” that also matches the samples orchard and season. If a historic sample that matches the samples block key\season\orchard exists we update the repmetriccalcclearanceoutput table with the matching inheritance data and pass. 

This procedure is also responsible for setting some of the TZG inheritance values, Sizes Achieved for dry matter at a sample level in the RepMetricCalcDryMatterTestOutput and at a size level we update the KSPassInheritted and MPPassInheritted in the [rep].[RepMetricCalcClearanceSizeBandOutput] table.

We then iterate through all the staged sample requests and execute the USPSampleRequestStateUpdate to update the status to either “Cleared” or “Failed” (if Type of Clearance) or “Completed” (if Type of Monitoring).
