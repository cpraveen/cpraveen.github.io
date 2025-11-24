---
layout: default
---

# SLURM

```shell
sinfo 
sinfo -N -l
sinfo --long —-partition=big_compute
sbatch script.sh
squeue
squeue --me
scancel <jobid>
```

## Sample slurm script

```bash
#!/bin/bash
#SBATCH --partition=big_compute         # Partition name
#SBATCH --nodes=5                       # Number of nodes
#SBATCH --ntasks-per-node=192           # ranks per node <= no. of cores/node
#SBATCH --cpus-per-task=1               # 1 is default
#SBATCH --time=0-01:00:00               # days-hours:min:sec
#SBATCH --job-name=NAME                 # Job name
#SBATCH -o slurm.%j.out                 # Slurm output file (%j = job ID)
#SBATCH -e slurm.%j.err                 # Slurm error file
#SBATCH --mail-user=you@mail.com
#SBATCH --mail-type=ALL                 # Mail on job BEGIN, END, FAIL
#SBATCH --export=ALL                    # Export environment variables

cd $SLURM_SUBMIT_DIR

# Report job context
echo "Job $SLURM_JOB_ID began"
echo "Running on host $(hostname)"
echo "Time is $(date)"
echo "Directory is $(pwd)"
echo "Using ${SLURM_NTASKS} processors across ${SLURM_JOB_NUM_NODES} nodes"

# Load proper env and modules

# Executable
EXE=./build/main
INPUT=input.prm
LOG=log.txt

mpirun -np $SLURM_NTASKS $EXE $INPUT > $LOG

echo "Job $SLURM_JOB_ID ended"
echo "Time is $(date)"
```
In this script, total number of ranks = `nodes * ntasks-per-node = SLURM_NTASKS`.  Instead of specifying `nodes` and `ntasks-per-node`, you can specify the total number of ranks

```bash
#SBATCH --nodes=960                     # Total number of ranks
```

and let slurm decide the number of ranks per node.

## More info

* [Slurm tutorial](https://support.ceci-hpc.be/doc/SubmittingJobs/SlurmTutorial)
* [Slurm guide for beginners](https://blog.ronin.cloud/slurm-intro)
