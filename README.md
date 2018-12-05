# BCB546X-Fall2018-FinalProject
Final Project Presentation can be found here: https://docs.google.com/presentation/d/1Zhym3RUuCn06fQulqfDDNMcJ4lr2ww_iJKD8QkOl9WI/edit?usp=sharing

Contents in the directory:

* `data` is a folder containing all data needed to reproduce the results. The original files provided by Chen et al in the supplementary material, found here http://www.g3journal.org/content/6/12/3803.supplemental. Those are put in a subfolder called `raw_data`. Items within the raw data folder include the following: 
  * phenotype data - `BLUE-Pheno.txt` 
  * genotype data - `GenotypeHapmap.txt`
  * Population data formatted for ICIMapping software:
    * `POP1.csv` 
    * `POP2.csv`
    * `POP3.csv`
    * `POP4.csv`
  * Population data formatted for R/QTL script:
    * `ChenPop1.csv`
    * `ChenPop2.csv`
    * `ChenPop3.csv`
    * `ChenPop4.csv` 		 
* Our `scripts` folder has individual markdown files we used to reproduce different parts of the analysis in Chen et al. 2016. Inside it includes:
  * `Association mapping filtering attempt + Figure1`
  * `formatting for structure`
  * `PCA_ggplot`
  * `R-QTL_Chen_Fusarium`
* `software_output` is a folder that contains extra images and/or detail of software used to re-run any part of the analysis. It includes
  * `NJ tree`
  * `PCA results using Tassel with plots made in r`
* `Chen-etal-2016.md` introduces original paper, explains technical details of replication of analyses and summarizes replication of original results

Member Contributions - 

​	JJ: Ran QTL Mapping in R and IciMapv3.2, recreated Table 5

​	TM: Recreated Fig. 1, Used Tassel and R to run PCA

​	PM: STRUCTURE analysis

​	KN: Introduction and intro/ methods in presentation, bulk of Chen-et-al 2016.md

​	BC: Initial Data inspection and formatting using R and Unix, formatting repository
