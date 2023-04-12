# celeste-tunicate-cells

This repo is dedicated to a bioinformatics project for Spring 2023 FISH 546. My version of this project will involve the replication of some aspects of the following BioProject https://github.com/course-fish546-2023/celeste-tunicate-devo90 files.

Briefly, colonial marine tunicates like *Botryllus schlosseri* are capable of both sexually reproducing through a single fertilized egg (embryogenesis) and through asexual reproduction where new generations are derived from somatic cells of the parental body (blastogenesis). In healthy *Botryllus schlosseri*, blastogenesis occurs as a weekly synchronized process. Transcriptomic data available from this project isolated RNA across several developmental stages of *Botryllus schlosseri* from the whole body.

I will be evaluate early blastogenic stage b5 to b6 in the secondary bud and the takeover blastogenic stage in the adult zooid.

Within the code folder will be several Rmarkdown files titled with the corresponding week of the spring quarter containing captions and code chunks with weekly updates on progress of this project.

The data folder will remain empty on GitHub since much of the files necessary to the workflow exceed the 100 MB limit. However, the code will be able to access the following data files.



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
