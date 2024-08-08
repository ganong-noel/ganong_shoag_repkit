# Why Has Regional Income Convergence in the U.S. Declined? Ganong and Shoag Repkit(2017) Replication

For questions and feedback, contact: ganong@uchicago.edu.

## Overview

This repository contains the replication code for the paper "Why Has Regional Income Convergence in the U.S. Declined?" by Peter Ganong and Daniel W. Shoag (2017). The code is structured to reproduce the figures and tables presented in the paper.


Here's how you can properly clone the repository and work with the datasets:

1. **Clone the Repository**:
   Clone the repository using the following command in your terminal:

   ```
   git clone <repository-url>
   ```

   Replace `<repository-url>` with the actual URL of the repository.


## [src_data](https://www.dropbox.com/sh/021z1nvxym2fmv1/AAA2Xz7UGdZ8CBEpihnbIyJPa?dl=0)
2. **Download this dropbox** 
Unzip the src_data folder after downloading and make sure it is in the same parent directory as the cloned repository.

3. **Update the path.do file to match your local directory structure**
Change the username to your stata username and update the placeholders with the file paths on your local machine.

if ("`c(username)'" == "stata username")`
`global code = "/path/to/ganong_shoag_repkit"`
`global src = "/path/to/src_data"`
`global work = "/path/to/work_final"`
`global out = "/path/to/out_final"`

4. **Run the master.do file to replicate all the figures in one pass.**
Each do file can be run separately, but running master.do is easier and less time consuming.


# ORDER OF RUNNING SCRIPTS

set more off
do path
cap ssc inst _gwtmean

***STATE/LMA LEVEL ANALYSIS***

1. `build/inflate.do` compiles historical inflation data from various sources, merges it into a consistent dataset, and corrects for data inconsistencies to create a continuous inflation index for analysis.

2. `build/prepHc.do` prepares two analysis samples from the "usa_00088" microdata: one for convergence and inequality analysis and another for human capital analysis.

3. `build/hc_stock_series.do` analyzes income convergence by demographic variables over time through aggregation, regression, and comparison of income measures.

4. `build/constructLma.do` performs data preparation, merging, and analysis to investigate economic and demographic trends at different geographic levels in the United States.

5. `build/constructState.do` compilies multiple datasets, generate economic measures, and prepares data for statistical examination.

6. `analyze/rolling.do` output table generation for economic indicators such as per capita income, population, and wage income across different years in TABLE 1, APPENDIX TABLES 1-2

7. `analyze/graphStateSlides.do` generates graphs depicting income convergence rates, population growth rates, and housing value changes in the U.S. for various time periods in FIGURES 1, 2

8. `analyze/hcConverge.do` visualizes the extent of human capital convergence resulting from migration over time in the U.S. in FIGURE A2

9. `analyze/analysis.do` generate tables and figures with various interaction in TABLE 2, TABLE 3, FIGURE 7, FIGURE 8, APPENDIX TABLE 5

10. `analyze/nonhomothetic.do` visualize the connection between housing share of income and average income per adult, instrumented with education, for metropolitan areas in APPENDIX FIGURE 1 

11. `analyze/summary_stats.do` merges data from different sources to calculate and summarize the mean and standard deviation of the variables in Table 1

12. `analyze/compare_regulations.do` correlates various measures related to regional development by merging datasets and conducting a correlation analysis with additional variables for the year 1990 in Footnote 26

13. `analyze/revised_scalings.do` outputs the results of regression analyses in Appendix Table 6

***MICRO DATA ANALYSIS***

14. `build/borjas1940.do` processes individual and household data from the year 1940 to calculate indicators for skilled individuals, housing costs, migration rates, and nominal and real household income

15. `build/borjas1940robustness.do` processes and analyzes demographic and economic data for the year 1940

16. `build/borjas2000.do` processes and analyzes data related to migration and income for the year 2000. Note: This code is a little slow. It takes a little less than 5 minutes to run.

17. `build/borjas2000robustness.do` analyzes migration and household data for the year 2000, generating skill-specific income and migration statistics under various scenarios and populations. Note: This code is a little slow. It takes a little less than five minutes to run.

18. `build/price_file_prep.do` calculates demographic characteristics, average household income, and skill-related variables for different years  by state and birth state. It also computes housing costs, scaled income, and generates instrument variables for further analysis. Note: This code is slow. It takes more than five minutes to run.

19. `analyze/mig_returns_and_flows.do` generates various figures in figure 3, 4, 5, and appendix tables 3, and 4 relating to migration and income data, including scatter plots, regression results, and data manipulation, for different years (1940, 2000, etc.), skills (skilled and unskilled), and demographics, and exports the results to various file formats

***CSV files***
To replicate figures independently, every figure has a csv file with a title format "name_of_plot_fig_XXX.csv" in the out_final folder. For plots in Figures 1, 2, 3, 4, and 5, coefficients need to be constructed first, so make sure to run the code that does this before plotting. Stata automatically converts variable names to lowercase when importing a csv file. To change this, specify the case option by adding `, case(preserve)` in the import delimited command.
