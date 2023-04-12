# celeste-tunicate-cells

This repo is dedicated to a bioinformatics project for Spring 2023 FISH 546 at SAFS. My version of this project will involve the replication of some aspects of BioProject [PRJNA579844](https://www.ncbi.nlm.nih.gov/bioproject/PRJNA579844) which has 90 RNAseq run files.

Briefly, colonial marine tunicates like *Botryllus schlosseri* are capable of both sexually reproducing through a single fertilized egg (embryogenesis) and through asexual reproduction where new generations are derived from somatic cells of the parental body (blastogenesis). In healthy *Botryllus schlosseri*, blastogenesis occurs as a weekly synchronized process. Transcriptomic data available from this project isolated RNA across several developmental stages of *Botryllus schlosseri* from the whole body.

Within this project I will evaluate two replicates for both early blastogenic stage b5 to b6 in the secondary bud and the takeover blastogenic stage in the adult zooid.

Within the code folder will be several Rmarkdown files titled with the corresponding week of the spring quarter containing captions and code chunks with weekly updates on progress of this project.

The data folder will remain empty on GitHub since much of the files necessary to the workflow exceed the 100 MB limit. However, the code will be able to access the following data files.

#Metadata for the four runs I will evaluate

| Run         	| Bases       	| BioProject  	| BioSample    	| Bytes      	| dev_stage 	| Experiment 	| Instrument  	| Isolate                         	| Organism             	| Platform 	| Sample Name                           	| SRA Study 	| TISSUE       	| REPLICATE 	|
|-------------	|-------------	|-------------	|--------------	|------------	|-----------	|------------	|-------------	|---------------------------------	|----------------------	|----------	|---------------------------------------	|-----------	|--------------	|-----------	|
| SRR10352205 	| 10576501436 	| PRJNA579844 	| SAMN13134439 	| 6996363570 	| b5-b6     	| SRX7061986 	| NextSeq 500 	| 5491b.2                         	| Botryllus schlosseri 	| ILLUMINA 	| HISeq-Sample_3411_IL2574-4            	| SRP227136 	| whole system 	|           	|
| SRR10352206 	| 3609019200  	| PRJNA579844 	| SAMN13134437 	| 1836994542 	| b5-b6     	| SRX7061984 	| NextSeq 500 	| 944a x BYd196.6-4.180 + 5869*-2 	| Botryllus schlosseri 	| ILLUMINA 	| 4017_944axbyd196_stageC1to2_SecBud    	| SRP227136 	| whole system 	|           	|
| SRR10352224 	| 4847587800  	| PRJNA579844 	| SAMN13134463 	| 2533047747 	| TO        	| SRX7061961 	| NextSeq 500 	| Sc109e.109                      	| Botryllus schlosseri 	| ILLUMINA 	| 3902_Sc109e_olds_zooid_D_early_mid_kp 	| SRP227136 	| whole system 	|           	|
| SRR10352254 	| 5482368900  	| PRJNA579844 	| SAMN13134462 	| 2984116333 	| TO        	| SRX7061960 	| NextSeq 500 	| Sc109e.113                      	| Botryllus schlosseri 	| ILLUMINA 	| 3890_Sc109e_old_zooid_D_mid_Late_kp   	| SRP227136 	| whole system 	|           	|


### Meta-metadata to describe column names metadata

| Column Name        | Description                                                                                                                                                                                                 |
|-------------|-----------------------------------------------------------|
| Run                | NCBI accession number for SRA run.                                                                                                                                                                          |
| assay_type         | Method used for assay.                                                                                                                                                                                      |
| Bases              | Number of nucleic acid bases sequenced for each run.                                                                                                                                                        |
| BioProject         | Accession number of whole NCBI project titled: Sequencing of Botryllus schlosseri developmental stages and tissues.                                                                                         |
| Bytes              | Size of information per run.                                                                                                                                                                                |
| datastore_filetype | Types of files produced per run.                                                                                                                                                                            |
| dev_stage          | The developmental stage at which RNA was sampled from organism. See [notebook post](https://valeste.github.io/2023-04-07-2023-04-07-Devo-Bsc/) to view cyclical stage development referenced in black text. |
| Instrument         | Instrument on which microarray was conducted.                                                                                                                                                               |
| LibraryLayout      | Type of sequencing conducted. Either paired-end or single-end sequencing.                                                                                                                                   |
| LibrarySource      | Source can either be proteomic, genomic, transcriptomic.                                                                                                                                                    |
| Organism           | Scientific name of organism from which sequence runs are derived.                                                                                                                                           |
| Platform           | Sequencing platform type.                                                                                                                                                                                   |
| tissue             | The tissue type relating to sequence run.                                                                                                                                                                   |
| replicate          | Identification of biological replicate.                                                                                                                                                                     |
