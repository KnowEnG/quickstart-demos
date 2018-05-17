

This file contains information about the files in this repo (e.g., what's in them, how they were created, where they came from).


### Feature Prioritization (FP)

#### `demo_FP.genomic.txt`
#### `demo_FP.phenotypic.txt`


### Gene Set Characterization (GSC)

#### `demo_GSC.list.txt`
#### `demo_GSC.spreadsheet.txt`


### Signature Analysis (SA)

#### samples file: name: `demo_SA.samples.txt.bz2`

This file was created as follows.  First, a set of files were selected using the CGC Data Browser:
```
Dataset: TCGA GRCh38
  Entity: File
    Properties:
      Data category: Transcriptome Profiling
      Data format: TXT
  Entity: Investigation
    Properties:
      Disease type: Lung Squamous Cell Carcinoma
```

This yields 1,653 files, with names of the form `*.htseq.counts.tz`, `*.FPKM-UQ.txt`, and `*.FPKM.txt`.  Remove all that match the first two patterns, leaving only the `*.FPKM.txt` (551 files).

Next, the [Spreadsheet Builder](https://cgc.sbgenomics.com/u/mepstein/geneprioritization/apps/#mepstein/geneprioritization/spreadsheet-builder/25) (SB) was run with these files as the input files.  (All of the parameters were left blank, which means that the default settings were used. In particular this means that a z-score normalization was done on the output that was generated.)

The demo samples file was the *Genomic Spreadsheet File* output file of this run.

([Here](https://cgc.sbgenomics.com/u/mepstein/geneprioritization/tasks/e92155f4-c02d-4b9e-b717-279f9ca1ee17/) is the run that created this file.)

Two additional steps were done to reduce the size of this file to allow it to be stored on github.  First, the values were rounded when written, using a line of code (python) like the following:
```df.to_csv(output_file , sep="\t", float_format="%g")```
And then it was compressed using `bzip2`.

#### Demo signatures file: name: `demo_SA.signatures.txt`

This file was taken from this publication (original name `predictor.centroids.csv`):

Wilkerson, M.D. et al. (2010) Lung squamous cell carcinoma mRNA expression subtypes are reproducible, clinically important and correspond to normal cell types.

Available at [http://cancer.unc.edu/nhayes/publications/scc/](http://cancer.unc.edu/nhayes/publications/scc/).

#### Demo signatures file, mapped version: name: `demo_SA.signatures.mapped.txt`

(This is simply a version of the signatures file that has had the gene names mapped, for instances where it's necessary to start off with a mapped version.)


### Samples Clustering (SC)

#### `demo_SC.genomic.txt`
#### `demo_SC.phenotypic.txt`


### Spreadsheet Visualizer (SSV)

#### `demo_SSV.genomic.txt`
#### `demo_SSV.phenotypic.txt`


