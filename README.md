GitHub repository containing a Snakemake pipeline to run 
ADMIXTURE and a Quarto example report summarizing and plotting 
the results: 

- `report/` contains the Quarto report `admixture.report.pdf`, 
along with all files needed to render the report from 
`admixture.report.qmd`
- `workflow/` contains the Snakemake pipeline that was run on 
the HPC cluster Dardel (PDC/KTH) to execute ADMIXTURE, including 
the required configuration and metadata files 
