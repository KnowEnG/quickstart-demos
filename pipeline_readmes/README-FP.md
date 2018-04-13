This file contains a description of the different output files of the feature prioritization (FP) pipeline. The downloaded zip archive will contain up to eight other files for users to further examine and understand their results.  These other files are:

#### Results Files
- A) features_ranked_per_phenotype - Scores for Ranked Features for Each Phenotype
- B) top_features_by_phenotype_matrix - Top Ranked Feature Sets per Phenotype

#### Reference Files
- C) clean_features_matrix.txt - Features Spreadsheet File
- D) clean_phenotypic_matrix.txt - Processed Phenotype Spreadsheet File
- E) gene_map.txt - Gene ID Mapping File (if KN guided analysis)
- F) run_params.yml - Run Parameters File
- G) run_cleanup_params.yml - Cleanup Run Parameters File
- H) interaction_network.metadata - Knowledge Network Metadata (if KN guided analysis)

Below are descriptions for the contents of each of these files:

#### A) features_ranked_per_phenotype - Scores for Ranked Features for Each Phenotype
The output format of this file will depend on the choices you made in configuring the analysis.

##### Option 1 (Pearson Correlation): 
- Choices: 
  - Primary prioritization method = Absolute Pearson Correlation
  - Use knowledge Network = No
  - Use bootstrapping = No
- Output Format:
  1) Response: Name of the phenotype of interest.
  2) Feature_ID: The feature identifier.
  3) quantitative_sorting_score: The absolute value of the Pearson correlation coefficient between the phenotype and the feature.  A higher score shows the feature is more relevant to the phenotype. This value is between 0 and 1.
  4) visualization_score: The min-max normalized value of quantitative_sorting_score. This value is always between 0 and 1.
  5) baseline_score: The Pearson correlation coefficient between the phenotype and the feature.

##### Option 2 (Robust Pearson Correlation):
- Choices:
  - Primary prioritization method = Absolute Pearson Correlation
  - Use knowledge Network = No
  - Use bootstrapping = Yes
- Output Format:
  1) Response: Name of the phenotype of interest.
  2) Feature_ID: The feature identifier.
  3) quantitative_sorting_score: The aggregate score of the feature.  This score is obtained by aggregating ranked lists of features using Borda method. Each ranked list corresponds to one instance of bootstrap sampling and is ranked using the absolute Pearson correlation coefficient. A higher score shows the feature is more relevant to the phenotype. This value is always between 1 and the total number of features.
  4) visualization_score: The min-max normalized value of quantitative_sorting_score. This value is always between 0 and 1.
  5) baseline_score: The Pearson correlation coefficient between the phenotype and the feature.

##### Option 3 (ProGENI Pearson):
- Choices:
  - Primary prioritization method = Absolute Pearson Correlation
  - Use knowledge Network = Yes
  - Use bootstrapping = No
- Output Format: 
  1) Response: Name of the phenotype of interest.
  2) Feature_ID: The feature identifier.
  3) quantitative_sorting_score: The ProGENI score of the gene.  A higher score shows the gene is more relevant to the phenotype. This value is always between -1 and 1.
  4) visualization_score: The min-max normalized value of quantitative_sorting_score. This value is always between 0 and 1.
  5) baseline_score: The Pearson correlation coefficient between the phenotype and the gene.
  6) Percent_appearing_in_restart_set: Multiplying this number with 100 gives the percent of the bootstrapping instances in which this gene was used in the restart set of ProGENI. Since no bootstrapping was done in this option, these values are either 0 or 1.

##### Option 4 (Robust-ProGENI Pearson):
- Choices:
  - Primary prioritization method = Absolute Pearson Correlation
  - Use knowledge Network = Yes
  - Use bootstrapping = Yes
- Output Format: 
  1) Response: Name of the phenotype of interest.
  2) Feature_ID: The feature identifier.
  3) quantitative_sorting_score: The aggregate score of the gene.  This score is obtained by aggregating ranked lists of genes using Borda method. Each ranked list corresponds to one instance of bootstrap sampling and is ranked using the ProGENI score. A higher score shows the gene is more relevant to the phenotype. This value is always between 1 and the total number of genes.
  4) visualization_score: The min-max normalized value of quantitative_sorting_score. This value is always between 0 and 1.
  5) baseline_score: The Pearson correlation coefficient between the phenotype and the gene.
  6) Percent_appearing_in_restart_set: Multiplying this number with 100 gives the percent of the bootstrapping instances in which this gene was used in the restart set of ProGENI.

##### Option 5 (T-test):
- Choices:
  - Primary prioritization method = T-test
  - Use knowledge Network = No
  - Use bootstrapping = No
- Output Format: 
  1) Response: Name of the phenotype of interest.
  2) Feature_ID: The feature identifier.
  3) quantitative_sorting_score: The absolute value of the T-statistic.  A higher score shows the feature is more differentially valued. 
  4) visualization_score: The min-max normalized value of quantitative_sorting_score. This value is always between 0 and 1.
  5) baseline_score: The T-statistic for each feature obtained by comparing feature values for the two phenotype options.

##### Option 6 (Robust T-test):
- Choices:
  - Primary prioritization method = T-test
  - Use knowledge Network = No
  - Use bootstrapping = Yes
- Output Format: 
  1) Response: Name of the phenotype of interest.
  2) Feature_ID: The feature identifier.
  3) quantitative_sorting_score: The aggregate score of the feature.  This score is obtained by aggregating ranked lists of features using Borda method. Each ranked list corresponds to one instance of bootstrap sampling and is ranked using the absolute value of the T-statistic. A higher score shows the feature is more differentially valued. This value is always between 1 and the total number of features.
  4) visualization_score: The min-max normalized value of quantitative_sorting_score. This value is always between 0 and 1.
  5) baseline_score: The T-statistic for each feature obtained by comparing feature values for the two phenotype options.

##### Option 7 (ProGENI T-test):
- Choices:
  - Primary prioritization method = T-test
  - Use knowledge Network = Yes
  - Use bootstrapping = No
- Output Format: 
  1) Response: Name of the phenotype of interest.
  2) Feature_ID: The feature identifier.
  3) quantitative_sorting_score: The ProGENI score of the gene.  A higher score shows the gene is more relevant to the phenotype. This value is always between -1 and 1.
visualization_score: The min-max normalized value of quantitative_sorting_score. This value is always between 0 and 1.
  4) baseline_score: The T-statistic for each gene obtained by comparing gene expression for the two phenotype options.
  5) Percent_appearing_in_restart_set: Multiplying this number with 100 gives the percent of the bootstrapping instances in which this gene was used in the restart set of ProGENI. Since no bootstrapping was done in this option, these values are either 0 or 1.

##### Option 8 (Robust-ProGENI T-test):
- Choices:
  - Primary prioritization method = T-test
  - Use knowledge Network = Yes
  - Use bootstrapping = Yes
- Output Format: 
  1) Response: Name of the phenotype of interest.
  2) Feature_ID: The feature identifier.
  3) quantitative_sorting_score: The aggregate score of the gene.  This score is obtained by aggregating ranked lists of genes using Borda method. Each ranked list corresponds to one instance of bootstrap sampling and is ranked using the ProGENI score. A higher score shows the gene is more relevant to the phenotype. This value is always between 1 and the total number of genes.
  4) visualization_score: The min-max normalized value of quantitative_sorting_score. This value is always between 0 and 1.
  5) baseline_score: The T-statistic for each gene obtained by comparing gene expression for the two phenotype options.
  6) Percent_appearing_in_restart_set: Multiplying this number with 100 gives the percent of the bootstrapping instances in which this gene was used in the restart set of ProGENI.

#### B) top_features_by_phenotype_matrix - Top Ranked Feature Sets per Phenotype
- This file contains a matrix with the phenotype names as the column headers and the feature identifiers as the rows. A ‘1’ in this table indicates that the row feature was one of the top 100 ranking (highest scoring) features for that specific column phenotype using the method of choice.  All other values are 0. If the features are genes, this file can be used in the Gene Set Characterization pipeline.

#### C) clean_features_matrix.txt - Features Spreadsheet File
- This file contains the user's input feature matrix. If the KN was used in the analysis, rows with gene names that are unable to be mapped or are not unique are discarded from this clean output.

#### D) clean_phenotypic_matrix.txt - Processed Phenotype Spreadsheet File
- This file contains a modified version of the user’s input phenotypic matrix where foreign characters are removed and NAs are notated with a specific value.

#### E) gene_map.txt - Gene ID Mapping File (if KN guided analysis)
- The columns of this file are defined as follows:
  1) user_supplied_gene_name: the gene/transcript/protein identifier supplied by the user in the original genomic spreadsheet.
  2) status: if the user-supplied gene name could be mapped to a stable Ensembl gene ID, this column will contain the Ensembl gene ID; otherwise, this column will contain the reason mapping failed ("unmapped-none" if no match was found, or "unmapped-many" if multiple matches were found).

#### F) run_params.yml - Run Parameters File
- This yaml file contains the run parameters file that was used by the computation container that ran the KnowEnG analysis pipeline (implementation available on GitHub) on the input data.

#### G) run_cleanup_params.yml - Cleanup Run Parameters File
- This yaml file contains the run parameters file that was used by the computation container that ran the KnowEnG data-cleanup pipeline (implementation available on GitHub) on the input data.

#### H) interaction_network.metadata - Knowledge Network Metadata (if KN guided analysis)
- This yaml file contains information about the interaction network if used in the analysis.  Its keys include summarizations about the network size (“data”), its public data source details (“datasets”), information about the meaning of its edges (“edge_type”), and some commands and configurations used in its construction (“export”).

The licensing terms of the source code and containers to perform this analysis can be found at https://knoweng.github.io/. Licensing information relating to the data in the Knowledge Network can be found https://knoweng.org/kn-data-references/#kn_data_resources. 
