# Poulami Ghosh

**Computational Researcher** · Bioinformatics · Machine Learning · Research Software Engineering

I am a computational researcher with expertise in statistical modelling, machine learning, and high-dimensional data analysis. I specialise in designing reproducible pipelines for multi-modal and multi-omics data, with a research focus on the genomic and epidemiological determinants of early-onset and hereditary breast cancer, and a clinical application background spanning paediatric oncology and cancer genomics more broadly. My work increasingly intersects with genomic equity: building tools and analyses that are robust across diverse ancestral populations and that interrogate biological questions with causal, not just correlative, rigour.

## Research interests

I study the molecular mechanisms that distinguish early-onset and hereditary breast cancer from sporadic, late-onset disease. My computational work is organised around three questions: what mutational processes drive tumourigenesis in young patients; how germline variants interact with somatic landscapes to shape tumour evolution and clinical outcome; and how genomic tools can be built to remain valid and equitable across diverse ancestral populations. I approach these questions through reproducible pipeline engineering, statistical genomics, causal inference, and close attention to the limits of what data-driven methods can and cannot claim.

## Technical expertise

| Category | Skills and tools |
| --- | --- |
| **Languages** | Python, R, Bash, C/C++, SQL, MATLAB |
| **Machine learning** | PyTorch, TensorFlow, Scikit-learn, U-Net, ResNet, SimCLR, MoCo, VAE, CausalPy/DoWhy |
| **Bioinformatics** | PLINK, Nextflow DSL2, Snakemake, BWA/BWA-MEM2, STAR, GATK, Samtools, multi-omics integration |
| **Infrastructure** | AWS (EC2, S3, RDS, Lambda, KMS), Linux/HPC (BlueBEAR), Docker, Docker Compose, CI/CD |
| **Visualisation** | Tableau, Chart.js, ggplot2/qqman, HTML |

## Selected repositories

### Bioinformatics and clinical pipelines

- **[Genomic-Sequence-Variation-Analysis](https://github.com/g-Poulami/Genomic-Sequence-Variation-Analysis)**: how genetic variation differs across individuals and populations, and what it reveals about ancestry, population structure, and evolutionary history. An end-to-end R pipeline for SNP variation from multi-sample VCF input, built for two domains (bacterial genomics and ancient human DNA). Covers quality filtering (QUAL, depth, missingness, MAF), PCA with LD pruning, pairwise Weir and Cockerham FST, ADMIXTURE parsing with CV-error selection of optimal K, neighbour-joining phylogenetics with bootstrap support, and aDNA-specific processing (pseudo-haploid calling, C>T/G>A deamination reporting, mapDamage2 integration). Seven modular R scripts orchestrated by one master pipeline.
- **[COSMIC-Signatures-EarlyOnset-BRCA](https://github.com/g-Poulami/COSMIC-Signatures-EarlyOnset-BRCA)**: does the mutagenic fingerprint of a breast tumour differ between young and older patients? COSMIC v3.3.1 signature analysis across 992 TCGA-BRCA whole-exome samples, comparing APOBEC, HRD, and clock-like signature exposures between early-onset (≤45) and late-onset (≥55) disease using MutationalPatterns refitting, Mann-Whitney U testing, and Benjamini-Hochberg correction. A reproducible null result with full biological interpretation: no signature survives FDR correction in pooled WXS data, motivating subtype-stratified WGS analyses.
- **[Germline-Variant-QC-BRCA](https://github.com/g-Poulami/Germline-Variant-QC-BRCA)**: what inherited variants predispose individuals to breast cancer, and how do we find them reliably in an ancestrally heterogeneous cohort? A Snakemake pipeline implementing GWAS-standard germline variant QC (MAF, missingness, HWE) followed by PCA-based ancestry stratification of TCGA-BRCA samples, demonstrating that unadjusted association analyses on this cohort would be confounded by population structure.
- **[Breast-Cancer-Survival-Risk-Model](https://github.com/g-Poulami/Breast-Cancer-Survival-Risk-Model)**: how much does the molecular identity of a tumour matter for survival, beyond clinical stage alone? Survival risk stratification on the METABRIC cohort (~2,000 patients) combining Kaplan-Meier estimators, Cox proportional hazards modelling, and PCA over 20,000+ gene expression features. Integrating 50 genomic PCs improves held-out C-index from 0.654 to 0.663; PAM50 and Claudin-low subtype stratification reveals divergent survival trajectories, with Basal-like tumours showing the steepest early mortality.
- **[GenEquityFlow](https://github.com/g-Poulami/GenEquityFlow)**: if a biomarker discovered in a European-majority cohort is applied to a patient of African or East Asian ancestry, how likely is it to give the wrong answer? An ancestry-aware Snakemake pipeline quantifying the generalisability gap in protein-altering variant frequencies and clinical annotation density across EUR, AFR, EAS, SAS, and AMR populations (BWA-MEM alignment, BCFtools calling, quality filtering, functional annotation, population-level gap analysis). The largest gaps appear between AFR and EUR populations.
- **[Genomic-Analysis-Pipeline-on-AWS](https://github.com/g-Poulami/Genomic-Analysis-Pipeline-on-AWS)**: a production-grade R framework for multi-ethnic cancer mutational analysis at scale with HIPAA-compliant security. VCF loading from S3, QC reporting, annotation against gnomAD/ClinVar/COSMIC, and population-specific allele frequency analysis, with AWS KMS encryption, SHA-256 sample anonymisation, and full audit logging. Deployable via Docker to EC2/ECS with Lambda and Batch integration.
- **[cfDNA-CNV-Pipeline](https://github.com/g-Poulami/cfDNA-CNV-Pipeline)**: can genomic instability in breast cancer be detected from a blood draw rather than a tumour biopsy? A workflow for detecting copy number variations from cell-free DNA, supporting liquid biopsy as a minimally invasive alternative to tissue-based profiling.

### Pipeline engineering (Nextflow DSL2 and Docker)

- **[nf-gatk-pipeline](https://github.com/g-Poulami/nf-gatk-pipeline)**: a production-grade Nextflow DSL2 germline variant calling pipeline implementing the GATK best-practices workflow end to end: FastQC, Trimmomatic, BWA-MEM2, SAMtools, Picard MarkDuplicates, GATK BQSR, HaplotypeCaller, GenotypeGVCFs, VariantFiltration, MultiQC. Supports SLURM, Docker, Singularity, and conda profiles, optional joint genotyping, and GitHub Actions CI with stub-run testing.
- **[nf-align-pipeline](https://github.com/g-Poulami/nf-align-pipeline)**: a modular Nextflow DSL2 short-read alignment pipeline demonstrating DSL2 module reuse: FastQC, Trimmomatic, BWA-MEM, SAMtools sort/index/flagstat, MultiQC. Supports Docker, Singularity, conda, and SLURM profiles with configurable adapter trimming and read group tagging.
- **[docker-pipeline](https://github.com/g-Poulami/docker-pipeline)**: a variant calling pipeline orchestrated entirely with Docker Compose: FastQC, Trimmomatic, BWA, SAMtools, GATK HaplotypeCaller, and MultiQC, each in optimised multi-stage containers (~45 MB BWA image), with named volumes, non-root container users, and GitHub Actions CI.
- **[RNA-seq-QC-Pipeline](https://github.com/g-Poulami/RNA-seq-QC-Pipeline)**: a containerised transcriptomic quality control pipeline built as a four-step Snakemake DAG, deployable on AWS, GCP, and SLURM HPC environments.

### Machine learning and statistical modelling

- **[Simclr-v1-50k-automated-pipeline](https://github.com/g-Poulami/Simclr-v1-50k-automated-pipeline)** *(collaborative work with Arindam Roy)*: can visual representations be learned without labels, and how far does self-supervised contrastive learning go on a 50k-sample dataset? An end-to-end automated pipeline implementing SimCLR v1 (Chen et al., 2020): stochastic augmentation, a shared ResNet encoder, an MLP projection head, and NT-Xent contrastive loss, with automated training, checkpointing, and linear evaluation on 50,000 samples.
- **[MoCo-v2-50k-automated-pipeline](https://github.com/g-Poulami/MoCo-v2-50k-automated-pipeline)** *(collaborative work with Arindam Roy)*: how does Momentum Contrast compare to SimCLR when memory efficiency matters? An automated pipeline implementing MoCo v2 (Chen et al., 2020): a momentum encoder updated via exponential moving average, a dynamic negative-sample queue of up to 65,536 keys, and an MLP projection head, trained on 50,000 samples for controlled comparison with SimCLR v1 under matched data conditions.
- **[scVAE-State](https://github.com/g-Poulami/scVAE-State)**: what does the transcriptomic landscape of individual immune cells reveal about cellular state heterogeneity? A deep generative model of single-cell RNA-seq using a custom PyTorch variational autoencoder trained on 10x Genomics PBMC 3k data, with a Softplus-activated decoder for non-negative count reconstruction, UMAP latent manifold visualisation, and immune cell state validation using canonical markers (CD3E, MS4A1, LYZ).
- **[causal-gene-expression](https://github.com/g-Poulami/causal-gene-expression)**: when a drug changes gene expression, how do we know the effect is causal rather than a consequence of batch effects or co-expressed confounders? A causal inference framework using DoWhy structural DAGs and the backdoor criterion, with CausalPy/PyMC for Bayesian counterfactual estimation, quantifying a ~1.91 unit causal effect of Drug X on EGFR expression, validated by placebo refutation (effect drops to ~−0.01).
- **[Diffusion-Models-for-Molecular-Generation](https://github.com/g-Poulami/Diffusion-Models-for-Molecular-Generation)**: de novo molecular design using 2D graph diffusion, with CI/CD via GitHub Actions and automated chemical validity testing using RDKit.

### Medical imaging and dashboards

- **[Neuroimaging_Dashboard](https://github.com/g-Poulami/Neuroimaging_Dashboard)**: a live site visualising MRI/MRS data and survival analysis for paediatric neuro-oncology research.

## Selected publications and presentations

- **Journal article:** Apps J.R., ..., Ghosh P., et al. (2026). *Imaging of Tumours Study: Past, Present and Future.* Journal of Neuro-Oncology (submitted).
- **Preprint:** Roy A., Ghosh P., et al. (2026). *Breaking the Bottleneck: a self-supervised deep learning framework for fully automated fossil CT segmentation.* bioRxiv. [doi:10.64898/2026.06.07.730692](https://www.biorxiv.org/content/10.64898/2026.06.07.730692v1)
- **Conference paper:** Ghosh P. and Sarkar A. (2023). *Characterization of Simple Sequence Repeats: Evolutionary Implications from Ancient Human Mitochondrial Genome.* Artificial Intelligence, CCIS, vol. 1695, pp. 36–43. Springer Nature.
- **Preprint:** Ghosh P. and Sarkar A. (2024). *Identification and analysis of microsatellites in Coronaviridae.* Authorea.
- **Presentation:** Poster delegate, Birmingham Brain Tumour Network Symposium (November 2025).

## Education and experience

- **MSc Bioinformatics (Merit)**, University of Birmingham, UK (2024–2025)
- **MTech Computer Technology (First Class)**, Jadavpur University, India (2019–2022)
- **BTech Electronics and Communication Engineering (First Class)**, MAKAUT, India (2015–2019)
- **Project Associate-I**, CSIR, Indian Institute of Chemical Biology, India (2022–2024). Developed automated pipelines for multi-omics data analysis and mentored students in machine learning applications.

## Contact

- LinkedIn: [poulami-ghosh-879439304](https://linkedin.com/in/poulami-ghosh-879439304)
- Email: poulamighosh738@gmail.com
