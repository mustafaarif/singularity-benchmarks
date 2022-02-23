# Gromacs with MPICH

## Clone this repo on host where you have root access
```
git clone https://github.com/mustafaarif/singularity-benchmarks.git
cd singularity-benchmarks/gromacs-build
```

## Build singularity image file using definition file
```
singularity build gromacs2020.sif singularity.def
```

## Copy container and slurm job file to Dardel
```
#Make sure you have ~/opt and ~/gromacs-run present on Dardel
scp gromacs2020.sif user@dardel.pdc.kth.se:~/opt/
scp slurm.job user@dardel.pdc.kth.se:~/gromacs-run/
```

## Login to Dardel and prepare test run directory
```
mkdir -p gromacs-run && cd gromacs-run
wget https://repository.prace-ri.eu/ueabs/GROMACS/1.2/GROMACS_TestCaseA.tar.gz
tar -xzf GROMACS_TestCaseA.tar.gz
```
## Submit slurm job
```
#Modify slurm.job file to add relevant SLURM account/partition/reservation 
sbatch slurm.job
```
