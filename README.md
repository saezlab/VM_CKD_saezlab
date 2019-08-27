# VM_CKD_saezlab

Created by: Victoria Muckerson

This repo explores microarray datasets containing chronic kidney disease (CKD) samples and attempts to separate
and identify CKDs from healthy control samples and other CKDs by their molecular data. Separation is attempted
via hierarchical clustering of the gene expression matrix and the most variable genes for each data set,
differential expression analysis is used to obtain these most variable genes and identify potential disease
signature genes, and pathway analysis is used to attempt to define diseases by their pathway representation and
pathway activities. 


**How to run**

The code should be run starting with Data_download_and_pca to obtain and visualize data from GEO, followed
by Clustering to attempt to cluster the data, then DEA via Limma, and finally Functional Analysis for SPIA and
pathway activity prediction via Progeny.


The Data_download_and_pca code is built to be an executable file for well annotated microarray datasets.


When clustering the data:
The phenotypic data and gene expression data is used from the downloaded data obtained by the first script.
A pca is run again in this script albeit using only the most variable genes.


The differential expression analysis:
This script uses the phenotypic and gene expression data obtained from the downloaded data in
the first script. Limma is used to perform DEA and the resulting t scores in combination with the expression
matrix of each dataset (for the disease of interest and control samples) are used to create a linear model
using matrix multiplication to produce what is refered to as a "disease score". The disease score illustrates
the degree of similarity between differentially expressed genes from different datasets of the same disease and
is visualized via box plots.


Functional Analysis:
This script uses phenotypic, feature, and gene expression data obtained in the first script as well as the DEA
results produced in the DEA script. Using this data, SPIA is performed to obtain pathway impact information. This
information is then used with Progeny to predict pathway activities. SPIA is not the only input option for Progeny
and can therefore be skipped if another input option is preferable for the observed data.


The original datasets used to create this repo were GSE20602, GSE32591, GSE37460, and GSE47183. However, for
simplification and due to time sensitivity, the datasets used in the final draft of this code were changed to
GSE104948, GSE32591, and GSE37460 which include only glomerular data of which the diseases Lupus Nephropathy/Systemic
Lupus Erythematosus, IgA Nephropathy, and Hypertensive Nephropathy were used to compare to controls.


Dependencies:

- GEOquery
- qusage
- Biobase
- annotate
- hgu133a.db
- ggbiplot
- tidyverse
- Rtsne
- msigdbr
- SPIA
- dplyr
- plyr
- progeny
- cluster
- dbscan
- BiocManager
- mclust
- ConsensusClusterPlus
- ALL
- ComplexHeatmap
- limma
