# MiCon

This repository has the code and dataframe for the model developed published in the paper: 
[MICon JMD paper](https://www.jmdjournal.org/article/S1525-1578(23)00105-8/fulltext)

Microhaplotype Contamination Detection workflow using Supervised learning approach.

Innovation in sequencing instrumentation is increasing the per-batch data volumes and decreasing the per-base costs. Multiplexed chemistry protocols after the addition of index tags have further contributed to efficient and cost-effective sequencer utilization. With these pooled processing strategies, however, comes an increased risk of sample contamination. Sample contamination poses a risk of missing critical variants in a patient sample or wrongly reporting variants derived from the contaminant, which are particularly relevant issues in oncology specimen testing where low variant allele frequencies have clinical relevance. Small custom targeted Next Generation Sequencing (NGS) panels yield limited variants and pose challenges in delineating true somatic variants versus contamination calls. A number of popular contamination identification tools have the ability to perform well in whole genome/exome sequencing data, but in smaller gene panels there are fewer variant candidates for the tools to perform accurately. To prevent clinical reporting of potentially contaminated samples in small NGS panels, we have developed MICon (Microhaplotype Contamination detection) - a novel contamination detection model that utilizes microhaplotype site variant allele frequencies. In a heterogeneous hold-out test cohort of 210 samples, the model demonstrated state-of-the-art performance with an AUROC of 0.995. 

## PYTHON NOTEBOOK FOR METHOD AND MODEL DATA:
The microhap_main_final.ipynb notebook has all the modeling snippets and results shared. 

## RESULT
MiCon outperforms popular methods in a heterogenous test dataset we used. 

![alt text](https://github.com/jagadhesh89/MiCon/blob/main/AUROC.jpg)

## COMMANDS USED FOR INDIVIDUAL BENCHMARKING TOOLS

### VERIFYBAMID 2: (Version:2.0.1)
VerifyBamID2 --BamFile <bamFILE>--Reference <REFERENCEfile> --UDPath <gnomadfile> --BedPath <bedfile> --MeanPath af-only <gnomad_af> --DisableSanityCheck --Output <samplename>

### VERIFYBAMID: (Version: 1.1.3)
verifyBamID --vcf <vcffile_1000G> --bam <bamfile> --bai <bamfile>. bai --out <samplename>. verifybamid --ignoreRG --noPhoneHome --verbose --maxDepth 500 --precise --minQ 25

### CALCULATECONTAMINATION: (From GATK version 4.1.8.1)
gatk GetPileupSummaries -I <bamfile> -V <vcffile> -O outputs.table -L <MH.bed> --read-validation-stringency SILENT --QUIET
gatk CalculateContamination -I outputs.table -O contamination.table


### Please cite:
Balan J, Koganti T, Basu S, Dina MA, Artymiuk CJ, Barr Fritcher EG, Halverson KE, Wu X, Jenkinson G, Viswanatha DS. MICon Contamination Detection Workflow for Next-Generation Sequencing Laboratories Using Microhaplotype Loci and Supervised Learning. J Mol Diagn. 2023 Aug;25(8):602-610. doi: 10.1016/j.jmoldx.2023.05.001. Epub 2023 May 25. PMID: 37236547.
