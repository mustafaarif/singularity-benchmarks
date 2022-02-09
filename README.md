# Singularity Testing/Benchmarking on Dardel

These benchmarks are done to verify Singularity on Dardel system.

## Singularity and MPI
MPI with Singularity can work in two modes:
- *Hybrid*
  - In this mode, the container MPI works with host MPI via PMI interface. This has proven to be slower.
- *Bind*
  - In this mode, the container MPI is only used at the time of compiling application inside the container. While running the container, the Host MPI is bind mount inside the container. This has better performance since container is utilizing the Host MPI which is optimized for the system.

## Benchmakrs Configuration

The benchmark tests are done in following configurations.
- mpi-bind
  - MPI app runs inside a container and links to host(cray) MPI.
- mpi-hybrid
  - MPI app runs inside a container and links to MPI present in the cotnainer.
- mpi-host
  - MPI app runs on host without any containerization.

## Results

![bandwidth_benchmarks](https://user-images.githubusercontent.com/10483719/153181812-b089ac0e-0008-4628-864f-689858f84833.png)
