Downloading complete uniprot database.

    cd ../data
    curl -O https://ftp.uniprot.org/pub/databases/uniprot/current_release/knowledgebase/complete/uniprot_sprot.fasta.gz
    mv uniprot_sprot.fasta.gz uniprot_sprot_r2023_01.fasta.gz
    gunzip -k uniprot_sprot_r2023_01.fasta.gz
    ls ../data

Using the NCBI blast software command ‘makeblastdb’ to create a blast
database from the uniprot fasta file.

    /home/shared/ncbi-blast-2.11.0+/bin/makeblastdb \
    -in /home/shared/8TB_HDD_02/cvaldi/celeste-tunicate-devo/data/uniprot_sprot_r2023_01.fasta \
    -dbtype prot \
    -out /home/shared/8TB_HDD_02/cvaldi/celeste-tunicate-devo/output/blastdb/uniprot_sprot_r2023_01

Lets look at what’s in the sequence.fata file before we BLAST it.

    head - n 20 ../data/psuedo-alignment/sequence.fasta
    echo "How many sequences are there?"
    grep -c ">" ../data/psuedo-alignment/sequence.fasta

Blasting the reference transcriptome:

    /home/shared/ncbi-blast-2.11.0+/bin/blastx \
    -query ../data/sequence.fasta \
    -db ../output/blastdb/uniprot_sprot_r2023_01 \
    -out ../output/Bsc-uniprot_blastx.tab \
    -evalue 1E-20 \
    -num_threads 20 \
    -max_target_seqs 1 \
    -outfmt 6

Lets take a little peak at the tab file we just created:

    head -2 ../output/Bsc-uniprot_blastx.tab
    wc -l ../output/Bsc-uniprot_blastx.tab
