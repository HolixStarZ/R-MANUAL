# Part 1: Fundamentals of scRNAseq and R Setup
## 1.1 Fundamentals of scRNAseq
This is section, we are going to look at common file types that are raw data coming out of scRNAseq. Different file types have different usages alonside with their own  advantages and disadvantages. Choosing the right file type can allow your data be processed quicker and easier, but more importantly, producing the appropreate graphs and diagrams for publication. Since this section will be a summary of all commonly seen file types, additional links will be provided if one wants to learn more about a certain file type and its usage. 

### 1.1.1 FASTQ file
FASTQ files are text-based format used for storing read sequences represented by single-letter codes that might appear as raw data from scRNAseq. 

### 1.1.2 Cell Ranger
Cell Ranger is a set of analysis pipelines that process Chromium single-cell data to align reads, generate feature-barcode matrices, perform clustering and other secondary analysis, and more. It help us to generate the RNA reads count matrix we will use later. A few important concepts:
- GEM WELL: also known as GEM GROUP are repetitioned cells from one single 10X genomics channel. One or more sequencing libraries can be derived from a GEM well. 
- Library: library types may include Gene Expression, Antibody Capture, CRISPR Guide Capture, TCR-enrichment, etc and are derrived from a single GEM well (or multiple libriaries from one well). Libraries features barcodes or V (D) J assays for analysis. 
- Sequencing Run (or Flowcell): A flowcell containing data from one sequencing instrument run.

#### File Outputs from Cell Ranger
Cell Ranger output files are contained in one single folder that has the ```outs``` folder. The ```outs``` folder overview shows the summary of all items from the 10X genomics analysis, ranging from sequencing data, the annotated read sequences, and gene expression matrices. Important files to look at are ```Matrices``` ```Web Summary .html``` ```Secondary Analysis CSV``` ```BAM``` ```Molecule Info (h5)``` ```Loupe File (.cloupe)```. 

Matrices are creations from the 10X because it does not only analyse transcriptome but also molecular, meaning ```Cell Associated Barcodes``` are also created 

### 1.1.3 Star Solo

### 1.1.4 Doublets




## 1.2 R Setup
The following packages are needed for the Seurat object to function:
```
setwd ("C:/Users/X") #You have to set your own working directory so save files are organised.

library(dplyr)
library(Seurat)
library(patchwork)
library(ggplot2)
```

To read any files from 10X, we use the ```Read10X_h5``` command to read the hdf5 files. If we want to read data using the output of the cellranger pipeline from 10X directly, we can use ```Read10X()```. The values in this matrix represent the number of molecules for each feature (i.e. gene; row) that are detected in each cell (column). It can be used to read both scATAC-seq and scRNA-seq matrices. We use this matrix to create the ```Seurat Object```. 

For this example, we are using the examplar files from the 10X website [LINK]
```
# Load the PBMC dataset
pbmc.data <- Read10X_h5("./data/10k_PBMC.h5")

# Initialize the Seurat object with the raw (non-normalized data).
pbmc <- CreateSeuratObject(counts = pbmc.data, project = "pbmc10k", min.cells = 3, min.features = 200)
pbmc
```
Reading the loaded enviroment should give the following codes:
```
An object of class Seurat 
22432 features across 10813 samples within 1 assay 
Active assay: RNA (22432 features, 0 variable features)
```

### 1.2.1 Standard of Workflow
Just like any other analytical proccesses, the workflow of using 10X data represents the selection and filtration of cells based on quality control metrics, data normalization and scaling, and the detection of highly variable features. This applies to all the RNA read count matrices we get from any ```Cell Ranger``` or ```STARsolo``` output. 

### 1.2.2 Quality Control and Selecting Viable Cells
There are a few catagories that we look for while conducting QC tests on 10X data:
- Percentage of unique genes detected in each cell
  - 
- Percentage of mitochondrial gene reads
