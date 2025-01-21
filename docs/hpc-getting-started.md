## CECI Intro

All info you need to start using the CECI cluster can be found on their [website](https://support.ceci-hpc.be/doc/). 
Particularly useful is the [script wizard](https://www.ceci-hpc.be/scriptgen.html).

Given the walltimes of the different servers, Dragon1 (walltime up to 41 days) and Dragon2 (walltime up to 21 days) are most interesting for our purposes. 

## GPU nodes

The lab has acces to its own compute node. If you want acces to this, go by Simon and he can arrange this. 

Specifically, on this node you have acces to 32 CPUs (with a maximum use of 125 GB RAM each) and 4 GPUs. The walltime currently is set to 35 days.

An example job submission script can be found below:

```
#!/bin/bash

# Running jobs in parallel over CPUs -- e.g. if you want one process that can use X cores for multithreading: set --ntasks=1 and --cpus-per-task=X
# With --gres, you can, optionally, detail how many GPUs your job will use: --gres="gpu:1" (with 4 the maximum). The number of GPUs can be omitted.

#SBATCH --job-name=<job name>
#SBATCH --ntasks=1
#SBATCH --cpus-per-task=1
#SBATCH --gres="gpu" or --gres="gpu:>1, 2, 3 or 4>" 
#SBATCH --time=<runtime in format DD-hh:mm:ss>
```

To show info on running jobs, and in particular to check that the GPU resource is used, use the `squeue` command after adding the following line to your `.bashrc` (and sourcing it).

```
export SQUEUE_FORMAT="%.18i %.9P %.8j %.8u %.2t %.10M %.6D %.20R %b"
```


