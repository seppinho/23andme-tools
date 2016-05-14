# 23andMe Tools - Convert your 23andMe genotypes to VCF files

This repository provides a Java implementation to convert 23andMe genotype data into compressed VCFs (vcf.gz). VCF files can be useful for **imputation** with the [Michigan Imputation Server](https://imputationserver.sph.umich.edu) or for **mitochondrial haplogroup classification** with [HaploGrep](http://haplogrep.uibk.ac.at).

## Download your data
Your personal genome can be downloaded from [here](https://www.23andme.com/you/download). After entering your secure answer, the complete dataset can be downloaded at once.

## Generate VCF files
VCF files are generated by combining information from your 23andMe genotype data with a fasta reference file. The current version of the 23andMe genotyping chip v4 (> Nov 2013) uses the GRCh37 reference (aka g1k, v37) ```human_g1k_v37.fasta```. Each chromosome (chr1-22,X,Y,MT) is written to a seperate vcf.gz file.

```bash
git clone https://github.com/seppinho/23andme-tools.git
cd 23andme-tools
mvn install
java -jar vcf-tools-0.1.jar vcf-generator --genome <your-genome.txt> --ref <human_g1k_v37.fasta> --chromosomes <set of chromosomes> --out <vcf-destination-folder>

```
The human_g1k_v37.fasta reference is not included in this repository but can be downloaded like this:

```bash
wget ftp://ftp.1000genomes.ebi.ac.uk/vol1/ftp/technical/reference/human_g1k_v37.fasta.gz
wget ftp://ftp.1000genomes.ebi.ac.uk/vol1/ftp/technical/reference/human_g1k_v37.fasta.fai
gunzip human_g1k_v37.fasta.gz
```
