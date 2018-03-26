This file contains a description of the different output files of the gene set characterization (GSC) pipeline. The downloaded zip file will contain up to nine other reference files. The format of some output files will vary depending on the parameter options selected.

#### Results File
 - A) gsc_results.txt - Gene Set Characterization Results File

#### Reference Files:
 - B) clean_gene_set_matrix.txt - Mapped Genomic Spreadsheet File
 - C) gene_map.txt - Gene ID Mapping File
 - D) gene_map_exceptions.txt - Gene ID Mapping Exceptions File
 - E) dropped_genes.txt - Dropped Genes File
 - F) run_params.yml - Run Parameters File
 - G) run_cleanup_params.yml - Cleanup Run Parameters File
 - H) property_networks.metadata - Gene Set Collection Metadata 
 - I) interaction_network.metadata - Knowledge Network Metadata (if KN guided analysis)

Below are descriptions for the contents of each of these files:

#### A) gsc_results.txt - Gene Set Characterization Results File
- The columns of this file will depend on the choice you made whether to "Use the Knowledge Network"
- If "Yes" Option (DRaWR):
  1) user_gene_set: the names of the gene sets that you submitted
  2) property_gene_set_id: the internal KnowEnG ids for public gene sets from one public gene set collection
  3) property_gene_set_alias: alias for the gene set from its original data source
  4) property_gene_set_description: description for the gene set from its original data source
  5) difference_score: difference of query_score (col4) and baseline_score(col5) divided by the largest difference in the file. This value is between 0 and 1 and reported when it is greater than 0.5
  6) query_score: converged stationary probability of being at the property_gene_set node in the chosen heterogenous network given that you restart at any only gene node from the user gene set. This value is between 0 and 1.
  7) baseline_score: converged stationary probability of being at the property_gene_set node in the chosen heterogenous network given that you restart at any gene node. This value is between 0 and 1.
- If "No" Option (Fisher Exact):
  1) user_gene_set: the names of the gene sets that you submitted
  2) property_gene_set_id: the internal KnowEnG ids for public gene sets from one public gene set collection
  3) property_gene_set_alias: alias for the gene set from its original data source
  4) property_gene_set_description: description for the gene set from its original data source
  5) pvalue: the -1 * log10 pvalue of the one sided (alternative = 'greater') Fisher Exact Test using the contingency table corresponding to the user set and property gene set of the row. This value is reported when it is greater than 2.
      + NOTE1: You can take 10^-x to convert these values back into the original pvalues.
      + NOTE2: These pvalues (-1*log10) have not been corrected for multiple hypothesis testing.
  6) universe_count: total number of genes annotated by the public gene set collection and listed in your spreadsheet (or known for the species of your submitted gene list).
  7) user_count: size of your gene set in the universe
  8) property_count: size of the public gene set in the universe
  9) overlap_count: size of the overlap between the two in the universe

#### B) clean_gene_set_matrix.txt - Mapped Genomic Spreadsheet File
- This file contains a modified version of the user’s input genomic matrix. Rows whose gene names could not be mapped to stable Ensembl gene IDs or are not unique are discarded from this clean output.  Only the remaining genes are used for the gene universe for the gene set characterization method.

#### C) gene_map.txt - Gene ID Mapping File
- The columns of this file are defined as follows:
  1) KN_gene_id: the stable Ensembl gene ID that KnowEnG uses internally
  2) user_gene_id: the corresponding gene/transcript/protein identifier supplied by the user in the original genomic spreadsheet.

#### D) gene_map_exceptions.txt - Gene ID Mapping Exceptions File (if KN guided analysis)
- The columns of this file are defined as follows:
  1) user_gene_id: the gene/transcript/protein identifier supplied by the user in the original genomic spreadsheet.
  2) error_code: the reason the user_gene_id was not mapped to a stable Ensembl gene ID.

#### E) dropped_genes.txt - Dropped Genes File
- The columns of this file are defined as follows:
  1) collection: the public gene set collection whose processing required dropping the gene
  2) gene_name: the gene identifier as provided by the user in the original input
  3) gene_id: the stable Ensembl gene ID for the gene_name

#### F) run_params.yml - Run Parameters File
- This yaml file contains the run parameters that were used by the computation container that ran the KnowEnG analysis pipeline (implementation available on GitHub) on the input data. The file contains one block of parameters per public gene set collection.

#### G) run_cleanup_params.yml - Cleanup Run Parameters File
- This yaml file contains the run parameters file that was used by the computation container that ran the KnowEnG data-cleanup pipeline (implementation available on GitHub) on the input data.

#### H) property_networks.metadata - Gene Set Collection Metadata 
- This yaml file contains information about the gene set collection used for the results.  There is one block per public gene set collection, and within each block, keys include summarizations about the network size (“data”), its public data source details (“datasets”), information about the meaning of its edges (“edge_type”), and some commands and configurations used in its construction (“export”).

#### I) interaction_network.metadata - Knowledge Network Metadata (if KN guided analysis)
- This yaml file contains information about the interaction network if used in the analysis.  Its keys include summarizations about the network size (“data”), its public data source details (“datasets”), information about the meaning of its edges (“edge_type”), and some commands and configurations used in its construction (“export”).

The licensing terms of the source code and containers to perform this analysis can be found at https://knoweng.github.io/. Licensing information relating to the data in the Knowledge Network can be found https://knoweng.org/kn-data-references/#kn_data_resources. 
