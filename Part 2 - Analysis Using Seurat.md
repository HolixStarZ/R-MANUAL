# Analysis Using Seurat
We use [Seurat 4.0](https://satijalab.org/seurat/index.html) as a toolkit to help us anylse 10X genomics data. The following examples are going to use the sample data provided by 10X genomics. In this section, we are going to look at ```Read 10X sequencing data and change it into a seurat object```, ```QC and selecting cells for further analysis```, ```Feature selection```, ```Data modification```, and ```Visualization```.

## 2.1 Setup the Seurat Object
A few pacages have to be loaded before using the Seurat object, simply use the following commands in R:
```
library(dplyr)
library(Seurat)
library(patchwork)
library(ggplot2)
```
```(Seurat)``` is the main package we are using to analyse 10X data, ```(dplyr)``` and ```(patchwork)``` are packages that help with the functionality of the Seurat package, making functions viable in R, ```(ggplot2)``` is a package that creates publication ready graphs (which is very usful for us). 

Reading 10X genomics files requires the function ```Read10X_h5```, which is embedded inside the Seurat object. The ```Read10X_h5``` readed 10X CellRanger hdf5 file, allowing the creation of unique molecular identification (UMI) on the data. Each row represents the number of molecules for each feature (e.g. genes and features) and each column represents each individual cell. 

Loading the hdf5 file will result in the following codes:
``` 
setwd ("C:/Users/cleme/OneDrive/Desktop/BEL/scRNA-sec Workshop") #Setting up working directory
pbmc.data <- Read10X_h5("10k_PBMC.h5")
pbmc <- CreateSeuratObject(counts = pbmc.data, project = "pbmc10k", min.cells = 3, min.features = 200)
pbmc 
```
```
An object of class Seurat 
22432 features across 10813 samples within 1 assay 
Active assay: RNA (22432 features, 0 variable features)
``` 
A quick check of the formatting of the Seurat object, around 20,000 features and 10,000 cells, perfect data for analysis. If the file an output directly from the CellRanger workflow, use the command ```Read10X``` to read the file. 

## 2.2 Pre-Processing Workslow
