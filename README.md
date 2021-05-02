#NEUZZ: a neural-network-assisted fuzzer

Workaround to get NEUZZ to work on a Mac.

## Prerequisite
- Python 3
- Tensorflow 2
- Keras
## Build
```bash
    gcc -O3 -funroll-loops ./neuzz.c -o neuzz
```
## Usage
We use readelf as an example.<br/>
Open a terminal, start nn module
```bash
    #python nn.py [program [arguments]]
    python nn.py ./readelf -a
```
open another terminal, start neuzz module.
```bash
    #./neuzz -i in_dir -o out_dir -l mutation_len [program path [arguments]] @@
    ./neuzz -i neuzz_in -o seeds -l 7506 ./readelf -a @@  
```
If you want to try NEUZZ on a new program, 
1. Compile the new program from source code using afl-gcc.
2. Collect the training data by running AFL on the binary for a while(about an hour), then copy the queue folder to neuzz_in.
3. Follow the above two steps to start NN module and NEUZZ module.


Original Work - NEUZZ: a neural-network-assisted fuzzer (S&P'19)
See IEEE S&P(Oakland)'19 [slides](https://drive.google.com/file/d/1_A33wucTOA2nZpKVArvsXajh-2LNrCZK/view?usp=sharing) and paper [NEUZZ: Efficient Fuzzing with Neural Program Smoothing](https://arxiv.org/abs/1807.05620) for details.

Original Repository - https://github.com/Dongdongshe/neuzz 
