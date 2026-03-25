## SNP Curation Workflow for MS Risk Variants
Summary statistics for the trait “multiple sclerosis” were downloaded from the GWAS Catalog (doi.org/10.1093/nar/gkae1070) on February, 2026. Because results included MS-like conditions like neuromyelitis optica, results were further filtered to include only the multiple sclerosis trait. SNPs meeting GWAS significance at p < 5e-8 were included. Our inclusion criteria for curating MS risk SNPs were studies that compared a group of MS patients to a cohort of healthy controls, and these studies are listed in Table S1. Therefore, studies that compared traits within the MS cohort (i.e., antibody status, drug response), and studies that compared MS to another trait (i.e. MS compared to cardiovascular disease or cancers) were excluded.  

### Annotation of LD-Expanded Variants
To nominate unique risk loci, the list of GWAS-nominated tag SNPs were LD-pruned using PLINK (doi.org/10.1086/519795) with a cutoff of R^2 > 0.8. These risk loci were then LD-expanded using PLINK and the 1000Genomes phase 3 database (doi.org/10.1038/nature15393). The expanded SNPs that were not given a rsID were labeled with one, if applicable, using UCSC SNP table dbSnp155 (doi.org/10.1093/nar/gky1048). Allele frequencies for tag and expanded SNPs were computed using PLINK and the 1000Genome phase 3 database. SNPs that were not found in this database were supplemented with information from the 1000Genomes 30X coverage database (doi.org/10.1016/j.cell.2022.08.004). Risk allele annotations were assigned based on whether the given risk allele corresponded to the major or minor allele. For example, if the risk allele of a tag variant is A which happens to be the major allele, the risk allele of the expanded variant is the major allele. In cases where the given risk allele did not correspond to either major or minor allele, the risk allele was manually cross checked with the original manuscript. Gene annotations for each SNP were obtained from SNPNexus (doi.org/10.1093/nar/gkaa420). 

### Libraries required:
library(readxl)
library(writexl)
library(dplyr)
library(openxlsx)
library(stringr)
library(chromoMap)
library(rtracklayer)
library(stringr)
library(readr)
library(tidyr)

Other requirements such as RELI are noted in the .qmd file. 