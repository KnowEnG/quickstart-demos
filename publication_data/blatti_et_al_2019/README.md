![Logo of the project](https://knoweng.org/wp-content/uploads/2016/08/knoweng_wordmark_all_versions_knoweng_logo_LtBkg_LongTag-1.png)

# Recreate Knowledge-Guided Analysis with KnowEnG

With the following data files and input parameters, users of the [KnowEnG Analysis Platform](https://knoweng.org/analyze/) can recreate the eight different primary analyses reported in: 

Blatti, et al. Knowledge-guided analysis of ‘omics’ data using the KnowEnG cloud platform. _In preparation_.

## Table of Contents
1. [Background](#background)
2. [How To Use This Guide](#how-to-use-this-guide)
3. [Analysis Runs](#analysis-runs)
    1. [Run1: Knowledge-guided clustering of mutation profiles](#run1-knowledge-guided-clustering-of-mutation-profiles)
    2. [Run2: Clustering of multi-omics data](#run2-clustering-of-multi-omics-data)
    3. [Run3: Clustering for patient stratification](#run3-clustering-for-patient-stratification)
    4. [Run4: Knowledge-guided gene prioritization](#run4-knowledge-guided-gene-prioritization)
    5. [Run5: Functional enrichment of tumor-associated genes](#run5-functional-enrichment-of-tumor-associated-genes)
    6. [Run6: Signature analysis for patient subtyping](#run6-signature-analysis-for-patient-subtyping)
    7. [Run7: Prioritization of subtype-associated genes](#run7-prioritization-of-subtype-associated-genes)
    8. [Run8: Pathway analysis of subtype-associated genes](#run8-pathway-analysis-of-subtype-associated-genes)
4. [KnowEnG Links](#knoweng-links)
5. [Contact Us](#contact-us)
6. [License](#license)

## Background

‘KnowEnG’ (Knowledge Engine for Genomics, pronounced ‘knowing’) is a Cloud-based platform that provides a suite of powerful machine-learning tools for analysis of genomics data sets. These tools, also referred to as ‘pipelines’, are geared towards data sets represented as spreadsheets or tables (genes x samples) that record typical genomic profiles such as gene expression, mutation counts, etc. for a collection of samples, at the resolution of individual genes. The pipelines help identify biologically meaningful patterns in the provided spreadsheet data, through _ab initio_ analysis as well as by contextualizing with prior knowledge. In Blatti et al., we demonstrated the capabilities of the KnowEnG engine by using it for common bioinformatics analyses such as patient stratification, gene prioritization, gene set characterization and signature analysis on a few major data sets in cancer genomics ([TCGA](https://portal.gdc.cancer.gov/) and [METABRIC](http://molonc.bccrc.ca/aparicio-lab/datasets/)), and reproducing key results of original studies ([Pan-Cancer](https://www.ncbi.nlm.nih.gov/pubmed/25109877), [EMAT](https://www.biorxiv.org/content/10.1101/219410v2), and [ESCA](https://www.ncbi.nlm.nih.gov/pubmed/28052061)) as well as gleaning new biological insights. In doing so, we highlighted both the sophisticated level of analysis possible and the ease-of-use with which multiple pipelines can be invoked, individually as well as in combination, to generate a multi-faceted narrative of the insights that the data have to offer.  

## How To Use This Guide
In the following section, we highlight eight analyses from our publication that can be recreated in the [KnowEnG Analysis Platform](https://knoweng.org/analyze/) (or the SevenBridges [Cancer Genomics Cloud](https://cgc.sbgenomics.com/public/apps#q?search=knoweng)).  For each analysis, we first let the user know which pipeline is applicable. We provide the input spreadsheets(s) for that pipeline which must be uploaded into the user's account on the platform. When there are multiple input files for a step, the "File Type" provided in the table indicate for which step of pipeline configuration each input is intended. All the files can be downloaded from a single zipped [archive](https://s3.amazonaws.com/knoweng-publication-data/blatti_et_al_2019.tar.gz), individually from the spreadsheets [directory](spreadsheets/) in this repo, or from the links in the input data tables below. Files larger than 1 MB will need to be unzipped before loading them into the platform. After the input data table for each analysis, we provide the parameters of the pipeline that are needed to recreate the highlighted analysis in the paper. These parameters appear in the order and with the vocabulary found in the [KnowEnG Analysis Platform](https://knoweng.org/analyze/). (The parameters names and requirements will likely differ in the SevenBridges [Cancer Genomics Cloud](https://cgc.sbgenomics.com/public/apps#q?search=knoweng) depending on the pipeline). Once an analysis is submitted and finished in the platform, the pipeline visualization and several downloadable outputs will be produced. We have provided the primary downloadable output of interest that can be examined in detail. Often, this primary downloadable output is also the input to the next analysis.  Besides the eight exemplary analyses explained here, most of the baseline and alternative analyses described in the paper can be recreated by modification of the Knowledge Network related parameters. 

## Analysis Runs

The eight analyses below use novel combinations of knowledge-guided analysis pipelines and cancer datasets. The pipeline, data files, and parameters necessary to recreate the major analyses in the [KnowEnG Analysis Platform](https://knoweng.org/analyze/) are provided below along with the primary output file from each run.

### Run1: Knowledge-guided clustering of mutation profiles

This is an application of the *Sample Clustering* pipeline on TCGA PANCAN12 somatic mutation data. **Note:** This analysis will run for a very long time before completing, however, it is not required to complete it before moving on to the other analyses presented here.

#### Input Files
**File Name**|**File Type**|**Size**|**Dimensions**|**Values**|**Original Source**|**Description**
---|---|---|---|---|---|---
[in1_SC_pancanMutations](spreadsheets/in1_SC_pancanMutations.bz2)|omics feature file|391 MB|31152 genes by 3276 samples|0/1-valued|TCGA_PANCAN12_mutation-2015-01-28.tgz file from UCSC Cancer Genome Browser PANCAN12 collection|presence of non-silent somatic mutation in protein coding region of gene for sample, gene names have been mapped to Ensembl IDs by [KN_Mapper](https://github.com/KnowEnG/KN_Mapper)
[in1_SC_pancanClinical](spreadsheets/in1_SC_pancanClinical.bz2)|phenotype file|1.1 MB|3276 samples by 28 phenotypic categories|mixed|TCGA_PANCAN12_mutation-2015-01-28.tgz file from UCSC Cancer Genome Browser PANCAN12 collection|clinical data for TCGA samples

#### Input Parameters
Knowledge Network: `Yes`  
Species: `Human (Hsap)`  
Interaction Network: `HumanNet Integrated Network`  
Network Smoothing: `50%`  
Num Clusters: `14`  
Use Bootstrapping: `No` 

#### Primary Output File
The primary output file [out1_SC_pancanMutationClusters](spreadsheets/out1_SC_pancanMutationClusters) is a clustering assignment of 3276 samples that follows the format specified [here](https://github.com/KnowEnG/quickstart-demos/blob/master/pipeline_readmes/README-SC.md#a-sample_labels_by_clustertxt---sample-cluster-assignment-file).


### Run2: Clustering of multi-omics data

This is an application of the *Sample Clustering* pipeline on previously clustered TCGA PANCAN12 multi-omics data. 

#### Input Files
**File Name**|**File Type**|**Size**|**Dimensions**|**Values**|**Original Source**|**Description**
---|---|---|---|---|---|---
[in2_SC_pancanMultiomicsClusters](spreadsheets/in2_SC_pancanMultiomicsClusters)|omics feature file|622 KB|80 clusters by 3542 samples|0/1-valued|Jupyter output|presence of sample in cluster from previous clusterings
[in2_SC_pancanClinical](spreadsheets/in2_SC_pancanClinical.bz2)|phenotype file|1.2 MB|3542 samples by 28 phenotypic categories|mixed|TCGA_PANCAN12_mutation-2015-01-28.tgz file from UCSC Cancer Genome Browser PANCAN12 collection|clinical data for TCGA samples

#### Input Parameters
Knowledge Network: `No`  
Num Clusters: `13`  
Clustering Algorithm: `Hierarchical`  
Affinity Metric: `Euclidean`  
Linkage Criterion: `Ward`    
Use Bootstrapping: `Yes`  
Num Bootstraps: `200`  
Bootstrap Percent: `80%`  

#### Primary Output File
The primary output file [out2_SC_cocaClusters](spreadsheets/out2_SC_cocaClusters) is a clustering assignment of 3542 samples that follows the format specified [here](https://github.com/KnowEnG/quickstart-demos/blob/master/pipeline_readmes/README-SC.md#a-sample_labels_by_clustertxt---sample-cluster-assignment-file).


### Run3: Clustering for patient stratification

This is an application of the *Sample Clustering* pipeline on METABRIC breast cancer gene expression data. 

#### Input Files
**File Name**|**File Type**|**Size**|**Dimensions**|**Values**|**Original Source**|**Description**
---|---|---|---|---|---|---
[in3_SC_metabricExpression](spreadsheets/in3_SC_metabricExpression.bz2)|omics feature file|4.3 MB|229 genes by 1058 samples|non-negative real|microarray gene expression breast cancer dataset from [OASIS](http://oasis-genomics.org/)|absolute values of z-normalized log2 transformed probe intensity values of  EMT-related genes from the METABRIC study, gene names have been mapped to Ensembl IDs by [KN_Mapper](https://github.com/KnowEnG/KN_Mapper) and sample IDs have been converted to variable names
[in3_SC_metabricClinical](spreadsheets/in3_SC_metabricClinical)|phenotype file|816 KB|1058 samples by 117 phenotypic categories|mixed|Supplementary [data](https://www.nature.com/articles/nature10983#supplementary-information) from Curtis et al. |clinical data for METABRIC samples with converted sample IDs

#### Input Parameters
Knowledge Network: `Yes`  
Species: `Human (Hsap)`  
Interaction Network: `HumanNet Integrated Network`  
Network Smoothing: `50%`  
Num Clusters: `2`  
Use Bootstrapping: `No`  

#### Primary Output File
The primary output file [out3_SC_metabricClusters](spreadsheets/out3_SC_metabricClusters) is a clustering assignment of 1058 samples that follows the format specified [here](https://github.com/KnowEnG/quickstart-demos/blob/master/pipeline_readmes/README-SC.md#a-sample_labels_by_clustertxt---sample-cluster-assignment-file).


### Run4: Knowledge-guided gene prioritization

This is an application of the *Feature Prioritization* pipeline on the TCGA PANCAN12 gene expression data. 

#### Input Files
**File Name**|**File Type**|**Size**|**Dimensions**|**Values**|**Original Source**|**Description**
---|---|---|---|---|---|---
[in4_FP_pancanExpression](spreadsheets/in4_FP_pancanExpression.bz2)|omics feature file|427 MB|14373 genes by 3599 samples|real values|TCGA_PANCAN12_exp_HiSeqV2-2015-01-28.tgz file from UCSC Cancer Genome Browser PANCAN12 collection, more information [here](https://www.synapse.org/#!Synapse:syn1715755)|gene normalized log2 expression of gene for sample, missing values are filled with gene mean, gene names have been mapped to Ensembl IDs by [KN_Mapper](https://github.com/KnowEnG/KN_Mapper)
[in4_FP_pancanDiseaseType](spreadsheets/in4_FP_pancanDiseaseType)|response file|197 KB|5040 samples by 12 disease types|0/1-valued|TCGA_PANCAN12_exp_HiSeqV2-2015-01-28.tgz file from UCSC Cancer Genome Browser PANCAN12 collection|clinical data for TCGA samples where "_primary_disease" field is transformed into membership matrix by "Category to Binary" tool in Spreadsheet Transformations Jupyter notebook

#### Input Parameters
Knowledge Network: `Yes`  
Species: `Human (Hsap)`  
Interaction Network: `HumanNet Integrated Network`  
Network Smoothing: `50%`  
Prioritization Method: `T-test`  
Missing Values: `Average`  
Response-Correlated Features: `50`  
Exported Features: `100`  
Use Bootstrapping: `No`  

#### Primary Output File
The primary output file [in5_GSC_diseaseGenes_out4](spreadsheets/in5_GSC_diseaseGenes_out4) is a gene set membership spreadsheet for 12 disease type gene sets that follows the format specified [here](https://github.com/KnowEnG/quickstart-demos/blob/master/pipeline_readmes/README-FP.md#b-top_features_by_phenotype_matrix---top-ranked-feature-sets-per-phenotype).


### Run5: Functional enrichment of tumor-associated genes 

This is an application of the *Gene Set Characterization* pipeline on the results found in the the primary output of Run4. 

#### Input File
**File Name**|**File Type**|**Size**|**Dimensions**|**Values**|**Original Source**|**Description**
---|---|---|---|---|---|---
[in5_GSC_diseaseGenes_out4](spreadsheets/in5_GSC_diseaseGenes_out4)|membership spreadsheet|562 KB|14373 genes by 12 disease types|0/1-valued|run4 FP primary output|[format description](https://github.com/KnowEnG/quickstart-demos/blob/master/pipeline_readmes/README-FP.md#b-top_features_by_phenotype_matrix---top-ranked-feature-sets-per-phenotype)

#### Input Parameters
Species: `Human (Hsap)`  
Public Gene Sets: `Ontologies > Gene Ontology`  
Knowledge Network: `No`  

#### Primary Output File
The primary output file [out5_GSC_diseaseGeneOntology](spreadsheets/out5_GSC_diseaseGeneOntology.bz2) is a list of enriched gene set pairs that follows the format specified [here](https://github.com/KnowEnG/quickstart-demos/blob/master/pipeline_readmes/README-GSC.md#a-gsc_resultstxt---gene-set-characterization-results-file).


### Run6: Signature analysis for patient subtyping

This is an application of the *Signature Analysis* pipeline relating ESCC tumor samples from TCGA to known LUSC gene expression signatures. 

#### Input Files
**File Name**|**File Type**|**Size**|**Dimensions**|**Values**|**Original Source**|**Description**
---|---|---|---|---|---|---
[in6_SA_esccExpression](spreadsheets/in6_SA_esccExpression.bz2)|omics query file|27 MB|17842 genes by 79 samples|real values|TCGA data from the SevenBridges Cancer Genomics Cloud, instructions for download found [here](https://github.com/KnowEnG/KnowEnG_CWL/tree/master/CGC#gathering-the-tcga-input-files)|gene normalized log2(FPKM +1) gene expression of gene for sample, gene names have been mapped to Ensembl IDs by [KN_Mapper](https://github.com/KnowEnG/KN_Mapper)
[in6_SA_luscSignatures](spreadsheets/in6_SA_luscSignatures)|signature file|18 KB|197 genes by 4 subtypes|real values|“predictor.centroids” signature data from Wilkerson et al. study found on [here]([http://cancer.unc.edu/nhayes/publications/scc/).|Normalized lung squamous cell carcinoma signatures from microarray expression measurements, gene names have been mapped to Ensembl IDs by [KN_Mapper](https://github.com/KnowEnG/KN_Mapper)

#### Input Parameter
Similarity Measure: `Spearman`  

#### Primary Output File
The primary output file [in7_FP_esccBestSignature_out6](spreadsheets/in7_FP_esccBestSignature_out6) is a membership matrix that maps each ESCC sample to one of four LUSC subtypes and follows the format specified [here](https://github.com/KnowEnG/quickstart-demos/blob/master/pipeline_readmes/README-SA.md#b-similarity_matrixbinarytsv---indicates-the-signature-with-the-maximum-score-for-each-sample).


### Run7: Prioritization of subtype-associated genes

This is an application of the *Feature Prioritization* pipeline on the results found in the primary output of Run6. 

#### Input Files
**File Name**|**File Type**|**Size**|**Dimensions**|**Values**|**Original Source**|**Description**
---|---|---|---|---|---|---
[in7_FP_esccExpression](spreadsheets/in7_FP_esccExpression.bz2)|omics query file|27 MB|17842 genes by 79 samples|real values|TCGA data from the SevenBridges Cancer Genomics Cloud, instructions for download found [here](https://github.com/KnowEnG/KnowEnG_CWL/tree/master/CGC#gathering-the-tcga-input-files)|gene normalized log2(FPKM +1) gene expression of gene for sample, gene names have been mapped to Ensembl IDs by [KN_Mapper](https://github.com/KnowEnG/KN_Mapper)
[in7_FP_esccBestSignature_out6](spreadsheets/in7_FP_esccBestSignature_out6)|response file|2 KB|79 samples by 4 subtypes|0/1-valued|run6 SA primary output|[format description](https://github.com/KnowEnG/quickstart-demos/blob/master/pipeline_readmes/README-SA.md#b-similarity_matrixbinarytsv---indicates-the-signature-with-the-maximum-score-for-each-sample)

#### Input Parameters
Knowledge Network: `No`  
Prioritization Method: `T-test`  
Missing Values: `Reject`  
Exported Features: `100`  
Use Bootstrapping: `No`  

#### Primary Output File
The primary output file [in8_GSC_signatSpecificGenes_out7](spreadsheets/in8_GSC_signatSpecificGenes_out7) is a gene set membership spreadsheet for 4 subtype gene sets that follows the format specified [here](https://github.com/KnowEnG/quickstart-demos/blob/master/pipeline_readmes/README-FP.md#b-top_features_by_phenotype_matrix---top-ranked-feature-sets-per-phenotype).


### Run8: Pathway analysis of subtype-associated genes

This is an application of the *Gene Set Characterization* pipeline on the results found in the primary output of Run7. 

#### Input File
**File Name**|**File Type**|**Size**|**Dimensions**|**Values**|**Original Source**|**Description**
---|---|---|---|---|---|---
[in8_GSC_signatSpecificGenes_out7](spreadsheets/in8_GSC_signatSpecificGenes_out7)|membership spreadsheet|419 KB|17842 genes by 4 subtypes|0/1-valued|run7 FP primary output|[format description](https://github.com/KnowEnG/quickstart-demos/blob/master/pipeline_readmes/README-FP.md#b-top_features_by_phenotype_matrix---top-ranked-feature-sets-per-phenotype)

#### Input Parameters
Species: `Human (Hsap)`  
Public Gene Sets: `Pathways > Enrichr Pathway Membership`  
Knowledge Network: `Yes`  
Interaction Network: `HumanNet Integrated Network`  
Network Smoothing: `50%`  

#### Primary Output File
The primary output file [out8_GSC_pathwayEnrichments](spreadsheets/out8_GSC_pathwayEnrichments) is a list of enriched gene set pairs that follows the format specified [here](https://github.com/KnowEnG/quickstart-demos/blob/master/pipeline_readmes/README-GSC.md#a-gsc_resultstxt---gene-set-characterization-results-file).


## KnowEnG Links

Here are a collection of useful links if you wish to explore the KnowEnG Analytics Platform further:

- Platform homepage: [https://knoweng.org/analyze/](https://knoweng.org/analyze/)
- Platform Quickstart Guides and Videos: 
[https://knoweng.org/quick-start/](https://knoweng.org/quick-start/)
- Knowledge Network Contents: 
[https://knoweng.org/kn-overview/](https://knoweng.org/kn-overview/) and 
[https://github.com/KnowEnG/KN_Fetcher/blob/master/Contents.md](https://github.com/KnowEnG/KN_Fetcher/blob/master/Contents.md)
- KnowEnG in Seven Bridges Cancer Genomics Cloud: [https://cgc.sbgenomics.com/public/apps#q?search=knoweng](https://cgc.sbgenomics.com/public/apps#q?search=knoweng)
- GitHub Repositories: [https://knoweng.github.io/](https://knoweng.github.io/)
- Dockerhub: [https://hub.docker.com/u/knowengdev/](https://hub.docker.com/u/knowengdev/)
- Jupyter: [https://knowtebook.knoweng.org/](https://knowtebook.knoweng.org/)


## Contact Us

Have questions or feedback about the KnowEnG Platform? KnowEnG Center staff will respond to your technical support questions by email M-F during normal business hours and as we are able.

Contact us at [knoweng-support@illinois.edu](mailto:knoweng-support@illinois.edu)

## License

The code in this project is licensed under a MIT license: [LICENSE](https://github.com/KnowEnG/KN_Mapper/blob/master/LICENSE).
