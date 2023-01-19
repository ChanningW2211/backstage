# **Kiwifruit Varieties and Testing**
- [Fruit testing](#fruit-testing)
- [Helper Samples](#helper-samples)
- [GA](#ga)
- [HE](#he)
- [HW](#hw)
- [RS](#rs)
- [WK](#wk)

At this point Zespri are maturity testing 5 varieties of kiwifruit which are known in MCS by their 2 digit variety code:

- GA - Gold3
- HE - Green14
- HW - Hayward 
- RS - Red19
- WK - Wilkins (this looks to be phasing out though)

(numbers after the name are just the way they determine different versions of that variety through their breeding programs) There have been approx 26 varieties over the years but Zespri are only currently testing the 5 above.

The group of tests that are performed/requested per sample is based on the **Test Code** loaded against the specific Sample Request. Each Test Code includes a set of tests and the number of fruit that should be collected and tested to get a valid result. (See Test Code management section which hasn't been written yet)
## **Fruit testing**
Different fruit varieties have different characteristics that Zespri require to be tested as part of the maturity clearance process. All of the tests are captured in the Test Group Management UI within MCS but boil down to the following list (which includes the number of actual measures taken per fruit):

- Weight (1) (W)
- Colour (6) (C)
- Pressure (2) (P)
- Dry Matter (1) (D)
- Brix (equatorial) (1) (BEQ)
- Black seeds (% of fruit with black vs white seeds) (1) (S)

**Weight**: always tested for every fruit variety.

**Colour**: tested for GA and HE fruit only. GA we are looking for low colour degree values, HE we are looking for high values (on the colour scale, gold is lower and green is higher).

**Pressure**: at the beginning of the season, as there is no fruit in the coolstores, everything that is picked is basically shipped for sale immediately. We therefore don’t need to test the pressure of the fruit in the beginning of the season but do later when the fruit will end up in a coolstore for a length of time (the last fruit is picked in late June and the last tray leaves the coolstore in November).

**Dry Matter**: always tested for every fruit variety. Dry matter is basically a slice of the fruit that has been weighed and then dried out (in big ovens) to work out the amount of dry matter in the fruit vs moisture. In a perfect world, you would dry the whole fruit. In terms of making this a much faster process, a slice from the same place and the same size for each fruit that is tested gives a representative answer. 

**Brix**: always tested for every fruit variety. Brix is a measure of sugar content in the fruit. There are three ways of measuring Brix:

- Brix Equatorial (middle of the fruit - this is what is currently used)
- Brix Stem (measuring Brix at the stem end of the fruit)
- Brix Blossom (measuring Brix at the blossom end of the fruit)

**Seeds**: only tested in green varieties of kiwifruit and only at the beginning of the season. The later in the season, the more black seeds there are so we stop testing seeds after the Kiwistart period finishes.
## **Helper Samples**
Helper samples are taken for certain Test Codes (eg GA clearance samples). These are always a smaller sample size (60 fruit vs 90 fruit for standard clearance samples) and always taken in conjunction with the parent sample (giving a total of 150 fruit for that sample). The helper samples have a different blinded sample number but share the same sample request number so they can be married up. These are always collected as smaller sized fruit which enables a better regression line to be drawn through some of the metric graphs based by size. Only a subset of tests are conducted on the helper samples. 
## **GA**
Gold3 is a Licensed variety of Zespri Kiwifruit. This means a grower is not allowed to plant/grow Gold3 vines without paying a license fee to Zespri per hectare of vines (one of the previous tenders for Gold3 licenses came in at over $220,000 per hectare for a 30 year license).

GA (Gold3 also known as G3) are (clearly!) gold fruit that are sweeter than green but not as sweet as Red.

For GA fruit, Labs test the following and send the data back to MCS:

- W
- C
- P
- D
- BEQ

Helper Sample:

- W
- C
- D
## **HE**
Green14 is unlicensed. Anyone can grow this fruit. To sell is under the Zespri banner, it must go through the maturity clearance process. 

For HE fruit, Labs test the following and send the data back to MCS:

- C
- P
- D
- BEQ
- S
## **HW**
Hayward is unlicensed. Anyone can grow this fruit. To sell is under the Zespri banner, it must go through the maturity clearance process. 

For HW fruit, Labs test the following and send the data back to MCS:

- W
- P
- D
- BEQ
- S
## **RS**
Red19 a Licensed variety of Zespri Kiwifruit and is currently only grown in limited orchards. This means a grower is not allowed to plant/grow RS vines without paying a license fee to Zespri per hectare of vines.

RS are the sweetest variety of Kiwifruit (taste like a cross between banana and strawberries, no hint of kiwifruit tang).

For RS fruit, Labs test the following and send the data back to MCS:

- W
- C
- P
- D
- BEQ
- S
## **WK** 
Isn't worth talking about at this point.
