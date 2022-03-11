# ASTER tutorial
Tutorial for [ASTER](https://github.com/chaoszhang/ASTER.git)

# Installation
```
git clone https://github.com/chaoszhang/ASTER.git
cd ASTER
make
make aaa-gpu
g++ -std=gnu++11 -march=native -Ofast -pthread src/asterisk-biallelic.cpp -o bin/asterisk-biallelic
```

# Testing CPU multithreading
## A toy example
```
bin/astral-pro -t NUM_THREADS example/multitree.nw
```
## 1KP
Download and unzip [1KP](https://github.com/chaoszhang/ASTER-tutorial/raw/main/1kp-12na-gentrees.tre.gz) gene trees.
You can start with one round of exploration. (Replace NUM_THREADS with your desired number of threads)
```
bin/astral-pro -r 1 -s 0 -t NUM_THREADS 1kp-12na-gentrees.tre
```
The you can run
```
bin/astral-pro -t NUM_THREADS 1kp-12na-gentrees.tre
```

# Testing GPU code
## A toy example
```
bin/asterisk-biallelic-cuda -t NUM_THREADS -y example/example.phylip
```
## S200
Download and unzip [S200](https://github.com/chaoszhang/ASTER-tutorial/raw/main/all-genes.phylip.gz) alignments.
You can start with one round of exploration. (Replace NUM_THREADS with your desired number of threads)
```
bin/asterisk-biallelic-cuda -r 1 -s 0 -t NUM_THREADS -y all-genes.phylip
```
The you can run
```
bin/asterisk-biallelic-cuda -t NUM_THREADS -y all-genes.phylip
```
You can compare its running time with the CPU implementation:
```
bin/asterisk-biallelic -r 1 -s 0 -t NUM_THREADS -y all-genes.phylip
```
and
```
bin/asterisk-biallelic -t NUM_THREADS -y all-genes.phylip
```
