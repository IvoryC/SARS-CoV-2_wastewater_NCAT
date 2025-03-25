# Evaluating SARS-CoV-2 Surveillance, Sampling Methods, and Seasonal Infection Trends on a University Campus

SARS-CoV-2 Epidemiology & Wastewater Surveillance at North Carolina Agricultural and Technical State University in 2021-2023

## See outputs

The scripts to create outputs and some input files are stored in the git repository itself.  The outputs they make, such as figures, are available as non-tracked attachements, see the releases page: [https://github.com/FodorLab/SARS-CoV-2_wastewater_NCAT/releases](https://github.com/FodorLab/SARS-CoV-2_wastewater_NCAT/releases). These can be downloaded to browse locally.

## Project File Structure

This project is designed to be compatible with specific software: Code Ocean and BioLockJ.

### Code Ocean

This project is designed to work with [Code Ocean](https://codeocean.com/).

See corresponding Code Ocean Capsule ["SARS-CoV-2_wastewater_NCAT"](https://codeocean.com/capsule/8844928/tree).

To work with the Code Ocean platform, the top level directories are named to match the 4 "Core Files" folders:

 * `metadata`
 * `environment`
 * `data`
 * `code` (pretty much everything is in here)
 
**metadata**
 
_This directory has the metadata.yml generated by Code Ocean.  For data describing samples (ie metadata) see **code/analysis/input/meta**._
 
**environment**

_This directory has the files to create the environment to run the pipeline._  

This includes: 

  * the `Dockerfile` that is automatically generated by Code Ocean based on information entered in the Environment IDE. It is important to NOT EDIT this file except through the Code Ocean IDE.
  * the `postInstall` script that installs anything else required.
  * the `alternatives/docker/Dockerfile` which can be used locally to create a container for running the pipeline on a local machine.
  
_Note:_ Both Code Ocean and BioLockJ use docker containers.  When running on Code Ocean, the docker container is managed by Code Ocean which uses the container defined in `/environment/Dockerfile`, and BioLockJ runs the pipeline inside that container and does not know that it is operating inside a container.  If you choose to run the pipeline on a local machine you may choose to have BioLockJ manage docker containers locally, using the container(s) available thru the docker hub or defined in `/environment/alternatives/Dockerfile`. BioLockJ could also be used to run the pipeline on a local machine as long the required software is installed.  

To run locally, you will need the following:

R (version 4.4.0 was used)

Most modules require following R packages:
  * tidyr
  * dplyr
  * ggplot2
  * ggrepel
  * lubridate
  * Hmisc

Rendering markdowns requires:
  * markdown

**data**

_Code Ocean will store and manage large files that should not be commited in git. Here, we have the folder for reference, and the README in that folder will have instructions on how to acquire any data needed to run the analysis that is not directly commited in git._


**code**

_This is the main folder.  This is the folder that Code Ocean expects all other git-committed files to be in._


For a compelling argument in favor of using Code Ocean, check out the 2021 editorial ["Promoting reproducibility with Code Ocean"](https://genomebiology.biomedcentral.com/articles/10.1186/s13059-021-02299-x) by Barbara Cheifet, an editor at _Genome Biology_.

### BioLockJ

[BioLockJ](https://biolockj-dev-team.github.io/BioLockJ/) is a pipeline manager. It takes a set of inputs and scripts and generates a new project space with a set structure. To run the pipeline, use the following command on a system where these files are stored and BioLockJ is installed:

`biolockj covid_wastewater_NCAT.config`

The project structure here matches the structure that BioLockJ creates, so relative file paths that work in a given run of the pipeline also work in this repository directly.  Thus, the `code` folder is equivalent to the top level of a pipeline run folder. 

Note that module folders have numbers but these numbers are arbitrary. It keeps them in an intuitive order, but the numbers are not guaranteed to be the same in a given run.

For any given script, its working directory in a run will be `<pipeline>/<module>/<subdir>`; that is **a directory one level down from the module directory**. For example: 

 * project file: `code/analysis/03_Dorms-and-methods/script/Dorm-to-dorm-correlations.Rmd`
 * becomes `covid_wastewater_NCAT_<date>/03_Dorms-and-methods/resources/Dorm-to-dorm-correlations.Rmd` in a given BioLockJ run.

BioLockJ can copy any specified input files into the `input` folder for the run.  For any inputs that are stored in git, it is convenient to store them in `analysis/input` to mach the relative files paths of a run.

For more details about BioLockJ, see the [BioLockJ User Guide](https://biolockj-dev-team.github.io/BioLockJ/) and the README file in the `analysis` folder.

## Publication info

Title: "Wastewater Speaks: Evaluating SARS-CoV-2 Surveillance, Sampling Methods, and Seasonal Infection Trends on a University Campus"

Lead author: Shilpi Bhatia

Preprint posted at https://www.preprints.org/manuscript/202502.1636

Abstract:
Wastewater surveillance has emerged as a cost-effective and equitable approach for tracking the spread of SARS-CoV-2. In this study, we monitored the prevalence of SARS-CoV-2 on a university campus over three years (2021–2023) using wastewater-based epidemiology (WBE). Wastewater samples were collected from 11 manholes on campus, each draining wastewater from a corresponding dormitory building, and viral RNA concentrations were measured using reverse transcription quantitative PCR (RT-qPCR). Weekly clinical case data were also obtained from the university health center. A strong positive and significant correlation was observed between Grab and Composite sampling methods, supporting their robustness as equally effective approaches for sample collection. Specifically, a strong correlation was observed between Aggie Village 4 Grab and Aggie Village 4 Composite samples (R² = 0.84, p = 0.00) and between Barbee Grab and Barbee Composite samples (R² = 0.80, p = 0.00). Additionally, higher viral RNA copies of SARS-CoV-2 (N1 gene) were detected during the Spring semester compared to the Fall and Summer semesters. Notably, elevations in raw N1 concentrations were observed shortly after the return of college students to campus, suggesting that these increases were predomi-nantly associated with students returning at the beginning of the Fall and Spring semesters (January and August). To account for variations in fecal loading, SARS-CoV-2 RNA concentrations were normalized using Pepper Mild Mottle Virus (PMMoV), a widely used viral fecal biomarker. However, normalization using PMMoV did not improve correlations between SARS-CoV-2 RNA levels and clinical case data. Despite these findings, our study did not establish WBE as a consistently reliable complement to clinical testing in a university campus setting, contrary to many retrospective studies. One key limitation was that numerous off-campus students did not contribute to the campus wastewater system corresponding to the monitored dormitories. However, some off-campus students were still subjected to clinical testing at the university health center under mandated pro-tocols. Moreover, the university health center discontinued reporting cases per dormitory after 2021, making direct comparisons more challenging. Nevertheless, this study highlights the continued value of WBE as a surveillance tool for monitoring infectious diseases and provides critical insights into its application in campus environments.

