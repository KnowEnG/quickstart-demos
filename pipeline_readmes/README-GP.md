This file contains a description of the different output files of the gene prioritization (GP) pipeline. The downloaded zip archive will contain up to seven other files for users to further examine and understand their results.  These other files are:

#### Results Files
- A) genes_ranked_per_phenotype - Scores for Ranked Genes for Each Phenotype
- B) top_genes_by_phenotype_matrix - Top Ranked Gene Sets per Phenotype

#### Reference Files
- C) clean_genomic_matrix.txt - Mapped Genomic Spreadsheet File
- D) clean_phenotypic_matrix.txt - Processed Phenotype Spreadsheet File
- E) gene_map.txt - Gene ID Mapping File
- F) run_params.yml - Run Parameters File
- G) interaction_network.metadata - Knowledge Network Metadata (if KN guided analysis)

Below are descriptions for the contents of each of these files:

#### A) genes_ranked_per_phenotype - Scores for Ranked Genes for Each Phenotype
The output format of this file will depend on the choices you made in configuring the analysis.

##### Option 1 (Pearson Correlation): 
- Choices: 
  - Primary prioritization method = Absolute Pearson Correlation
  - Use knowledge Network = No
  - Use bootstrapping = No
- Output Format  :
  1) Response: Name of the phenotype of interest.
  2) Gene_ENSEMBL_ID: The ENSEMBL ID of the gene.
  3) quantitative_sorting_score: The absolute value of the Pearson correlation coefficient between the phenotype and the gene.  A higher value shows the gene is more relevant to the phenotype. This value is between 0 and 1.
  4) visualization_score: The min-max normalized value of quantitative_sorting_score. This value is always between 0 and 1.
  5) baseline_score: The Pearson correlation coefficient between the phenotype and the gene.

##### Option 2 (Robust Pearson Correlation):
- Choices:
  - Primary prioritization method = Absolute Pearson Correlation
  - Use knowledge Network = No
  - Use bootstrapping = Yes
- Output Format:
  1) Response: Name of the phenotype of interest.
  2) Gene_ENSEMBL_ID: The ENSEMBL ID of the gene.
  3) quantitative_sorting_score: The aggregate score of the gene.  This score is obtained by aggregating ranked lists of genes using Borda method. Each ranked list corresponds to one instance of bootstrap sampling and is ranked using the absolute Pearson correlation coefficient. A higher value shows the gene is more relevant to the phenotype. This value is always between 1 and the total number of genes.
  4) visualization_score: The min-max normalized value of quantitative_sorting_score. This value is always between 0 and 1.
  5) baseline_score: The Pearson correlation coefficient between the phenotype and the gene.

##### Option 3 (ProGENI Pearson):
- Choices:
  - Primary prioritization method = Absolute Pearson Correlation
  - Use knowledge Network = Yes
  - Use bootstrapping = No
- Output Format: 
  1) Response: Name of the phenotype of interest.
  2) Gene_ENSEMBL_ID: The ENSEMBL ID of the gene.
  3) quantitative_sorting_score: The ProGENI score of the gene.  A higher value shows the gene is more relevant to the phenotype. This value is always between -1 and 1.
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
  2) Gene_ENSEMBL_ID: The ENSEMBL ID of the gene.
  3) quantitative_sorting_score: The aggregate score of the gene.  This score is obtained by aggregating ranked lists of genes using Borda method. Each ranked list corresponds to one instance of bootstrap sampling and is ranked using the ProGENI score. A higher value shows the gene is more relevant to the phenotype. This value is always between 1 and the total number of genes.
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
  2) Gene_ENSEMBL_ID: The ENSEMBL ID of the gene.
  3) quantitative_sorting_score: The absolute value of the T-statistic.  A higher value shows the gene is more differentially expressed. 
  4) visualization_score: The min-max normalized value of quantitative_sorting_score. This value is always between 0 and 1.
  5) baseline_score: The T-statistic for each gene obtained by comparing gene expression for the two phenotype options.

##### Option 6 (Robust T-test):
- Choices:
  - Primary prioritization method = T-test
  - Use knowledge Network = No
  - Use bootstrapping = Yes
- Output Format: 
  1) Response: Name of the phenotype of interest.
  2) Gene_ENSEMBL_ID: The ENSEMBL ID of the gene.
  3) quantitative_sorting_score: The aggregate score of the gene.  This score is obtained by aggregating ranked lists of genes using Borda method. Each ranked list corresponds to one instance of bootstrap sampling and is ranked using the absolute value of the T-statistic. A higher value shows the gene is more differentially expressed. This value is always between 1 and the total number of genes.
  4) visualization_score: The min-max normalized value of quantitative_sorting_score. This value is always between 0 and 1.
  5) baseline_score: The T-statistic for each gene obtained by comparing gene expression for the two phenotype options.

##### Option 7 (ProGENI T-test):
- Choices:
  - Primary prioritization method = T-test
  - Use knowledge Network = Yes
  - Use bootstrapping = No
- Output Format: 
  1) Response: Name of the phenotype of interest.
  2) Gene_ENSEMBL_ID: The ENSEMBL ID of the gene.
  3) quantitative_sorting_score: The ProGENI score of the gene.  A higher value shows the gene is more relevant to the phenotype. This value is always between -1 and 1.
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
  2) Gene_ENSEMBL_ID: The ENSEMBL ID of the gene.
  3) quantitative_sorting_score: The aggregate score of the gene.  This score is obtained by aggregating ranked lists of genes using Borda method. Each ranked list corresponds to one instance of bootstrap sampling and is ranked using the ProGENI score. A higher value shows the gene is more relevant to the phenotype. This value is always between 1 and the total number of genes.
  4) visualization_score: The min-max normalized value of quantitative_sorting_score. This value is always between 0 and 1.
  5) baseline_score: The T-statistic for each gene obtained by comparing gene expression for the two phenotype options.
  6) Percent_appearing_in_restart_set: Multiplying this number with 100 gives the percent of the bootstrapping instances in which this gene was used in the restart set of ProGENI.

#### B) top_genes_by_phenotype_matrix - Top Ranked Gene Sets per Phenotype
- This file contains a matrix with the phenotype names as the column headers and stable Ensembl gene_ids as the rows. A ‘1’ in this table indicates that the row gene was one of the top 100 ranking (highest scoring) genes for that specific column phenotype using the method of choice.  All other values are 0. This file can be used in the Gene Set Characterization pipeline.

#### C) clean_genomic_matrix.txt - Mapped Genomic Spreadsheet File
- This file contains a modified version of the user’s input genomic matrix where the original gene identifiers provided have been mapped to stable Ensembl gene_ids where possible.  When using the Knowledge Network guided analysis, rows with original gene names that are unable to be mapped or are not unique are discarded from this clean output.

#### D) clean_phenotypic_matrix.txt - Mapped Genomic Spreadsheet File
- This file contains a modified version of the user’s input phenotypic matrix where foreign characters are removed and NAs are notated with a specific value.

#### E) gene_map.txt - Gene ID Mapping File
- The columns of this file are defined as follows:
  1) KN_gene_id: the stable Ensembl gene ID that KnowEnG uses internally
  2) user_gene_id: the corresponding gene/transcript/protein identifier supplied by the user in the original genomic spreadsheet.

#### F) run_params.yml - Run Parameters File
- This yaml file contains the run parameters file that was used by the computation container that ran the KnowEnG pipeline (implementation available on GitHub) on the input data.

#### G) interaction_network.metadata - Knowledge Network Metadata (if KN guided analysis)
- This yaml file contains information about the interaction network if used in the analysis.  Its keys include summarizations about the network size (“data”), its public data source details (“datasets”), information about the meaning of its edges (“edge_type”), and some commands and configurations used in its construction (“export”).

The licensing terms of the source code, containers, and the Knowledge Network used to perform this analysis can be found at https://knoweng.github.io/.
