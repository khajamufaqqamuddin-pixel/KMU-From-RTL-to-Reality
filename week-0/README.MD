# 🧠 VSD SoC Labs – Week 0: Toolchain Setup

Welcome to **Week 0** of the **RISC-V Reference SoC Tapeout Program** by [VLSI System Design (VSD)](https://www.vlsisystemdesign.com/soc-labs/). This repository documents the setup and verification of essential open-source tools required throughout the 20-week SoC design journey.

---

## 🚀 Objective

In this initial week, the goal is to install and validate the following tools:

- **Yosys** – RTL synthesis
- **Icarus Verilog** – simulation
- **GTKWave** – waveform viewer

These tools form the foundation for digital design, verification, and SoC development workflows.

---

## 💻 System Requirements

To ensure smooth tool installation and usage, the following system specifications are recommended:

- **Operating System**: Ubuntu 20.04 LTS or higher
- **Memory**: 6 GB RAM (minimum)
- **Storage**: 50 GB free HDD space
- **CPU**: 4 vCPU (or dual-core with threads)

---

## 🖥️ Optional: Resize Ubuntu VM Window (VirtualBox)

 Ubuntu in a VirtualBox environment, follow the steps below to install Guest Additions and enable full-screen resizing:

```bash
$ sudo apt update
$ sudo apt install build-essential dkms linux-headers-$(uname -r)
$ cd /media/spatha/VBox_GAs_7.1.8/
$ ./autorun.sh
```
---
### TOOLS INSTALLATION

## ✅ **Yosys Installation**
```bash
$ sudo apt-get update
$ git clone https://github.com/YosysHQ/yosys.git
$ cd yosys
$ sudo apt install make               # If make is not installed
$ sudo apt-get install build-essential clang bison flex \
    libreadline-dev gawk tcl-dev libffi-dev git \
    graphviz xdot pkg-config python3 libboost-system-dev \
    libboost-python-dev libboost-filesystem-dev zlib1g-dev
$ make config-gcc
# Yosys build depends on a Git submodule called abc, which hasn't been initialized yet. You need to run the following command before running make
$ git submodule update --init --recursive
$ make 
$ sudo make install
```
YOSYS.jpeg
![alt text](YOSYS.jpeg)
## ✅ **Iverilog Installation**
```bash
$ sudo apt-get update
$ sudo apt-get install iverilog
```
![alt text](IVERILOG.jpeg)
## ✅ **Gtkwave**
```
$ sudo apt update
$ sudo apt install gtkwave
```

![alt text](GTKWAVE.jpeg)

## ✅ **Ngspice**
After downloading the tarball from https://sourceforge.net/projects/ngspice/files/ to a local directory, unpack it using:
```bash
$ tar -zxvf ngspice-37.tar.gz
$ cd ngspice-37
$ mkdir release
$ cd release
$ ../configure  --with-x --with-readline=yes --disable-debug
$ make
$ sudo make install
```
![alt text](NGSPICE.jpeg)

## ✅ **Magic**
Install the required dependencies:
```bash
$ sudo apt-get install m4
$ sudo apt-get install tcsh
$ sudo apt-get install csh
$ sudo apt-get install libx11-dev
$ sudo apt-get install tcl-dev tk-dev
$ sudo apt-get install libcairo2-dev
$ sudo apt-get install mesa-common-dev libglu1-mesa-dev
$ sudo apt-get install libncurses-dev
```
Clone and build Magic:
```bash
$ git clone https://github.com/RTimothyEdwards/magic
$ cd magic
$ ./configure
$ make
$ sudo make install
```
![alt text](MAGIC.jpeg)

## ✅ **Tool Versions**
```bash
$ git --version
$ docker --version
$ python3 --version
$ make --version
```
![alt text](GIT.jpeg)
