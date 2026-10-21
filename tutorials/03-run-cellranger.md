Cell Ranger performs several essential steps, including processing cell barcodes and unique molecular identifiers (UMIs), aligning sequencing reads to a reference transcriptome, assigning reads to genes, and counting unique RNA-derived molecules.

By the end of this tutorial, you will have executed a complete Cell Ranger count pipeline and generated the files required for downstream analysis.

Before jumping to run the cellranger, try some basic commands and change your working directory:

## Some basic commands
You can check your username by typing:
```bash
whoami
```
Expected output (for example):
```text
> roya
```
Check your current directory:
```bash
pwd
```
Expected output (for example):
```text
> /home/roya
```
List files and directories:
```bash
ls
```
A more detailed list:
```bash
ls -l
```
File sizes in a more readable format:
```bash
ls -lh
```
Check if cellranger is available:
```bash
cellranger --version
```
This should display the installed Cell Ranger version.

## Workshop directory structure
```text
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
 #### FASTQ files
 https://www.10xgenomics.com/datasets/5k_Human_Donor1_PBMC_3p_gem-x 
 FASTQ files from the 10x Genomics 5k Human PBMC Donor 1 dataset (sequencing lane 1, L001).

* R1 — Read 1, containing cell barcode and UMI information.

* R2 — Read 2, containing the transcript-derived sequence.

* I1 and I2 — Index reads, depending on the sequencing configuration.

#### Reference transcriptome
We will use the GRCh38 reference provided by 10x Genomics:
https://cf.10xgenomics.com/supp/cell-exp/refdata-gex-GRCh38-2024-A.tar.gz


## Running Cell Ranger

1. Navigate to your own working directory:
   ```bash
   cd /data/work/$(whoami)
   ```

2. Copy and paste the following command into your terminal:
   ```bash
   /usr/bin/time -v cellranger count \
    --id=PBMC5k_$(whoami) \
    --transcriptome=/data/shared/reference/refdata-gex-GRCh38-2024-A \
    --fastqs=/data/shared/fastq \
    --sample=5k_Human_Donor1_PBMC_3p_gem-x_GEX \
    --lanes=1 \
    --localcores=4 \
    --localmem=16 \
    --create-bam=false \
    --nosecondary
   ```
   Cell Ranger will begin processing the FASTQ files and display information about the different stages of the pipeline.

3. When Cell Ranger completes successfully, it prints a completion message and reports the location of the output files.

For example, you may see:
```text
> Pipestance completed successfully!
```
you may also see entries such as:
```text
> Elapsed (wall clock) time (h:mm:ss or m:ss): 33:02.41
User time (seconds): ...
System time (seconds): ...
Maximum resident set size (kbytes): ...
```
4. Check if the output is generated
   ```bash
   ls -lh
   ```
   You should see a directory similar to:
   ```text
   PBMC5k_roya/
   ```
   Enter the output directory:
   ```bash
   cd PBMC5k_$(whoami)
   ```
   And, list the contents:
   ```bash
   ls
   ```
   The main results are stored in the outs/ directory. Inspect it:
   ```bash
   ls -lh outs/
   ```
   Look for the following files:
   ```text
   > filtered_feature_bc_matrix/
   filtered_feature_bc_matrix.h5
   raw_feature_bc_matrix/
   raw_feature_bc_matrix.h5
   molecule_info.h5
   ```
   For our downstream analysis, we will primarily use:
   ```text
   > filtered_feature_bc_matrix.h5
   ```
5. Download the Cell Ranger output to your computer
   a. Open a new terminal on your computer, keep your existing SSH session open.
   b. In your local terminal, enter:
   ```bash
   scp YOUR_USERNAME@SERVER_IP:/data/work/YOUR_USERNAME/PBMC5k_YOUR_USERNAME/outs/filtered_feature_bc_matrix.h5 .
   ```
   
   

   


 Disconnect from the server

When you finish working, you can disconnect from the server.

Type:

exit

Alternatively, press Ctrl + D.

Your SSH connection will close, and you will return to the terminal on your personal computer.

Note: Disconnecting from the server does not delete your files. However, closing an SSH session while Cell Ranger is running in the foreground will generally interrupt the analysis. During the exercise, keep your terminal open until Cell Ranger finishes.
