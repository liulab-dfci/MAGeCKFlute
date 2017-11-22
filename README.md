# MAGeCKFlute
Integrative analysis pipeline for pooled CRISPR functional genetic screens

## Abstract
Genome-wide CRISPR (clustered regularly interspaced short palindrome repeats) coupled with nuclease Cas9 (CRISPR/Cas9) screens represent a promising technology to systematically evaluate gene functions. Data analysis for CRISPR/Cas9 screens is a critical process that includes identifying screen hits and exploring biological functions for these hits in downstream analysis. We have previously developed two algorithms, MAGeCK and MAGeCK-VISPR, to analyze CRISPR/Cas9 screen data in various scenarios. These two algorithms allow users to perform quality control, read count generation and normalization, and calculate beta score to evaluate gene selection performance. In downstream analysis, biological functional analysis is required for understanding biological functions of these identified genes with different screening purposes.

  Here, We developed MAGeCKFlute for supporting downstream analysis, utilizing the data provided through MAGeCK and MAGeCK-VISPR. MAGeCKFlute provides several strategies to remove potential biases within sgRNA-level read counts and gene-level beta scores. The downstream analysis with the package includes identifying essential, non-essential, and target-associated genes, and performing biological functional category analysis and pathway enrichment analysis of these genes. The package also visualizes genes in the context of pathways to benefit users exploring screening data. Collectively, MAGeCKFlute enables accurate identification of essential, non-essential, and targeted genes, as well as their related biological functions. 

## Install package MAGeCKFlute

~~~
source("http://bioconductor.org/biocLite.R")
biocLite("MAGeCKFlute")

#or (R >= 3.5)
install.packages("devtools")
library(devtools)
install_github("WubingZhang/MAGeCKFlute")

#or (R >= 3.4.2)
install.packages("devtools")
library(devtools)
install_bitbucket("WubingZhang/mageckflute")
~~~

## Quick start
Here we show the most basic steps for integrative analysis pipeline using `gene summary file`. Before using MAGeCKFlute, analysing CRISPR/Cas9 screen data using MAGeCK RRA (in MAGeCK [@Wei2014]) or MAGeCK MLE (in MAGeCK-VISPR [@Wei2015]) is neccessary, which result in the generation of the gene summary file. We will discuss gene summary file below in detail. 

To run MAGeCKFlute pipeline, we need gene summary file generated by running MAGeCK RRA or MAGeCK MLE.
MAGeCKFlute package provides two example data, one is `MLE_Data` and the other is `RRA_Data`. 
We will work with them in this document.

### Downstream analysis pipeline for MAGeCK MLE

~~~
##Load gene summary data in MAGeCK MLE results
data("MLE_Data")
##Run the downstream analysis pipeline for MAGeCK MLE
FluteMLE(MLE_Data, ctrlname=c("D7_R1", "D7_R2"), treatname=c("PLX7_R1","PLX7_R2"), prefix="BRAF", organism="hsa")

~~~

All pipeline results are written into local directory `./BRAF_Flute_Results/`, and all figures are integrated into file
 `BRAF_Flute.mle_summary.pdf`.

###Downstream analysis pipeline for MAGeCK RRA

~~~##Load gene summary data in MAGeCK RRA results
data("RRA_Data")
##Run the downstream analysis pipeline for MAGeCK RRA
FluteRRA(RRA_Data, prefix="BRAF", organism="hsa")
~~~

All pipeline results are written into local directory `./BRAF_Flute_Results/` too, and all figures are integrated into file  `BRAF_Flute.rra_summary.pdf`.

## Contacts

* Wubing Zhang (Watson5bZhang@gmail.com)
* Binbin Wang (wangbinbintj@gmail.com)
* Feizhen Wu
