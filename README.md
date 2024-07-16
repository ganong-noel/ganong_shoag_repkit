# Why Has Regional Income Convergence in the U.S. Declined? Ganong and Shoag Repkit(2017) Replication

For questions and feedback, contact: ganong@uchicago.edu.

## Overview

This repository contains the replication code for the paper "Why Has Regional Income Convergence in the U.S. Declined?" by Peter Ganong and Daniel W. Shoag (2017). The code is structured to reproduce the figures and tables presented in the paper.

## Note
This repository contains various files related to the Ganong Shoag Repkit project. Please note that some of these files are managed using Git LFS. These datasets are tracked using Git LFS (Large File Storage). Git LFS helps manage large files more efficiently, keeping the repository size manageable while still providing access to the necessary data.

**Using Datasets Tracked with Git LFS**
 
Here's how you can properly clone the repository and work with the datasets:

1. **Clone the Repository**:
   Clone the repository using the following command in your terminal:

   ```
   git clone <repository-url>
   ```

   Replace `<repository-url>` with the actual URL of the repository.

2. **Install Git LFS**:
   Make sure you have Git LFS installed on your system. If not, you can download and install it from the [Git LFS website](https://git-lfs.com/).

3. **Navigate to the Repository Directory**:
   After cloning the repository, navigate to the repository directory using the terminal:

   ```
   cd project-name
   ```

   Replace `project-name` with the name of your project directory.

4. **Fetch Large Files**:
   Run the following command to fetch the actual content of the large files tracked by Git LFS:

   ```
   git lfs pull
   ```

   This command downloads the content of the large files from the Git LFS server.

5. **Checkout the Files**:
   The large files are represented in the repository as pointers. To replace the pointers with the actual content, use the following command:

   ```sh
   git lfs checkout
   ```

   This command replaces the pointers with the actual data in your working directory. It downloads and fills in the real data into your working directory, so you can use the large files as you normally would.

6. **Work with Datasets**:
   You can now work with the datasets. The large files should be available in their respective directories.



## Files Managed with Git LFS

The following files in this repository are managed using Git LFS to handle their large size efficiently:

- `journalist`
- `src_data`
- `work_final`

# ORDER OF RUNNING SCRIPTS

set more off
do path
cap ssc inst _gwtmean

***STATE/LMA LEVEL ANALYSIS***

`00_build/inflate.do` compiles historical inflation data from various sources, merges it into a consistent dataset, and corrects for data inconsistencies to create a continuous inflation index for analysis.

`01_build/prepHc.do` prepares two analysis samples from the "usa_00088" microdata: one for convergence and inequality analysis and another for human capital analysis.

`02_build/hc_stock_series.do` analyzes income convergence by demographic variables over time through aggregation, regression, and comparison of income measures.

`03_build/constructLma.do` performs data preparation, merging, and analysis to investigate economic and demographic trends at different geographic levels in the United States.

`04_build/constructState.do` compilies multiple datasets, generate economic measures, and prepares data for statistical examination.

`00_analyze/rolling.do` output table generation for economic indicators such as per capita income, population, and wage income across different years in TABLE 1, APPENDIX TABLES 1-2

`01_analyze/graphStateSlides.do` generates graphs depicting income convergence rates, population growth rates, and housing value changes in the U.S. for various time periods in FIGURES 1, 2

`02_analyze/hcConverge.do` visualizes the extent of human capital convergence resulting from migration over time in the U.S. in FIGURE A2

`03_analyze/analysis.do` generate tables and figures with various interaction in TABLE 2, TABLE 3, FIGURE 7, FIGURE 8, APPENDIX TABLE 5

`04_analyze/nonhomothetic.do` visualize the connection between housing share of income and average income per adult, instrumented with education, for metropolitan areas in APPENDIX FIGURE 1 

`05_analyze/summary_stats.do` merges data from different sources to calculate and summarize the mean and standard deviation of the variables in Table 1

`06_analyze/compare_regulations.do` correlates various measures related to regional development by merging datasets and conducting a correlation analysis with additional variables for the year 1990 in Footnote 26

`07_analyze/revised_scalings.do` outputs the results of regression analyses in Appendix Table 6

***MICRO DATA ANALYSIS***

`08_build/borjas1940.do` processes individual and household data from the year 1940 to calculate indicators for skilled individuals, housing costs, migration rates, and nominal and real household income

`09_build/borjas1940robustness.do` processes and analyzes demographic and economic data for the year 1940

`10_build/borjas2000.do` processes and analyzes data related to migration and income for the year 2000.

`11_build/borjas2000robustness.do` analyzes migration and household data for the year 2000, generating skill-specific income and migration statistics under various scenarios and populations.

`12_build/price_file_prep.do` calculates demographic characteristics, average household income, and skill-related variables for different years  by state and birth state. It also computes housing costs, scaled income, and generates instrument variables for further analysis.

`13_analyze/mig_returns_and_flows.do` generates various figures in figure 3, 4, 5, and appendix tables 3, and 4 relating to migration and income data, including scatter plots, regression results, and data manipulation, for different years (1940, 2000, etc.), skills (skilled and unskilled), and demographics, and exports the results to various file formats
