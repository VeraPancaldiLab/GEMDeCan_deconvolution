# GEMDeCan
GEMDeCan: Gene Expression and Methylation based Deconvolution for Cancer 

## Welcome to the GEMDeCan repository.  
You will find here two snakemake pipelines to process and perform deconvolution on gene expression and methylation data, in the respectively named folders.  
Each pipeline comes with a readme detailing its installation and usage.

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

