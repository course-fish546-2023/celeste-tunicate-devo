# Differential Gene Expression Analysis of two Distinct Asexual Stages in a Marine Tunicate

[![DOI](https://zenodo.org/badge/621994954.svg)](https://zenodo.org/badge/latestdoi/621994954)

### View [Project Compendium](https://rpubs.com/cvaldi/1040648) page to see whole workflow in one place.

### Objectives

The final objective for this project was to conduct a differential gene expression analysis of transcriptomic data from two distinct blastogenic stages in the marine model tunicate *Botryllus schlosseri*. This will then be followed up with a functional enrichment analysis to extract biological meaning from significantly differently expressed genes.

### Summary of project

This repo is dedicated to a bioinformatics project for Spring 2023 FISH 546 at SAFS. My version of this project will involve the replication of some aspects of BioProject [PRJNA579844](https://www.ncbi.nlm.nih.gov/bioproject/PRJNA579844) which has 90 RNAseq run files.

Briefly, colonial marine tunicates like *Botryllus schlosseri* are capable of both sexually reproducing through a single fertilized egg (embryogenesis) and through asexual reproduction where new generations are derived from somatic cells of the parental body (blastogenesis). In healthy *Botryllus schlosseri*, blastogenesis occurs as a weekly synchronized process. Transcriptomic data available from this project isolated RNA across several developmental stages of *Botryllus schlosseri* from the whole body.

Within this project I will evaluate the whole transcriptome of an the early blastogenic stage b5 to b6 in the secondary bud and the late takeover blastogenic stage in the adult zooid.

![TO vs b5-b6](https://github.com/valeste/valeste.github.io/blob/master/assets/img/sex_asex_devo_TO_b5.jpeg?raw=true)

### Metadata

| Run         | Bases       | dev_stage | Isolate                          | Organism             | Tissue       |
|-------|-------|-------|-------|-------|-------|
| SRR10352205 | 10576501436 | b5-b6     | 5491b.2                          | Botryllus schlosseri | whole system |
| SRR10352206 | 3609019200  | b5-b6     | 944a x BYd196.6-4.180 + 5869\*-2 | Botryllus schlosseri | whole system |
| SRR10352224 | 4847587800  | TO        | Sc109e.109                       | Botryllus schlosseri | whole system |
| SRR10352254 | 5482368900  | TO        | Sc109e.113                       | Botryllus schlosseri | whole system |

### Meta-metadata to describe above column names

| Column Name | Description                                                                                                                                                                                      |
|----------------|--------------------------------------------------------|
| Run         | NCBI accession number for SRA run.                                                                                                                                                               |
| Bases       | Number of nucleic acid bases sequenced for each run.                                                                                                                                             |
| dev_stage   | The developmental stage at which RNA was sampled from organism. See [notebook post](https://valeste.github.io/2023-04-07-Devo-Bsc/) to view cyclical stage development referenced in black text. |
| Organism    | Scientific name of organism from which sequence runs are derived.                                                                                                                                |
| tissue      | The tissue type relating to sequence run.                                                                                                                                                        |

### Checksums

Below are the checksums generated for each fastq file downloaded for this project.

| Checksum                         | fastq files         |
|----------------------------------|---------------------|
| 509022c6a21cdd5bf0f5066f9b9c346c | SRR10352205_1.fastq |
| 473b2a1e27fbe5ffed8003a00e48a684 | SRR10352205_2.fastq |
| afd3278c40c120e00dc8b2d109afd6b6 | SRR10352206_1.fastq |
| d895814f5a2238e9bb02767354c59b11 | SRR10352206_2.fastq |
| c5a9b8ee11c148374eab253bb5a31d61 | SRR10352224_1.fastq |
| 0822524636d5771899451bdff467f11a | SRR10352224_2.fastq |
| d021331125fe3f3b36ed00395b2521bb | SRR10352254_1.fastq |
| a6f10754f23cb7d0e07e5371aacc0c16 | SRR10352254_2.fastq |
