# Computing equipment

## CECI-clusters

All info you need to start using a CECI cluster can be found on their [website](https://support.ceci-hpc.be/doc/). Given the walltimes of the different servers, Dragon1 (walltime up to 41 days) and Dragon2 (walltime up to 21 days) are likely the most interesting for choices for your needs. 

After you've [set up the public-private key pair](https://support.ceci-hpc.be/doc/_contents/QuickStart/ConnectingToTheClusters/FromAUnixComputer.html?highlight=ssh), it is useful to also walk through the [ssh config wizard](https://www.ceci-hpc.be/sshconfig.html) as this will enable you to connect to your cluster of choice, e.g. Dragon1, with simple and short commands:

```bash
ssh dragon1
```

The Slurm  workload manager [script wizard](https://www.ceci-hpc.be/scriptgen.html) has also proven very useful.

## SpELL-cluster (GPU computing)

The lab has acces to its own compute node. If you want to use it, pass by Simon and he can arrange you get an account on this. 

On this node you have acces to 32 CPUs (with a maximum memory use of 125 GB RAM each) and, more interesting for phylogenetic analyses, 4 GPUs. The walltime currently is set to 35 days. As for the CECI-clusters, workload on this node is also managed using Slurm. 

An example job submission script for using GPUs can be found below:

```bash	
#!/bin/bash

# Running jobs in parallel over CPUs -- e.g. if you want one process that can use X cores for multithreading: set --ntasks=1 and --cpus-per-task=X
# With --gres, you can, optionally, detail how many GPUs your job will use: --gres="gpu:1" (with 4 the maximum). The number of GPUs can be omitted.

#SBATCH --job-name=<job name>
#SBATCH --ntasks=1
#SBATCH --cpus-per-task=1
#SBATCH --gres="gpu" # or --gres="gpu:<1, 2, 3 or 4>" 
#SBATCH --time=<requested walltime in format DD-hh:mm:ss>
```

To show info on running jobs, and in particular to check that the GPU resource is used, use the `squeue` command.
We've found it useful to add the following line to `~/.bashrc`:

```bash
export SQUEUE_FORMAT="%.18i %.9P %.8j %.8u %.2t %.10M %.6D %.20R %b"
```

To immediately make use of this, source `.bashrc` (this will not be necessary the following times you log in):

```bash
source ~/.bashrc
```

