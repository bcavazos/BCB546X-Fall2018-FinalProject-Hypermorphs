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


Tassel
I worked in Tassel with the file “GenotypeHapmap.txt”,to transfrom SNP calling (letters) on the file "GenotypeHapmap.txt and convert it to numeric (1= homozygotes major, 0= homo minor, o.5 hetero). I removed heterozygote markers. After this, i exported from Tassel in hapmap format into R.
 WORKING IN 'R'
 
 #ACCESSING THE FILE
 
 geno <- read.delim("GenotypeHapmap_patrick_numeric.txt", h=T, sep = "\t",stringsAsFactors = F, check.names = F, skip = 1, na.strings = NA)
 
 #TRANSFORMING INTO MATRIX
 
 geno <- as.matrix(geno)
 
 #size of matrix
 dim(geno)
 
 #RANDOMLY SELECTING 2000 MARKERS
 
 seed = 1
length(sample(2:dim(geno)[2],53103,replace=F))geno2 <- geno[,-sample(2:dim(geno)[2],53103,replace=F)]
dim(geno2)

 The new data now (geno 2), has just 2000 markers and 854 individuals
 
 #REPLACING NA WITH -9
 
 i = 2 
 j = 1
 for (i in i:dim(geno2)[2]){
j = 1
for (j in j:dim(geno2)[1]){
if (is.na(geno2[j,i] == TRUE)){
geno2[j,i] <- -9}}}

#THEN I ADDED ANOTHER COLUMN TO INDICATE THE FAMILY. I SCORED ALL IMDIVIDUALS AS 1.

geno2 <- cbind(geno2, 1)
dim(geno2)

#ORDERING COLUMNS

geno <- geno2[,c(1,2002,2:2001)]

#DUPLICATION OF FILES

geno_final <- geno

#Structure requires repetitions from a given individual based on the ploidy level. For example, since this is a dipolid species, I duplicated each of the inbred lines and ordered them by their name. By doing that,the file will have twice the numbers of individual in rows.

geno_final <- geno[rep(1:nrow(geno), times = 2), ]
geno_final <- geno_final[order(geno[,1]),]

#The name of the markers were complicated,which could pose a problem in structure.I replaced the markers names by SNP_1, SNP_2,..............

colnames(geno_final) <- c("","",paste("SNP", seq(1:2000), sep = "_"))

geno_final <- as.matrix(geno_final)

#Export from R into excel

write.table(teste2, "structure_duplicate.txt",
sep = " ", dec = ",", row.names = FALSE)

#Excel

Open the file "structure_duplicate.txt) and save it 

