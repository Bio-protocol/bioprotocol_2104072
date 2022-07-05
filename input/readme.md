Source: https://figshare.com/s/acc45cb6fb5cbd819d69

Software: Anvi’o v7 (https://merenlab.org/software/anvio/)

The following are some details about the plant-microbiome data-pack: 
In the dataset directory, you will see that the data-pack contains an anvi'o merged profile database (that describes 6 metagenomes - 3 from plants and 3 from fecal samples), an anvi'o contigs database, and other extra data that is required by various sections in this tutorial. Here are some basic descriptions of several of these files, as well as how they were created:

The profile and contigs databases. We produced the anvi'o contigs database utilizing the program anvi-gen-contigs-database. This anvi'o database keeps all the information that is associated with the contigs: k-mer frequencies for each contig, open reading frames positions, taxonomic and functional annotation of genes, among others. We also used the tool anvi-profile to create a merged anvi'o profile database. Anvi'o profile databases store sample-specific information on contigs.  Each profile database is linked to a contigs database, and anvi'o use the program anvi-merge to merge single profiles that are linked to the same contigs database into an anvi'o merged profile.

Single-copy core genes in contigs. Among the contigs, we utilized the program anvi-run-hmms to find single-copy core genes for Bacteria, Archaea, and Eukarya, as well as ribosomal RNA sequences. The contigs database stores all these results as well. This data enables us to learn the completeness and redundancy estimations of freshly detected bins using the interactive interface. Note that if all single copy-core genes for a given domain are discovered once in the chosen bin, the completion rate is 100% and the redundancy rate is 0%. The redundancy score will rise if a few genes are discovered several times. In case a few genes are missing, the completion value will be reduced.

