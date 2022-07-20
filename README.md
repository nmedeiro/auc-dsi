# auc-dsi
TIER Protocol example for AUC-DSI workshop
README - Midlife Crisis
 Ingo Rohlfing
 2021-07-02

Folder structure and files
This is the README file for all material on the R Markdown implementation of the Midlife Crisis project. The material is organized into three folders. The README file is on the top level of folder structure.
Note on working directories When the master script master.R is executed, the working directory needs to be set to the folder ScriptsAndReports hosting master.R.
When individual .Rmd files are knitted or selected code chunks are executed, the .Rmd file quietly uses the working directory hosting the file in the background and does not change the working directory.
Information about files and folders:
•	README.Rmd: README file for entire project (this one)
•	README.rtf: README file as rtf produced with README.Rmd
•	Data: Stores data prepared for analysis in three subfolders
–	InputData: Stores original raw data
•	original-wdi.xlsx: Original WDI country data
•	original-pew.sav: Original PEW survey data
–	TempData: Stores intermediate data for further processing
•	pew_processed.rds
•	wdi_processed.rds
–	AnalysisData: Stores data produced in the analysis
•	country_level.rds: Data for country-level analysis
•	individual_level.rds: Data for individual-level analysis
•	Output: Stores all output exported by analysis scripts
–	Tables are stored in Word and LaTeX format to be included in Word and LaTeX papers
•	ScriptsAndReports: Stores all scripts and codebook
–	master.R: Master script executing all other scripts.
–	data_processing.Rmd:
•	Loads data from InputData
•	Stores data in TempData and AnalysisData
–	data_processing.html: R Markdown html report for data_processing.Rmd
–	data_analysis.Rmd:
•	Loads data from AnalysisData
•	Stores output (figures, tables) in ScriptsAndResults
•	data_analysis.html: R Markdown html report for data_analysis.Rmd
–	data_paper.Rmd: File for producing a paper with tables and figures and no code.
–	data_paper.PDF: PDF produced with data_paper.Rmd
Reproduction parameters
The system parameters and package versions for knitr and rmarkdown (used for all scripts) at the last execution of the script (rSys.time()`):
•	platform: x86_64-w64-mingw32
•	R version: R version 4.0.3 (2020-10-10)
•	RStudio: 1.4.1106
•	knitr: 1.30
•	rmarkdown: 2.7
Package versions used in scripts
If you want to use the same versions of the packages that are loaded with the library() commands, you first need the devtools package (we used 2.3.2 & 2.4.0). With this package, one can install older versions from CRAN. The current versions of the packages, if they have been installed before, will be replaced if the specified versions are installed in the R library.
For information on the version of all packages that devtools includes in the session_info(), see the html-reports of the Rmd-scripts.
data_processing.Rmd:
install_version("dplyr", version = "1.0.5", 
                repos = "http://cran.us.r-project.org")
install_version("rio", version = "0.5.26", 
                repos = "http://cran.us.r-project.org")
install_version("tidyr", version = "1.1.2", 
                repos = "http://cran.us.r-project.org")
data_analysis.Rmd
install_version("dplyr", version = "1.0.5", 
                repos = "http://cran.us.r-project.org")
install_version("formattable", version = "0.2.0.1", 
                repos = "http://cran.us.r-project.org")
install_version("ggplot2", version = "3.3.2", # 3.3.3 works too
                repos = "http://cran.us.r-project.org")
install_version("lfe", version = "2.8-6", 
                repos = "http://cran.us.r-project.org")
install_version("sjPlot", version = "2.8.7", 
                repos = "http://cran.us.r-project.org")
install_version("texreg", version = "1.37.5", 
                repos = "http://cran.us.r-project.org")
install_version("xtable", version = "1.8-4", 
                repos = "http://cran.us.r-project.org")
data_appendix.Rmd
install_version("dplyr", version = "1.0.5", 
                repos = "http://cran.us.r-project.org")
install_version("formattable", version = "0.2.0.1", 
                repos = "http://cran.us.r-project.org")
install_version("ggplot2", version = "3.3.2", # 3.3.3 works too
                repos = "http://cran.us.r-project.org")
data_paper.Rmd
install_version("dplyr", version = "1.0.5", 
                repos = "http://cran.us.r-project.org")
install_version("formattable", version = "0.2.0.1", 
                repos = "http://cran.us.r-project.org")
install_version("ggplot2", version = "3.3.2",  # 3.3.3 works too
                repos = "http://cran.us.r-project.org")
install_version("knitr", version = "1.30", 
                repos = "http://cran.us.r-project.org")
install_version("lfe", version = "2.8-6", 
                repos = "http://cran.us.r-project.org")
install_version("sjPlot", version = "2.8.7", 
                repos = "http://cran.us.r-project.org")
install_version("texreg", version = "1.37.5", 
                repos = "http://cran.us.r-project.org")
All session parameters from last execution of script.
## - Session info ------------------------------------------------------------------------------------------
##  setting  value                       
##  version  R version 4.0.3 (2020-10-10)
##  os       Windows 10 x64              
##  system   x86_64, mingw32             
##  ui       RStudio                     
##  language (EN)                        
##  collate  German_Germany.1252         
##  ctype    German_Germany.1252         
##  tz       Europe/Berlin               
##  date     2021-07-02                  
## 
## - Packages ----------------------------------------------------------------------------------------------
##  package      * version date       lib source        
##  assertthat     0.2.1   2019-03-21 [1] CRAN (R 4.0.0)
##  backports      1.1.10  2020-09-15 [1] CRAN (R 4.0.2)
##  bayestestR     0.8.0   2020-12-05 [1] CRAN (R 4.0.3)
##  boot           1.3-25  2020-04-26 [2] CRAN (R 4.0.3)
##  broom          0.7.6   2021-04-05 [1] CRAN (R 4.0.5)
##  callr          3.6.0   2021-03-28 [1] CRAN (R 4.0.4)
##  cli            2.3.1   2021-02-23 [1] CRAN (R 4.0.4)
##  coda           0.19-4  2020-09-30 [1] CRAN (R 4.0.2)
##  colorspace     1.4-1   2019-03-18 [1] CRAN (R 4.0.0)
##  crayon         1.4.1   2021-02-08 [1] CRAN (R 4.0.4)
##  DBI            1.1.0   2019-12-15 [1] CRAN (R 4.0.0)
##  desc           1.2.0   2018-05-01 [1] CRAN (R 4.0.0)
##  devtools     * 2.3.2   2020-09-18 [1] CRAN (R 4.0.2)
##  digest         0.6.27  2020-10-24 [1] CRAN (R 4.0.4)
##  dplyr        * 1.0.5   2021-03-05 [1] CRAN (R 4.0.5)
##  effectsize     0.4.3   2021-01-18 [1] CRAN (R 4.0.3)
##  ellipsis       0.3.1   2020-05-15 [1] CRAN (R 4.0.0)
##  emmeans        1.5.3   2020-12-09 [1] CRAN (R 4.0.3)
##  estimability   1.3     2018-02-11 [1] CRAN (R 4.0.3)
##  evaluate       0.14    2019-05-28 [1] CRAN (R 4.0.0)
##  fansi          0.4.1   2020-01-08 [1] CRAN (R 4.0.0)
##  farver         2.0.3   2020-01-16 [1] CRAN (R 4.0.0)
##  formattable  * 0.2.0.1 2016-08-05 [1] CRAN (R 4.0.0)
##  Formula        1.2-3   2018-05-03 [1] CRAN (R 4.0.0)
##  fs             1.4.2   2020-06-30 [1] CRAN (R 4.0.2)
##  generics       0.0.2   2018-11-29 [1] CRAN (R 4.0.0)
##  ggeffects      1.0.1   2020-12-14 [1] CRAN (R 4.0.3)
##  ggplot2      * 3.3.3   2020-12-30 [1] CRAN (R 4.0.5)
##  glue           1.4.2   2020-08-27 [1] CRAN (R 4.0.2)
##  gtable         0.3.0   2019-03-25 [1] CRAN (R 4.0.0)
##  highr          0.8     2019-03-20 [1] CRAN (R 4.0.0)
##  htmltools      0.5.0   2020-06-16 [1] CRAN (R 4.0.2)
##  htmlwidgets    1.5.3   2020-12-10 [1] CRAN (R 4.0.4)
##  httr           1.4.2   2020-07-20 [1] CRAN (R 4.0.2)
##  insight        0.12.0  2021-01-14 [1] CRAN (R 4.0.3)
##  jsonlite       1.7.2   2020-12-09 [1] CRAN (R 4.0.5)
##  knitr          1.30    2020-09-22 [1] CRAN (R 4.0.2)
##  labeling       0.3     2014-08-23 [1] CRAN (R 4.0.0)
##  lattice        0.20-41 2020-04-02 [2] CRAN (R 4.0.3)
##  lfe          * 2.8-6   2021-01-11 [1] CRAN (R 4.0.3)
##  lifecycle      1.0.0   2021-02-15 [1] CRAN (R 4.0.5)
##  lme4           1.1-23  2020-04-07 [1] CRAN (R 4.0.2)
##  magrittr       2.0.1   2020-11-17 [1] CRAN (R 4.0.5)
##  MASS           7.3-53  2020-09-09 [2] CRAN (R 4.0.3)
##  Matrix       * 1.2-18  2019-11-27 [2] CRAN (R 4.0.3)
##  memoise        1.1.0   2017-04-21 [1] CRAN (R 4.0.0)
##  minqa          1.2.4   2014-10-09 [1] CRAN (R 4.0.2)
##  modelr         0.1.8   2020-05-19 [1] CRAN (R 4.0.3)
##  munsell        0.5.0   2018-06-12 [1] CRAN (R 4.0.0)
##  mvtnorm        1.1-1   2020-06-09 [1] CRAN (R 4.0.0)
##  nlme           3.1-149 2020-08-23 [2] CRAN (R 4.0.3)
##  nloptr         1.2.2.2 2020-07-02 [1] CRAN (R 4.0.2)
##  parameters     0.11.0  2021-01-15 [1] CRAN (R 4.0.3)
##  performance    0.6.1   2020-12-09 [1] CRAN (R 4.0.3)
##  pillar         1.4.6   2020-07-10 [1] CRAN (R 4.0.2)
##  pkgbuild       1.1.0   2020-07-13 [1] CRAN (R 4.0.2)
##  pkgconfig      2.0.3   2019-09-22 [1] CRAN (R 4.0.0)
##  pkgload        1.1.0   2020-05-29 [1] CRAN (R 4.0.0)
##  prettyunits    1.1.1   2020-01-24 [1] CRAN (R 4.0.0)
##  processx       3.5.1   2021-04-04 [1] CRAN (R 4.0.5)
##  ps             1.6.0   2021-02-28 [1] CRAN (R 4.0.5)
##  purrr          0.3.4   2020-04-17 [1] CRAN (R 4.0.0)
##  R6             2.4.1   2019-11-12 [1] CRAN (R 4.0.0)
##  Rcpp           1.0.4.6 2020-04-09 [1] CRAN (R 4.0.0)
##  remotes        2.3.0   2021-04-01 [1] CRAN (R 4.0.5)
##  rlang          0.4.10  2020-12-30 [1] CRAN (R 4.0.4)
##  rmarkdown      2.7     2021-02-19 [1] CRAN (R 4.0.3)
##  rprojroot      1.3-2   2018-01-03 [1] CRAN (R 4.0.0)
##  rsconnect      0.8.16  2019-12-13 [1] CRAN (R 4.0.2)
##  rstudioapi     0.11    2020-02-07 [1] CRAN (R 4.0.0)
##  sandwich       2.5-1   2019-04-06 [1] CRAN (R 4.0.0)
##  scales         1.1.1   2020-05-11 [1] CRAN (R 4.0.0)
##  sessioninfo    1.1.1   2018-11-05 [1] CRAN (R 4.0.0)
##  sjlabelled     1.1.7   2020-09-24 [1] CRAN (R 4.0.2)
##  sjmisc         2.8.5   2020-05-28 [1] CRAN (R 4.0.2)
##  sjPlot       * 2.8.7   2021-01-10 [1] CRAN (R 4.0.3)
##  sjstats        0.18.1  2021-01-09 [1] CRAN (R 4.0.3)
##  statmod        1.4.35  2020-10-19 [1] CRAN (R 4.0.3)
##  stringi        1.5.3   2020-09-09 [1] CRAN (R 4.0.3)
##  stringr        1.4.0   2019-02-10 [1] CRAN (R 4.0.0)
##  testthat       3.0.2   2021-02-14 [1] CRAN (R 4.0.5)
##  texreg       * 1.37.5  2020-06-18 [1] CRAN (R 4.0.2)
##  tibble         3.0.4   2020-10-12 [1] CRAN (R 4.0.3)
##  tidyr          1.1.2   2020-08-27 [1] CRAN (R 4.0.3)
##  tidyselect     1.1.0   2020-05-11 [1] CRAN (R 4.0.0)
##  usethis      * 1.6.3   2020-09-17 [1] CRAN (R 4.0.2)
##  utf8           1.1.4   2018-05-24 [1] CRAN (R 4.0.0)
##  vctrs          0.3.6   2020-12-17 [1] CRAN (R 4.0.4)
##  withr          2.3.0   2020-09-22 [1] CRAN (R 4.0.2)
##  xfun           0.22    2021-03-11 [1] CRAN (R 4.0.5)
##  xtable       * 1.8-4   2019-04-21 [1] CRAN (R 4.0.0)
##  yaml           2.2.1   2020-02-01 [1] CRAN (R 4.0.2)
##  zoo            1.8-8   2020-05-02 [1] CRAN (R 4.0.0)
## 
## [1] C:/Users/Ingo R/Documents/R/win-library/4.0
## [2] C:/Program Files/R/R-4.0.3/library
