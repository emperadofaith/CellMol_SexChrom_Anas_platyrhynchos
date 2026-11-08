# Bioinformatics Workflow: Sex-Chromosome Dosage Analysis in Pekin Duck #

**Step 1. Selecting the organism and reference genome**

<img width="600" height="350" alt="image" src="https://github.com/user-attachments/assets/b1238265-db27-464f-a998-f8f3f7dfc181" />

I first selected the Pekin duck (Anas platyrhynchos) as my organism for the sex-chromosome dosage analysis. I searched the NCBI database for its reference genome and selected the assembly Pekin_C18 (GCA_037218355.1). I chose this assembly because it was chromosome-level, allowing me to identify and compare individual chromosomes.

**Step 2. Downloading the reference genome**

<img width="600" height="350" alt="image" src="https://github.com/user-attachments/assets/f97ed41a-5f0b-4ff2-926d-4f7eb8decf73" />

After selecting the assembly, I downloaded its genome sequence in FASTA format using NCBI Datasets. I uploaded the FASTA file into Galaxy to use as my reference genome for sequence alignment. I also obtained the assembly information files, particularly the sequence_report.jsonl, which helped me identify the chromosome names and accession numbers.

**Part 3. Importing the sequencing reads**

<img width="600" height="350" alt="image" src="https://github.com/user-attachments/assets/0ff51175-fcbb-4e32-9e07-5b8d1f95d6e2" />

Next, I obtained whole-genome sequencing reads using the SRA accession SRR18178819. I imported the data into Galaxy using the ***Faster Download and Extract Reads in FASTQ*** tool. The resulting FASTQ file contained the DNA sequencing reads and their quality information. I used the single-end reads for the succeeding analysis.

**Part 4. Checking read quality using FastQC**

<img width="340" height="300" alt="image" src="https://github.com/user-attachments/assets/fa981cbd-dd89-4115-a4db-f894a6ecb600" /> <img width="340" height="300" alt="image" src="https://github.com/user-attachments/assets/93ed6461-2d1f-4150-8bcb-2651da57f32e" />
<img width="340" height="300" alt="image" src="https://github.com/user-attachments/assets/0206b809-4b9e-4441-b34a-4a8ecbf67407" /> <img width="340" height="300" alt="image" src="https://github.com/user-attachments/assets/7e339313-a921-44e5-8a72-ed823f3d9291" /> <img width="340" height="300" alt="image" src="https://github.com/user-attachments/assets/34dc772b-e162-4804-b257-10291c12c8d9" />
<img width="150" height="300" alt="image" src="https://github.com/user-attachments/assets/0f93354a-db43-4da9-93ba-361273670ff2" />

Before alignment, I used the FastQC tool to evaluate the quality of my sequencing reads. I examined the per-base sequence quality, per-sequence quality, GC content, adapter content, and sequence duplication.

My results showed generally high per-base quality scores of around Q36–Q40, with almost no adapter contamination. Although the GC content showed a warning, the overall quality was acceptable, so additional trimming was not considered necessary.

**Part 5. Aligning reads using BWA-MEM2**

After quality checking, I used BWA-MEM2 to align the FASTQ reads against the Pekin_C18 reference genome. I selected the reference FASTA file and the single-end sequencing reads as inputs. I used the Simple Illumina mode and selected coordinate-sorted BAM as the output format.

<img width="340" height="300" alt="image" src="https://github.com/user-attachments/assets/e71320b1-9d1a-4863-8913-aff02bcd92b5" />

The resulting BAM file contained the sequencing reads aligned to their corresponding positions in the reference genome.

**Part 6. Calculating chromosome coverage using Samtools**

I then used Samtools Coverage to calculate the sequencing coverage of the aligned reads. I selected the BAM file as input and set the minimum mapping quality and base quality to 20.

<img width="340" height="300" alt="image" src="https://github.com/user-attachments/assets/9f8adb15-6cbf-40d4-a384-70b6b6f78a1e" />

The tool generated a table containing the reference chromosome names and their corresponding coverage measurements, including meandepth. I downloaded this result and saved it as chromosome_coverage.tsv.

**Part 7. Identifying and labeling the chromosomes**

To identify the autosomes and sex chromosome, I examined the sequence_report.jsonl file from NCBI Datasets. I compared the chromosome accession numbers in this report with the reference names in my coverage table.

<img width="340" height="300" alt="image" src="https://github.com/user-attachments/assets/ff1a7fa0-fe4e-4f90-97e8-d7c46e6f87be" />

I identified five autosomes and one Z chromosome for the initial analysis. I labeled the autosomes as A and the Z chromosome as Z. I excluded unplaced scaffolds because they were not assigned as chromosome-level sequences. I also did not include a W chromosome because the assembly did not contain an assembled W chromosome.

<img width="246" height="223" alt="image" src="https://github.com/user-attachments/assets/b2845588-1e64-4da5-b8ad-bdb93fdcfe72" />

I saved these chromosome labels in a CSV file named chromosome_groups.csv.

**Part 8. Preparing the files for R analysis**

Finally, I prepared the two files needed for the R analysis: chromosome_coverage.tsv, which contained the Samtools coverage results, and chromosome_groups.csv, which contained the chromosome classifications.

<img width="340" height="300" alt="image" src="https://github.com/user-attachments/assets/fb2fd7e7-329c-4ebf-874a-f2b61cee351b" />

I placed both files in the same folder as my R script so that R could read the data and calculate the relative sequencing depth of the Z chromosome compared with the autosomes.

# Galaxy workflow link

https://usegalaxy.org/u/faith_emperado/h/sex-dosage-anas-platyrhynchos-1

