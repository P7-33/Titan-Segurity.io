---
title: 'Whole Exome Sequencing May Skip Large Segments of DNA'
date: 2020-01-08T02:47:00+01:00
draft: false
---

![](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/clinchem/Issue/66/1/1/m_clinchem_66_1cover.png?Expires=1641399669&Signature=ZPDIR~4GdI5UksQuLQRBFUSxNZTgMb66jYjClehs38N37JYOyhOXKU7S5uLGRN1ZCCulnaXTMuwiMWIA80pzGjnGRUJIYd2STdf-JmiEhmg-klCQfSyiKRMmQwZW4Xky35th7xzhUcgYpkEEH35mblBIdDItG8nkpVoDg8WfWYgvp-1eYIt~-KrV6DkE6l-deGomzbGNyFF~Z7RigNCNqzzIT~Q5E~0NyrSYN-e0TLM4iFMNzhG66oPmquREf5Z3UkgSqL7l77MWSU6I0ilvfFUpl32~S27GXuFQglHwwyXoTyO8iXb8lhyu0F4MTqpV09zqQx7HG6iMvTucZ3LVHg__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA "Clinical Exome Studies Have Inconsistent Coverage | Clinical Chemistry | Oxford Academic")  

Abstract
--------

BACKGROUND

Exome sequencing has become a commonly used clinical diagnostic test. Multiple studies have examined the diagnostic utility and individual laboratory performance of exome testing; however, no previous study has surveyed and compared the data quality from multiple clinical laboratories.

METHODS

We examined sequencing data from 36 clinical exome tests from 3 clinical laboratories. Exome data were compared in terms of overall characteristics and coverage of specific genes and nucleotide positions. The sets of genes examined included genes in Consensus Coding Sequence (CCDS) (n = 17723), a subset of genes clinically relevant to epilepsy (n = 108), and genes that are recommended for reporting of secondary findings (n = 57; excludes X-linked genes).

RESULTS

The average exome nucleotide coverage (≥20×) of each laboratory varied at 96.49% (CV = 3%), 96.54% (CV = 1%), and 91.68% (CV = 4%), for laboratories A, B, and C, respectively. For CCDS genes, the average number of completely covered genes varied at 12184 (CV = 29%), 11687 (CV = 13%), and 5989 (CV = 37%), for laboratories A, B, and C, respectively. With smaller subsets of genes related to epilepsy and secondary findings, the CV revealed low consistency, with a maximum CV seen in laboratory C for both epilepsy genes (CV = 60%) and secondary findings genes (CV = 71%).

CONCLUSIONS

Poor consistency in complete gene coverage was seen in the clinical exome laboratories surveyed. The degree of consistency varied widely between the laboratories.

Exome sequencing has become a routine clinical test for the evaluation of complex multigenic diseases or rare diseases with nonspecific patient presentations. In both the clinical and research setting, the diagnostic yield for exome sequencing is <50% (1–3). One likely contributing factor to negative exome testing is inadequate gene coverage (4–6). Exome sequencing does not consistently analyze all coding nucleotides. The range of coding nucleotide coverage varies by methods, between laboratories, and within a single laboratory. A previous survey of clinical exome laboratories reported an average coverage of targeted bases between 90% to 96% when using a metric of ≥10 sequencing reads per nucleotide position (7). The variation in gene coverage can have a significant negative effect on clinically significant variant locations. In one study, >50% of clinically significant nucleotide locations in coding sequence had inadequate coverage (<20×) for interpretation (5).

Prior studies of the quality of exome testing have focused on differences between sequencing library preparations, probe manufacturers (i.e., capture kits), or other variabilities encountered by a single laboratory. The present study focuses on the inter- and intralaboratory variation of gene coverage for clinical samples analyzed at multiple clinical exome laboratories.

Materials and Methods
---------------------

### INSTITUTIONAL REVIEW

The study was performed under a protocol approved by the UT Southwestern Medical Center Institutional Review Board (STU 052014–035, Reanalysis of Next-Generation Sequencing Data).

### PATIENT AND PUBLIC INVOLVEMENT

The patients enrolled in this study were all evaluated in a pediatric genetics clinic. Exome sequencing was performed from 2012 to 2016 as part of clinical standard of care; all samples were peripheral blood. No sample was sent to > 1 laboratory. After results were returned, the patients or adult family members reviewed the protocol with a genetic counselor and signed a consent to participate. The data were acquired from the laboratories by whatever consent process they required; the study protocol was only provided if the laboratory requested it. We selected samples that allowed an equal number of comparisons of samples from the laboratories most often used by our facility. If a patient or guardian requested information about whether a specific gene or genes were covered adequately, the requested information on the coverage was returned to them.

### CLINICAL EXOME DATA FILES

Raw sequencing data (bam or fastq files) were obtained from clinical exome laboratories that have been in operation since 2012 (7). For laboratories providing fastq files, the alignment was performed by a clinically validated (CLIA 88) next-generation sequencing pipeline to generate a bam file (Children's Health Dallas). All clinical laboratories mapped sequence reads to the hg19 reference genome. Genotyping/variant calling was not examined in this study.

### COVERAGE OF GENES

For uniformity of analysis across samples from male and female participants, only autosomal genes identified in Consensus Coding Sequence (CCDS) were used (n = 17723) (genes located in the X or Y chromosome were not analyzed). Only coding nucleotides were evaluated for gene coverage. The genomic coordinates of the coding nucleotides of each CCDS gene were used to generate a bed file. Subsets of autosomal genes associated with epilepsy (n = 108) or secondary findings (8) (n = 57 because limited to autosomes) were also evaluated (see online Data Supplement).

### COVERAGE OF CLINICALLY SIGNIFICANT NUCLEOTIDE POSITIONS

Nucleotide positions annotated as pathogenic or likely pathogenic in clinical significance were obtained from ClinVar (May 2017; [ftp://ftp.ncbi.nlm.nih.gov/pub/clinvar/](ftp://ftp.ncbi.nlm.nih.gov/pub/clinvar/)). Only single-nucleotide variants associated with an HGNC\_ID were used. Nucleotide positions in the mitochondrial genome, X chromosome, or Y chromosome were excluded. A total of 34907 nucleotide positions were examined; these nucleotide positions are in both coding and noncoding regions. Some of these ClinVar nucleotide positions are not specifically assessed by exome tests.

### CALCULATION OF COVERAGE OF TARGET REGIONS

Data files of aligned sequence (bam) were analyzed for the number of sequencing reads at specific nucleotide positions defined by a bed file (NextGENe v2.4.1, Softgenetics). The bam files were used for coverage statistics. The bed files of targeted genes and nucleotides were used to determine which genes were adequately covered. In brief, the bam and bed files were loaded into NextGENe and the Coverage Curve report was run. Adequacy of coverage depth was defined as ≥20 sequencing reads per nucleotide position (20× depth of coverage). A gene was considered to have an inadequate coverage if any coding nucleotide position had <20× depth of coverage. Prior studies have studied the variant-calling sensitivity at an exome depth of coverage of 20× (9, 10).

### STATISTICAL ANALYSIS

A graphical summary of exome consistency was created by traditional statistical control plots (Levey–Jennings plots), which are used by clinical laboratories (11). Variability of coverage of genes and nucleotide positions was calculated and plotted as control charts with the calculated average ±1 SD and CV. Spearman rank correlation coefficient was used to assess the relationship between nucleotide and gene coverage.

Results
-------

Three clinical laboratories (7) were used for testing of 36 clinical samples (see Table 1 in the Data Supplement that accompanies the online version of this article). Exome tests were performed from 2012 through 2016. The data sets comprised 20 probands and 16 parents of a subset of probands when trio analysis was performed. Laboratories A and C data sets were only trio analyses, whereas laboratory B data sets were only probands without testing of the parents. For probands, the median age at the time of testing was 3 years (range, 1–14), and 55% of participants were female. Neurologic conditions were the most common reason for testing (15 of 20); the majority of these neurologic conditions included epilepsy (n = 9). Overall, 20% of probands (n = 4) had a diagnostic finding related to their clinical presentation.

The 3 laboratories used different exome capture methods (Table 1). Laboratory A uses 2 different capture methods interchangeably: VCRome v2.0 (Roche Sequencing Solutions) or xGen Exome Research Panel v1.0 (IDT); patient reports and raw data files do not indicate which capture method was used on a specific sample. All laboratory B samples used the VCRome v2.1 (Roche) method. Laboratory C used SureSelect XT2 All Exon v4 (Agilent Technologies) for the first 2 trios (samples 25–30) and then used Clinical Research Exome (Agilent) for the second 2 trios (samples 31–36). The highest average number of genome-aligned reads (101789647) and the highest average number of reads aligned to CCDS genes (53912875) was seen for laboratory B. For all 3 laboratories, the number of aligned reads correlated with the number of reads in CCDS genes. Laboratory B had the highest average number of CCDS coding nucleotides covered at 20×, which correlated with the number of reads on CCDS genes. Interestingly, although laboratory C had a greater number of reads aligned to CCDS genes than laboratory A, laboratory C had on average 4.86% fewer coding nucleotides covered (91.68%) than laboratory A (96.54%). In contrast to the wide variation in coding nucleotide coverage between laboratories, variation within laboratories was relatively low (CV of 3%, 1%, and 4% for laboratories A, B, and C, respectively). The lower coverage of coding nucleotides by laboratory C (91.68%) was associated with a smaller number of CCDS genes covered (5989 of 17723, on average) ranging from 3139 to 8067 with a CV of 37%. In comparison, laboratories A and B had CVs of 29% and 13%, respectively. Laboratories A and B had approximately 2-fold higher number of CCDS genes fully covered than laboratory C, with averages of 12184 and 11687 genes for laboratories A and B, respectively.

Table 1

Performance characteristics of exome laboratories.

Exome Capture Method 

Laboratory A

* * *

 

Laboratory B

* * *

 

Laboratory C

* * *

 

VCRome v2.0 (Roche Nimblegen) or xGen Exome Research Panel v1.0 (IDT)a

* * *

 

VCRome v2.1 (Roche Nimblegen)

* * *

 

SureSelect XT2 All Exon v4 (Agilent) or Clinical Research Exome (Agilent)b

* * *

 

 

Average ± 1 SD 

CV, % 

Average ± 1 SD 

CV, % 

Average ± 1 SD 

CV, % 

Aligned readsc 

44657502 ± 14,854,077 

33 

101789647 ± 11792779 

12 

75279130 ± 11261669 

15 

Reads on CCDS genes 

33405007 ± 11981173 

36 

53912875 ± 6968867 

13 

46606929 ± 6815034 

15 

CCDS coding nucleotides 

96.49% ± 2.88% 

3 

96.54% ± 0.81% 

1 

91.68% ± 3.28% 

4 

CCDS genes 

12184 ± 3527 

29 

11687 ± 1487 

13 

5989 ± 2239 

37 

Epilepsy genes 

72 ± 27 

38 

80 ± 12 

16 

44 ± 26 

60 

ACMG genes 

35 ± 12 

36 

42 ± 6 

15 

19 ± 14 

71 

ClinVar variant position 

33731 ± 1322 

4 

34538 ± 179 

1 

33221 ± 883 

3 

Exome Capture Method 

Laboratory A

* * *

 

Laboratory B

* * *

 

Laboratory C

* * *

 

VCRome v2.0 (Roche Nimblegen) or xGen Exome Research Panel v1.0 (IDT)a

* * *

 

VCRome v2.1 (Roche Nimblegen)

* * *

 

SureSelect XT2 All Exon v4 (Agilent) or Clinical Research Exome (Agilent)b

* * *

 

 

Average ± 1 SD 

CV, % 

Average ± 1 SD 

CV, % 

Average ± 1 SD 

CV, % 

Aligned readsc 

44657502 ± 14,854,077 

33 

101789647 ± 11792779 

12 

75279130 ± 11261669 

15 

Reads on CCDS genes 

33405007 ± 11981173 

36 

53912875 ± 6968867 

13 

46606929 ± 6815034 

15 

CCDS coding nucleotides 

96.49% ± 2.88% 

3 

96.54% ± 0.81% 

1 

91.68% ± 3.28% 

4 

CCDS genes 

12184 ± 3527 

29 

11687 ± 1487 

13 

5989 ± 2239 

37 

Epilepsy genes 

72 ± 27 

38 

80 ± 12 

16 

44 ± 26 

60 

ACMG genes 

35 ± 12 

36 

42 ± 6 

15 

19 ± 14 

71 

ClinVar variant position 

33731 ± 1322 

4 

34538 ± 179 

1 

33221 ± 883 

3 

Table 1

Performance characteristics of exome laboratories.

Exome Capture Method 

Laboratory A

* * *

 

Laboratory B

* * *

 

Laboratory C

* * *

 

VCRome v2.0 (Roche Nimblegen) or xGen Exome Research Panel v1.0 (IDT)a

* * *

 

VCRome v2.1 (Roche Nimblegen)

* * *

 

SureSelect XT2 All Exon v4 (Agilent) or Clinical Research Exome (Agilent)b

* * *

 

 

Average ± 1 SD 

CV, % 

Average ± 1 SD 

CV, % 

Average ± 1 SD 

CV, % 

Aligned readsc 

44657502 ± 14,854,077 

33 

101789647 ± 11792779 

12 

75279130 ± 11261669 

15 

Reads on CCDS genes 

33405007 ± 11981173 

36 

53912875 ± 6968867 

13 

46606929 ± 6815034 

15 

CCDS coding nucleotides 

96.49% ± 2.88% 

3 

96.54% ± 0.81% 

1 

91.68% ± 3.28% 

4 

CCDS genes 

12184 ± 3527 

29 

11687 ± 1487 

13 

5989 ± 2239 

37 

Epilepsy genes 

72 ± 27 

38 

80 ± 12 

16 

44 ± 26 

60 

ACMG genes 

35 ± 12 

36 

42 ± 6 

15 

19 ± 14 

71 

ClinVar variant position 

33731 ± 1322 

4 

34538 ± 179 

1 

33221 ± 883 

3 

Exome Capture Method 

Laboratory A

* * *

 

Laboratory B

* * *

 

Laboratory C

* * *

 

VCRome v2.0 (Roche Nimblegen) or xGen Exome Research Panel v1.0 (IDT)a

* * *

 

VCRome v2.1 (Roche Nimblegen)

* * *

 

SureSelect XT2 All Exon v4 (Agilent) or Clinical Research Exome (Agilent)b

* * *

 

 

Average ± 1 SD 

CV, % 

Average ± 1 SD 

CV, % 

Average ± 1 SD 

CV, % 

Aligned readsc 

44657502 ± 14,854,077 

33 

101789647 ± 11792779 

12 

75279130 ± 11261669 

15 

Reads on CCDS genes 

33405007 ± 11981173 

36 

53912875 ± 6968867 

13 

46606929 ± 6815034 

15 

CCDS coding nucleotides 

96.49% ± 2.88% 

3 

96.54% ± 0.81% 

1 

91.68% ± 3.28% 

4 

CCDS genes 

12184 ± 3527 

29 

11687 ± 1487 

13 

5989 ± 2239 

37 

Epilepsy genes 

72 ± 27 

38 

80 ± 12 

16 

44 ± 26 

60 

ACMG genes 

35 ± 12 

36 

42 ± 6 

15 

19 ± 14 

71 

ClinVar variant position 

33731 ± 1322 

4 

34538 ± 179 

1 

33221 ± 883 

3 

The examination of smaller subsets of genes such as those associated with epilepsy (108 genes) or the American College of Medical Genetics and Genomics (ACMG) secondary findings guideline (57 genes) demonstrated findings similar to the CCDS gene set. Laboratories A and B had on average an approximately 2-fold higher number of genes fully covered than laboratory C for both epilepsy and secondary findings genes. In addition to poor gene coverage, laboratory C also had low consistency for complete gene coverage, with a CV of 60% for epilepsy genes and 71% for secondary findings genes. In comparison, laboratory B had much lower variability across samples examined, with CVs for epilepsy and secondary findings genes of ≤16%.

A consideration for the marked variation in laboratory C exome data was the difference in capture kits used for samples 25–30 vs samples 31–36. However, the highest variability of laboratory C data was seen within the 6 samples with the same capture kit (samples 31–36). These 6 samples had an average CCDS nucleotide coverage of 91.31% with a CV of 4.88%. This subset of laboratory C data, in comparison to all laboratory C samples, had both sample 33 with the lowest nucleotide coverage (85.62%) and sample 36 with the highest nucleotide coverage (96.20%) (see the online Data Supplement).

For laboratories A, B, and C, the parameters examined for completeness of coverage (≥20×) were plotted for each sample with reference to the average and ±1 SD measurements (Figs. 1 and 2). The control plots emphasize that the 3 laboratories have marked variation in consistency, with laboratory B having the highest consistency for all parameters. Laboratory A has some analytical advantages over laboratory B, with samples 1 through 8 demonstrating better performance features such as CCDS nucleotide and gene coverage; however, laboratory A has problematic samples (9 and 11) that deviate >1 SD from average (see online Data Supplement). Laboratory C has the lowest consistency with samples exceeding both the +1 SD and the −1 SD thresholds for CCDS nucleotide and gene coverage. In addition, laboratory C had the lowest average coverage for all parameters examined.

### Variability in exome coverage.

Fig. 1.

The coverage statistics are summarized for each sample sequenced at Labs A (circles, 1–12), B (diamonds, 13–24), and C (triangles, 25–36). The average value for each plot (double line) is flanked by the ±1 standard deviation (dotted lines). The top row summarizes the percentage of coding nucleotides covered in each sample. The bottom row summarizes the genes with all CCDS coding nucleotides covered (maximum of 17723 genes) in each sample. Full coverage for these panels is defined as coverage at a minimum of 20× (reads per nucleotide position). The laboratory A trio (proband = 7; parents = 8, 9) is further described in Fig. 1 in the online Data Supplement.

Fig. 1.

The coverage statistics are summarized for each sample sequenced at Labs A (circles, 1–12), B (diamonds, 13–24), and C (triangles, 25–36). The average value for each plot (double line) is flanked by the ±1 standard deviation (dotted lines). The top row summarizes the percentage of coding nucleotides covered in each sample. The bottom row summarizes the genes with all CCDS coding nucleotides covered (maximum of 17723 genes) in each sample. Full coverage for these panels is defined as coverage at a minimum of 20× (reads per nucleotide position). The laboratory A trio (proband = 7; parents = 8, 9) is further described in Fig. 1 in the online Data Supplement.

The graphical control plots also suggest the possibility of using exome-wide parameters such as CCDS nucleotides and gene coverage to predict consistency of subsets of genes. For laboratory A, the 3 samples with the worst performance in coding nucleotide coverage (9, 10, and 11) are also the worst performing samples for CCDS genes, epilepsy genes, ACMG/secondary findings genes, and ClinVar variant locations (Figs. 1 and 2). For laboratory B, the overall similar performance at the coding nucleotide level is reflected generally with low SD and CV across the other parameters; however, with the subset of genes in epilepsy and ACMG/secondary findings, sample 13 shows a deviation that exceeds −1 SD. The variation in laboratory C shows similarities between coding nucleotides and CCDS genes: samples below the average in coding nucleotides are below the average in CCDS complete gene coverage; samples that are above average in 1 parameter are similarly above average in the other parameter. However, these trends in performance for laboratory C are not maintained with the examination of smaller subsets of genes. Samples 28, 29, and 30, show exome-wide parameters that are above the average; however, on examination of smaller subsets of genes, these samples show below-average performance (Fig. 2).

### Variability in gene subsets and clinically significant variant locations.

Fig. 2.

(A), The genes with all coding nucleotides covered for epilepsy (maximum of 108, top row) or ACMG secondary findings (maximum of 57 genes, bottom row) were examined within the exome samples sequenced at Labs A (circles, 1–12), B (diamonds, 13–24), and C (triangles, 25–36). (B), The ClinVar pathogenic or likely pathogenic variant locations covered (maximum of 34907 coordinates) are also plotted. The average value for each plot (double line) is flanked by the ±1 SD (dotted lines). Full coverage for these panels is defined as coverage at a minimum of 20× (reads per nucleotide position).

Fig. 2.

(A), The genes with all coding nucleotides covered for epilepsy (maximum of 108, top row) or ACMG secondary findings (maximum of 57 genes, bottom row) were examined within the exome samples sequenced at Labs A (circles, 1–12), B (diamonds, 13–24), and C (triangles, 25–36). (B), The ClinVar pathogenic or likely pathogenic variant locations covered (maximum of 34907 coordinates) are also plotted. The average value for each plot (double line) is flanked by the ±1 SD (dotted lines). Full coverage for these panels is defined as coverage at a minimum of 20× (reads per nucleotide position).

We studied whether nucleotide coverage was predictive of complete gene coverage. Each sample was examined by plotting the fraction of genes completely covered against the overall CCDS coding nucleotides covered (Fig. 3). All 36 samples were examined for their correlation between complete genes covered (CCDS, epilepsy, and ACMG) and the CCDS coding nucleotides. As expected, the correlation was very high for the largest data set \[Spearman ρ (_rs_) = 0.99\]. However, when smaller sets of genes were examined, such as in a standard epilepsy panel or the ACMG list, the correlation was slightly weaker (_rs_ = 0.89 and _rs_ = 0.79, respectively). Importantly, high-nucleotide coverage (≥95%) did not guarantee equally high gene coverage, with some samples having fewer than half of genes completely covered (see the area to the right of the vertical dashed line in Fig. 3). This difference was more noticeable when looking at smaller samples of genes, such as the ACMG set.

### Correlation between complete gene subsets and CCDS nucleotide coverage.

Fig. 3.

The left panel summarizes the fraction of CCDS genes fully covered at 20× compared to the percentage of CCDS coding nucleotides covered at 20×. In the middle and right panels, the fraction of epilepsy genes and ACMG genes, respectively, are similarly summarized. Dotted lines show 95% coverage. Linear regression analysis was performed to determine coefficient of determination, R2. The fraction of each set of fully covered genes was determined for CCDS (n = 17723), epilepsy (n = 108), and ACMG (n = 57) (see online Data Supplement). Samples from each laboratory are designated as follows: A, circles; B, diamonds; C, triangles.

Fig. 3.

The left panel summarizes the fraction of CCDS genes fully covered at 20× compared to the percentage of CCDS coding nucleotides covered at 20×. In the middle and right panels, the fraction of epilepsy genes and ACMG genes, respectively, are similarly summarized. Dotted lines show 95% coverage. Linear regression analysis was performed to determine coefficient of determination, R2. The fraction of each set of fully covered genes was determined for CCDS (n = 17723), epilepsy (n = 108), and ACMG (n = 57) (see online Data Supplement). Samples from each laboratory are designated as follows: A, circles; B, diamonds; C, triangles.

Laboratory consistency was also determined by noting the genes that were always covered (≥20×) or never covered fully covered across all samples (Fig. 4). For laboratory A, only 2610 of 17723 genes were always covered (samples 1–12). For laboratories B and C, 4785 genes (samples 13–24) and 920 genes (samples 25–36) were fully covered across all samples, respectively. Only 253 genes were consistently covered among all 3 laboratories across all 36 samples. Similarly, when examining genes never fully covered, 1550 genes (samples 1–12), 2877 genes (samples 13–24), and 4969 genes (samples 25–36) were identified across all samples, for laboratories A, B, and C, respectively. The number of genes never covered across all 36 samples from the 3 laboratories was 468.

### Exome gene coverage consistency.

Fig. 4.

Venn diagrams illustrating the genes that are always fully covered or never fully covered by each lab across all 36 exome samples. Fully covered (left) was defined as coverage across all 12 exome data sets used for each lab. Labs A, B, and C had consistent coverage of 2610, 4785, and 920 genes, respectively. Never fully covered (right) was defined as incomplete coverage of genes in all 12 exome data sets used for each lab. Labs A, B, and C had consistent incomplete coverage of 1550, 2877, and 4969, respectively. The gene coverage consistency was evaluated out of a maximum possible 17723 CCDS genes assessed. Full coverage for these panels is defined as coverage at a minimum of 20× (reads per nucleotide position).

Fig. 4.

Venn diagrams illustrating the genes that are always fully covered or never fully covered by each lab across all 36 exome samples. Fully covered (left) was defined as coverage across all 12 exome data sets used for each lab. Labs A, B, and C had consistent coverage of 2610, 4785, and 920 genes, respectively. Never fully covered (right) was defined as incomplete coverage of genes in all 12 exome data sets used for each lab. Labs A, B, and C had consistent incomplete coverage of 1550, 2877, and 4969, respectively. The gene coverage consistency was evaluated out of a maximum possible 17723 CCDS genes assessed. Full coverage for these panels is defined as coverage at a minimum of 20× (reads per nucleotide position).

Poor consistency in exome testing could have a specific consequence in the examination of trios. Samples 7, 8, and 9 (laboratory A) were from the same biologic trio (proband, 7; parents, 8 and 9). The marked decrease in performance of sample 9 resulted in poor coverage across the exome and in the subsets of genes examined. A total of 2227 genes were poorly covered among all 3 exomes (see Fig. 1 in the online Data Supplement). The mother's exome (sample 9) had the worst coverage with 13887 of 17723 genes incompletely covered. As an example of the consequence of low-precision exome testing in trios, specific genomic locations with known clinical significance may be missed in a trio sample (see Fig. 1 in the online Data Supplement). In Fig. 2 in the online Data Supplement, the target regions of _BRCA1_7 exon 4 and _MLH1_ exon 3 are illustrated with the locations of known clinically significant variants (ClinVar) (the sample data are shown as individual sequencing reads; see bam file). Although the proband (sample 7) and father (sample 8) had coverage >20× in this region, the mother (sample 9) had 6× coverage at this location; 6× coverage is insufficient for variant calling. The lack of coverage in one trio sample decreases the utility of trio analysis for the discovery of inheritance patterns or de novo variants.

Discussion
----------

Using exome sequencing for clinical diagnosis requires recognition of the substantial possibility of inadequate depth and breadth of sequencing coverage at clinically relevant genomic locations. Inadequate coverage may contribute to false-negative clinical exome results. The comparison between laboratories identifies that some laboratories may have greater consistency in exome coverage. Other laboratories may have poor consistency in coverage, which leads to less reliability in the analytical performance of the exome test.

There are several limitations to this study. First, no analysis of duplicate samples was performed. Ideally, the same samples would have been sent repeatedly to all the laboratories; however, this study was limited to samples that had been run as part of clinical care. A future analysis including repeated measurements of the same reference material such as the National Institute of Standards and Technology genome reference material 8398 (Coriell cell line NA12878) (12) would be informative. Not only would the use of the same reference material decrease biologic variations that may exist between participants (i.e., sex), but genome reference material can allow examination of other important quality parameters such as precision of variant calling; variant calling was not examined in this study. A second limitation of this study is the limited number of samples that were surveyed (n = 36). This small survey may exaggerate the effects of specific time points or events that could have occurred in the laboratories. For example, the poor consistency seen in laboratories A and C may have occurred during a period of instrument service or reagent lot change. However, the findings in the study emphasize the importance of real-time assessment of exome precision, because these were all results deemed by the laboratories to be sufficient for clinical reports. Another limitation is the type of file provided by the laboratories. Laboratory B would only provide fastq files not bam files, so we had to construct our own bam files for the analysis. This action could affect the interlaboratory comparison, but it does not affect the intralaboratory variability.

Consistency is particularly important for trio assessment. Trio analysis is a combined exome analysis of the proband and both biologic parents to determine variant structure (cis vs trans) or whether a variant is inherited or de novo. Gene-specific variant locations must have similar assessments across trio samples. With low consistency, a trio analysis may artificially indicate that a variant in a proband is de novo, but in fact a variant location is not assessed (not covered) in either parent.

A possible application of the findings of this study would be to expand the current College of American Pathologists Proficiency Testing Program for Next-Generation Sequencing (CAP NGS PT). Currently, this program sends blinded genomic proficiency testing material to laboratories and grades laboratories on their ability to identify a specific variant at a genomic location. This type of PT program could be expanded to include laboratories submitting data files (i.e., bam) to examine the coverage consistency between laboratories. In addition, as part of on-going quality measures, clinical laboratories should be required to document the intersample consistency by measures demonstrated by this study (i.e., control plotting). Accreditation and regulatory inspectors could rapidly audit control plots to assess the intersample coverage quality and the overall performance of the laboratory. Although genomic testing is complex, traditional quality-control tools such as control charting may be useful in visually demonstrating the importance of intersample sequencing assessment for entire genes or specific variant locations.

Regardless of regulatory requirements, laboratories should seek to continuously improve the consistency of their exome-testing performance. The use of average measurements in large data sets such as exome/genome is only meaningful when the average is further described in combination with other summary statistics such as standard deviation and coefficient of variation. Additional statistics such as genes completely covered will also allow a more accurate assessment of the test's validity and would pressure clinical laboratories to achieve higher consistency.

From a clinical perspective, providers and patients should demand more complete coverage information from the clinical exome laboratories they plan on using. Certainly, there is value in knowing a laboratory has high consistency (laboratory B) vs poor consistency (laboratory C). Consistency directly affects the genes that are completely covered. The highest number of CCDS genes completely covered across all samples was 15196 (sample 7); in comparison, the lowest number of completely covered CCDS genes was 3139 (sample 31). This 4.8-fold difference should be carefully considered when testing patients for rare or undiagnosed genetic diseases. A negative or nondiagnostic exome test should prompt a provider to assess the laboratory's completeness of gene coverage and rule out the possibility of a false-negative result. In addition, the low number of genes completely covered in smaller sets suggests caution be used when using exome sequencing in place of smaller gene sequencing panels.

7

Human Genes:

 *   _BRCA1_
    
    BRCA1 DNA repair associated
    
 *   _MLH1_
    

(see editorial on page 9)

**Author Contributions:** _All authors confirmed they have contributed to the intellectual content of this paper and have met the following 4 requirements: (a) significant contributions to the conception and design, acquisition of data, or analysis and interpretation of data; (b) drafting or revising the article for intellectual content; (c) final approval of the published article; and (d) agreement to be accountable for all aspects of the article thus ensuring that questions related to the accuracy or integrity of any part of the article are appropriately investigated and resolved._

G. Gotway, provision of study material or patients; J. Kozlitina, statistical analysis; C. Xing, statistical analysis; C. Hornbuckle, administrative support, provision of study material or patients; D. Michel, administrative support, provision of study material or patients; C. Uhles, provision of study material or patients; J.Y. Park, financial support, administrative support.

**Authors' Disclosures or Potential Conflicts of Interest:** _Upon manuscript submission, all authors completed the author disclosure form. Disclosures and/or potential conflicts of interest:_

**Employment or Leadership:** E. Crossley, Children's Health; C. Hornbuckle, Children's Health; D. Michel, Children's Health; C. Uhles, Children's Health; J.Y. Park, _Clinical Chemistry_, AACC.

**Consultant or Advisory Role:** J.Y. Park, Miraca Holdings. Subsidiaries of Miraca include Baylor Genetics and Fujirebio, Inc.

**Stock Ownership:** None declared.

**Honoraria:** None declared.

**Research Funding:** None declared.

**Expert Testimony:** None declared.

**Patents:** None declared.

**Role of Sponsor:** No sponsor was declared.

References
----------

1.

, et al. 

Clinical whole-exome sequencing for the diagnosis of Mendelian disorders

.

N Engl J Med

 

2013

;

369

:

1502

–

11

.

2.

, et al. 

Molecular findings among patients referred for clinical whole-exome sequencing

.

JAMA

 

2014

;

312

:

1870

–

9

.

3.

, et al. 

Use of exome sequencing for infants in intensive care units: ascertainment of severe single-gene disorders and effect on medical management

.

JAMA Pediatr

 

2017

;

171

:

e173438

.

4.

, et al. 

Clinical interpretation and implications of whole-genome sequencing

.

JAMA

 

2014

;

311

:

1035

–

45

.

5.

.

Clinical exome performance for reporting secondary genetic findings

.

Clin Chem

 

2015

;

61

:

213

–

20

.

6.

, et al. 

Achieving high-sensitivity for clinical applications using augmented exome sequencing

.

Genome Med

 

2015

;

7

:

71

.

7.

, et al. 

Practices and policies of clinical exome sequencing providers: analysis and implications

.

Am J Med Genet A

 

2013

;

161A

:

935

–

50

.

8.

, et al. 

Recommendations for reporting of secondary findings in clinical exome and genome sequencing, 2016 update (ACMG SF v2.0): a policy statement of the American College of Medical Genetics and Genomics

.

Genet Med

 

2017

;

19

:

249

–

55

.

9.

.

Variant detection sensitivity and biases in whole genome and exome sequencing

.

BMC Bioinformatics

 

2014

;

15

:

247

.

10.

.

Quantifying single nucleotide variant detection sensitivity in exome sequencing

.

BMC Bioinformatics

 

2013

;

14

:

195

.

11.

.

Quality control of the analytical examination process

. In:

, eds.

Tietz textbook of clinical chemistry and molecular diagnostics

 .

St Louis, MO

:

Elsevier

;

2018

. p.

126

–

37

.

12.

, et al. 

Medical implications of technical accuracy in genome sequencing

.

Genome Med

 

2016

;

8

:

24

.

© 2019 American Association for Clinical Chemistry

  
  
from Hacker News https://ift.tt/2ZWn33g