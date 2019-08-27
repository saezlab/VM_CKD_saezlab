# VM_CKD_saezlab

Created by: Victoria Muckerson
            victoria.muckerson@gmail.com

This repo explores microarray datasets containing chronic kidney disease (CKD) samples and attempts to separate
and identify CKDs from healthy control samples and other CKDs by their molecular data. The desired separation is attempted
via hierarchical clustering of the gene expression matrix and the most variable genes for each data set.
Differential expression analysis (DEA) is used to obtain these most variable genes and identify potential disease
signature genes while pathway analysis is used to attempt to define diseases by their pathway representation and
pathway activities. 



## How to run

The original datasets used to create this repo are listed in the .tsv file [DATASETS_LIST_Vic's](https://github.com/saezlab/VM_CKD_saezlab/blob/master/DATASETS_LIST%20_Vic's.tsv). However, for
simplification purposes, the datasets used in the final draft of this code were limited to [GSE104948](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE104948), [GSE32591](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE32591), and [GSE37460](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi) which include only glomerular data of which the diseases Lupus Nephropathy/Systemic Lupus Erythematosus, IgA Nephropathy, and Hypertensive Nephropathy were used in addition to control samples.
Original R files for these Rmds can be found [here](https://github.com/vmuckerson/Chronic_kidney_disease).


The code should be run starting with [Data_download_and_pca](https://github.com/saezlab/VM_CKD_saezlab/blob/master/Data_download_and_pca.Rmd) to obtain and visualize data from GEO, followed
by [Clustering](https://github.com/saezlab/VM_CKD_saezlab/blob/master/Clustering.Rmd) to attempt to cluster the data, then [DEA](https://github.com/saezlab/VM_CKD_saezlab/blob/master/DEA.Rmd) via [Limma](https://bioconductor.org/packages/release/bioc/html/limma.html), and finally [Functional_Analysis](https://github.com/saezlab/VM_CKD_saezlab/blob/master/Functional_Analysis.Rmd) for signal
pathway impact analysis ([SPIA](http://bioconductor.org/packages/release/bioc/html/SPIA.html)) and pathway activity prediction via [Progeny](http://bioconductor.org/packages/release/bioc/html/progeny.html).



#### Data Importation

The [Data_download_and_pca](https://github.com/saezlab/VM_CKD_saezlab/blob/master/Data_download_and_pca.Rmd) code is built to be an executable file for well annotated microarray datasets.



#### Clustering

The phenotypic data and gene expression data is used from the downloaded data obtained by the first script.
A `pca` is run again in this script albeit using only the most variable genes.



#### DEA

This script uses the phenotypic and gene expression data obtained from the downloaded data in
the first script. [Limma](https://bioconductor.org/packages/release/bioc/html/limma.html) is used to perform `DEA` and the resulting t scores in combination with the expression
matrix of each dataset (for the disease of interest and control samples) are used to create a linear model
using matrix multiplication to produce what is refered to as a "disease score". The disease score illustrates
the degree of similarity between differentially expressed genes from different datasets of the same disease and
is visualized via box plots.



#### Functional Analysis

This script uses phenotypic, feature, and gene expression data obtained in the first script as well as the `DEA`
results produced in the [DEA](https://github.com/saezlab/VM_CKD_saezlab/blob/master/DEA.Rmd) script. Using this data, `SPIA` is performed to obtain pathway impact information. This
information is then used with `Progeny` to predict pathway activities. `SPIA` is not the only input option for `Progeny`
and can therefore be skipped if another input option is preferable for the observed data.




#### Dependencies:

- ALL
- annotate
- Biobase
- BiocManager
- cluster
- ComplexHeatmap
- ConsensusClusterPlus
- dbscan
- GEOquery
- ggbiplot
- hgu133a.db
- limma
- mclust
- msigdbr
- progeny
- qusage
- Rtsne
- SPIA
- tidyverse
