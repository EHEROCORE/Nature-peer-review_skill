# Nature Reporting Summary — Reviewer-Time Checklist

The Reporting Summary is a structured form Nature-family journals require authors to complete at acceptance. Reviewers are expected to flag obvious omissions during peer review so that the published version meets these standards. This document reformulates the Reporting Summary into checkable items a reviewer can scan against a manuscript draft.

The official Reporting Summary template lives at: https://www.nature.com/documents/nr-reporting-summary.pdf

## Statistics

These checks apply to **every paper that performs any quantitative comparison**.

### Sample size
- [ ] How sample size was determined — power calculation, or explicit justification (e.g., "all available cases in cohort")
- [ ] Sample size reported per group / condition / subgroup, not just in total
- [ ] For pilot or exploratory studies, this is acknowledged

### Data exclusions
- [ ] Any pre-specified exclusion criteria stated
- [ ] Any post-hoc exclusions justified and quantified
- [ ] Numbers excluded reported, with reasons

### Replication
- [ ] Number of biological replicates explicitly stated
- [ ] Number of technical replicates explicitly stated
- [ ] These two are not conflated
- [ ] Reproducibility of key findings across independent experiments reported

### Randomization
- [ ] Allocation to groups described
- [ ] If randomization not used, justification provided
- [ ] For longitudinal/sequential studies, randomization of processing order described

### Blinding
- [ ] Investigator blinding during data collection described
- [ ] Investigator blinding during analysis described
- [ ] If blinding not used, justification provided

### Statistical tests
- [ ] Every comparison's statistical test named (no "appropriate tests were used")
- [ ] Test assumptions checked OR non-parametric used
- [ ] Effect sizes reported alongside p-values
- [ ] 95% confidence intervals reported for primary estimates
- [ ] Multiple-testing correction stated when multiple tests are run
- [ ] Exact p-values reported (except < 0.001)
- [ ] Two-sided vs one-sided tests specified
- [ ] Mixed models / clustered data correctly handled (independence not assumed when violated)

---

## Software and Code

### Software for data collection
- [ ] All software used named, with version numbers

### Software for data analysis
- [ ] All software / packages named, with version numbers
- [ ] Custom code deposited in a public repository (GitHub, GitLab, Bitbucket)
- [ ] Repository has a DOI (e.g., Zenodo release)
- [ ] README / documentation sufficient to reproduce key figures
- [ ] License stated (MIT, BSD, GPL, CC-BY etc.)

---

## Data

### Data availability statement
- [ ] Present in the manuscript
- [ ] Concrete — names repositories and accession numbers if applicable
- [ ] Does NOT say "available upon reasonable request" without justification
- [ ] Restrictions justified (e.g., patient consent, embargo, third-party data)

### Specific data types
- [ ] **Sequencing data** deposited in SRA / ENA / DDBJ
- [ ] **Microarray data** deposited in GEO / ArrayExpress
- [ ] **Proteomics data** deposited in PRIDE / MassIVE
- [ ] **Structural data** deposited in PDB / EMDB / BMRB
- [ ] **Imaging data** deposited in BioImage Archive / EMPIAR
- [ ] **Cohort data** access pathway clear (e.g., UK Biobank application process)
- [ ] **Code** as above

---

## Materials and Reagents

### Antibodies
- [ ] Vendor and catalog number for every antibody used
- [ ] Clone identifier for monoclonals
- [ ] RRID (Research Resource Identifier) where available
- [ ] Validation evidence: citation, knockout/knockdown control, vendor datasheet
- [ ] Concentration / dilution used

### Cell lines
- [ ] Source institution / vendor
- [ ] Authentication method (STR profiling for human; species verification for non-human)
- [ ] Mycoplasma testing reported and negative
- [ ] If commonly misidentified cell lines (per ICLAC list) used, explicitly justified

### Animals
- [ ] Species, strain, source
- [ ] Sex (and reported by sex if applicable)
- [ ] Age and weight ranges
- [ ] Housing conditions (light, temperature, humidity, food, water)
- [ ] IACUC / equivalent approval, with approval number
- [ ] Welfare assessment and humane endpoints
- [ ] Sample size justification
- [ ] ARRIVE 2.0 compliance

### Human research participants
- [ ] IRB / ethics committee approval, with approval number
- [ ] Informed consent obtained, written or with documented exception
- [ ] Compensation if any
- [ ] Source population (e.g., UK Biobank, BioMe, hospital cohort)
- [ ] Inclusion / exclusion criteria explicit
- [ ] Reporting by sex / gender where applicable
- [ ] Reporting by race / ethnicity where applicable, with framework cited
- [ ] Recruitment biases acknowledged

### Clinical data (additional)
- [ ] Trial registration number if interventional
- [ ] CONSORT flow diagram if RCT
- [ ] STROBE compliance if observational
- [ ] TRIPOD compliance if prediction model
- [ ] Data linkage methodology described

---

## Research-Specific Reporting

### Genomics / sequencing
- [ ] Library preparation kit named with version
- [ ] Sequencer named with read length and depth
- [ ] Alignment software named with version and parameters
- [ ] Variant caller named with version and parameters
- [ ] Quality control metrics reported per sample
- [ ] Population stratification handled appropriately
- [ ] Sex chromosomes handled correctly

### Single-cell
- [ ] Platform and chemistry named
- [ ] Doublet detection method
- [ ] QC thresholds reported (genes/cell, UMI/cell, mitochondrial %)
- [ ] Clustering method, resolution, and rationale
- [ ] Cell type annotation method
- [ ] Batch correction method

### Imaging
- [ ] Microscope or scanner named
- [ ] Acquisition parameters (resolution, channels, dwell time)
- [ ] Software versions
- [ ] Quantification method
- [ ] Blinding during quantification

### Behavioral / experimental
- [ ] Apparatus described
- [ ] Test/training protocol described
- [ ] Experimenter blinding
- [ ] Animal exclusions

---

## Field-Specific Items

### MRI / neuroimaging
- [ ] Scanner field strength and manufacturer
- [ ] Sequence parameters
- [ ] Preprocessing pipeline (e.g., FSL, FreeSurfer, fMRIPrep) with version
- [ ] Motion correction reported
- [ ] Multiple-comparison correction stated for voxel-wise analyses
- [ ] COBIDAS compliance

### Flow cytometry
- [ ] Sample preparation
- [ ] Instrument and configuration
- [ ] Antibody panel with fluorophores and clones
- [ ] Compensation / unmixing approach
- [ ] Gating strategy in supplementary
- [ ] Cell counts and viability

### ChIP-seq / ATAC-seq
- [ ] Crosslinking conditions (for ChIP)
- [ ] Sonication / fragmentation
- [ ] Antibody validation
- [ ] Input / negative control
- [ ] Peak caller and parameters

---

## AI / LLM Disclosure

### Use of generative AI
- [ ] Any use of LLMs (ChatGPT, Claude, etc.) in writing disclosed in Methods or Acknowledgments
- [ ] Any use of generative AI for figures explicitly stated
- [ ] Authors confirm they take responsibility for the content

### AI methods
- [ ] Models named with version
- [ ] Hyperparameters reported
- [ ] Training data described
- [ ] Compute resources reported (where claims are made about practicality)
- [ ] Random seeds for reproducibility
- [ ] Bias / fairness analysis if applicable

---

## Editorial Policy Checklist (separate from Reporting Summary)

Nature-family journals also enforce the Editorial Policy Checklist. Key items reviewers can check:

- [ ] Dual-use research (biosecurity, surveillance, weaponizable methods) considered
- [ ] Competing interests declared
- [ ] Funding sources declared with grant numbers
- [ ] Author contributions stated using CRediT taxonomy
- [ ] Code availability statement separate from data availability statement
- [ ] Pre-registration cited if applicable

---

## How to use this checklist as a reviewer

You do not need to verify every item personally. Your job is to spot **obvious gaps that should be addressed before acceptance**. Specifically:

1. Skim Methods, Data Availability, and Code Availability sections.
2. For every quantitative claim in Results, ask: is sample size, test, effect size, CI, and multiple-testing handling reported?
3. For every figure, ask: are statistics inside the legend, including n, test, and exact p?
4. Flag missing items in the **Minor Comments** section of your report, grouped if many are missing.
5. If the missing items are severe (e.g., the headline claim has no CI; cell lines not authenticated; ethics not reported), elevate to **Major Comments**.

A useful one-line frame for the review:

> *"Several Reporting Summary items appear unaddressed in the current draft and should be completed before acceptance: [list]. The most consequential omission is [X], which directly affects interpretation of the headline claim, and should be addressed in revision."*
