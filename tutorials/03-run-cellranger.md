Cell Ranger performs several essential steps, including processing cell barcodes and unique molecular identifiers (UMIs), aligning sequencing reads to a reference transcriptome, assigning reads to genes, and counting unique RNA-derived molecules.

By the end of this tutorial, you will have executed a complete Cell Ranger count pipeline and generated the files required for downstream analysis.

Before jumping to run the cellranger, try some basic commands and change your working directory:

## Some basic commands
You can check your username by typing:
```
whoami
```
Expected output (for example):
```
roya
```
Check your current directory:
```
pwd
```
Expected output (for example):
```
/home/roya
```
List files and directories:
```
ls
```
A more detailed list:
```
ls -l
```
File sizes in a more readable format:
```
ls -lh
```
Check if cellranger is available:
```
cellranger --version
```
This should display the installed Cell Ranger version.

## Workshop directory structure
```
/data/
├── shared/
│   ├── fastq/
│   │   └── ... sequencing files
│   └── reference/
│       └── refdata-gex-GRCh38-2024-A/
└── work/
    ├── andreea/
    ├── annemarie/
    ├── bing/
    └── ... other students
```

 ### Input files
 https://www.10xgenomics.com/datasets/5k_Human_Donor1_PBMC_3p_gem-x 
 FASTQ files from the 10x Genomics 5k Human PBMC Donor 1 dataset (sequencing lane 1, L001).

* R1 — Read 1, containing cell barcode and UMI information.

* R2 — Read 2, containing the transcript-derived sequence.

* I1 and I2 — Index reads, depending on the sequencing configuration.


## Running Cell Ranger

1. Navigate to your own working directory:
   ```
   cd /data/work/$(whoami)
   ```
   


 Disconnect from the server

When you finish working, you can disconnect from the server.

Type:

exit

Alternatively, press Ctrl + D.

Your SSH connection will close, and you will return to the terminal on your personal computer.

Note: Disconnecting from the server does not delete your files. However, closing an SSH session while Cell Ranger is running in the foreground will generally interrupt the analysis. During the exercise, keep your terminal open until Cell Ranger finishes.
