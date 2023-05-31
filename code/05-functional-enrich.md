# Functional Enrichment Overview

Currently, this portion of the workflow is a work in progress as of
05/09/2023.

Functional enrichment analysis is a valuable tool to interpret the
results of differential gene expression analysis by identifying the
biological processes, molecular functions, and pathways that are
overrepresented among a set of differentially expressed genes. The
general steps to do a functional enrichment analysis:

1.  Select a functional annotation database: There are several databases
    available that provide functional annotations for genes, such as
    Gene Ontology (GO), KEGG, Reactome, and others. Choose the database
    that best fits your research question and the species you are
    studying.

2.  Determine the background gene set: This set of genes should include
    all genes expressed in your experiment. You can use a reference
    genome or the genes detected in your RNA-Seq experiment as the
    background set.

3.  Select the differentially expressed genes. We have already made a
    DEGlist.tab in the psuedo alignment script. so we can directly read
    this in.

4.  Perform functional enrichment analysis: Using a tool such as
    clusterProfiler, input the list of differentially expressed genes
    and the background gene set, and perform enrichment analysis against
    the chosen functional annotation database. The output will provide a
    list of significantly enriched GO terms, KEGG pathways, and other
    functional categories, along with the associated p-values and false
    discovery rate (FDR) values.

5.  Interpret the results: Interpret the enriched functional categories
    in the context of your research question and the available
    literature. This will help you gain insight into the underlying
    biological processes and pathways involved in the differential
    expression of genes.

======= \# Do DESeq2 We will use the R package DESeq2 to help us digest
the gene abundance count matrix we generated.

Below, I am reading in and modifying the count matrix we generated from
Kallisto.

We need to create objects in our global environment that can be used
towards completing a functional enrichment analysis.

Below we read in the counts matrix, rename the row names from 1-n to the
value of the first column, remove the first column, and round the values
in the count matrix.

    countmatrix <- read.delim("../output/kallisto_01.isoform.counts.matrix", header = TRUE, sep = '\t') %>%
      {rownames(.) <- .$X; .} %>%
      {.[,-1]} %>%
      {round(., 0)}

We will then make a new data frame that will contain information about
the treatment groups and the type of RNAseq data produced. This will an
object called “deseq2.colData”. We then use the DESeqDataSetFromMatrix
function from the DESeq2 package to make a dataset that we can use in
our DEseq function to do the analysis.

    deseq2.colData <- data.frame(condition=factor(c(rep("b5-b6", 2), rep("TO", 2))), 
                                 type=factor(rep("paired-end", 4)))
    deseq2.dds <- DESeqDataSetFromMatrix(countData = countmatrix,
                                         colData = deseq2.colData, 
                                         design = ~ condition)

Next we will conduct a DESeq analysis using the DESeq function:

    deseq2.dds <- DESeq(deseq2.dds) 
    deseq2.res <- results(deseq2.dds) #this places the results in an object that we can open
    deseq2.res <- deseq2.res[order(rownames(deseq2.res)), ] #reorders the rows
    head(deseq2.res) #take a peak

    ## log2 fold change (MLE): condition TO vs b5.b6 
    ## Wald test p-value: condition TO vs b5.b6 
    ## DataFrame with 6 rows and 6 columns
    ##             baseMean log2FoldChange     lfcSE      stat    pvalue      padj
    ##            <numeric>      <numeric> <numeric> <numeric> <numeric> <numeric>
    ## AF201094.1   0.00000             NA        NA        NA        NA        NA
    ## AF201095.1   0.00000             NA        NA        NA        NA        NA
    ## AF201096.1   0.00000             NA        NA        NA        NA        NA
    ## AF201097.1   3.10213       -3.00407   3.36211 -0.893508  0.371585        NA
    ## AF201098.1   0.00000             NA        NA        NA        NA        NA
    ## AF201099.1   0.00000             NA        NA        NA        NA        NA

### Reading in whole annotated transcriptome

    blast_go <- read.delim(file = "../output/blast_annot_go.tab")
    colnames(blast_go)[1] <- 'access_num' #renaming the first column 

    # Merge together all results from DESeq analysis with blast_go data frame
    res_df <- as.data.frame(deseq2.res) %>%
      mutate(access_num = rownames(.)) %>%
      distinct()

    #clean up the blast annotated table to keep only unique rows
    blast_go_small <- distinct(blast_go, access_num, .keep_all = TRUE)

    transcriptome_anno <- merge(blast_go_small, res_df, by = "access_num", all = TRUE)

### Reading in the list of differentially expressed genes:

We will read in the annotated DEG list that was created in the 04-blast
code script.

    diff_genes <- read.delim(file = "../output/annote_DEGlist.tab", sep =" ")

    #peak at annotated DEG list
    head(diff_genes)

    ##   access_num  baseMean log2FoldChange    lfcSE      stat       pvalue
    ## 1 AF201134.1  48.40695      -6.972899 2.421542 -2.879528 3.982710e-03
    ## 2 AF201259.1 189.65058      -8.943305 2.422191 -3.692237 2.222898e-04
    ## 3 AY159281.1  49.51016      -7.005987 2.429210 -2.884060 3.925842e-03
    ## 4 EE743591.1 307.58870      -9.640638 2.355167 -4.093398 4.250971e-05
    ## 5 FF339616.1  67.95408      -7.461979 2.404802 -3.102949 1.916025e-03
    ## 6 FN178505.1  37.13056       8.578527 2.182042  3.931422 8.444502e-05
    ##          padj     V3          V4       V13
    ## 1 0.034511690 P27604  SAHH_CAEEL 4.60e-100
    ## 2 0.007245743 P62246   RS15A_RAT  2.22e-82
    ## 3 0.034305090 P12716  ACTC_PISOC 5.79e-118
    ## 4 0.002401130 Q90474 H90A1_DANRE 1.99e-127
    ## 5 0.024035365 Q7TSK7  ATL2_MOUSE  1.23e-26
    ## 6 0.003704028 P13789 TNNT2_BOVIN  5.68e-39
    ##                                                                                               Protein.names
    ## 1 Adenosylhomocysteinase (AdoHcyase) (EC 3.13.2.1) (Protein dumpy-14) (S-adenosyl-L-homocysteine hydrolase)
    ## 2                                                                                40S ribosomal protein S15a
    ## 3                     Actin, cytoplasmic (EC 3.6.4.-) [Cleaved into: Actin, cytoplasmic, intermediate form]
    ## 4                                                                         Heat shock protein HSP 90-alpha 1
    ## 5                              ADAMTS-like protein 2 (ADAMTSL-2) (TSP1-repeat-containing protein 1) (TCP-1)
    ## 6                                      Troponin T, cardiac muscle (TnTc) (Cardiac muscle troponin T) (cTnT)
    ##                                                  Organism
    ## 1                                  Caenorhabditis elegans
    ## 2                                 Rattus norvegicus (Rat)
    ## 3 Pisaster ochraceus (Ochre sea star) (Asterias ochracea)
    ## 4             Danio rerio (Zebrafish) (Brachydanio rerio)
    ## 5                                    Mus musculus (Mouse)
    ## 6                                     Bos taurus (Bovine)
    ##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      Gene.Ontology..biological.process.
    ## 1                                                                                                                                                                                                                                                                                                                                                                                                                                             one-carbon metabolic process [GO:0006730]; S-adenosylhomocysteine catabolic process [GO:0019510]; S-adenosylmethionine cycle [GO:0033353]
    ## 2                                                                                                                                                                                                                                                                                                                                                                                                           positive regulation of cell cycle [GO:0045787]; positive regulation of cell population proliferation [GO:0008284]; response to virus [GO:0009615]; translation [GO:0006412]
    ## 3                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
    ## 4 cellular response to heat [GO:0034605]; leukocyte migration [GO:0050900]; muscle organ development [GO:0007517]; myofibril assembly [GO:0030239]; positive regulation of nitric oxide biosynthetic process [GO:0045429]; protein folding [GO:0006457]; protein stabilization [GO:0050821]; response to metal ion [GO:0010038]; sarcomerogenesis [GO:0048769]; skeletal muscle myosin thick filament assembly [GO:0030241]; skeletal muscle thin filament assembly [GO:0030240]; skeletal myofibril assembly [GO:0014866]; striated muscle myosin thick filament assembly [GO:0071688]
    ## 5                                                                                                                                                                                                                                                                                                                                                                                    extracellular matrix organization [GO:0030198]; lobar bronchus epithelium development [GO:0060481]; negative regulation of transforming growth factor beta receptor signaling pathway [GO:0030512]
    ## 6                                                                                                                                                                                                                                                                                                                                                                                                                          cardiac muscle contraction [GO:0060048]; muscle contraction [GO:0006936]; regulation of muscle contraction [GO:0006937]; sarcomere organization [GO:0045214]
    ##                                                                                                                                                                                                                                                                                                                                            Gene.Ontology.IDs
    ## 1                                                                                                                                                                                                                                                                                                 GO:0004013; GO:0005829; GO:0006730; GO:0019510; GO:0033353
    ## 2                                                                                                                                                                                                                                                 GO:0003735; GO:0005737; GO:0006412; GO:0008284; GO:0009615; GO:0022626; GO:0022627; GO:0045202; GO:0045787
    ## 3                                                                                                                                                                                                                                                                                                             GO:0005524; GO:0005737; GO:0005856; GO:0016787
    ## 4 GO:0005524; GO:0005634; GO:0005829; GO:0005886; GO:0006457; GO:0007517; GO:0010038; GO:0014866; GO:0016887; GO:0030018; GO:0030235; GO:0030239; GO:0030240; GO:0030241; GO:0031672; GO:0032991; GO:0034605; GO:0042470; GO:0043025; GO:0043209; GO:0045429; GO:0048471; GO:0048769; GO:0050821; GO:0050900; GO:0051082; GO:0071688; GO:0097718; GO:0140662
    ## 5                                                                                                                                                                                                                                                                                     GO:0005576; GO:0030198; GO:0030512; GO:0031012; GO:0050436; GO:0060481
    ## 6                                                                                                                                                                                                                                                             GO:0005523; GO:0005861; GO:0006936; GO:0006937; GO:0030172; GO:0031013; GO:0045214; GO:0060048

## define gene list and background

    gene_list <- diff_genes$access_num
    background <-transcriptome_anno$access_num
    go_ids <- diff_genes$Gene.Ontology.IDs
    go_bp_annotations <- diff_genes$Gene.Ontology..biological.process
    deg_data <- data.frame(gene = gene_list, GO_ID = go_ids, GO_BP = go_bp_annotations)

    #peak at deg_data
    head(deg_data)

    ##         gene
    ## 1 AF201134.1
    ## 2 AF201259.1
    ## 3 AY159281.1
    ## 4 EE743591.1
    ## 5 FF339616.1
    ## 6 FN178505.1
    ##                                                                                                                                                                                                                                                                                                                                                        GO_ID
    ## 1                                                                                                                                                                                                                                                                                                 GO:0004013; GO:0005829; GO:0006730; GO:0019510; GO:0033353
    ## 2                                                                                                                                                                                                                                                 GO:0003735; GO:0005737; GO:0006412; GO:0008284; GO:0009615; GO:0022626; GO:0022627; GO:0045202; GO:0045787
    ## 3                                                                                                                                                                                                                                                                                                             GO:0005524; GO:0005737; GO:0005856; GO:0016787
    ## 4 GO:0005524; GO:0005634; GO:0005829; GO:0005886; GO:0006457; GO:0007517; GO:0010038; GO:0014866; GO:0016887; GO:0030018; GO:0030235; GO:0030239; GO:0030240; GO:0030241; GO:0031672; GO:0032991; GO:0034605; GO:0042470; GO:0043025; GO:0043209; GO:0045429; GO:0048471; GO:0048769; GO:0050821; GO:0050900; GO:0051082; GO:0071688; GO:0097718; GO:0140662
    ## 5                                                                                                                                                                                                                                                                                     GO:0005576; GO:0030198; GO:0030512; GO:0031012; GO:0050436; GO:0060481
    ## 6                                                                                                                                                                                                                                                             GO:0005523; GO:0005861; GO:0006936; GO:0006937; GO:0030172; GO:0031013; GO:0045214; GO:0060048
    ##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   GO_BP
    ## 1                                                                                                                                                                                                                                                                                                                                                                                                                                             one-carbon metabolic process [GO:0006730]; S-adenosylhomocysteine catabolic process [GO:0019510]; S-adenosylmethionine cycle [GO:0033353]
    ## 2                                                                                                                                                                                                                                                                                                                                                                                                           positive regulation of cell cycle [GO:0045787]; positive regulation of cell population proliferation [GO:0008284]; response to virus [GO:0009615]; translation [GO:0006412]
    ## 3                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
    ## 4 cellular response to heat [GO:0034605]; leukocyte migration [GO:0050900]; muscle organ development [GO:0007517]; myofibril assembly [GO:0030239]; positive regulation of nitric oxide biosynthetic process [GO:0045429]; protein folding [GO:0006457]; protein stabilization [GO:0050821]; response to metal ion [GO:0010038]; sarcomerogenesis [GO:0048769]; skeletal muscle myosin thick filament assembly [GO:0030241]; skeletal muscle thin filament assembly [GO:0030240]; skeletal myofibril assembly [GO:0014866]; striated muscle myosin thick filament assembly [GO:0071688]
    ## 5                                                                                                                                                                                                                                                                                                                                                                                    extracellular matrix organization [GO:0030198]; lobar bronchus epithelium development [GO:0060481]; negative regulation of transforming growth factor beta receptor signaling pathway [GO:0030512]
    ## 6                                                                                                                                                                                                                                                                                                                                                                                                                          cardiac muscle contraction [GO:0060048]; muscle contraction [GO:0006936]; regulation of muscle contraction [GO:0006937]; sarcomere organization [GO:0045214]

### Brainstorming, code may or may not work below, beware…

    enrich_result <- enricher(gene = gene_list,
                              pAdjustMethod = "BH",
                              universe = background,
                              TERM2GENE = deg_data,
                              pvalueCutoff = 0.05,
                              qvalueCutoff = 0.05)
