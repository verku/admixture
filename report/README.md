# Report 

This directory contains the files needed to render the Quarto 
report `admixture.report.qmd`, summarizing an admixture analysis 
and plotting the results with python. 

## Requirements

Quarto has to be installed on your computer, following the 
instructions on https://quarto.org/docs/get-started/. 

The conda environment admx has to be created from the file 
`admixture/workflow/environment.yaml` and activated, it 
contains the necessary python packages to render the report. 

## How to render the report

From within the activated conda environment admx, run the 
following command: 

```
quarto render report.qmd
```