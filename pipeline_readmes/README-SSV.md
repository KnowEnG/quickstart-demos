This file contains a description of the different output files of the spreadsheet
visualization (SSV) pipeline. The other files in this zip archive are as follows:

#### Reference Files

All of the user spreadsheets included in the analysis are copied into the zip
archive. Each spreadsheet is oriented such that the columns correspond to
samples, in order to match the visualization layout. If that orientation does
not match the file's original orientation, `_transposed` is appended to the
original file name.

#### Results Files

For each spreadsheet from *Reference Files* that consists entirely of numeric
data (not including row labels and column labels), the zip archive contains a
separate spreadsheet of row variances. The name of the row variances spreadsheet
is the reference spreadsheet's name followed by `.variances.txt`. The
spreadsheet has two columns. In each row, the first column is the row label from
the reference spreadsheet, and the second column is the variance of the row's
values as found in the reference spreadsheet.
