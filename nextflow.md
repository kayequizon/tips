# Nextflow
References:
  * Using nextflow on HPC https://lescailab.unipv.it/guides/eos_guide/use_nextflow.html
  * Nextflow channel cheatsheet https://github.com/danrlu/Nextflow_cheatsheet/blob/main/nextflow_cheatsheet.pdf
  * https://github.com/danrlu/nextflow_cheatsheet
  * https://training.nextflow.io/hello_nextflow/02_hello_world/
    
### Project directory
  * `${workflow.projectDir}`
    * Usually the folder that contains `main.nf`
    * e.g. `publishDir "${workflow.projectDir}/output", mode: 'copy'`
  * `${workflow.launchDir}`
    * The current working directory (~`$pwd`) of the terminal when running `nextflow main.nf`
      
### Work directories
  * Specify the location of the parent working directory using either
    * `workDir = '/path_to_tmp/'` OR
    * `-w` option when running `nextflow main.nf`
  * Every execution of a process creates a work directory that contains/will contain
    *   symlinks of files from the input channel
    *   intermediate files
    *   log files
    *   output files
  * Files for `publishDir` must be specified in both `publishDir` and output channels.
    * Don't use `publishDir "path", mode:'move'` unless there's no following process that uses the output file. This moves the output file away from the working directory so it can't be used as an input for another process.
  * Run `nextflow clean -f` to clean up the working directories every once in a while.
    
### Params
  * `params` hold command line arguments. Used to specify options (e.g. filenames and processing options) at run time and not while writing the script.
   * e.g.
     ```
     output:
         path 'output.txt'
     ```
     becomes
     ```
     output:
         path params.output_file
     ```
   * Declare params by prepending the prefix `params.` to a variable name
   * Specify the value of a param at the command line by prefixing teh param name with a double dash character (e.g. `--param`)
### Processes
  * Make debugging easier by making process names UPPERCASE.
    
### Channels and items
  * Channels are the input type for processes

### HPC/slurm
Launch a nextflow workflow as an sbatch submission by writing a launch job script, e.g. `launch_nf.job`
```
#!/usr/bin/env bash

#SBATCH --partition NMLResearch
#SBATCH --mem 4G
#SBATCH -c 1

PIPELINE=$1
CONFIG=$2

mamba activate nextflow-24.02.0-edge

nextflow -C ${CONFIG} run ${PIPELINE}
```
and then running it
```
sbatch -p NMLResearch -c 1 --mem=4G launch_nf.job $NFPIPELINEPATH $NFCONFIGPATH
```
