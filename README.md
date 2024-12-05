## Evolution of child acute malnutrition during war in the Gaza Strip, 2023-2024: retrospective estimates and scenario-based projections
### Description of input dataset and R analysis scripts
December 2024

Funding support: UK Humanitarian Innovation Hub

## General description
This repository contains data and R scripts needed to replicate the above analysis. The input datasets required are found in the `\in` folder, and are read automatically when the code is run. Every row in dataset `sdn_cam_data_final_public.xlsx` contains an individual record of a deceased person, as contained in one of three independent lists generated by the study. The Excel file also contains a variable dictionary.
All the code is found in the `\code` folder. To replicate the analysis, follow these steps:
* Download and unzip the repository to any folder in your computer (other than the Downloads folder, which usually gets wiped automatically). The folder is identified automatically when the code is run.
* Download R and RStudio (see download links on [https://posit.co/download/rstudio-desktop/]). While R is sufficient to run the analysis, it is recommended to instead run the scripts from the RStudio interface.
* Open and run the entire `00_master_code.R` script (just press Alt+Ctrl+R). This will create an `\out` folder with further sub-folders, to which output tables and graphs will be saved automatically. As this scripts calls all the others, it alone is sufficient to replicate the analysis, but note below re: unavailability of one necessary dataset, to circumvent which we have already created an `\out` sub-folder in this directory, with files needed for subsequent steps.

## Description of each R script
### Codes 0# : these scripts need to be run every time
* `00_master_code.R` installs or loads R packages needed for this analysis, sets general parameters and sources the other scripts in logical order. Scroll down for a representation of the inter-dependency among scripts and resulting outputs.
* `01_functions.R` contains functions needed for different steps in the analysis.
* `02_read_prepare_inputs.R` reads input data, carries out several data cleaning and management tasks and prepare objects for further analysis steps.

### Codes 1# : these scripts need to be run only once
* `11_estimate_growth_curves.R` fits additive models to Gaza growth monitoring data and estimates weight and height growth curves by sex.
* `12_calibrate_wt_model.R` estimates parameters requires to calibrate the weight model so as to accurately reproduce observed variability in growth curves.
* `13_validate_wt_model.R` tests the weight model against WHO growth standards and other sources of data.
* `14_model_infectious_disease.R` computes the relationships between period prevalence, point prevalence and incidence of ARI and diarrhoea.
* `15_model_caloric_sacrifice.R` implements a static microsimulation of households to estimate the relationship between maximum percent of caloric availabiity that adults will be willing to sacrifice, percent of children's caloric need that adults will preserve, mean caloric availability per capita and the resulting ratio of children's caloric intake under the above parameters to intake with no caloric sacrifice.
Script 11 requires raw data on 2.2M growth monitoring observations from Gaza: these are not included in the repository as the file is extremely large and we do not have permission to share these data. It also requires about a day to run. Scripts 12 and 13 are dependent on first running script 11. Script 12 also requires about a day. Scripts 14 and 15 do nor require running 11, 12, and 13 and the inputs provided in the repository are sufficient.
To facilitate replication, we have included in the `/out` subfolder all the output files from the above scripts. This enables users to implement the rest of the analysis. These outputs also enable the user to pick up the analysis from script 12. In other words, only scripy 11 is not replicable.

### Codes 2#: these scripts need to be run every time
* `21_prepare_timeline.R` prepares data on retrospective and scenario-based projections by setting up a timeline and preparing output objects.
* `22_run_scenarios.R` implements the model simulation including retrospective and scenario-based projections, as desired, gathers the results and outputs some visualisations.

## Description of each input file
The input files include:
* 