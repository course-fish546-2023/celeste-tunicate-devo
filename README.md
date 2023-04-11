# celeste-tunicate-cells

This repo is dedicated to a bioinformatics project for Spring 2023 FISH 546. My version of this project will involve the replication of some aspects of the following research paper [Kowarsky et al., 2021](https://doi.org/10.1016/j.celrep.2020.108681) which produced 90 RNAseq data files.

Briefly, colonial marine tunicates like *Botryllus schlosseri* are capable of both sexually reproducing through a single fertilized egg (embryogenesis) and through asexual reproduction where new generations are derived from somatic cells of the parental body (blastogenesis). In healthy *Botryllus schlosseri*, blastogenesis occurs as a weekly synchronized process. Transcriptomic data available from this project isolated RNA from several stages during embryogenesis and blastogenesis of *Botryllus schlosseri* from either the whole system (meaning the whole animal), ampullae (vasculature system), testis, or nervous system.

Within the code folder will be several Rmarkdown files titled with the corresponding week of the spring quarter containing captions and code chunks with weekly updates on progress of this project.

The data folder will remain empty on GitHub since much of the files necessary to the workflow exceed the 100 MB limit. However, the code will be able to access the following data files.

### Metadata regarding all 90 RNAseq runs produced in [Kowarsky et al., 2021](https://doi.org/10.1016/j.celrep.2020.108681) project

| Run         | Bases       | BioProject  | BioSample    | dev_stage   | Experiment | Isolate                          | Library Name                                                                                                                       | LibraryLayout | LibrarySource  | Organism             | version | Sample Name                                                                                                                        | SRA Study | TISSUE       | REPLICATE              |
|-------------|-------------|-------------|--------------|-------------|------------|----------------------------------|------------------------------------------------------------------------------------------------------------------------------------|---------------|----------------|----------------------|---------|------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|------------------------|
| SRR10352197 | 3968168400  | PRJNA579844 | SAMN13134449 | B3-B3/b3-b4 | SRX7061997 | 6176\*a                          | Sample_4178_6176_a\_primary_secondary_bud_stage_B1_approx6months_naive                                                             | PAIRED        | TRANSCRIPTOMIC | Botryllus schlosseri | 1       | Sample_4178_6176_a\_primary_secondary_bud_stage_B1_approx6months_naive                                                             | SRP227136 | whole system |                        |
| SRR10352198 | 15242160271 | PRJNA579844 | SAMN13134447 | B1-B2/b1-b2 | SRX7061995 | Sc109e.7                         | HISeq-Sample_sc109e_bud_stage_a\_IL2381-10                                                                                         | PAIRED        | TRANSCRIPTOMIC | Botryllus schlosseri | 1       | HISeq-Sample_sc109e_bud_stage_a\_IL2381-10                                                                                         | SRP227136 | whole system | biological replicate 3 |
| SRR10352199 | 270825748   | PRJNA579844 | SAMN13134445 | B1-B2/b1-b2 | SRX7061993 | Sc109e.7                         | A1M1B-Sample_sc109e_bud_stage_a\_IL2381-10                                                                                         | PAIRED        | TRANSCRIPTOMIC | Botryllus schlosseri | 1       | A1M1B-Sample_sc109e_bud_stage_a\_IL2381-10                                                                                         | SRP227136 | whole system | biological replicate 1 |
| SRR10352200 | 4613439000  | PRJNA579844 | SAMN13134443 | B1-B2/b1-b2 | SRX7061991 | 6089e                            | Sample_4111_2\_6089_e\_primary_bud_1PrimaryBud_stageA2_naive_young_2weeks                                                          | PAIRED        | TRANSCRIPTOMIC | Botryllus schlosseri | 1       | Sample_4111_2\_6089_e\_primary_bud_1PrimaryBud_stageA2_naive_young_2weeks                                                          | SRP227136 | whole system | Replicate 1            |
| SRR10352201 | 4973585100  | PRJNA579844 | SAMN13134441 | B to B      | SRX7061989 | Sc109e.109                       | 3900_Sc109e_Sec_bud_D\_early_mid_kp                                                                                                | PAIRED        | TRANSCRIPTOMIC | Botryllus schlosseri | 1       | 3900_Sc109e_Sec_bud_D\_early_mid_kp                                                                                                | SRP227136 | whole system |                        |
| SRR10352203 | 354155692   | PRJNA579844 | SAMN13134446 | B1-B2/b1-b2 | SRX7061994 | Sc109e.7                         | A1L34-Sample_sc109e_bud_stage_a\_IL2381-10                                                                                         | PAIRED        | TRANSCRIPTOMIC | Botryllus schlosseri | 1       | A1L34-Sample_sc109e_bud_stage_a\_IL2381-10                                                                                         | SRP227136 | whole system | biological replicate 2 |
| SRR10352204 | 5727627300  | PRJNA579844 | SAMN13134459 | A3-A4       | SRX7061947 | 5432b.1                          | 2372_5432b1_zooid_naive_stageAtoB                                                                                                  | PAIRED        | TRANSCRIPTOMIC | Botryllus schlosseri | 1       | 2372_5432b1_zooid_naive_stageAtoB                                                                                                  | SRP227136 | whole system |                        |
| SRR10352205 | 10576501436 | PRJNA579844 | SAMN13134439 | b5-b6       | SRX7061986 | 5491b.2                          | HISeq-Sample_3411_IL2574-4                                                                                                         | PAIRED        | TRANSCRIPTOMIC | Botryllus schlosseri | 1       | HISeq-Sample_3411_IL2574-4                                                                                                         | SRP227136 | whole system |                        |
| SRR10352206 | 3609019200  | PRJNA579844 | SAMN13134437 | b5-b6       | SRX7061984 | 944a x BYd196.6-4.180 + 5869\*-2 | 4017_944axbyd196_stageC1to2_SecBud                                                                                                 | PAIRED        | TRANSCRIPTOMIC | Botryllus schlosseri | 1       | 4017_944axbyd196_stageC1to2_SecBud                                                                                                 | SRP227136 | whole system |                        |
| SRR10352224 | 4847587800  | PRJNA579844 | SAMN13134463 | TO          | SRX7061961 | Sc109e.109                       | 3902_Sc109e_olds_zooid_D\_early_mid_kp                                                                                             | PAIRED        | TRANSCRIPTOMIC | Botryllus schlosseri | 1       | 3902_Sc109e_olds_zooid_D\_early_mid_kp                                                                                             | SRP227136 | whole system |                        |
| SRR10352225 | 2931478500  | PRJNA579844 | SAMN13134461 | A5-A6       | SRX7061959 | Sc109e. 7 (? Vs. 5491b.3)        | 3396_Sc109e.7_zooid_stage-C                                                                                                        | PAIRED        | TRANSCRIPTOMIC | Botryllus schlosseri | 1       | 3396_Sc109e.7_zooid_stage-C                                                                                                        | SRP227136 | whole system |                        |
| SRR10352234 | 3991726200  | PRJNA579844 | SAMN13134460 | A5-A6       | SRX7061948 | 5423b.1                          | 2375_5423b1_zooidsremains_naive_stageC1                                                                                            | PAIRED        | TRANSCRIPTOMIC | Botryllus schlosseri | 1       | 2375_5423b1_zooidsremains_naive_stageC1                                                                                            | SRP227136 | whole system |                        |
| SRR10352235 | 11618802246 | PRJNA579844 | SAMN13134458 | A1-A2       | SRX7061946 | L11HMBY15 x Sc6a-b-40.1          | HISeq-Sample_3435_IL2578-12                                                                                                        | PAIRED        | TRANSCRIPTOMIC | Botryllus schlosseri | 1       | HISeq-Sample_3435_IL2578-12                                                                                                        | SRP227136 | whole system |                        |
| SRR10352236 | 423034200   | PRJNA579844 | SAMN13134456 | B to A      | SRX7061944 | 944axBYd196.6-4.231              | Sample_4145_944axBYd196_6\_4_231_primary_bud_5primaryBud_stageD_midLate_old_14years_naive                                          | PAIRED        | TRANSCRIPTOMIC | Botryllus schlosseri | 1       | Sample_4145_944axBYd196_6\_4_231_primary_bud_5primaryBud_stageD_midLate_old_14years_naive                                          | SRP227136 | whole system |                        |
| SRR10352237 | 2960909100  | PRJNA579844 | SAMN13134455 | B to A      | SRX7061943 | 6105b                            | Sample_4190_6150b_primary_bud_primaryBud_stageD_early_gonads_naive_approx6months                                                   | PAIRED        | TRANSCRIPTOMIC | Botryllus schlosseri | 1       | Sample_4190_6150b_primary_bud_primaryBud_stageD_early_gonads_naive_approx6months                                                   | SRP227136 | whole system |                        |
| SRR10352238 | 5223888600  | PRJNA579844 | SAMN13134454 | B5-B6       | SRX7061942 | 6208t                            | Sample_4184_6208t_primary_bud_stageC2_possibleTestesInBuds_approx6months_naive                                                     | PAIRED        | TRANSCRIPTOMIC | Botryllus schlosseri | 1       | Sample_4184_6208t_primary_bud_stageC2_possibleTestesInBuds_approx6months_naive                                                     | SRP227136 | whole system |                        |
| SRR10352239 | 2825441700  | PRJNA579844 | SAMN13134451 | B3-B3/b3-b4 | SRX7061941 | 5869 settlement slide-3          | 4041_5869settelmentslide_Primaryandsecbud_stageB1                                                                                  | PAIRED        | TRANSCRIPTOMIC | Botryllus schlosseri | 1       | 4041_5869settelmentslide_Primaryandsecbud_stageB1                                                                                  | SRP227136 | whole system |                        |
| SRR10352240 | 2566845900  | PRJNA579844 | SAMN13134453 | B5-B6       | SRX7061940 | 6101b                            | Sample_4193_6106b_primary_bud_2primaryBud_stageC_C1C2_gonads_naive_approx6months                                                   | PAIRED        | TRANSCRIPTOMIC | Botryllus schlosseri | 1       | Sample_4193_6106b_primary_bud_2primaryBud_stageC_C1C2_gonads_naive_approx6months                                                   | SRP227136 | whole system |                        |
| SRR10352244 | 2967522000  | PRJNA579844 | SAMN13134452 | B3-B3/b3-b4 | SRX7061939 | 944axBYd196.6-4.227              | Sample_4129_944axBYd196_6\_4_227_primary_secondary_bud_7primaryAndsecondaryBud_stageB_old_14years_naive                            | PAIRED        | TRANSCRIPTOMIC | Botryllus schlosseri | 1       | Sample_4129_944axBYd196_6\_4_227_primary_secondary_bud_7primaryAndsecondaryBud_stageB_old_14years_naive                            | SRP227136 | whole system |                        |
| SRR10352245 | 2220981600  | PRJNA579844 | SAMN13134457 | A1-A2       | SRX7061945 | Sc109e.109                       | 3868_Sc109e_zooid_buds_intestine_A2_kp                                                                                             | PAIRED        | TRANSCRIPTOMIC | Botryllus schlosseri | 1       | 3868_Sc109e_zooid_buds_intestine_A2_kp                                                                                             | SRP227136 | whole system |                        |
| SRR10352246 | 1853648400  | PRJNA579844 | SAMN13134436 | b5-b6       | SRX7061937 | 6348\*                           | Sample_4355_6348_Settlement_Slide_secondary_bud_4\_secondary_bud_stage_C1_C2_naive_121016_sampled\_\_N383Barcode_P80_G8_S78_R1_001 | PAIRED        | TRANSCRIPTOMIC | Botryllus schlosseri | 1       | Sample_4355_6348_Settlement_Slide_secondary_bud_4\_secondary_bud_stage_C1_C2_naive_121016_sampled\_\_N383Barcode_P80_G8_S78_R1_001 | SRP227136 | whole system | Replicate 2            |
| SRR10352247 | 291467700   | PRJNA579844 | SAMN13134435 | b5-b6       | SRX7061936 | 6348\*                           | Sample_4355_6348_Settlement_Slide_secondary_bud_4\_secondary_bud_stage_C1_C2_naive_121016_sampled\_\_N383Barcode_P39_D3_S38_R1_001 | PAIRED        | TRANSCRIPTOMIC | Botryllus schlosseri | 1       | Sample_4355_6348_Settlement_Slide_secondary_bud_4\_secondary_bud_stage_C1_C2_naive_121016_sampled\_\_N383Barcode_P39_D3_S38_R1_001 | SRP227136 | whole system | Replicate 1            |
| SRR10352251 | 3688220400  | PRJNA579844 | SAMN13134438 | b5-b6       | SRX7061985 | 5869 settlement slide-5          | 4033_5869setelmentslide_stageC2_4secondarybuds                                                                                     | PAIRED        | TRANSCRIPTOMIC | Botryllus schlosseri | 1       | 4033_5869setelmentslide_stageC2_4secondarybuds                                                                                     | SRP227136 | whole system |                        |
| SRR10352252 | 6056760300  | PRJNA579844 | SAMN13134440 | B to B      | SRX7061987 | Sc109e.113                       | 3887_Sc109e_Sec_Bud_D\_mid_late_kp                                                                                                 | PAIRED        | TRANSCRIPTOMIC | Botryllus schlosseri | 1       | 3887_Sc109e_Sec_Bud_D\_mid_late_kp                                                                                                 | SRP227136 | whole system |                        |
| SRR10352254 | 5482368900  | PRJNA579844 | SAMN13134462 | TO          | SRX7061960 | Sc109e.113                       | 3890_Sc109e_old_zooid_D\_mid_Late_kp                                                                                               | PAIRED        | TRANSCRIPTOMIC | Botryllus schlosseri | 1       | 3890_Sc109e_old_zooid_D\_mid_Late_kp                                                                                               | SRP227136 | whole system |                        |
| SRR10352257 | 66618600    | PRJNA579844 | SAMN13134444 | B1-B2/b1-b2 | SRX7061992 | 6089e                            | Sample_4111_4\_6089_e\_primary_bud_1PrimaryBud_stageA2_naive_young_2weeks                                                          | PAIRED        | TRANSCRIPTOMIC | Botryllus schlosseri | 1       | Sample_4111_4\_6089_e\_primary_bud_1PrimaryBud_stageA2_naive_young_2weeks                                                          | SRP227136 | whole system | Replicate 2            |
| SRR10352258 | 3829989600  | PRJNA579844 | SAMN13134450 | B3-B3/b3-b4 | SRX7061998 | 6208b.2                          | Sample_4171_6208b_2\_primary_secondary_bud_stageB_B1B2_approx5months_naive                                                         | PAIRED        | TRANSCRIPTOMIC | Botryllus schlosseri | 1       | Sample_4171_6208b_2\_primary_secondary_bud_stageB_B1B2_approx5months_naive                                                         | SRP227136 | whole system |                        |
| SRR10352273 | 10676450834 | PRJNA579844 | SAMN13134448 | B1-B2/b1-b2 | SRX7061996 | L11HMBY15 x Sc6a-b-40.1          | HISeq-Sample_3434_IL2577-7                                                                                                         | PAIRED        | TRANSCRIPTOMIC | Botryllus schlosseri | 1       | HISeq-Sample_3434_IL2577-7                                                                                                         | SRP227136 | whole system |                        |
| SRR10352277 | 11893113900 | PRJNA579844 | SAMN13134442 | B to B      | SRX7061990 | 944axBYd196.6-4.231              | Sample_4144_944axBYd196_6\_4_231_secondary_bud_5secondaryBud_stageD_midLate_old_14years_naive                                      | PAIRED        | TRANSCRIPTOMIC | Botryllus schlosseri | 1       | Sample_4144_944axBYd196_6\_4_231_secondary_bud_5secondaryBud_stageD_midLate_old_14years_naive                                      | SRP227136 | whole system |                        |

### Meta-metadata to describe column names metadata

| Column Name        | Description                                                                                                                                                                                                 |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
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
