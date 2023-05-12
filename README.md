# celeste-tunicate-devo

## [Project Compendium](https://rpubs.com/cvaldi/1040648)


### Objectives
The final objectives of this bioinformatics project is to conduct a differential gene expression analysis of transcriptomic data from two distinct blastogenic stages in the marine model tunicate *Botryllus schlosseri*. This will then be followed up with a functional enrichment analysis to extract biological meaning from significantly differently expressed genes.

### Summary of project
This repo is dedicated to a bioinformatics project for Spring 2023 FISH 546 at SAFS. My version of this project will involve the replication of some aspects of BioProject [PRJNA579844](https://www.ncbi.nlm.nih.gov/bioproject/PRJNA579844) which has 90 RNAseq run files.

Briefly, colonial marine tunicates like *Botryllus schlosseri* are capable of both sexually reproducing through a single fertilized egg (embryogenesis) and through asexual reproduction where new generations are derived from somatic cells of the parental body (blastogenesis). In healthy *Botryllus schlosseri*, blastogenesis occurs as a weekly synchronized process. Transcriptomic data available from this project isolated RNA across several developmental stages of *Botryllus schlosseri* from the whole body.

Within this project I will evaluate the whole transcriptome of an the early blastogenic stage b5 to b6 in the secondary bud and the late takeover blastogenic stage in the adult zooid.

Within the code folder will be several Rmarkdown files titled with the corresponding week of the spring quarter containing captions and code chunks with weekly updates on progress of this project.

The data folder will remain empty on GitHub since much of the files necessary to the workflow exceed the 100 MB limit. However, the code will be able to access the following data files.

### Metadata for the four runs I will evaluate

| Run         | Bases       | BioProject  | Bytes      | dev_stage | Instrument  | Isolate                          | Organism             | Platform | Sample Name                            | TISSUE       |
|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| SRR10352205 | 10576501436 | PRJNA579844 | 6996363570 | b5-b6     | NextSeq 500 | 5491b.2                          | Botryllus schlosseri | ILLUMINA | HISeq-Sample_3411_IL2574-4             | whole system |
| SRR10352206 | 3609019200  | PRJNA579844 | 1836994542 | b5-b6     | NextSeq 500 | 944a x BYd196.6-4.180 + 5869\*-2 | Botryllus schlosseri | ILLUMINA | 4017_944axbyd196_stageC1to2_SecBud     | whole system |
| SRR10352224 | 4847587800  | PRJNA579844 | 2533047747 | TO        | NextSeq 500 | Sc109e.109                       | Botryllus schlosseri | ILLUMINA | 3902_Sc109e_olds_zooid_D\_early_mid_kp | whole system |
| SRR10352254 | 5482368900  | PRJNA579844 | 2984116333 | TO        | NextSeq 500 | Sc109e.113                       | Botryllus schlosseri | ILLUMINA | 3890_Sc109e_old_zooid_D\_mid_Late_kp   | whole system |

### Meta-metadata to describe column names of metadata

| Column Name | Description                                                                                                                                                                                                 |
|-------------|-----------------------------------------------------------|
| Run         | NCBI accession number for SRA run.                                                                                                                                                                          |
| Bases       | Number of nucleic acid bases sequenced for each run.                                                                                                                                                        |
| BioProject  | Accession number of whole NCBI project titled: Sequencing of Botryllus schlosseri developmental stages and tissues.                                                                                         |
| Bytes       | Size of information per run.                                                                                                                                                                                |
| dev_stage   | The developmental stage at which RNA was sampled from organism. See [notebook post](https://valeste.github.io/2023-04-07-Devo-Bsc/) to view cyclical stage development referenced in black text. |
| Instrument  | Instrument on which microarray was conducted.                                                                                                                                                               |
| Organism    | Scientific name of organism from which sequence runs are derived.                                                                                                                                           |
| Platform    | Sequencing platform type.                                                                                                                                                                                   |
| SampleName  |  The name given to the sample from which the sequence read is derived. I retained this to verify that they were isolated from different animals.                                                            |
| tissue      | The tissue type relating to sequence run.                                                                                                                                                                   |

### Checksums

Below are the checksums generated in file 1 of 2 (week-02-accessing-data.Rmd) for each fastq file downloaded for this project.

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

