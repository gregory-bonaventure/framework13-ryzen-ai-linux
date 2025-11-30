---
layout: default
title: Home
---

<p align="right">
  <a href="../">🇫🇷</a> |
  <strong>🇬🇧</strong> |
  <a href="../de/">🇩🇪</a> |
  <a href="../es/">🇪🇸</a> |
  <a href="../pt/">🇵🇹</a> |
  <a href="../it/">🇮🇹</a> |
  <a href="../nl/">🇳🇱</a> |
  <a href="../pl/">🇵🇱</a> |
  <a href="../ru/">🇷🇺</a> |
  <a href="../zh/">🇨🇳</a> |
  <a href="../ja/">🇯🇵</a> |
  <a href="../ko/">🇰🇷</a>
</p>

# Framework Laptop 13 - AMD Ryzen AI NPU on Linux

Complete guide to get the **AMD XDNA 2 NPU** working on a **Framework Laptop 13** with an **AMD Ryzen AI 9 HX 370** processor running **Debian 13 (Trixie)**.

## 🚀 Results

| Test | Result |
|------|--------|
| **Performance** | 51 TOPS |
| **Latency** | 56 µs |
| **Throughput** | 81,442 ops/s |
| **Status** | ✅ Working |

## 📋 Tested Configuration

| Component | Details |
|-----------|---------|
| Laptop | Framework Laptop 13 (AMD Ryzen AI 300) |
| Processor | AMD Ryzen AI 9 HX 370 |
| NPU | XDNA 2 (Strix) - 50 TOPS |
| RAM | 96 GB DDR5 |
| OS | Debian 13 (Trixie) |
| Kernel | 6.12.48 |

## 📚 Documentation

- [**Full Installation**](installation.html) — Step-by-step guide to compile and install the driver
- [**Troubleshooting**](troubleshooting.html) — Solutions to common issues
- [**Ryzen AI SDK**](sdk.html) — Run AI models on the NPU

## ⚡ Quick Start

```bash
# Clone the driver
git clone https://github.com/amd/xdna-driver.git
cd xdna-driver
git submodule update --init --recursive

# Build XRT
cd xrt/build
./build.sh -npu -opt
sudo apt reinstall ./Release/xrt_*-amd64-base.deb ./Release/xrt_*-amd64-npu.deb

# Build and install XDNA driver
cd ../../build
./build.sh -release
sudo apt reinstall ./Release/xrt_plugin.*-x86_64-amdxdna.deb

# Configure environment
source /opt/xilinx/xrt/setup.sh
xrt-smi validate
```

## 🔗 Useful Links

- [AMD XDNA Driver (GitHub)](https://github.com/amd/xdna-driver)
- [Ryzen AI Documentation](https://ryzenai.docs.amd.com/en/latest/linux.html)
- [Framework Laptop 13](https://frame.work/laptop13)

## 📄 License

This guide is provided "as is" without warranty. Free to distribute and modify.

---

*Guide created on November 30, 2025 by Gregory Bonaventure*
