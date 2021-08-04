# Part 1: Fundamentals of scRNAseq and R Setup
## 1.1 Fundamentals of scRNAseq
This is section, we are going to look at common file types that are raw data coming out of scRNAseq. Different file types have different usages alonside with their own  advantages and disadvantages. Choosing the right file type can allow your data be processed quicker and easier, but more importantly, producing the appropreate graphs and diagrams for publication. Since this section will be a summary of all commonly seen file types, additional links will be provided if one wants to learn more about a certain file type and its usage. 

### 1.1.1 FASTQ file
FASTQ files are text-based format used for storing read sequences represented by single-letter codes that might appear as raw data from scRNAseq. 

### 1.1.2 Cell Ranger
Cell Ranger is a set of analysis pipelines that process Chromium single-cell data to align reads, generate feature-barcode matrices, perform clustering and other secondary analysis, and more. It help us to generate the RNA reads count matrix we will use later. A few important concepts:
- GEM WELL: also known as GEM GROUP are repetitioned cells from one single 10X genomics channel. One or more sequencing libraries can be derived from a GEM well. 
- Library: library types may include Gene Expression, Antibody Capture, CRISPR Guide Capture, TCR-enrichment, etc and are derrived from a single GEM well (or multiple libriaries from one well). Libraries features barcodes or V (D) J assays for analysis. 

### 1.1.3 Star Solo

### 1.1.4 Doublets




## 1.2 R Setup
