# Why Has Regional Income Convergence in the U.S. Declined? Ganong and Shoag Repkit(2017) Replication

For questions and feedback, contact: ganong@uchicago.edu.

## Overview

This repository contains the replication code for the paper "Why Has Regional Income Convergence in the U.S. Declined?" by Peter Ganong and Daniel W. Shoag (2017). The code is structured to reproduce the figures and tables presented in the paper.

## Note
This repository contains various files related to the Ganong Shoag Repkit project. Please note that some of these files are managed using Git LFS (These are large files storage over 100MB).

## Files Managed with Git LFS

The following files in this repository are managed using Git LFS to handle their large size efficiently:

- `journalist`
- `src_data`
- `work_final`

This code uses Git LFS to prevent bloating the repository's commit history with large binary files. When you clone the repository, make sure to use the `git lfs pull` command to fetch the actual content of the files that uses git lfs.

## Getting Started

To get started with the Ganong Shoag Repkit project, follow these steps:

1. Clone the repository using the following command:
`git clone <repository_url>`

2. Navigate to the repository directory:
`cd project-name`

3. Fetch the actual content o2f Git LFS files:
`git lfs pull`

4. Continue working on your code and make any needed adjustment, commit, and push as needed.

# ORDER OF RUNNING SCRIPTS

set more off
do path
cap ssc inst _gwtmean

***STATE/LMA LEVEL ANALYSIS***
do 00_build/inflate compiles historical inflation data from various sources, merges it into a consistent dataset, and corrects for data inconsistencies to create a continuous inflation index for analysis.
do 01_build/prepHc prepares two analysis samples from the "usa_00088" microdata: one for convergence and inequality analysis and another for human capital analysis.
do 02_build/hc_stock_series analyzes income convergence by demographic variables over time through aggregation, regression, and comparison of income measures.
do 03_build/constructLma performs data preparation, merging, and analysis to investigate economic and demographic trends at different geographic levels in the United States.
do 04_build/constructState compilies multiple datasets, generate economic measures, and prepares data for statistical examination.

set more off
do 00_analyze/rolling output table generation for economic indicators such as per capita income, population, and wage income across different years in TABLE 1, APPENDIX TABLES 1-2
do 01_analyze/graphStateSlides generates graphs depicting income convergence rates, population growth rates, and housing value changes in the U.S. for various time periods in FIGURES 1, 2
do 02_analyze/hcConverge visualizes the extent of human capital convergence resulting from migration over time in the U.S. in FIGURE A2
do 03_analyze/analysis generate tables and figures with various interaction in TABLE 2, TABLE 3, FIGURE 7, FIGURE 8, APPENDIX TABLE 5

do 04_analyze/nonhomothetic.do visualize the connection between housing share of income and average income per adult, instrumented with education, for metropolitan areas in APPENDIX FIGURE 1 
do 05_analyze/summary_stats.do merges data from different sources to calculate and summarize the mean and standard deviation of the variables in Table 1
do 06_analyze/compare_regulations.do correlates various measures related to regional development by merging datasets and conducting a correlation analysis with additional variables for the year 1990 in Footnote 26
do 07_analyze/revised_scalings.do outputs the results of regression analyses in Appendix Table 6

***MICRO DATA ANALYSIS***
do 08_build/borjas1940.do processes individual and household data from the year 1940 to calculate indicators for skilled individuals, housing costs, migration rates, and nominal and real household income
do 09_build/borjas1940robustness.do processes and analyzes demographic and economic data for the year 1940

do 10_build/borjas2000.do processes and analyzes data related to migration and income for the year 2000.
do 11_build/borjas2000robustness.do analyzes migration and household data for the year 2000, generating skill-specific income and migration statistics under various scenarios and populations.
do 12_build/price_file_prep.do calculates demographic characteristics, average household income, and skill-related variables for different years  by state and birth state. It also computes housing costs, scaled income, and generates instrument variables for further analysis.

do 13_analyze/mig_returns_and_flows.do generates various figures in figure 3, 4, 5, and appendix tables 3, and 4 relating to migration and income data, including scatter plots, regression results, and data manipulation, for different years (1940, 2000, etc.), skills (skilled and unskilled), and demographics, and exports the results to various file formats

I've added two-digit numbers to each script name to provide a clear order of execution.
