Visualizing, Binning and Refining of MAGs With Anvi’o

High throughput ‘omics technologies generate huge datasets that need to be properly analyzed in order to decipher the biological implications. The workflow of handling such datasets must be user-friendly to facilitate rapid analysis. Here, we demonstrated the use of the anvi’o workflow, which is a visualization platform and allows for advanced analysis for metagenomics data. In this protocol, we have provided the pre-packaged plant-microbiome dataset. Then we used the dataset to visualize, perform manual binning, and refinement of metagenome-assembled genomes (MAGs). Anvi’o works with an easy-to-use interface, and also helps the users to test and implement research ideas in a timely manner.
To guide the readers, we have introduced the purposes of the dir system:
graphs: the figures produced during the analysis.  
input: the source of the input data is mentioned, along with explanation and guidelines of the input data are provided.
lib: the source code used within the workflow.
output: the output results of the workflow.
workflow: step by step of the pipeline.

Anvi’o Installation: (https://anvio.org/install/)

(1)	Conda setup: If the conda is not installed in the system, it is necessary to open a terminal such as iTerm.
Command:
conda install

	To verify whether you already have conda installed, copy and paste the following command into your terminal.
Command:
conda --version

	Always make sure that you work in an up-to-date conda environment by using the following command:
Command:
conda update conda
(2)	Anvi’o environment setup
	You should creat a new conda environment using the command:
	Command:
	conda create -y --name anvio-7.1 python=3.6

Then activate it using the command:
Command:
	conda activate anvio-7.1

(3)	Installing Anvi’o
The first step is to download the python source package for the anvi’o release using the following command:
Command: 
	curl -L https://github.com/merenlab/anvio/releases/download/v7.1/anvio-7.1.tar.gz \
        --output anvio-7.1.tar.gz

	Then use the following command to install anvi’o:
	Command:
pip install anvio-7.1.tar.gz

Updating anvi’o databases:

If the anvi’o databases are not compatible with the latest versions of anvi’o, there are options to update the anvi’o databases.

Safer option is to use:
Command:
anvi-migrate --migrate-dbs-safely *.db

When using this option, anvi’o will generate a backup of a copy of each database. If there is an error during the migration, the anvi’o will let know the users about what went wrong and will be able to restore the original database from the copy it made.

Another option is to use:

Command:
anvi-migrate --migrate-dbs-quickly *.db

This option does not create any backup files, but might be useful when there are lot of databases to migrate.

Downloading the pre-packaged Plant-Microbiome Dataset (Input data):

Plant-microbiome data-pack can be downloaded from https://figshare.com/s/acc45cb6fb5cbd819d69

The following are some details about the plant-microbiome data-pack: 
In the dataset directory, you will see that the data-pack contains an anvi'o merged profile database (that describes 6 metagenomes - 3 from plants and 3 from fecal samples), an anvi'o contigs database, and other extra data that is required by various sections in this tutorial. Here are some basic descriptions of several of these files, as well as how they were created:

The profile and contigs databases. We produced the anvi'o contigs database utilizing the program anvi-gen-contigs-database. This anvi'o database keeps all the information that is associated with the contigs: k-mer frequencies for each contig, open reading frames positions, taxonomic and functional annotation of genes, among others. We also used the tool anvi-profile to create a merged anvi'o profile database. Anvi'o profile databases store sample-specific information on contigs.  Each profile database is linked to a contigs database, and anvi'o use the program anvi-merge to merge single profiles that are linked to the same contigs database into an anvi'o merged profile.

Single-copy core genes in contigs. Among the contigs, we utilized the program anvi-run-hmms to find single-copy core genes for Bacteria, Archaea, and Eukarya, as well as ribosomal RNA sequences. The contigs database stores all these results as well. This data enables us to learn the completeness and redundancy estimations of freshly detected bins using the interactive interface. Note that if all single copy-core genes for a given domain are discovered once in the chosen bin, the completion rate is 100% and the redundancy rate is 0%. The redundancy score will rise if a few genes are discovered several times. In case a few genes are missing, the completion value will be reduced.

Assigning functions towards genes. We performed anvi-run-ncbi-cogs and anvi-run-kegg-kofams and stored genes functions results in the contigs database. 

Workflow:

<img width="454" alt="Workflow" src="https://user-images.githubusercontent.com/83604437/177424832-22b61a9b-4d5a-4b85-b213-2209fca528fb.png">

Expected Results:

Proper manual refinement of MAGs is necessary to elucidate meaningful biological implications. In this protocol, we used a plant-microbiome dataset to identify 69 bins and then curated the bins manually to remove the outliers and contaminants. It is recommended to perform manual refining after automatic binning to recover higher quality MAGs.
