# Technical Document - Multiclass Cancer Classification using Gene Expression Data

## Executive Summary

Advances in high-throughput sequencing have enabled the profiling of microRNAs (miRNAs), resulting in an abundance of sequencing data that if leveraged properly has the potential for cancer classification. Previously, the diagnosis of complex diseases such as cancer has involved relying on non-molecular criteria such as the stage of cancer, tumor type (primary, metastasized, malignant, benign), and other pathological features. However, with advancements in sequencing technology and lowered sequencing costs, there is great interest in the scientific community to use genetic expression profiles to develop a more robust method of diagnosing a cancer patient with a higher degree of accuracy than standard pathology practices alone. 

By collating the expression data of a panel of miRNAs from thousands of samples derived from various cancer patients, we can apply deep learning techniques to discern patterns in expression data that otherwise could not be done feasibly from one sequencing experiment alone. 

## Part 1: Problem Statement

Can a deep learning model in conjunction with miRNA expression data be trained to accurately classify multiple cancer types? 

## Part 2: Raw Data Acquisition

The [NCI GDC data portal](https://portal.gdc.cancer.gov/repository) provides an interface to obtain biological data. We will be using microRNA (miRNA) expression quantification data derived from sequencing experiments. 

For the purposes of building a tumor diagnosis classifier, we will obtain data about several different cancers from the The Cancer Genome Atlas (TCGA) consortium via the NCI GDC data portal. 

- TCGA-BRCA
- TCGA-LUAD
- TCGA-KIRC
- TCGA-UCEC
- TCGA-HNSC
- TCGA-LGG

Using the interface, in the Cases tab, select the TCGA program and the above projects in the Project section. In the Files tab, select Transcriptome profiling in the Data Category section, and miRNA expression quantification in the Data type section. This should return a list of 4,068 txt files. Add all the files to the cart. Go to cart and select the manifest option upon pressing the download button. The manifest is a txt file containing the file id numbers of the selected files and will be used in conjuction with the GDC's Data Transfer Tool to download the files selected. 

Download the [Data Transfer Tool](https://gdc.cancer.gov/access-data/gdc-data-transfer-tool) by downloading the appropriate binary distribution for your machine, unzipping it, and copying it over to a location that's in the user's PATH variable in the terminal. Follow the DTT's command line [documentation](https://docs.gdc.cancer.gov/Data_Transfer_Tool/Users_Guide/Data_Download_and_Upload/) to download data using the manifest file. 

Create a directory to house the data dump and run the following command to download the data.

! gdc-client download -m gdc_manifest_20190204_230647.txt

## Part 3: Data Mining

In order to construct a working dataset from the datafiles obtained from the GDC repository, we need to extract each the miRNA expression data from each file and assemble it into a working dataset with its associated tumor classification. In our case, we will be using the Project ID as assigned by TCGA to denote the cancer classification as the Project ID represents data that's derived from the respective cancer type. 

For our purposes, let $(x_{i}, y_{i})^{n}_{i = 1}$ be a collection of n observations, where $x_{i}$ is a vector consisting of the expression levels of $m$ genes for the $i$-th observation, and $y_{i}$ is the class label or tumor type of the $i$-th observation, $i = 1, ..., n$.

Put simply, the rows should be the samples with the columns as the miRNA. The values of the matrix represent the expression level of a given miRNA in a given sample. Each sample would have its associated tumor diagnosis.

Later, in the modeling phase, the tumor type will be the target value to predict based on the gene expression data.

## Part 4: Classification modeling



## Part 5: Model Evaluation and Insights





## Part 6: Future Directions


