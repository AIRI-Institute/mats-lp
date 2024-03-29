<div align="center">

[![Example](https://raw.githubusercontent.com/Tviskaron/pogema-svg/main/mats-lp-ep00001-half-maze-seed0.svg)](https://github.com/AIRI-Institute/mats-lp) 

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1CwDqAbbu-UJParx172Z1nEv-YsQY0Roh?usp=sharing)
[![arXiv](https://img.shields.io/badge/arXiv-2312.15908-b31b1b.svg)](https://arxiv.org/abs/2312.15908)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Decentralized Monte Carlo Tree Search for Partially Observable Multi-agent Pathfinding**



</div> 

This study addresses the challenging problem of decentralized lifelong multi-agent pathfinding. The proposed **MATS-LP** 
approach utilizes a combination of Monte Carlo Tree Search and reinforcement learning for resolving conflicts.

**Paper:** [Decentralized Monte Carlo Tree Search for Partially Observable Multi-agent Pathfinding](https://arxiv.org/abs/2312.15908)


## Installation:

To run MATS-LP, your system needs C++ Build Tools (CMake, g++, build-essential), python3 and ONNX runtime. 

Installation of Python packages:
```bash
pip3 install -r docker/requirements.txt
```

Installation of ONNX runtime:
```bash
wget https://github.com/microsoft/onnxruntime/releases/download/v1.14.1/onnxruntime-linux-x64-1.14.1.tgz \
    && tar -xf onnxruntime-linux-x64-1.14.1.tgz \
    && cp onnxruntime-linux-x64-1.14.1/lib/* /usr/lib/ && cp onnxruntime-linux-x64-1.14.1/include/* /usr/include/
```

Optionally, you could use the Dockerfile to build the image:
```bash
cd docker && sh build.sh
```
Alternatively, to pull the pre-built image from Docker Hub and tag it for local use, execute: 
```bash
docker pull tviskaron/mats-lp && docker tag tviskaron/mats-lp mats-lp
```

## Running MATS-LP:

To execute the **MATS-LP** algorithm and produce an animation using pre-trained weights of CostTracer, use the following command:

```bash
python3 main.py
```

You can adjust the environment and algorithm's parameters using arguments. For example:

```bash
python3 main.py --map_name wfi_warehouse --num_agents 10
python3 main.py --map_name pico_s24_od30_na32 --num_agents 10 --seed 42
python3 main.py --map_name mazes-s0_wc8_od55 --num_expansions 500 --num_threads 8
```

The animation will be stored in the `renders` folder.
The default parameters of MATS-LP are set to the values used in the paper.

Using docker: 
```bash
docker run --rm -ti -u $(id -u):$(id -g) -v $(pwd):/code -w /code mats-lp python3 main.py
```

We offer a Google Colab example that simplifies the process:
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1CwDqAbbu-UJParx172Z1nEv-YsQY0Roh?usp=sharing)


## Raw Data: 



The raw data, comprising the results of our experiments for MATS-LP, can be downloaded from the following link:
[Download Raw Data](https://github.com/AIRI-Institute/mats-lp/releases/download/v0/mats-lp-raw-data.zip)

## Citation:

If you find this code helpful in your research, please cite our paper as follows:
```bibtex
@article{skrynnik2023decentralized,
  title={Decentralized Monte Carlo Tree Search for Partially Observable Multi-agent Pathfinding},
  author={Skrynnik, Alexey and Andreychuk, Anton and Yakovlev, Konstantin and Panov, Aleksandr},
  journal={arXiv preprint arXiv:2312.15908},
  year={2023}
}
```
