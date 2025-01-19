# Forest restoration and fuels reduction work: Different pathways for achieving success in the Sierra Nevada

[https://doi.org/10.5061/dryad.bzkh189gb](https://doi.org/10.5061/dryad.bzkh189gb)

Inventory data and code needed to produce figures, tables, and statistical results for the paper. Raw data have been aggregated to the resolution used for the various analyses.

## Description of the data and file structure

analysis.RMD (and analysis.html) is/are a (knit) Rmarkdown script which performs the statistical analyses featured in the paper and produces figures and summary tables. Data for each component analysis are included as .csv files. Each .csv file is named for the corresponding data object in the analysis script.

Included data files and columns are:

* cc\_data.csv
    * plot\_id: Character string identifying a physical inventory plot
    * year: Integer year of observation
    * inv\_type: Character code identifying the scheme for sampling. Only type "N"
        ("normal") plots are included.
    * canopy: Integer giving the canopy cover in percent observed.
    * comp: Compartment (experimental treatment unit) code. Plots are nested within compartments.
    * treatment: Treatment regime for the compartment containing the observation. Options are "control", "mech", "burn", and "mechburn"
    * canopy\_perc: Canopy cover expressed as a proportion, with the range 0-1.
    * canopy\_trans: Canopy cover transformed so as to map from the range 0 &lt;= cover &lt;= 1 to the range 0 &lt; cover &lt; 1. See analysis.rmd for details.
* duff\_data.csv
    * treatment: See above description
    * comp: See above description
    * timestep: The timestep for the observation (e.g. "Pretreatment" for pretreatment observations in 2001, "post\_18" for observations 18 years after the installation of treatments in 2002)
    * plot\_id: See above description
    * duff\_mgha: Observed duff load in megagrams per hectare
    * log\_duff\_mgha: Observed duff load transformed by adding the minimum nonzero value to all observations and then log-transforming
* growth\_and\_removals.csv
    * treatment: See above description
    * Change: The type of change in live basal area; either "Growth", "Mortality", or "Harvest"
    * delta: The magnitude of the change in basal area (in square meters per hectare) from 2003 to 2020 in each treatment type.
    * delta\_ba\_m2hayr: The magnitude of the change in basal area from 2003 to 2020 in square meters per hectare per year in each treatment type
* large\_tree\_stats.csv
    * treatment: See above description
    * comp: see above description
    * plot\_id: see above description
    * timestep: see above description
    * tph: The stems per hectare (stems greater than 76.2 cm DBH) observed on the plot at the timestep
    * count: The total number of stems greater than 76.2 cm DBH on the plot at the timestep
    * Treatment: See above description
    * Timestep: See above description
* net\_ba\_data.csv
    * treatment: see above description
    * comp: see above description
    * post\_1: The observed live basal area (square meters per hectare) in 2003 (one year post treatment) on the plot
    * post\_18: The observed live basal area (square meters per hectare) in 2020 (18 years post-treatment) on the plot
    * delta\_ba\_m2ha: The change in live basal area from 2003 to 2020 in square meters per hectare
    * delta\_ba\_m2hayr: The change in live basal area from 2003 to 2020 in square meters per hectare per year
* ptorch\_data.csv
    * comp: see above description
    * plot\_id: see above description
    * treatment: see above description
    * timestep: see above description
    * ptorch: The PTorch value (from 0 to 1) estimated by FVS for the plot
    * pmort: The PMort value (from 0 to 100) estimated by FVS for the plot
    * ptorch\_transformed: The Ptorch value estimated by FVS and transformed so that the bounds of the interval 0 &lt; x &lt; 1 are closed, rather than open. See methods and script for details.
* sdi\_data.csv
    * plot\_id: see above description
    * inv\_year: see above description
    * timestep: see above description
    * treatment: see above description
    * sdi\_metric: The stand density index (trees per hectare) as calculated in NOrth et al. 2021.
    * max\_sdi: The theoretical maximum stand density index for mesic mixed conifer forests as given in Long and Shaw 2012
    * rel\_sdi: The relative stand density index as described in the methods (sdi\_metrid / max\_sdi)
    * sdi\_zone: The rel\_sdi binned into categories
    * comp: see above description
* sltc\_data.csv
    * treatment: see above description
    * comp: see above description
    * plot\_id: see above description
    * carbon\_mgha: Live aboveground tree carbon in megagrams per hectare
    * pmort: FVS-predicted PMort
    * stable\_ltc\_mgha: Stavle live tree carbon in megagrams per hectare
* surface\_fuels\_data.csv
    * treatment: see above description
    * comp: see above description
    * timestep: see above description
    * plot\_id: see above description
    * surface\_mgha: Observed megagrams per hectare of surface fuels (litter, fine woody debris, and coarse woody debris)
    * log\_surface\_mgha: The observed megagrams per hectare of surface fuels transformed by adding the minimum non-zero value to all observations and then log-transforming

## Sharing/Access information

Data was derived from the following sources:

* Raw inventory datasheets compiled by Blodgett Forest and UC Berkeley field crews.

## Code/Software

Output of sessionInfo():

```
R version 4.1.1 (2021-08-10)
Platform: x86_64-w64-mingw32/x64 (64-bit)
Running under: Windows 10 x64 (build 19045)

Matrix products: default

locale:
[1] LC_COLLATE=English_United States.1252  LC_CTYPE=English_United States.1252    LC_MONETARY=English_United States.1252
[4] LC_NUMERIC=C                           LC_TIME=English_United States.1252    

attached base packages:
[1] stats     graphics  grDevices utils     datasets  methods   base     

other attached packages:
 [1] DHARMa_0.4.3    glmmTMB_1.1.3   lubridate_1.9.2 forcats_1.0.0   stringr_1.5.0   dplyr_1.1.2     purrr_1.0.1     readr_2.1.4    
 [9] tidyr_1.3.0     tibble_3.2.1    ggplot2_3.4.2   tidyverse_2.0.0 here_1.0.1     

loaded via a namespace (and not attached):
 [1] tidyselect_1.2.0    xfun_0.31           TMB_1.7.21          splines_4.1.1       lattice_0.20-44     colorspace_2.0-2   
 [7] vctrs_0.6.3         generics_0.1.0      htmltools_0.5.5     yaml_2.2.2          utf8_1.2.2          rlang_1.1.1        
[13] pillar_1.9.0        nloptr_1.2.2.2      glue_1.6.1          withr_2.5.0         bit64_4.0.5         foreach_1.5.1      
[19] emmeans_1.8.6       lifecycle_1.0.3     munsell_0.5.0       gtable_0.3.0        mvtnorm_1.1-2       codetools_0.2-18   
[25] coda_0.19-4         evaluate_0.14       knitr_1.37          tzdb_0.1.2          fastmap_1.1.0       parallel_4.1.1     
[31] fansi_0.5.0         Rcpp_1.0.8          xtable_1.8-4        scales_1.2.1        vroom_1.6.3         bit_4.0.4          
[37] lme4_1.1-27.1       hms_1.1.3           digest_0.6.29       stringi_1.7.6       numDeriv_2016.8-1.1 grid_4.1.1         
[43] rprojroot_2.0.2     cli_3.6.1           tools_4.1.1         magrittr_2.0.3      crayon_1.4.1        pkgconfig_2.0.3    
[49] MASS_7.3-60         Matrix_1.3-4        estimability_1.4.1  timechange_0.2.0    iterators_1.0.13    minqa_1.2.4        
[55] rmarkdown_2.14      rstudioapi_0.14     R6_2.5.1            boot_1.3-28         nlme_3.1-153        compiler_4.1.1     
```