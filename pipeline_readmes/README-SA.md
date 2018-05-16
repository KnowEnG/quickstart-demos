This file contains a description of the different output files of the signature analysis (SA) pipeline. The downloaded zip archive will contain up to six other files for users to further examine and understand their results.  These other files are:

#### Results Files
- A) similarity_matrix.tsv - Scores for Signatures for each Sample
- B) similarity_matrix.binary.tsv - Indicates the Signature with the maximum Score for each Sample

#### Reference Files
- C) clean_samples_matrix.tsv - Cleaned/Mapped Samples Spreadsheet File
- D) clean_signatures_matrix.tsv - Cleaned/Mapped Samples Spreadsheet File
- E) gene_map.txt - Gene ID Mapping File
- F) run_params.yml - Run Parameters File

Below are descriptions for the contents of each of these files:

#### A) similarity_matrix.tsv - Scores for Signatures for each Sample
- This file is a spreadsheet with one row for each sample and one column for each signature, with each cell containing the similarity score for that signature for that sample, based on the specified similarity measure.

The format of the file is tab-separated values, with a header row indicating the column names (signatures) and the first column indicating the row names (samples).

#### B) similarity_matrix.binary.tsv - Indicates the Signature with the maximum Score for each Sample
- This file is of the same format as the previous file, with each row (sample) containing a 1 in the column for the signature with the highest similarity score, 0's in all the other columns.

#### C) clean_samples_matrix.tsv - Cleaned/Mapped Samples Spreadsheet File
- This file contains a modified version of the user’s input samples matrix where the original gene identifiers provided have been mapped to stable Ensembl gene_ids where possible.  Rows with original gene names that are unable to be mapped or are not unique are discarded from this clean output.  (This mapping is optional, and is on by default.)

#### D) clean_signatures_matrix.tsv - Cleaned/Mapped Samples Spreadsheet File
- This file contains a modified version of the user’s input signatures matrix where the original gene identifiers provided have been mapped to stable Ensembl gene_ids where possible.  Rows with original gene names that are unable to be mapped or are not unique are discarded from this clean output.  (This mapping is optional, and is on by default.)

#### E) gene_map.txt - Gene ID Mapping File
- The columns of this file are defined as follows:
  1) KN_gene_id: the stable Ensembl gene ID that KnowEnG uses internally
  2) user_gene_id: the corresponding gene/transcript/protein identifier supplied by the user in the original genomic spreadsheet.

#### F) run_params.yml - Run Parameters File
- This yaml file contains the run parameters file that was used by the computation container that ran the KnowEnG pipeline (implementation available on GitHub) on the input data.

The licensing terms of the source code and containers to perform this analysis can be found at https://knoweng.github.io/. Licensing information relating to the data in the Knowledge Network can be found https://knoweng.org/kn-data-references/#kn_data_resources.
