# VM_CKD_saezlab

Created by: Victoria Muckerson

This repo explores CKD datasets and attempts to classify different CKD by their molecular data.
Included in this analysis is, but not limited to, hierarchical clustering, differential
expression analysis, and signaling pathway impact analysis. 


**How to run**

The code should be run starting with Data_download_and_pca to obtain and visualize data from GEO, followed
by Clustering to attempt to cluster the data, then DEA, and finally Functional Analysis for SPIA.


The Data_download_and_pca code is built to be an executable file for well annotated microarray datasets.


When clustering the data:
The phenotypic data and gene expression data is used from the downloaded data obtained by the first script.
A pca is run again in this script albeit using only the most variable genes.


The differential expression analysis:
This script is performed using the phenotypic and gene expression data obtained from the downloaded data in
the first script. Limma is used to perform a DEA and the results are used in a matrix multiplication to produce
what I called a "disease score". The disease score is defined in the script and visualized via box plots.


Functional Analysis:
This script uses phenotypic, feature, and gene expression data obtained in the first script as well as the DEA
results produced in the DEA script. Using this data, SPIA is performed to obtain pathway impact information. This
information is then used with Progeny to predict pathway activities. SPIA is not the only input option for Progeny
and can therefore be skipped if another input option is preferable for the observed data.


The original datasets used to create this repo were GSE20602, GSE32591, GSE37460, and GSE47183. However, for
simplification and due to time sensitivity, the datasets used in the final draft of this code were changed to GSE104948,
GSE32591, and GSE37460 which include only glomerular data of which the diseases Lupus Nephropathy/Systemic Lupus
Erythematosus, IgA Nephropathy, and Hypertensive Nephropathy were used to compare to controls.


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
