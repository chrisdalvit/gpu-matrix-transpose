# GPU Matrix Transpose

This repository implements and benchmarks different matrix transpose algorithms for GPU's using CUDA.

## Repository structure
The ```data``` folder contains the original benchmark data from the tested architectures that was used in the experimental analyses. 

The ```lib``` folder contains C-functions used by all tested algorithms with the corresponding header file.

The ```src``` folder contains C files with the different algorithms for matrix transposition.

## Setup project
After cloning the repository you can run 
```
make
```
and the files in ```src``` are compiled, and the benchmark test is started and stored in the ```stats``` folder (that is created by the Makefile). __Waring: It can take a lot of time for the benchmarks to finish!__

If you only want to compile the files in ```src``` create a folder ```bin``` and run 
```
make compile_c
```
This should compile all C files in ```src``` and store them into the ```bin``` folder without starting the benchmarks. Compiled binaries follow the naming convention of ```<ALGORITHM>-<OPTIMIZATION LEVEL>```

In order to run the experiments on the Marzola cluster run 
```
make marzola
```
The script compiles the source code and launches SLURM jobs on the cluster. Results are stored in the ```stats/``` folder.

## Validate implementations
The correctness of the provided implementations can be verified by running the compiled binaries in 'debug mode'. After compilation you can run 
```
./bin/<BINARY> <MATRIX SIZE> --debug
```
For example 
```
./bin/naive-0 2 --debug
```
Should output a randomly initialized matrix with dimension 2^2 and the corresponding transposed matrix. Additionaly the execution time and the effective bandwidth are displayed.