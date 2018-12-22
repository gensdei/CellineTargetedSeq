# CellineTargetedSeq
"False-negative errors in next-generation sequencing contribute substantially to inconsistency in mutation databases."

Mutation calls from targeted sequencing for 170 genes in 35 cancer cell lines. 

The 35 cell lines are present in both the GDSC and CCLE databases. 

Alignment of targeted sequencing reads onto the reference sequence (hg19, UCSC genomes) was performed 
using the Burrows-Wheeler Aligner (BWA) to produce SAM files from FASTQ files. 

Sequence quality was assessed by FastQC (https://www.bioinformatics.babraham.ac.uk/projects/fastqc/) 
based on the phred-scaled score with a cutoff value of 20. 

Duplicated reads were removed by Picard (http://broadinstitute.github.io/picard/). 
Local realignment and score recalibration were performed with the Genome Analysis Tool Kit (GATK). 
In the cases of mutation calls, GATK MuTect2 in the tumor-only mode was used for variant call format (VCF) file generation 
(https://software.broadinstitute.org/gatk/documentation/tooldocs/3.8-0/org_broadinstitute_gatk_tools_walkers_cancer_m2_MuTect2.php), 
and Oncotator (portals.broadinstitute.org/oncotator/) was used for annotation.

Among the variations in the targeted NGS results, silent variants and those in the intronic or intergenic region were deselected first. Then, the exonic or splicing variation calls with mutant allelic frequency (AF) ≥ 10% and with population AF less than 1% based on databases from the 1000 Genomes Project (http://www.internationalgenome.org/1000-genomes-browsers/) and the UCSC genome were selected. Additionally, short in/del variants, which are frequently found in 35 cancer cells, also were removed, and the rest were used for further comparison analysis.

