The following README.txt file summarizes the information contained in the Person1.zip file. Contents of this folder include BST281_Final.Rmd and 3 folders -- RAW_DATA, INTERMEDIATE_DATA, and FINAL_DATA. Files that are marked as "too large" have not been uploaded to the folder and instead are liked in this document. 



BST281_Final.Rmd - This R-Markdown file contains the code used to execute Person1's role, broken up into 3 sections: 
* Raw Sample Extraction:  
	- SRA Toolkit (sra-tools 3.1.0) 
* Quality Control 
	- FASTQC (fastqc 0.12.1) 
	- MultiQC (multiqc 1.17) 
	- Cutadapt (cutadapt 4.4) 
* Quantification 
	- Salmon (salmon 1.10.2) 
 	- Tximeta (tximeta 1.20.3) 



RAW_DATA: 

* (too large) Bulk RNA-Seq FASTQ files for 5 IBD vs 5 non-IBD patients from NCBI GEO: https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE255720

* (too large) Human reference transcriptome from GENCODE Release 45 (GRCh38.p14): https://www.gencodegenes.org/human/ 
	- gencode.v45.pc_transcripts.fa: Protein-coding transcript sequences
	- gencode.v45.annotation.gtf : Comprehensive gene annotation
	- gencode.v45.annotation.gff3 : Comprehensive gene annotation

* colAnnotation.rds - This .rds file contains a data frame of the sample metadata, including different sample identifiers and their respective disease state (pan-colitic IBD or non-IBD healthy control) 

* SRR_Acc_List.txt - This .txt file contains a list of the 10 SRR Accession Numbers corresponding to our 10 IBD/control sequence samples 



INTERMEDIATE_DATA: 

* (too large) salmon_index - This folder contains various files that were outputted after running the salmon index function in order to create an index for the reference transcriptome. 

* (too large) salmon_output - This folder contains a folder for each of the 10 samples, labeled by their SRR Accession Number, each containing a quant.sf file (the output of the salmon quant function)

* matrix_gse_salmon_tximeta.rds - This file contains the gse object storing the processed data from Salmon (length, counts, abundance) with associated metadata obtained using the tximeta package in R. The abundance has been processed from transcript-level to gene level, and is normalized via the TPM method. 

* gse_tmm.rds - This file contains the gse object storing the same data as the matrix_gse_salmon_tximeta.rds file, but where abundance has been normalized via the TMM method. 

* rowAnnotation.rds - This .rds file contains a dataframe of the gene metadata, including the linkage of transcript ids to different gene ids (gene symbol, entrez ID, ensemble ID, etc.) 



FINAL_DATA: 

* multiqc_report.html - This .html file is a compilation of the 10 raw fastqc reports and contains important quality control plots including an overall status check heatmap, a per-base sequence quality plot, and an adapter content plot. 

* multiqc_report_trimmed.html - This .html file is similar to the multiqc_report.html file, but instead contains quality control plots for the trimmed fastq data. 

* TMM.rds - This .rds file is a data frame of gene-level TMM values, where each of the 10 columns corresponds to a given sample and each of the 20431 rows correspond to a given gene. 




Data that was passed on to Person2 included TMM.rds, colAnnotation.rds, and rowAnnotation.rds.


