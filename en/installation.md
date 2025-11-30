---
layout: default
title: Installation
---

<p align="right">
  <a href="../installation.html">🇫🇷</a> |
  <strong>🇬🇧</strong> |
  <a href="../de/installation.html">🇩🇪</a> |
  <a href="../es/installation.html">🇪🇸</a> |
  <a href="../pt/installation.html">🇵🇹</a> |
  <a href="../it/installation.html">🇮🇹</a> |
  <a href="../nl/installation.html">🇳🇱</a> |
  <a href="../pl/installation.html">🇵🇱</a> |
  <a href="../ru/installation.html">🇷🇺</a> |
  <a href="../zh/installation.html">🇨🇳</a> |
  <a href="../ja/installation.html">🇯🇵</a> |
  <a href="../ko/installation.html">🇰🇷</a>
</p>

# Installation Guide

Complete guide to install the AMD XDNA driver and get the NPU working on Framework Laptop 13 with Debian 13.

## Hardware Specifications

### AMD Ryzen AI 9 HX 370 Processor

| Specification | Details |
|---------------|---------|
| Architecture | Zen 5 (4 cores) + Zen 5c (8 cores) |
| Threads | 24 |
| Integrated GPU | Radeon 890M (16 CUs RDNA 3.5) |
| NPU | XDNA 2 (Strix) - 50 TOPS |
| TDP | 28W |

### NPU (Neural Processing Unit)

| Specification | Details |
|---------------|---------|
| Architecture | AMD XDNA 2 |
| Code name | Strix |
| Performance | 50 TOPS (INT8) |
| PCI ID | c2:00.1 |

## Prerequisites

### Verify NPU Detection

```bash
lspci | grep -i "Processing"
```

Expected output:

```
c2:00.1 Signal processing controller: Advanced Micro Devices, Inc. [AMD] Strix/Krackan/Strix Halo Neural Processing Unit (rev 10)
```

### Install Build Tools

```bash
sudo apt update
sudo apt install linux-headers-$(uname -r) build-essential git dkms \
    libcurl4-openssl-dev libtbb-dev pybind11-dev python3-pybind11
```

## Step 1: Clone xdna-driver Repository

```bash
cd ~/sources
git clone https://github.com/amd/xdna-driver.git
cd xdna-driver
git submodule update --init --recursive
```

## Step 2: Install Dependencies

```bash
sudo ./tools/amdxdna_deps.sh
```

## Step 3: Build XRT (Xilinx Runtime)

```bash
cd xrt/build
./build.sh -npu -opt
```

## Step 4: Install XRT Packages

```bash
sudo apt reinstall ./Release/xrt_*-amd64-base.deb ./Release/xrt_*-amd64-npu.deb
```

## Step 5: Build XDNA Driver

```bash
cd ~/sources/xdna-driver/build
./build.sh -release
```

## Step 6: Install XDNA Plugin

```bash
sudo apt reinstall ./Release/xrt_plugin.*-x86_64-amdxdna.deb
```

## Post-Installation Configuration

### Increase Locked Memory Limit

```bash
sudo sh -c 'echo "* soft memlock unlimited" >> /etc/security/limits.conf'
sudo sh -c 'echo "* hard memlock unlimited" >> /etc/security/limits.conf'
```

**Reboot** to apply changes.

### Configure XRT Environment

```bash
echo 'source /opt/xilinx/xrt/setup.sh' >> ~/.bashrc
```

## Verification

```bash
source /opt/xilinx/xrt/setup.sh
xrt-smi examine
xrt-smi validate
```

---

[← Home](index.html) | [Troubleshooting →](troubleshooting.html)
