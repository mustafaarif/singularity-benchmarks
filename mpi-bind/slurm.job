#!/bin/bash
#SBATCH -J mpi_test
#SBATCH -p main
#SBATCH --reservation=sing
#SBATCH --time=00:05:00
#SBATCH -N 2
#SBATCH -A pdc.staff
#SBATCH --ntasks-per-node=128
#SBATCH --output=slurm-%j.out
#SBATCH --error=slurm-%j.err

export LD_LIBRARY_PATH=$CRAY_LD_LIBRARY_PATH:$LD_LIBRARY_PATH
export LD_LIBRARY_PATH=/opt/cray/pe/lib64:/usr/lib64:$LD_LIBRARY_PATH
export SINGULARITYENV_LD_LIBRARY_PATH=$LD_LIBRARY_PATH
echo $SINGULARITYENV_LD_LIBRARY_PATH

# Show linking on mpi app to verify if host mpi libs are being used 
srun --ntasks=1 singularity exec -B /etc/libibverbs.d:/etc/libibverbs.d:ro -B /var/spool:/var/spool -B /usr/lib64:/usr/lib64:ro -B /opt:/opt:ro -B /var/opt:/var/opt:ro ./mpi-bw-bind.sif bash -c 'ldd /mpiapp/mpi_bandwidth'

# Run mpi app
srun --ntasks=256 singularity exec -B /etc/libibverbs.d:/etc/libibverbs.d:ro -B /var/spool:/var/spool -B /usr/lib64:/usr/lib64:ro -B /opt:/opt:ro -B /var/opt:/var/opt:ro ./mpi-bw-bind.sif bash -c '/mpiapp/mpi_bandwidth'
