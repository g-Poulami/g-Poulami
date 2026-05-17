# Poulami Ghosh | Computational Researcher

**Bioinformatics | Machine Learning | Research Software Engineering**

I am a computational researcher with expertise in statistical modelling, machine learning, and high-dimensional data analysis. I specialise in designing reproducible pipelines for multi-modal and multi-omics data, with a research focus on the genomic and epidemiological determinants of early-onset and hereditary breast cancer, and a clinical application background spanning paediatric oncology and cancer genomics more broadly. My work increasingly intersects with genomic equity — building tools and analyses that are robust across diverse ancestral populations and that interrogate biological questions with causal, not just correlative, rigour.

---

## Research Interests

I am interested in the molecular mechanisms that distinguish early-onset and hereditary breast cancer from sporadic, late-onset disease. My computational work is organised around three questions: what mutational processes drive tumourigenesis in young patients; how germline variants interact with somatic landscapes to shape tumour evolution and clinical outcome; and how genomic tools can be built to remain valid and equitable across diverse ancestral populations. I approach these questions through reproducible pipeline engineering, statistical genomics, causal inference, and close attention to the limits of what data-driven methods can and cannot claim.

---

## Technical Expertise

| Category | Skills & Tools |
| --- | --- |
| **Languages** | Python, R, Bash, C/C++, SQL, MATLAB |
| **Machine Learning** | PyTorch, TensorFlow, Scikit-learn, U-Net, ResNet, SimCLR, MoCo, VAE, CausalPy/DoWhy |
| **Bioinformatics** | PLINK, Nextflow DSL2, Snakemake, BWA/BWA-MEM2, STAR, GATK, Samtools, Multi-omics integration |
| **Infrastructure** | AWS (EC2, S3, RDS, Lambda, KMS), Linux/HPC (BlueBEAR), Docker, Docker Compose, CI/CD |
| **Visualization** | Tableau, Chart.js, ggplot2/qqman, HTML |

---

## Public Repositories & Open-Source Projects

---

### Bioinformatics & Clinical Pipelines

- **[COSMIC-Signatures-EarlyOnset-BRCA](https://github.com/g-Poulami/COSMIC-Signatures-EarlyOnset-BRCA)**: Does the mutagenic fingerprint of a breast tumour differ between young and older patients? End-to-end COSMIC v3.3.1 signature analysis across 992 TCGA-BRCA whole-exome sequencing samples — comparing APOBEC, HRD, and clock-like signature exposures between early-onset (≤45) and late-onset (≥55) breast cancer using MutationalPatterns refitting, Mann-Whitney U testing, and Benjamini-Hochberg FDR correction. Delivers a reproducible null result with full biological interpretation: no signature survives FDR correction in pooled WXS data, pointing toward the need for subtype-stratified WGS analyses.

- **[Germline-Variant-QC-BRCA](https://github.com/g-Poulami/Germline-Variant-QC-BRCA)**: What inherited variants predispose individuals to breast cancer — and how do we find them reliably in an ancestrally heterogeneous cohort? A reproducible Snakemake pipeline implementing GWAS-standard germline variant QC (MAF, missingness, HWE filtering) followed by PCA-based ancestry stratification of TCGA-BRCA samples. Demonstrates that unadjusted association analyses on this cohort would be confounded by population structure — validating the necessity of ancestry correction before any hereditary risk inference.

- **[Breast-Cancer-Survival-Risk-Model](https://github.com/g-Poulami/Breast-Cancer-Survival-Risk-Model)**: How much does the molecular identity of a breast tumour matter for survival, beyond clinical stage alone? Survival risk stratification model on the METABRIC cohort (~2,000 patients) combining Kaplan-Meier estimators, Cox Proportional Hazards modelling, and PCA over 20,000+ gene expression features. Integrating 50 genomic PCs improves held-out C-index from 0.654 to 0.663; PAM50 + Claudin-low subtype stratification reveals dramatically divergent survival trajectories with Basal-like tumours showing the steepest early mortality.

- **[GenEquityFlow](https://github.com/g-Poulami/GenEquityFlow)**: If a biomarker discovered in a European-majority cohort is applied to a patient of African or East Asian ancestry, how likely is it to give the wrong answer? Ancestry-aware Snakemake pipeline quantifying the "Generalisability Gap" — the difference in protein-altering variant frequencies and clinical annotation density across EUR, AFR, EAS, SAS, and AMR populations. Ten-step workflow: BWA-MEM alignment → BCFtools variant calling → quality filtering → functional annotation → population-level gap analysis. Finds the largest Generalisability Gaps between AFR and EUR populations, providing quantitative evidence for the clinical equity problem in cancer genomics.

- **[Genomic-Analysis-Pipeline-on-AWS](https://github.com/g-Poulami/Genomic-Analysis-Pipeline-on-AWS)**: Production-grade R framework for multi-ethnic cancer mutational analysis at scale, with HIPAA-compliant security infrastructure. VCF loading from S3, QC reporting, functional annotation against gnomAD/ClinVar/COSMIC, and population-specific allele frequency analysis (EUR, AFR, EAS, SAS, AMR). AWS KMS encryption, SHA-256 sample anonymisation, and full audit logging. Deployable via Docker to EC2/ECS with AWS Lambda and Batch integration.

- **[cfDNA-CNV-Pipeline](https://github.com/g-Poulami/cfDNA-CNV-Pipeline)**: Can genomic instability in breast cancer be detected from a blood draw rather than a tumour biopsy? Specialised workflow for detecting Copy Number Variations from cell-free DNA, supporting liquid biopsy research as a minimally invasive alternative to tissue-based genomic profiling.

*See also:* [Somatic-Variant-Calling-Nextflow](https://github.com/g-Poulami/Somatic-Variant-Calling-Nextflow)

---

### Pipeline Engineering (Nextflow DSL2 & Docker)

- **[nf-gatk-pipeline](https://github.com/g-Poulami/nf-gatk-pipeline)**: Production-grade Nextflow DSL2 germline variant calling pipeline implementing the GATK best-practices workflow end-to-end: FastQC → Trimmomatic → BWA-MEM2 → SAMtools → Picard MarkDuplicates → GATK BQSR → HaplotypeCaller → GenotypeGVCFs → VariantFiltration → MultiQC. Supports SLURM, Docker, Singularity, and conda profiles; optional joint genotyping; GitHub Actions CI with stub-run testing.

- **[nf-align-pipeline](https://github.com/g-Poulami/nf-align-pipeline)**: Modular Nextflow DSL2 short-read alignment pipeline demonstrating DSL2 module reuse patterns: FastQC → Trimmomatic → BWA MEM → SAMtools sort/index/flagstat → MultiQC. Supports Docker, Singularity, conda, and SLURM profiles with configurable adapter trimming and read group tagging.

- **[docker-pipeline](https://github.com/g-Poulami/docker-pipeline)**: Variant calling pipeline orchestrated entirely with Docker Compose — FastQC, Trimmomatic, BWA, SAMtools, GATK HaplotypeCaller, and MultiQC each run in optimised multi-stage containers (~45 MB BWA image). Named volumes for intermediate data, non-root container users, and GitHub Actions CI.

- **[RNA-seq-QC-Pipeline](https://github.com/g-Poulami/RNA-seq-QC-Pipeline)**: Containerised, reproducible transcriptomic quality control pipeline featuring a four-step Snakemake DAG. Deployable on AWS, GCP, and SLURM HPC environments.

---

### Machine Learning & Statistical Modelling

- **[Simclr-v1-50k-automated-pipeline](https://github.com/roy-arindam-1991/Simclr-v1-50k-automated-pipeline)**: Can visual representations be learned without labels — and how far does self-supervised contrastive learning go on a 50k-sample dataset? End-to-end automated pipeline implementing SimCLR v1 (Chen et al., 2020): stochastic data augmentation, a shared ResNet encoder, an MLP projection head, and NT-Xent contrastive loss optimisation. The pipeline automates training, checkpointing, and linear evaluation on 50,000 samples, providing a reproducible benchmark for label-efficient representation learning.

- **[MoCo-v2-50k-automated-pipeline](https://github.com/roy-arindam-1991/MoCo-v2-50k-automated-pipeline)**: How does Momentum Contrast compare to SimCLR when memory efficiency matters? Automated pipeline implementing MoCo v2 (Chen et al., 2020) — a momentum encoder updated via exponential moving average, a dynamic negative-sample queue of up to 65,536 keys, and an MLP projection head — trained on 50,000 samples. Designed for direct comparison with SimCLR v1 under matched data conditions, enabling controlled evaluation of contrastive learning strategies that differ in memory footprint and batch-size sensitivity.

- **[scVAE-State](https://github.com/g-Poulami/scVAE-State)**: What does the transcriptomic landscape of individual immune cells reveal about cellular state heterogeneity? Deep generative model of single-cell RNA-seq data using a custom PyTorch Variational Autoencoder trained on 10x Genomics PBMC 3k data. Softplus-activated decoder for non-negative count reconstruction; UMAP latent manifold visualisation; immune cell state validation using canonical marker genes (CD3E, MS4A1, LYZ).

- **[causal-gene-expression](https://github.com/g-Poulami/causal-gene-expression)**: When a drug changes gene expression, how do we know the effect is causal rather than a consequence of batch effects or co-expressed confounders? Causal inference framework using DoWhy structural DAGs and the backdoor criterion, with CausalPy/PyMC for Bayesian counterfactual estimation. Quantifies a ~1.91 unit causal effect of Drug X on EGFR expression, validated by placebo treatment refutation (effect drops to ~−0.01).

- **[Diffusion-Models-for-Molecular-Generation](https://github.com/g-Poulami/Diffusion-Models-for-Molecular-Generation)**: De novo molecular design using 2D graph diffusion. CI/CD via GitHub Actions with automated chemical validity testing using RDKit.

---

### Medical Imaging & Dashboards

- **[Neuroimaging_Dashboard](https://github.com/g-Poulami/Neuroimaging_Dashboard)**: [Live site](https://g-poulami.github.io/Neuroimaging_Dashboard/) visualising MRI/MRS data and survival analysis for paediatric neuro-oncology research.

---

## Selected Publications & Presentations

- **Journal Article**: Apps J.R., ..., **Ghosh P.**, et al. (2026) "Imaging of Tumours Study: Past, Present and Future." *Journal of Neuro-Oncology* (Submitted).
- **Conference Paper**: **Ghosh P.** and Sarkar A. (2023) "Characterization of Simple Sequence Repeats: Evolutionary Implications from Ancient Human Mitochondrial Genome." *Artificial Intelligence, CCIS*, vol. 1695, pp. 36–43. Springer Nature.
- **Preprint**: **Ghosh P.** and Sarkar A. (2024) "Identification and analysis of microsatellites in Coronaviridae." *Authorea*.
- **Presentation**: Poster Delegate, Birmingham Brain Tumour Network Symposium (Nov 2025).

---

## Education & Professional Experience

- **MSc Bioinformatics (Merit)** | University of Birmingham, UK (2024–2025)
- **MTech Computer Technology (1st Class)** | Jadavpur University, India (2019–2022)
- **BTech Electronics & Communication Engineering (1st Class)** | MAKAUT, India (2015–2019)
- **Project Associate-I** | CSIR – Indian Institute of Chemical Biology, India (2022–2024)
  - Developed automated pipelines for multi-omics data analysis and mentored students in machine learning applications.

---

## Contact & Links

- **LinkedIn**: [linkedin.com/in/poulami-ghosh-879439304](https://linkedin.com/in/poulami-ghosh-879439304)
- **Email**: poulamighosh738@gmail.com
