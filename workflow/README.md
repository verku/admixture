# ADMIXTURE pipeline

Snakemake pipeline to run ADMIXTURE on a merged and 
filtered VCF file.

## Requirements

- Conda/mamba. To run the pipeline, the admixture conda 
environment ("admx") needs to be created from the file 
`environment.yml` and activated. 

- Singularity/apptainer. The pipeline executes each rule 
in a container.

- A slurm profile is provided with the pipeline for runs
on HPC clusters with the slurm workload manager. Please add 
your compute project to the file 
`admixture/workflow/slurm/config.yaml` by modifying the 
following line: 

```
  slurm_account: XXX-XX-XXX # update this to your slurm account
```

- Edit the configuration file `admixture/workflow/config.yaml` 
to provide paths to the input data and output file locations 
as well as the numbers of K to be tested.

## Pipeline analysis steps

The pipeline performs the following analysis steps:

- Convert the population VCF files to plink format for 
ADMIXTURE using plink v1.90b6.12

- Run ADMIXTURE v1.3.0 for a range of K values (number of 
populations) as specified in the configuration file

## How to run the pipeline

### Dardel HPC cluster

- Start a tmux or screen session

- On Dardel, the conda environment can be activated as 
follows from a pre-installed conda environment (update the 
path to your conda environments): 

```
module load conda
export CONDA_ENVS_PATH=/path/to/your/conda_environments
conda activate admx
```

- Move into `admixture/workflow`, update the configuration 
file `config.yaml`, and start a dry run of the pipeline:

```
snakemake --profile slurm -n &> YYMMDD.dry.out
```

- Inspect the output from the dry run in the file 
`YYMMDD.dry.out` and if it worked without any 
errors, start the main run of the pipeline:

```
snakemake --profile slurm &> YYMMDD.main.out
```

- Inspect the file `YYMMDD.main.out` for any error 
messages. Log files from slurm jobs and from each rule are 
placed in the folder `logs` in respective subfolders.

## Further data analysis and plotting

An example for further data analysis can be found in 
the NBIS project report `admixture/report/admixture.report.qmd`,
a rendered version is available in HTML format 
(`admixture/report/admixture.report.html`). 