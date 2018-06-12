# Preparing Data for KnowEnG Analysis

## Overview
The ‘KnowEnG’ BD2K Center is an NIH-funded Center of Excellence in Big Data Computing that has 
created a platform for analyzing user-generated 'omics data while simulataneously integrating 
prior knowledge of known relationships/interactions between genes/proteins into the analysis.  

The [KnowEnG Platform](https://knoweng.org/analyze/) tools are designed to analyze 
**“‘omics spreadsheets”**, data matrices containing measurements/values for 
genes/transcripts/proteins for multiple samples/conditions.  

For example, 'omics spreadsheets can contain:
- transcriptomic profiles, 
- differential expression gene sets, 
- protein quantification measurements,
- gene-level somatic mutation data,
- gene promoter scores of accessibility or transcription factor binding
- etc.

### Available Analysis Tools
KnowEnG has tools for examining and analyzing these ‘omics spreadsheets using prior knowledge on 
genes/proteins. These tools include:

1. **Spreadsheet Visualizer**: for visualizing ‘omics spreadsheets and 
2. **Sample Clustering** [[NBS](https://www.nature.com/articles/nmeth.2651)]: for clustering the samples 
of the spreadsheet using prior knowledge.  

If your samples/conditions have related phenotypic/clinical data associated with them 
(captured in a **“phenotypic spreadsheet”**), then KnowEnG also has a tool:  

3. **Gene Prioritization** [[ProGENI](https://www.ncbi.nlm.nih.gov/pubmed/28800781)]: for identifying the 
‘omics features that are related to a phenotype of interest using interaction networks.

Finally, you can simply bring a set of genes you are interested in for KnowEnG’s specialized: 

4. **Gene Set Characterization** [[DRaWR](https://www.ncbi.nlm.nih.gov/pubmed/27153592)]: for finding pathways and Gene Ontology terms related to your input 
gene set using prior knowledge of gene/protein relationships.

## Supported Data Formats
If you have a dataset relating to one of our 20 supported species (see [list](https://knoweng.org/kn-data-references/#kn_contents_by_species)), 
you should prepare your data using the following formats.

### Formatting 'Omics Spreadsheets
![Omics Spreadsheet Example](https://github.com/KnowEnG/quickstart-demos/raw/master/pipeline_readmes/images/genomic_spreadsheet_sample.PNG "Omics Spreadsheet Example")

For any ‘omics spreadsheets, 
- the columns should represent samples/conditions and the first row must contain unique sample identifiers
- the rows should represent features for genes, transcripts, or proteins, and the first column should 
contain common identifiers/aliases for these entities.  The KnowEnG platform is able to internally 
handle entity name mapping for most types of standard identifiers.
- the numeric values of the data matrix should have consistent meaning and representation throughout 
the entire file (e.g. entirely binary (0/1), entirely non-negative values, or all continuous values) 
- the data matrix with its row and column names should be saved as a tab separated text file (e.g. “.txt” or “.tsv”) 
- For knowledge-guided **sample clustering** specifically:
  + the values of the data matrix should be entirely binary or entirely non-negative values.  Values will 
  be treated as importance scores, with larger values representing that the genomic feature is more important 
  to the sample. 
  + the data matrix must not contain any NA/Null values
- For knowledge-guided **gene prioritization** specifically:
  + The analysis assumes that the values of each `omic feature follows roughly a normal distribution.  
  For best results, we suggest that you apply the appropriate transformations to your data (e.g. log2 
  transform to microarray data) to satisfy this condition.

### Formatting Phenotypic Spreadsheets
![Phenotype Spreadsheet Example](https://github.com/KnowEnG/quickstart-demos/raw/master/pipeline_readmes/images/phenotype_spreadsheet_example.PNG "Phenotype Spreadsheet Example")

For any phenotypic spreadsheets
- the rows should represent the different samples/conditions with the first column containing sample 
identifiers that exactly match the ‘omics spreadsheets
- the columns should represent the different phenotypic/clinical variables measured in the samples 
with the first row containing a unique identifier for each phenotypic variable
- the phenotypic spreadsheet should also be saved as a tab separated text file (e.g. “.txt” or “.tsv”) 
- For knowledge-guided **gene prioritization** specifically:
  + the numeric values of the phenotypic data should be consistent throughout the entire file (e.g. 
  entirely binary (0/1), or entirely continuous values) 
	
## Contact Us
The KnowEnG team is eager to help demonstrate the power of knowledge-guided analysis for our users on their own 
research datasets. If you have any questions about preparing your data, please email 
[knoweng-support@illinois.edu](mailto:knoweng-support@illinois.edu) for more information. 
