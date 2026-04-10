# chipseq analysis tutorial
End-to-end ChIP-seq analysis pipeline for USF2 including alignment, peak calling, annotation, and visualization
##  Environment Setup & Verification

> ⚠️ Please complete this section before running the pipeline.

---

## Step 1: Create and activate environment

```bash
conda create -n homer_env python=3.10 -y
conda activate homer_env
```

## Step 2: Configure conda channels
```bash
conda config --env --add channels defaults
conda config --env --add channels bioconda
conda config --env --add channels conda-forge
conda config --env --set channel_priority strict
```
## Step 3: Install required tools
```bash
conda install -y wget samtools ucsc-bedgraphtobigwig ucsc-fetchchromsizes ucsc-bedtobigbed sra-tools trim-galore bedtools picard bwa deeptools
```
## Step 4: Create a directory for HOMER installation
```bash
mkdir -p $CONDA_PREFIX/homer
cd $CONDA_PREFIX/homer
```
## Step 5: Download the HOMER installation script
```bash
wget http://homer.ucsd.edu/homer/configureHomer.pl
```
## Step 6: Install HOMER with default settings
```bash
perl configureHomer.pl -install
```
## Step 7: Add HOMER executables to the PATH in this conda environment
```bash
echo 'export PATH=$CONDA_PREFIX/homer/bin:$PATH' >> $CONDA_PREFIX/etc/conda/activate.d/homer.sh
```
## Step 8: We deactivate + reactivate to reload environment so HOMER is added to PATH
```bash
conda deactivate
conda activate Env_Homer
```
## Step 9: Display all available reference genomes in HOMER
```bash
perl configureHomer.pl -list
```
## Step 10: Install human genome (hg38) for our analysis
```bash
perl configureHomer.pl -install hg38
```
 
