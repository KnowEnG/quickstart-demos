
This file contains a description of the different output files of the network prepper (NP) pipeline. The downloaded zip archive will contain six other files for users to further examine and understand their results.  These other files are:

#### Results Files
- A) *.clean.edge - Final Clean Network Edge File
- B) *.clean.node_map - Final Network Node Mapping File

#### Reference Files
- C) *.metadata - Network Prepper Metadata
- D) *.full_mapped_edges.tsv - Intermediate Network Edge File
- E) *.full_mapped_nodes.tsv - Intermediate Node Mapping File
- F) run_params.yml - Run Parameters File

Below are descriptions for the contents of each of these files:

#### A) *.clean.edge - Final Clean Network Edge File
This file contains the edges remaining in the network after nodes have been mapped to stable Ensembl identifiers, unmapped nodes and edges dropped, largest weight duplicate edges selected, and optional cleaning operations performed. The format of this file will be three columns and each row will represent a network edge:
  1) Edge Mapped Source: stable Ensembl identifier found by KnowEnG for the source node of the edge
  2) Edge Mapped Target: stable Ensembl identifier found by KnowEnG for the target node of the edge
  3) Edge Weight: maximum weight of all edges for the given pair of source and target

#### B) *.clean.node_map - Final Network Node Mapping File
This file contains information for the nodes in the final network that maps the original node names to entities in the Knowledge Network. The file has six columns:
  1) Original Node ID: user upload name for node
  2) KnowEnG Node ID: stable Ensembl identifier found by KnowEnG
  3) Node Type: indicator that node is of type 'Gene'
  4) Node Alias: standard short name for gene
  5) Node Description: full description of gene name
  6) Node Biotype: biotype of node gene

#### C) *.metadata - Network Prepper Metadata
- This yaml file contains information about the prepared network. Its keys include summarizations about the network size, information about the meaning of its edges, and some commands and configurations used in its construction.

#### D) *.full_mapped_edges.tsv - Intermediate Network Edge File
The rows of this file correspond one-to-one with the rows of the input edge file.  Four additional columns have been pre-pended to the original file:
  1) Source Mapped ID: stable Ensembl identifier found by KnowEnG for the source node of the edge
  2) Source Mapped Alias: standard short name for the source node of the edge
  3) Target Mapped ID: stable Ensembl identifier found by KnowEnG for the target node of the edge
  4) Target Mapped Alias: standard short name for the target node of the edge
  \* All remaining columns will correspond to the columns of the original input file

#### E) *.full_mapped_nodes.tsv - Intermediate Node Mapping File
This file contains information for all nodes in the original network and mapping information for those node names to entities in the Knowledge Network. The file has six columns:
  1) Original Node ID: user upload name for node
  2) KnowEnG Node ID: stable Ensembl identifier found by KnowEnG or one of two reasons for mapping failure ('unmapped-none'-original node name not found, 'unmapped-many'-multiple stable identifiers associated with original node name)
  3) Node Type: indicator that node is of type 'Gene' or 'None' if unmapped
  4) Node Alias: standard short name for gene or 'None' if unmapped
  5) Node Description: full description of gene name or 'None' if unmapped
  6) Node Biotype: biotype of node gene or 'None' if unmapped

#### F) run_params.yml - Run Parameters File
- This yaml file contains the run parameters file that was used by the computation container that ran the KnowEnG analysis pipeline (implementation available on GitHub) on the input data.

The licensing terms of the source code and containers to perform this analysis can be found at https://knoweng.github.io/. Licensing information relating to the data in the Knowledge Network can be found https://knoweng.org/kn-data-references/#kn_data_resources.
