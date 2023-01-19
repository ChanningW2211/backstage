# **MCS - Technology Stack**
### **Front End**

|**Technology**|**Description**|
| :-: | :-: |
|NextJS|Our front end code is written in Typescript using [NextJS](https://nextjs.org/learn/foundations/about-nextjs/what-is-nextjs)|
|Azure Front Door|Entry point for all web traffic to MCS|
### **Back End**

|**Technology**|**Description**|
| :-: | :-: |
|<p>Azure Function Apps</p><p>- C# API</p><p>- NextJS API</p>|APIs written in NextJs will be within the MCS-External in Azure Function and all APIs written in C3 will be within MCS-Orchard API|
|Azure SQL|<p>The database servers for the different MCS environments are named like this:</p><p>sqlsvr-zes-<ENV>-wu2-mcs.database.windows.net where <ENV> is either DEV, TST, PPE or PRD</p>|
|Azure Blob Storage|<p>Object Storage</p><p>stores the following:</p><p>- KPIN</p><p>- Maps</p><p>- CSVs</p><p>- Packhouse Id</p><p>- Temp Files</p><p>- admin</p>|
|SendGrid|SMTP Provider|
Click here to read related details around [MCS Components](https://sparknz.atlassian.net/wiki/spaces/BIGDATA/pages/10285645939/MCS+Maturity+Clearance+System+Overview)
