# VM_CKD_saezlab

Created by: Victoria Muckerson

This repo explores CKD datasets and attempts to classify different CKD by their molecular data.
Included in this analysis is, but not limited to, hierarchical clustering, differential
expression analysis, and signaling pathway impact analysis. 

**How to run**
The code should be run starting with Data_download_and_pca to obtain and visualize data from GEO, followed
by Clustering to attempt to cluster the data, then DEA, and finally Functional Analysis for SPIA.

The code is built to be an executable file for well annotated datasets that make use of two different
platforms. Therefore, when downloading the data:
To adjust for datasets with only one platform, comment out the objects ending in "2",
not including df12.
To use a different dataset GEO, simply replace the number in "(GEO = '')" in line 38
and change the respective file name when saving. 
The following libraries are required:
library(GEOquery)
library(qusage)
library(Biobase)
library(annotate)
library(hgu133a.db)
library(ggbiplot)
library(tidyverse)
library(Rtsne)

When clustering the data:
The phenotypic data and gene expression data is used from the downloaded data obtained by the first script.
The top 2000 most variable genes are used to cluster the data - in order to change the number of most variable
genes used, change the "2000" in lines 62-64 to the desired amount.
A pca is run again in this script albeit using only the most variable genes.
The following libraries are required:
library(cluster)
library(dbscan)
library(BiocManager)
library(mclust)
library(tidyverse)
library(ConsensusClusterPlus)
library(ALL)
library(dplyr)
library(ComplexHeatmap)
library(ggbiplot)

The differential expression analysis:
This script is performed using the phenotypic and gene expression data obtained from the downloaded data in
the first script. Limma is used to perform a DEA and the results are used in a matrix multiplication to produce
what I called a "disease score". The disease score is defined in the script and visualized via box plots.
The following libraries are required:
library(limma)
library(tidyverse)
library(BiocManager)

Functional Analysis:
This script uses phenotypic, feature, and gene expression data obtained in the first script as well as the DEA
results produced in the DEA script. Using this data, SPIA is performed to obtain pathway impact information. This
information is then used with Progeny to predict pathway activities. SPIA is not the only input option for Progeny
and can therefore be skipped if another input option is preferable for the observed data.
The following libraries are required:
library(msigdbr)
library(SPIA)
library(tidyverse)
library(dplyr)
library(plyr)
library(progeny)

The original datasets used to create this repo were GSE20602, GSE32591, GSE37460, and GSE47183. However, for
simplification and due to time sensitivity, the datasets used in the final draft of this code were changed to GSE104948,
GSE32591, and GSE37460 which include only glomerular data of which the diseases Lupus Nephropathy/Systemic Lupus
Erythematosus, IgA Nephropathy, and Hypertensive Nephropathy were used to compare to controls.
