# SLE777 Bioinformatics Assignment 4
This repository contains an RMarkdown workflow for comparative genomics and data analysis. The analysis is divided into two main parts: (1) data wrangling and statistical analysis of gene expression and growth data, and (2) comparative genomics analysis between *E. coli* and *Saprospirales bacterium*. This comparison analysis is done for learning purposes since *E. coli* is a species and *Saprospirales bacterium* is a bacterium order that cannot be directly compared.

## Repository Contents
- `assessment_report.Rmd`: Complete RMarkdown workflow containing all analyses
  - Part 1 (Questions 1-10): Data wrangling and statistical analysis
  - Part 2 (Questions 1-6): Comparative genomics analysis
  - Generates PDF and HTML reports with figures, tables, and interpretations

## Data Sources
### Part 1: Data Wrangling and Analysis
Input Files (automatically downloaded): 
- `gene_expression.tsv`
  - Source: https://raw.githubusercontent.com/ghazkha/Assessment4/main/gene_expression.tsv
  - Description: RNA-seq count data for three samples
  - Format: Tab-delimited file with gene identifiers as row names
  - Used in: Questions 1-5
- `growth_data.csv`
  - Source: https://raw.githubusercontent.com/ghazkha/Assessment4/main/growth_data.csv
  - Description: Tree circumference measurements at two sites (northeast and southwest) over 20 years (2005-2020)
  - Format: CSV file with columns for Site, Tree ID, and circumference measurements
  - Used in: Questions 6-10

### Part 2: Comparative Genomics Analysis
Input Files (automatically downloaded from Ensembl Bacteria):
- `ecoli_cds.fa`
  - Source: Ensembl Bacteria Release 62
  - Organism: Escherichia coli str. K-12 substr. MG1655 (GCA_000005845)
  - Description: All coding sequences (CDS) in FASTA format
  - Downloaded from: ftp.ensemblgenomes.ebi.ac.uk
- `sapro_cds.fa`
  - Source: Ensembl Bacteria Release 62
  - Organism: Saprospirales bacterium (GCA_003448025)
  - Description: All coding sequences (CDS) in FASTA format
  - Downloaded from: ftp.ensemblgenomes.ebi.ac.uk

## Analysis Workflow
### Part 1: Data Wrangling and Analysis
- Questions 1-5: Gene Expression Analysis
  - Import and display RNA-seq count data
  - Calculate mean expression across samples
  - Identify top 10 highly expressed genes
  - Count low-expression genes (< 10)
  - Visualize expression distribution with histogram
- Questions 6-10: Growth Data Analysis
  - Import tree growth measurements
  - Calculate summary statistics by site and timepoint
  - Create comparative boxplots
  - Analyze 10-year growth rates
  - Perform t-test to compare growth between sites
- Outputs:
  - 6 tables summarizing gene expression and growth statistics
  - 3 figures (histogram, boxplot, and statistical visualizations)

### Part 2: Comparative Genomics Analysis
- Question 1: Count and compare number of coding sequences (CDS)
- Question 2: Calculate total coding DNA length in base pairs and megabases
- Question 3: Analyze CDS length distributions
  - Summary statistics (mean, median, min, max, SD)
  - Boxplot comparison
- Question 4: Calculate nucleotide and amino acid frequencies
  - GC content analysis
  - Comparative bar plots for nucleotides and amino acids
- Question 5: Codon usage bias analysis
  - Calculate codon usage frequencies
  - Compute RSCU (Relative Synonymous Codon Usage)
  - Identify preferred codons (RSCU > 1.5)
  - Compare codon preferences within synonymous families
  - Analyze agreement between organisms
- Question 6: Protein k-mer analysis
  - Extract and translate CDS to protein sequences
  - Identify top 10 over- and under-represented k-mers (lengths 3-5)
  - Compare enrichment patterns between organisms
  - Generate multiple visualizations:
    - Bar plots of enrichment scores
    - Correlation scatter plots
    - Heatmaps of enrichment patterns
  - Statistical analysis of k-mer conservation
- Outputs:
  - 15+ tables with genomic statistics and comparisons
  - 10+ figures including distributions, comparisons, and enrichment analyses

## Prerequisites

This project requires R (>= 4.0) and the following R packages:

**Core Packages:**
```
rinstall.packages(c("knitr", "R.utils", "ggplot2", "reshape2", "dplyr", "tidyr"))
```

**Bioinformatics Packages:**
```
rif (!requireNamespace("BiocManager", quietly = TRUE))
    install.packages("BiocManager")
BiocManager::install("seqinr")
```

**Packages Used:**

*   `knitr` - Dynamic report generation
*   `R.utils` - File decompression (gunzip)
*   `seqinr` - Sequence analysis and manipulation
*   `ggplot2` - Data visualization
*   `reshape2` - Data reshaping
*   `dplyr` - Data manipulation
*   `tidyr` - Data tidying

## Running the Analysis
- Clone the repository:
```
bashgit clone [repository-url]
cd [repository-name]
```

- Open the RMarkdown file:
```
r# In RStudio or R console
rmarkdown::render("assignment4.Rmd")
```

- Output files generated:
  - assignment4.pdf - PDF report with all analyses
  - assignment4.html - HTML report with all analyses
  - part1/data/ - Downloaded gene expression and growth data
  - part2/genomic_data/ - Downloaded genomic sequences

## Key Features
- Automated Data Download
  - All required data files are automatically downloaded if not present
  - Creates necessary directory structures
  - Uses stable URLs from GitHub and Ensembl databases
- Reproducible Analysis
  - Complete workflow in single RMarkdown document
  - Automatic figure and table numbering
  - Session info included for reproducibility
- Comprehensive Visualizations
  - Distribution plots (histograms, boxplots)
  - Comparative bar plots
  - Correlation scatter plots
  - Heatmaps for multi-dimensional comparisons
- Statistical Rigor
  - Summary statistics with means, medians, and standard deviations
  - Hypothesis testing (t-tests)
  - Correlation analysis
  - Enrichment score calculations

## Output Interpretation
The analysis produces:
- Tables: Numbered sequentially with descriptive captions
- Figures: Numbered sequentially with detailed legends
- Statistical Results: P-values, confidence intervals, and effect sizes
- Biological Interpretations: Discussion of findings in genomic context

## Author
Irena Sugiarto (Student ID: 225545617)
This project is submitted as coursework for SLE777 Bioinformatics.

## Acknowledgments
- Ensembl Bacteria database for genomic sequences
- seqinr package developers for sequence analysis tools
- Course instructors and materials from SLE777
