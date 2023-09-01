# GEMDeCan
GEMDeCan: Gene Expression and Methylation based Deconvolution for Cancer 


## Welcome to the GEMDeCan repository.  
You will find here two snakemake pipelines to process and perform deconvolution on gene expression and methylation data, in the respectively named folders.  
Each pipeline comes with a readme detailing its installation and usage.


## Introduction
This computational pipeline takes as input BCL or FASTQ files of RNA-seq reads, performs trimming, quantification and deconvolution with the following softwares :
![](./assets/pipeline.png)



## Installation
Snakemake allows for a very efficient and user friendly way of using pipelines. It is designed so all you need to install is _mamba_ which is required to install Snakemake

Note that officially only Linux is supported for this pipeline. This also requires an Internet connection in order to use _mamba_ auto-generated environments for all necessary software and packages.

Mamba
* [Linux](https://github.com/mamba-org/mamba)
`curl -L -O "https://github.com/conda-forge/miniforge/releases/latest/download/Mambaforge-$(uname)-$(uname -m).sh"`
`bash Mambaforge-$(uname)-$(uname -m).sh`

Snakemake
* [Linux](https://snakemake.readthedocs.io/en/stable/getting_started/installation.html)
`conda activate base`
`mamba install snakemake -n base -c conda-forge -c bioconda`

## Dependencies
All dependencies are automatically installed by snakemake using the .yaml configuration files in Tools. So the user does not need to configure the conda environments as it is done within the pipeline.

## Configure your workspace
The snakefile shouldn't be modified. A provided `config.yaml` file takes as input all needed directories and files.

### General informations
 * **Output directory** : directory for all outputs. If you have multiple dataset, make one for each dataset.
 * **Input** : directory where your RNASeq data are located (`.fastq` or `.bcl`). If using only deconvolution, the path to your quantification matrix file (tab-separated TPM values). Note that your .fastq files should end with "R1" and "R2" to be properly processed by the pipeline.
 * **Threads** : number of threads allowed for each job.
 * 
### Deconvolution
 * **Signatures** : Path to folder containing signatures to use for the deconvolution




## Data availability
The code to reproduce all figures is available in this repository under `Paper_Figure_code.Rmd`.  
All data to reproduce those figures are freely available on Figshare :  
https://figshare.com/account/home#/projects/134069

## Citation 
To cite the pipeline, refer to our paper on [BiorXiv](https://www.biorxiv.org/content/10.1101/2021.04.09.439207v2) :  
**GEM-DeCan: Improved tumor immune microenvironment profiling through novel gene expression and DNA methylation signatures predicts immunotherapy response**  
Ting Xie, Jacobo Solorzano, Miguel Madrid-Mencía, Abdelmounim Essabbar, Julien Pernet, Mei-Shiue Kuo, Alexis Hucteau, Alexis Coullomb, Nina Verstraete, Olivier Delfour, Francisco Cruzalegui,  Vera Pancaldi 
bioRxiv 2021.04.09.439207; doi: https://doi.org/10.1101/2021.04.09.439207


### Included databases:
~~~
  - all_TCGA
  - Melanoma_GSE72056_not_metastatic # Single cell RNA-seq analysis of melanoma Tirosh
  - Melanoma_GSE93722 #RNA-seq from lymph node bulk samples from 4 melanoma patients.
  - Silico_1700
  - MultipleMyeloma
  - GSE1070112 # RNA-Seq profiling of 29 immune cell types and peripheral blood mononuclear cells
~~~
### Signatures:
~~~
- LM22 - Fig2ab-NSCLC_PBMCs_scRNAseq_sigmatrix - scRNA-Seq_melanoma_Tirosh_sigmatrix_SuppFig_3-b - sigmatrix_HNSCC_Fig2cd
~~~

# Linux packages:
~~~
sudo apt-get install zlib1g-dev

sudo apt-get install libpng-dev
~~~


# R packages to install
~~~
install.packages(c("remotes", "devtools", "dplyr", "tidyr", "readr", "stringr", "magrittr", "purrr", 'BiocManager'))
install.packages('devtools')
BiocManager::install(c("EpiDISH", "DeconRNASeq"))
devtools::install_github("ebecht/MCPcounter",ref="master", subdir="Source")
remotes::install_github("icbi-lab/immunedeconv")
devtools::install_github('dviraran/xCell')
~~~

### if `argparse` is missing
Install https://github.com/trevorld/r-argparse 
~~~
remotes::install_github("trevorld/r-argparse")
~~~


# How to run the pipeline (sudo/root permissions are mandatory)
`sudo snakemake --cores 8 all`

# CIBERSORTX
CIBERSORTx is included in the deconvolution methods in the GEMDeCaN pipeline, but it's not run by default as it's not an open-source program. 

To run it, please create a file named `credentials.txt` with your username and password on separate lines to activate this option.

```{r}
MAIL: username123@email.com
TOKEN: token_passowrd123
```


## Output files

### Deconvolution
* **deconvolution.txt** : results of deconvolution : a table of cell type per sample.
* An HTML summary report of the deconvolution results.

