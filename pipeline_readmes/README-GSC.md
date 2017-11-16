This file contains a description of the different output files of the gene set characterization (GSC) pipeline. The downloaded zip file will contain one directory for each public gene set collection that was selected during the analysis configuration as well as up to three other reference files. The format of some output files will vary depending on the parameter options selected.

#### Files in Gene Set Collection Directory:
 - A) gsc_results.txt - Gene Set Characterization Results File
 - B) gene_set_name_map.txt - Public Gene Set Mapping File
 - C) run_params.yml - Run Parameters File
 - D) *.metadata - Gene Set Collection Metadata 

#### Other Reference Files:
 - E) clean_genomic_matrix.txt - Mapped Genomic Spreadsheet File
 - F) gene_map.txt - Gene ID Mapping File
 - G) interaction_network.metadata - Knowledge Network Metadata (if KN guided analysis)

Below are descriptions for the contents of each of these files:

#### A) gsc_results.txt - Gene Set Characterization Results File
- The columns of this file will depend on the choice you made whether to "Use the Knowledge Network"
- If "Yes" Option (DRaWR):
  1) user_gene_set: the names of the gene sets that you submitted
  2) property_gene_set: the internal KnowEnG ids for public gene sets from one public gene set collection
  3) difference_score: difference of query_score (col4) and baseline_score(col5) divided by the largest difference in the file. This value is between 0 and 1 and reported when it is greater than 0.5
  4) query_score: converged stationary probability of being at the property_gene_set node in the chosen heterogenous network given that you restart at any only gene node from the user gene set. This value is between 0 and 1.
  5) baseline_score: converged stationary probability of being at the property_gene_set node in the chosen heterogenous network given that you restart at any gene node. This value is between 0 and 1.
- If "No" Option (Fisher Exact):
  1) user_gene_set: the names of the gene sets that you submitted
  2) property_gene_set: the internal KnowEnG ids for public gene sets from one public gene set collection
  3) pvalue: the -1 * log10 pvalue of the one sided (alternative = 'greater') Fisher Exact Test using the contingency table corresponding to the user set and property gene set of the row. This value is reported when it is greater than 2.
      + NOTE1: You can take 10^-x to convert these values back into the original pvalues.
      + NOTE2: These pvalues (-1*log10) have not been corrected for multiple hypothesis testing.
  4) universe_count: total number of genes annotated by the public gene set collection and listed in your spreadsheet (or known for the species of your submitted gene list).
  5) user_count: size of your gene set in the universe
  6) property_count: size of the public gene set in the universe
  7) overlap_count: size of the overlap between the two in the universe

#### B) gene_set_name_map.txt - Public Gene Set Mapping File
- The columns of this file are defined as follows:
  1) property_gene_set_id: the internal KnowEnG id for a the public gene set
  2) property_gene_set_id2: the internal KnowEnG id for a the public gene set
  3) gene_set_type: will always be “Property”
  4) property_gene_set_alias: alias for gene set from original data source
  5) property_gene_set_desc: description for gene set from original data source

#### C) run_params.yml - Run Parameters File
- This yaml file contains the run parameters file that was used by the computation container that ran the KnowEnG pipeline (implementation available on GitHub) on the input data.

#### D) *.metadata - Gene Set Collection Metadata 
- This yaml file contains information about the gene set collection used for the results in this directory.  Its keys include summarizations about the network size (“data”), its public data source details (“datasets”), information about the meaning of its edges (“edge_type”), and some commands and configurations used in its construction (“export”).

#### E) clean_genomic_matrix.txt - Mapped Genomic Spreadsheet File
- This file contains a modified version of the user’s input genomic matrix where the original gene identifiers provided have been mapped to stable Ensembl gene_ids where possible.  Rows with original gene names that are unable to be mapped or are not unique are discarded from this clean output.  Only the remaining genes are used for the gene universe for the gene set characterization method.

#### F) gene_map.txt - Gene ID Mapping File
- The columns of this file are defined as follows:
  1) KN_gene_id: the stable Ensembl gene ID that KnowEnG uses internally
  2) user_gene_id: the corresponding gene/transcript/protein identifier supplied by the user in the original genomic spreadsheet.

#### G) interaction_network.metadata - Knowledge Network Metadata (if KN guided analysis)
- This yaml file contains information about the interaction network if used in the analysis.  Its keys include summarizations about the network size (“data”), its public data source details (“datasets”), information about the meaning of its edges (“edge_type”), and some commands and configurations used in its construction (“export”).
