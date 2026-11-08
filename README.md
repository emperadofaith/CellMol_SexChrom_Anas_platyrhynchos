# CellMol_SexChrom_Anas_platyrhynchos

**Selected species:** *Anas platyrynchos*

**Study question:** Why are autosomes used as the reference when calculating relative chromosome depth?

## Accession links: ##
**Reference Assembly Accession:** GCA_037218355.1

**Assembly BioSample accession:** SAMN24405268

**WGS Run Accession:** SRR18178819

**WGS BioSample accession:** SAMN24405268

# Chosen Chromosome Groups

| rname       | group |
|-------------|-------|
| CM074391.1  | A     |
| CM074392.1  | A     |
| CM074393.1  | A     |
| CM074394.1  | A     |
| CM074395.1  | A     |
| CM074424.1  | Z     |

Chromosomes CM074391.1 to CM074395.1 were selected as autosomes (A) because they correspond to chromosomes 1–5 in the NCBI sequence report and are not identified as sex chromosomes. These five autosomes provide a reliable baseline for calculating median read depth and comparing chromosome coverage. CM074424.1 was selected as the Z chromosome because it is specifically identified as the Z sex chromosome. This selection allowed the Z chromosome's read depth to be compared with the autosomes to assess sex-chromosome dosage.

# Results and Discussion

**1. What species did you choose, and what evidence supports a diploid XX/XY or ZZ/ZW system?**

The selected species was the Pekin duck (*Anas platyrhynchos*). Ducks have a ZW sex-determination system, in which females are ZW and males are ZZ. This is supported by the species' avian sex-determination system and the NCBI reference assembly, which identifies a Z chromosome (CM074424.1). The expected diploid chromosome complements are therefore ZZ in males and ZW in females.

**2. What are your assembly accession, WGS run, and both BioSample accessions? Are the donors the same?**

The reference assembly used was GCA_037218355.1 (Pekin_C18), and the WGS run was SRR18178819. Both datasets are associated with the same BioSample, SAMN24405268, indicating that the reference genome and WGS reads came from the same male Pekin duck donor.

**3. Which sequences were used as autosomes and as X or Z? How did you verify their identities?**

The autosomes used were CM074391.1, CM074392.1, CM074393.1, CM074394.1, and CM074395.1, corresponding to chromosomes 1–5. The Z chromosome used was CM074424.1. Their identities were verified using the NCBI sequence_report.jsonl file, exported from NCBI dataset, which provides chromosome names, accessions, and sequence classifications. 

**4. What are the median autosomal depth, X:A or Z:A ratio, and inferred sex-chromosome complement?**

The median autosomal depth was 58.256, while the Z:A ratio was 0.976. The ratio is close to 1.0, indicating that Z-chromosome coverage was nearly equal to autosomal coverage. This supports a ZZ-like sex-chromosome complement.

**5. Does your result agree with the recorded sex of the WGS donor, if reported? Explain any discrepancy or uncertainty.**

Yes. The analysis agrees with the recorded male sex of the WGS donor. The Z:A ratio of 0.976 is close to the expected value of 1.0 for a male duck with two Z chromosomes (ZZ). No major discrepancy was observed.

**6. Why is a chromosome-level assembly alone insufficient for a reliable read-depth sex inference?**

A chromosome-level assembly identifies and organizes chromosome sequences, but it does not directly establish the sex of the sequenced individual. Reliable inference also requires quality WGS reads, sufficient sequencing coverage, accurate read mapping, and correctly identified sex chromosomes.

# References

https://www.ncbi.nlm.nih.gov/datasets/genome/GCA_037218355.1/

https://trace.ncbi.nlm.nih.gov/Traces?run=SRR18178819

https://usegalaxy.org/u/faith_emperado/h/sex-dosage-anas-platyrhynchos-1


