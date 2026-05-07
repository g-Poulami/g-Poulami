## Poulami Ghosh | Computational Researcher

**Bioinformatics | Machine Learning | Research Software Engineering**

I am a computational researcher with expertise in statistical modelling, machine learning, and high-dimensional data analysis. I specialize in designing reproducible pipelines for multi-modal and multi-omics data, with a professional focus on applying quantitative methods to clinical challenges, particularly in paediatric oncology. My work increasingly intersects with genomic equity — building tools and analyses that are robust across diverse ancestral populations and that interrogate biological questions with causal, not just correlative, rigour.

---

### Technical Expertise

| Category | Skills & Tools |
| --- | --- |
| **Languages** | Python, R, Bash, C/C++, SQL, MATLAB |
| **Machine Learning** | PyTorch, TensorFlow, Scikit-learn, U-Net, ResNet, SimCLR, VAE, CausalPy/DoWhy |
| **Bioinformatics** | PLINK, Nextflow DSL2, Snakemake, BWA/BWA-MEM2, STAR, GATK, Samtools, Multi-omics integration |
| **Infrastructure** | AWS (EC2, S3, RDS, Lambda, KMS), Linux/HPC (BlueBEAR), Docker, Docker Compose, CI/CD |
| **Visualization** | Tableau, Chart.js, ggplot2/qqman, HTML |

---

### Public Repositories & Open-Source Projects

---

#### Bioinformatics & Clinical Pipelines

- **[COSMIC-Signatures-EarlyOnset-BRCA](https://github.com/g-Poulami/COSMIC-Signatures-EarlyOnset-BRCA)**: End-to-end analysis of COSMIC v3.3.1 mutational signatures in 992 TCGA-BRCA whole-exome sequencing samples, comparing early-onset (≤45 years) vs late-onset (≥55 years) breast cancer. Combines MutationalPatterns refitting with Mann-Whitney U testing and Benjamini-Hochberg FDR correction to identify age-specific mutagenic mechanisms (APOBEC, HRD, clock-like signatures). Produces a full suite of visualisations: 96-channel trinucleotide spectra, per-sample stacked signature bars, clustered exposure heatmaps, group boxplots, and a volcano plot.

- **[Germline-Variant-QC-BRCA](https://github.com/g-Poulami/Germline-Variant-QC-BRCA)**: A reproducible Snakemake pipeline for Quality Control and population stratification of BRCA germline variants. Features automated PCA for ancestry correction and GWAS association mapping with Manhattan/Q-Q plot visualizations.

- **[Breast-Cancer-Survival-Risk-Model](https://github.com/g-Poulami/Breast-Cancer-Survival-Risk-Model)**: Clinical and genomic survival risk stratification model built on the METABRIC breast cancer dataset (~2,000 patients). Combines Kaplan-Meier estimators, Cox Proportional Hazards modelling, and PCA over 20,000+ gene expression features to stratify patients by molecular subtype (PAM50 + Claudin-low). Demonstrates how integrating 50 genomic PCs over clinical features improves held-out C-index from 0.6536 to 0.6634.

- **[Genomic-Sequence-Variation-Analysis](https://github.com/g-Poulami/Genomic-Sequence-Variation-Analysis)**: R pipeline for analysing SNP variation across bacterial and ancient human genomic datasets from VCF input. Covers quality filtering, PCA with LD pruning, pairwise FST, ADMIXTURE parsing, neighbour-joining phylogenetics with bootstrap support, and publication-quality visualisation. Supports both bacterial and ancient-DNA modes with configurable deamination filtering.

- **[Genomic-Analysis-Pipeline-on-AWS](https://github.com/g-Poulami/Genomic-Analysis-Pipeline-on-AWS)**: Production-grade R framework for multi-ethnic cancer mutational analysis with secure cloud data management. Features VCF loading from S3, QC reporting, functional annotation against gnomAD/ClinVar/COSMIC, population-specific allele frequency analysis (EUR, AFR, EAS, SAS, AMR), and HIPAA-compliant security (AWS KMS encryption, audit logging, SHA-256 anonymisation). Deployable via Docker to EC2/ECS with AWS Lambda and Batch integration.

- **[cfDNA-CNV-Pipeline](https://github.com/g-Poulami/cfDNA-CNV-Pipeline)**: A specialized workflow engineered for detecting Copy Number Variations from cell-free DNA to support liquid biopsy research.

- **[GenEquityFlow](https://github.com/g-Poulami/GenEquityFlow)**: Ancestry-aware biomarker analysis pipeline designed to quantify the "Generalisability Gap" in cancer genomics — the degree to which biomarker frequencies and clinical findings differ across ancestral populations (EUR, AFR, EAS, SAS, AMR). Orchestrated with Snakemake, the ten-step workflow runs BWA-MEM alignment → BCFtools variant calling → quality filtering (QUAL > 30) → functional annotation of protein-altering mutations → population-level gap analysis with Python/Pandas, producing CSV reports and visualisations. Fully reproducible with conda environments and GitHub Actions CI.

*See also:* [Somatic-Variant-Calling-Nextflow](https://github.com/g-Poulami/Somatic-Variant-Calling-Nextflow)

---

#### Pipeline Engineering (Nextflow DSL2 & Docker)

- **[nf-gatk-pipeline](https://github.com/g-Poulami/nf-gatk-pipeline)**: Production-grade Nextflow DSL2 germline variant calling pipeline: FastQC → Trimmomatic → BWA-MEM2 → SAMtools → Picard MarkDuplicates → GATK BQSR → HaplotypeCaller → GenotypeGVCFs → VariantFiltration → MultiQC. Supports SLURM, Docker, Singularity, and conda profiles; optional joint genotyping; and includes GitHub Actions CI with stub-run testing.

- **[nf-align-pipeline](https://github.com/g-Poulami/nf-align-pipeline)**: Modular Nextflow DSL2 short-read alignment pipeline: FastQC → Trimmomatic → BWA MEM → SAMtools sort/index/flagstat → MultiQC. Demonstrates DSL2 module reuse patterns and supports Docker, Singularity, conda, and SLURM profiles with configurable adapter trimming and read group tagging.

- **[docker-pipeline](https://github.com/g-Poulami/docker-pipeline)**: Variant calling pipeline orchestrated entirely with Docker Compose — FastQC, Trimmomatic, BWA, SAMtools, GATK HaplotypeCaller, and MultiQC each run in optimised multi-stage containers (~45 MB BWA image). Uses named volumes for intermediate data, non-root container users, and GitHub Actions CI.

- **[RNA-seq-QC-Pipeline](https://github.com/g-Poulami/RNA-seq-QC-Pipeline)**: A containerized, reproducible bioinformatics pipeline for transcriptomic quality control featuring a four-step DAG.

*See also:* [Nextflow-RNA-seq-Pipeline](https://github.com/g-Poulami/Nextflow-RNA-seq-Pipeline) · [Snakemake-Genomic-Pipeline](https://github.com/g-Poulami/Snakemake-Genomic-Pipeline)

---

#### Machine Learning & Statistical Modelling

- **[scVAE-State](https://github.com/g-Poulami/scVAE-State)**: Deep generative modelling of cellular heterogeneity using a custom Variational Autoencoder trained on 10x Genomics PBMC 3k scRNA-seq data. Features biological QC (mitochondrial filtering), a PyTorch VAE with Softplus-activated decoder for non-negative count reconstruction, and UMAP latent manifold visualisation. Validates learned immune cell states using canonical marker genes (CD3E, MS4A1, LYZ).

- **[causal-gene-expression](https://github.com/g-Poulami/causal-gene-expression)**: Causal inference framework for distinguishing drug-induced transcriptomic changes from batch effects and co-expression confounders. Constructs a structural DAG with DoWhy to apply the backdoor criterion, then uses CausalPy/PyMC for Bayesian counterfactual estimation, quantifying a ~1.91 unit causal effect of Drug X on EGFR expression. Validated by placebo treatment refutation (effect drops to ~−0.01). CI via GitHub Actions.

- **[Diffusion-Models-for-Molecular-Generation](https://github.com/g-Poulami/Diffusion-Models-for-Molecular-Generation)**: De novo design of molecules using 2D graph diffusion. Integrated CI/CD via GitHub Actions to automate chemical validity testing with RDKit.

---

#### Medical Imaging & Dashboards

- **[Neuroimaging_Dashboard](https://github.com/g-Poulami/Neuroimaging_Dashboard)**: Live site visualizing MRI/MRS data and survival analysis for paediatric neuro-oncology research.

---

### Selected Publications & Presentations

- **Journal Article**: Apps J.R., ..., **Ghosh P.**, et al. (2026) "Imaging of Tumours Study: Past, Present and Future." *Journal of Neuro-Oncology* (Submitted).
- **Conference Paper**: **Ghosh P.** and Sarkar A. (2023) "Characterization of Simple Sequence Repeats: Evolutionary Implications from Ancient Human Mitochondrial Genome." *Artificial Intelligence, CCIS*, vol. 1695, pp. 36-43. Springer Nature.
- **Preprint**: **Ghosh P.** and Sarkar A. (2024) "Identification and analysis of microsatellites in Coronaviridae." *Authorea*.
- **Presentation**: Poster Delegate, Birmingham Brain Tumour Network Symposium (Nov 2025).

---

### Education & Professional Experience

- **MSc Bioinformatics (Merit)** | University of Birmingham, UK (2024–2025)
- **MTech Computer Technology (1st Class)** | Jadavpur University, India (2019–2022)
- **BTech Electronics & Communication Engineering (1st Class)** | MAKAUT, India (2015–2019)
- **Project Associate-I** | CSIR – Indian Institute of Chemical Biology, India (2022–2024)
  * Developed automated pipelines for multi-omics and mentored students in ML applications.

---

### Contact & Links

- **LinkedIn**: [linkedin.com/in/poulami-ghosh-879439304](https://linkedin.com/in/poulami-ghosh-879439304)
- **Google Scholar**: Poulami Ghosh
- **Email**: poulamighosh738@gmail.com
