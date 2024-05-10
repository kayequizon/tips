# Nextflow
References:
  * Using nextflow on HPC https://lescailab.unipv.it/guides/eos_guide/use_nextflow.html
  * Nextflow channel cheatsheet https://github.com/danrlu/Nextflow_cheatsheet/blob/main/nextflow_cheatsheet.pdf
  * https://github.com/danrlu/nextflow_cheatsheet
  * 
### Project directory
  * 
### Work directories
  * Specify the location of the parent working directory using either
    * `workDir = '/path_to_tmp/' OR
    * `-w` option when running `nextflow main.nf`
  * Every execution of a process creates a work directory that contains/will contain
    *   symlinks of files from the input channel
    *   intermediate files
    *   log files
    *   output files
### Processes
  * Make debugging easier by making process names UPPERCASE.
### Channels and items
  * Channels are the input type for processes
### Slurm
