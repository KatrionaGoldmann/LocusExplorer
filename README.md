## PEAC Locus Explorer

This repo creates a shiny app to explore the PEAC QTL data. This was inspired by (and forked from) the Institute of Cancer Research's Oncogenetics team. Their code can be found on GitHub [here](https://github.com/oncogenetics/LocusExplorer). Below is their ReadMe input:

-----

## An interactive graphical illustration of genetic associations and their biological context.


<p>
<img src="www/Figure1_v07.jpeg" height="840px" width="700px">
</p>


### Disclaimer
LocusExplorer should be used for illustrative purposes only. Any results provided by LocusExplorer should be used with caution.

### Availability  
The source code and installation instructions for LocusExplorer are available at https://github.com/oncogenetics/LocusExplorer.

LocusExplorer is made available under the MIT license.

### Required Software
LocusExplorer runs in the R environment but is designed to be an easy to use interface that does not require familiarity with R as a prerequisite. LocusExplorer is platform agnostic and able to run on any operating system for which R is available.

LocusExplorer requires R version 3.2.2 to run and can be downloaded by following the instructions at [https://www.r-project.org/](https://www.r-project.org/). Some required packages are not available for earlier versions of R.

After installation of  the R software, R packages used by LocusExplorer must be installed prior to use. This may take a few minutes, but is only required on the first occasion. To install packages, open the R program, copy the following code into the R console and hit Return:





```R
#install CRAN packages, if missing
packages <- c("shiny","dplyr","tidyr","lazyeval","data.table","ggplot2","ggrepel","knitr","markdown","DT","lattice","acepack","cluster","DBI","colourpicker","igraph","visNetwork", "devtools")
if (length(setdiff(packages, rownames(installed.packages()))) > 0) {
  install.packages(setdiff(packages, rownames(installed.packages())), dependencies = TRUE)  
} else { print("All required CRAN packages installed")}

#install Bioconductor packages if missing
source("https://bioconductor.org/biocLite.R")
bioc <- c("ggbio","GenomicRanges","TxDb.Hsapiens.UCSC.hg19.knownGene","org.Hs.eg.db","rtracklayer")
if (length(setdiff(bioc, rownames(installed.packages()))) > 0) {
  biocLite(setdiff(bioc, rownames(installed.packages())))  
} else { print("All required Bioconductor packages installed")}

#install GitHub packages:
devtools::install_github("oncogenetics/oncofunco")
```
- In cases when user do not have admin rights, pop up window will prompt to set a personal library location for installation of packages, please click yes.
- If using R GUI then user might get prompted to choose CRAN mirror to use for package downloads, please choose the city nearer to your location.
- If prompted to "Update packages all/some/none [a/s/n]", type "n" and hit Return.


### Launch LocusExplorer
LocusExplorer runs through a web browser and uses an intuitive interface that does not require high level computational skills to operate.

#### 1. Using *runGitHub()* within RStudio

Open RStudio (start a new R session) copy the following code into the console and hit Return:
```R
library(shiny)  
runGitHub("LocusExplorer", "oncogenetics", launch.browser = TRUE)
```

#### 2. Using *Download as Zip* (Recommended)
Click on *Download as ZIP* button, this will download the repisotory locally as a zip file *LocusExplorer-master.zip*. Unzip the folder. Open *ui.R* file in RStudio (start a new R session) and click on *Run App* (Please ensure **Run External** option is selected for full functionality) button at top right corner, or run below code.

```R
library(shiny)  
runApp(launch.browser = TRUE)
```

### Cite LocusExplorer
**<a href="http://bioinformatics.oxfordjournals.org/content/early/2015/11/19/bioinformatics.btv690.abstract" target="_blank">LocusExplorer: a user-friendly tool for integrated visualisation of genetic association data and biological annotations</a>**   
Tokhir Dadaev<sup>1</sup>, Daniel A Leongamornlert<sup>1</sup>, Edward J Saunders<sup>1</sup>, Rosalind Eeles<sup>1,2</sup> , Zsofia Kote-Jarai<sup>1</sup>   


<sup>1</sup>Department of Genetics and Epidemiology, The Institute of Cancer Research, London, UK   
<sup>2</sup>Royal Marsden NHS Foundation Trust, London, UK

Bioinformatics first published online November 20, 2015 doi:10.1093/bioinformatics/btv690

#### Abstract
**Summary:** In this article we present LocusExplorer, a data visualisation and exploration tool for genetic association data. LocusExplorer is written in R using the Shiny library, providing access to powerful R-based functions through a simple user interface. LocusExplorer allows users to simultaneously display genetic, statistical and biological data for humans in a single image and allows dynamic zooming and customisation of the plot features. Publication quality plots may then be produced in a variety of file formats.  
**Availability and implementation:** LocusExplorer is open source and runs through R and a web browser. It is available at www.oncogenetics.icr.ac.uk/LocusExplorer/ or can be installed locally and the source code accessed from https://github.com/oncogenetics/LocusExplorer.

### Publications: LocusExplorer plots

* <a href="http://www.ncbi.nlm.nih.gov/pubmed/26025378" target="_blank">Multiple novel prostate cancer susceptibility signals identified by fine-mapping of known risk loci among Europeans.</a> Al Olama AA, *et al.*   
    + <a href="http://www.ncbi.nlm.nih.gov/pmc/articles/PMC4572072/figure/DDV203F1/" target="_blank">Figure 1</a>

* Accepted, not published yet:
    + Fine-mapping of Prostate Cancer Susceptibility Loci in a Large Meta-Analysis Identifies Candidate Causal Variants. Tokhir Dadaev, *et al.*    
    + Prostate cancer meta-analysis of more than 140,000 men identifies 63 novel prostate cancer susceptibility loci.  Fredrick R. Schumacher, *et al.*       
    + Germline Variation at 8q24 and Prostate Cancer Risk in Men of European Ancestry. Marco Matejcic, *et al.*    


### Frequently asked questions  
See [FAQ](https://github.com/oncogenetics/LocusExplorer/blob/master/Markdown/FAQ.md).

### Contact  
Questions, suggestions, and bug reports are welcome and appreciated.   
- Submit [suggestions and bug-reports](https://github.com/oncogenetics/LocusExplorer/issues)   
- Send [pull request](https://github.com/oncogenetics/LocusExplorer/pulls)   
- Contact email [T Dadaev](mailto: tokhir.dadaev@icr.ac.uk)   

### To-do List
https://github.com/oncogenetics/LocusExplorer/issues   

[![Issue Stats](http://issuestats.com/github/oncogenetics/LocusExplorer/badge/issue)](http://issuestats.com/github/oncogenetics/LocusExplorer)
[![Issue Stats](http://issuestats.com/github/oncogenetics/LocusExplorer/badge/pr)](http://issuestats.com/github/oncogenetics/LocusExplorer)
