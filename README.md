
# Early Onset Colorectal Cancer Analysis

The incidence and mortality of colorectal cancer (CRC) in the general population has been declining over the last decade, partially due to increased screening and early removal of polyps. However, colorectal cancer remains the third most common cancer and the second leading cause of cancer death in the United States. The incident among early-onset patients, those diagnosed between 20-49 years of age, has been increasing in annual incidence rates of over 1.5% per year in the past decade. This repository contains source code used to generate the results and figures reported in Yeo et. al. (submitted) that reports on the genetic and epidemiology elements that may be associated with this trend.  

The analysis is divided into two component. The first is analysis of The Cancer Genomic Atlas [(TCGA) CRC data](https://tcga-data.nci.nih.gov/docs/publications/coadread_2012/) and the second is the analysis of Surveillance, Epidemiology, and End Results Program [(SEER) CRC data](http://seer.cancer.gov/statfacts/html/colorect.html).

### General Notes
This code requires working knowledge of unix environment and R programming. This is not production-grade source code and is not intended, or likely, to works as-is (i.e. from clone) some code editing is required to regenerate the results. Specifically, the scripts that require external data files that are downloaded from TCGA gDAC or other sources are stored outside this source directory. The paths to these data files need to be set in each script. Note that in most R scripts plotting can be directed to screen or pdf file by setting of ‘plot2file’ variable (TRUE= pdf file, FALSE = to screen).

**Prerequisite**: R (v. 3.1.3) packages `dplyr`, `tidyr`, `ggplot2`, `grid`, `gridExtra`, `ggcounty`, `gpclib`, `reshape`, `scales`

### Analysis of TCGA CRC data
1. Download COREAD data set from the Broad gDAC database using `FetchBroadGDACMutationFiles.sh`. 
This script requires gDAC [firehose_get](https://confluence.broadinstitute.org/display/GDAC/Download)
2. Run `CRCAgeSubTypes.R` to generate the eCDF plots for analysis of age distribution in the various TCGA cluster groupings (Supplementary Figure 3,4). Use `CRCAgeMethylation.R` for similar analysis using TCGA methylation data.
3. Run `CRCAgeMutationRate.R` to generate an earlier version of mutation rates and CNV vs. age and use `CRCAgeMutationRateII.R` to generate the newer mutations rates figure (Supplementary Figure 2)

### Analysis of SEER CRC data
The `csv` files required for this analysis are included in the `data` subdirectory. 
These were generated by `SEERTableParse.py` which parses the respective spreadsheets in `frequencyv3.xlsx`. 

1. Run `CombineSEERCDCData.R` to generate the plots for E-CRC epidemiology risk factors and anatomical location (Figure 2).
2. `MapAgePlot.R` will generate the US and state maps displaying the rate of CRC in early, late age groups and ethnic grouping by county. 
Included are regression analysis of early/late onset CRC ratios (age adjusted) for 
various ethnic groups (Figure 3).
3. `CRCEthnicRates.R` to plot CRC and E-CRC 2000-2011 rates by ethnic groups (Supplementary Figure 1).
