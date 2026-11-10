## Sex-Chromosome Dosage Analysis of *Calypte anna*

## Project Information

**Laboratory Activity:** Sex-Chromosome Dosage in a Selected Animal Nuclear Genome Using NCBI, Galaxy, and R

**Selected Species:** *Calypte anna* (Anna's hummingbird)

**Objective:** To estimate the sex-chromosome complement of the individual that supplied the whole-genome sequencing (WGS) reads by comparing chromosome read depth.

---

## NCBI Data Information

| Data | Accession / Information |
|---|---|
| Species | *Calypte anna* |
| Genome assembly | GCF_003957555.1 |
| Assembly name | bCalAnn1_v1.p |
| WGS run | SRR943150 |
| Experiment | SRX327905 |
| BioSample | SAMN02265252 |
| BioProject | PRJNA212866 |
| SRA study | SRP028275 |
| Recorded BioSample sex | Female |
| Isolate | BGI_N300 |
| Geographic location | USA |

## NCBI Links

- [Genome Assembly](https://www.ncbi.nlm.nih.gov/datasets/genome/GCF_003957555.1/)
- [SRA Run SRR943150](https://www.ncbi.nlm.nih.gov/sra/?term=SRR943150)
- [BioSample SAMN02265252](https://www.ncbi.nlm.nih.gov/biosample/SAMN02265252)
- [BioProject PRJNA212866](https://www.ncbi.nlm.nih.gov/bioproject/PRJNA212866)

The genome assembly and WGS run are associated with BioSample SAMN02265252.

---

## Chromosome Groups

The following chromosome sequences were included in the analysis.

| Accession | Assigned Group |
|---|---|
| NC_044244.1 | A |
| NC_044245.1 | A |
| NC_044246.1 | A |
| NC_044247.1 | A |
| NC_044248.1 | A |
| NC_044274.1 | Z |

The five selected chromosome sequences were assigned to the autosomal group (A). The annotated Z chromosome was assigned to group Z.

## chromosome_groups.csv

```csv
rname,group
NC_044244.1,A
NC_044245.1,A
NC_044246.1,A
NC_044247.1,A
NC_044248.1,A
NC_044274.1,Z
```

---

## WGS Quality Assessment

**WGS Run:** SRR943150

The forward FASTQ dataset was assessed using FastQC.

| FastQC Information | Result |
|---|---|
| Total sequences | 61,679,287 |
| Total bases | 3 Gbp |
| Sequence length | 49 bp |
| GC content | 44% |
| Basic statistics | PASS |
| Per-base sequence quality | PASS |
| Per-sequence quality scores | PASS |
| Per-tile sequence quality | PASS |
| Per-sequence GC content | PASS |
| Per-base N content | PASS |
| Sequence length distribution | PASS |
| Adapter content | PASS |
| Per-base sequence content | WARN |
| Sequence duplication levels | WARN |
| Overrepresented sequences | WARN |

The FastQC report showed passing results for the listed quality measures, with warnings for per-base sequence content, sequence duplication levels, and overrepresented sequences.

---

## Chromosome Coverage Results

The chromosome coverage results were obtained from the Galaxy analysis and used as input for the R analysis.

## chromosome_relative_depth.csv

| Chromosome accession | Group | Mean depth | Relative depth |
|---|---|---:|---:|
| NC_044244.1 | A | 2.24678 | 1.00000 |
| NC_044245.1 | A | 2.14931 | 0.95662 |
| NC_044246.1 | A | 2.29667 | 1.02221 |
| NC_044247.1 | A | 2.56968 | 1.14372 |
| NC_044248.1 | A | 2.22062 | 0.98836 |
| NC_044274.1 | Z | 1.17739 | 0.52403 |

---

## R Analysis Results

The R analysis used the following input files:

- `chromosome_coverage.tsv`
- `chromosome_groups.csv`

The R script was named:

`sex_depth_analysis.R`

The analysis generated the following output files:

- `chromosome_relative_depth.csv`
- `chromosome_depth.png`
- `sex_inference.txt`

## Sex Inference Output

```text
Median autosome depth: 2.247
Z / A ratio: 0.524
W / A ratio: NA
Dosage interpretation: ZW-like
Compare with BioSample sex and discuss limitations.
```

## Result Interpretation

The median autosomal depth was 2.247. The Z-to-autosome depth ratio was 0.524, which is close to 0.5. This result is consistent with a ZW-like chromosome dosage pattern.

The W-to-autosome ratio was reported as NA because the W chromosome was not included in the chromosome grouping file. Therefore, this analysis does not establish the presence or absence of the W chromosome.

---

## Discussion Questions

## 1.  What species did you choose, and what evidence supports a diploid XX/XY or ZZ/ZW system?

The selected species was *Calypte anna* (Anna's hummingbird). The analysis included the annotated Z chromosome, NC_044274.1. The observed Z-to-autosome depth ratio was consistent with a ZW-like dosage pattern.

## 2. What are your assembly accession, WGS run, and both BioSample accessions? Are the donors the same?

The genome assembly used was GCF_003957555.1, and the WGS run was SRR943150. Both records are associated with BioSample SAMN02265252, indicating that they refer to the same submitted biological sample.

## 3. Which sequences were used as autosomes and as X or Z? How did you verify their identities?

The autosomal sequences were NC_044244.1, NC_044245.1, NC_044246.1, NC_044247.1, and NC_044248.1. The Z chromosome sequence was NC_044274.1. Their identities were checked using NCBI chromosome annotations.

## 4. What are the median autosomal depth, X:A or Z:A ratio, and inferred sex-chromosome complement?

The median autosomal depth was 2.247, and the Z:A ratio was 0.524. The ratio was close to the expected value of approximately 0.5 for a ZW-like dosage pattern. Therefore, the result was interpreted as ZW-like.

## 5. Does your result agree with the recorded sex of the WGS donor, if reported? Explain any discrepancy or uncertainty.

Yes. The ZW-like dosage interpretation agrees with the female sex recorded in BioSample SAMN02265252. However, read-depth analysis has limitations and does not independently establish the biological sex of the individual.

## 6. Why is a chromosome-level assembly alone insufficient for a reliable read-depth sex inference?

A chromosome-level assembly provides the reference genome sequences and chromosome annotations. However, it does not show the chromosome dosage of the individual that supplied the WGS reads. Read mapping and chromosome coverage comparison are necessary to estimate relative chromosome dosage.

---

## Limitations

The interpretation of chromosome dosage using read depth has limitations. These include sequencing coverage variation, mapping bias, repetitive sequences, pseudoautosomal regions, and possible reference assembly errors.

The W chromosome was not included in the grouping file. Therefore, its relative depth could not be calculated. The NA result should not be interpreted as evidence that the W chromosome is absent.

The result should be interpreted as a read-depth-based dosage estimate rather than definitive proof of the individual's chromosome complement.

---

## Project Files

The analysis used the following files:

```text
data/
├── chromosome_coverage.tsv
├── chromosome_groups.csv
├── sex_depth_analysis.R
└── results/
    ├── chromosome_relative_depth.csv
    ├── chromosome_depth.png
    └── sex_inference.txt
```
