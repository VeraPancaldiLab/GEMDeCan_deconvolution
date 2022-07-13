### Results: update 24 May 2022
Data can be found here 
~~~
 CRCT21/Mounim/deconvolution/Mai 2022
~~~

### Included databases:
~~~
Hugo - Krieg - Auslander - Cloughesy - GSE107011 - Gide - LUAD_RNAseq_TPM - Liu - Melanoma_GSE72056_no_malighant - Melanoma_GSE93722 - Riaz - Silico_1700 - Snyder - Thomas_RNAseq_part - all_TCGA - Maha - IP_TPM - PDAC_data_TPM
~~~
### Signatures:
~~~
- LM22 - Fig2ab-NSCLC_PBMCs_scRNAseq_sigmatrix - scRNA-Seq_melanoma_Tirosh_sigmatrix_SuppFig_3-b - sigmatrix_HNSCC_Fig2cd
~~~

# Linux packages
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

# From where take the generated CIBERSORTx signatures
`results/cibersortx_signatures`
And add them to the EpiDISH and DeconRNASeq explained in the next section

# Where to add more signatures to EpiDISH and DeconRNASeq
`scripts/deconvolution/signatures`

# Where to find the inputs folder
`/mnt/SERVER-CRCT-STORAGE/CRCT21/Private/Miguel/GEMDeCan/inputs`

# Where to find the credentials.txt file
`/mnt/SERVER-CRCT-STORAGE/CRCT21/Private/Miguel/GEMDeCan/credentials.txt`

# Where to find the final tables
`results/all_deconvolutions`
