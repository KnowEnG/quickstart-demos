This file contains a description of the different output files of the sample clustering (SC) pipeline. The downloaded zip archive will contain up to thirteen other files for users to further examine and understand their results.  These other files are:

#### Results Files
- A) sample_labels_by_cluster.txt - Sample Cluster Assignment File
- B) consensus_matrix.txt - Bootstrap Consensus Matrix File 
- C) top_features_by_cluster.txt - Cluster Features Spreadsheet File
- D) feature_avgs_by_cluster.txt - Cluster Means Spreadsheet File
- E) clustering_evalutations.txt - Phenotype Association File (if phenotypic input provided)
- F) silhouette_scores_per_sample.txt - Silhouette Scores for Samples File
- G) silhouette_scores_per_cluster.txt - Silhouette Scores for Clusters File
- H) silhouette_score_overall.txt - Silhouette Score Overall File

#### Reference Files
- I) clean_features_matrix.txt - Features Spreadsheet File (mapped if KN guided analysis)
- J) gene_map.txt - Gene ID Mapping File (if KN guided analysis)
- K) run_params.yml - Run Parameters File
- L) run_cleanup_params.yml - Cleanup Run Parameters File
- M) interaction_network.metadata - Knowledge Network Metadata (if KN guided analysis)

Below are descriptions for the contents of each of these files:

#### A) sample_labels_by_cluster.txt - Sample Cluster Assignment File 
- The columns of this file are defined as follows:
  1) sample_id: the identifier for a sample from the genomic spreadsheet
  2) cluster_assignment: integer value (from 0 to number_of_clusters - 1) for the sample’s assigned cluster 

#### B) consensus_matrix.txt - Bootstrap Consensus Matrix File   
- This file contains a matrix with the genomic spreadsheet sample_ids as the row and column names.  The values in the matrix indicate the proportion of the number of bootstraps where the corresponding samples co-cluster.  If bootstrapping was not used, these values will be binary {0, 1}. 

#### C) top_features_by_cluster.txt - Cluster Features Spreadsheet File
- This file contains a matrix with the cluster numbers as the columns headers and feature identifiers as the rows. A ‘1’ in this table indicates that the row feature was one of the top 100 most important (highest scoring) features for that specific column cluster.  All other values are 0.  Importance is calculated as the average value across the cluster.  If the Knowledge Network was used, then it is the average of the stationary probabilities of the random walks on each sample. If features are genes, this file can be used in the Gene Set Characterization pipeline.

#### D) feature_avgs_by_cluster.txt - Cluster Means Spreadsheet File
- This file contains a matrix with the cluster numbers as the columns headers and feature identifiers as the rows. The values in this table are the mean value for the row feature for that specific column cluster. If the Knowledge Network was used, then it is the average of the stationary probabilities of the random walks on each sample, otherwise it is the mean of the original input values.

#### E) clustering_evalutations.txt - Phenotype Association File (if phenotypic input provided)
- The columns of this file are defined as follows:
  1) phenotype_id: the identifier for a column in the phenotype spreadsheet file
  2) Measure: the type of statistical test applied to the cluster assignment and the phenotype values (F oneway ANOVA [‘f_oneway’] test for continuous phenotypes, Chi-squared [‘chisquare’] test for categorical phenotypes)
  3) Trait_length_after_dropna: Number of unique phenotype values after all samples with NA have been dropped
  4) Sample_number_after_dropna: Number of unique samples after dropping any with NAs (missing cluster assignment or given phenotype)
  5) chi/fval: Value of the test statistic
  6) pval: Significance of the test statistic
  7) SUCCESS/FAIL: For the given phenotype, whether or not a statistical test could be performed successfully
  8) Comments: NA for SUCCESS in Column 7, but descriptive message for FAIL case

#### F) silhouette_scores_per_sample.txt - Silhouette Scores for Samples File
- The columns of this file are defined as follows:
  1) sample_id: the identifier for a sample from the genomic spreadsheet
  2) silhouette_score: the silhouette score computed for the sample

#### G) silhouette_scores_per_cluster.txt - Silhouette Scores for Clusters File
- The columns of this file are defined as follows:
  1) cluster_assignment: the cluster_assignment value from sample_labels_by_cluster.txt
  2) silhouette_score: the mean silhouette score for all samples in the given cluster

#### H) silhouette_score_overall.txt - Silhouette Score Overall File
- The columns of this file are defined as follows:
  1) number_of_clusters: the number of clusters produced by the analysis
  2) silhouette_score: the mean silhouette score for all samples in the analysis

#### I) clean_features_matrix.txt - Features Spreadsheet File
- This file contains the user's input feature matrix. If the KN was used in the analysis, rows with gene names that are unable to be mapped or are not unique are discarded from this clean output.

#### J) gene_map.txt - Gene ID Mapping File (if KN guided analysis)
- The columns of this file are defined as follows:
  1) user_supplied_gene_name: the gene/transcript/protein identifier supplied by the user in the original genomic spreadsheet.
  2) status: if the user-supplied gene name could be mapped to a stable Ensembl gene ID, this column will contain the Ensembl gene ID; otherwise, this column will contain the reason mapping failed ("unmapped-none" if no match was found, or "unmapped-many" if multiple matches were found).

#### K) run_params.yml - Run Parameters File
- This yaml file contains the run parameters file that was used by the computation container that ran the KnowEnG analysis pipeline (implementation available on GitHub) on the input data.

#### L) run_cleanup_params.yml - Cleanup Run Parameters File
- This yaml file contains the run parameters file that was used by the computation container that ran the KnowEnG data-cleanup pipeline (implementation available on GitHub) on the input data.

#### M) interaction_network.metadata - Knowledge Network Metadata (if KN guided analysis)
- This yaml file contains information about the interaction network if used in the analysis.  Its keys include summarizations about the network size (“data”), its public data source details (“datasets”), information about the meaning of its edges (“edge_type”), and some commands and configurations used in its construction (“export”).

The licensing terms of the source code and containers to perform this analysis can be found at https://knoweng.github.io/. Licensing information relating to the data in the Knowledge Network can be found https://knoweng.org/kn-data-references/#kn_data_resources. 
