# 01 | Introduction: From Raw Sequencing Reads to Biological Insights

## Overview

Welcome to the hands-on section of the Single-Cell RNA-seq Analysis Workshop!

Single-cell RNA sequencing (scRNA-seq) allows us to study gene expression at the level of individual cells. Unlike bulk RNA-seq, which measures the average gene expression across a population of cells, scRNA-seq enables us to investigate cellular heterogeneity, identify distinct cell populations, and explore cell states and biological processes.

## Workflow
### Part I (Day 1) — Primary data processing

#### Raw sequencing data → Gene expression count matrix

This part includes:

1. Reading the sequencing data (FASTQ files).

2. Processing cell barcodes and UMIs.

3. Aligning sequencing reads to a reference transcriptome.

4. Assigning reads to genes and counting unique molecules.

5. Identifying cell-associated barcodes.

6. Generating a gene expression count matrix.

We will perform these steps using Cell Ranger, a software package developed by 10x Genomics.

### Part II (Day2) — Downstream analysis

#### Gene expression count matrix → Biological interpretation

This part typically includes:

1. Quality control and filtering.

2. Normalization.

3. Identification of highly variable genes.

4. Dimensionality reduction (PCA and UMAP).

5. Cell clustering.

6. Cell-type annotation.

7. Differential gene expression and biological interpretation.

We will explore these steps using Python and Scanpy in Google Colab.
