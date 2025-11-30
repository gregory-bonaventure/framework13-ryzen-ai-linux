---
layout: default
title: Installation
---

<p align="right">
  <a href="../installation.html">🇫🇷</a> |
  <a href="../en/installation.html">🇬🇧</a> |
  <strong>🇩🇪</strong> |
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

# Installationsanleitung

Vollständige Anleitung zur Installation des AMD XDNA-Treibers auf Framework Laptop 13 mit Debian 13.

## Hardware-Spezifikationen

### AMD Ryzen AI 9 HX 370 Prozessor

| Spezifikation | Details |
|---------------|---------|
| Architektur | Zen 5 (4 Kerne) + Zen 5c (8 Kerne) |
| Threads | 24 |
| Integrierte GPU | Radeon 890M (16 CUs RDNA 3.5) |
| NPU | XDNA 2 (Strix) - 50 TOPS |
| TDP | 28W |

## Voraussetzungen

### NPU-Erkennung überprüfen

```bash
lspci | grep -i "Processing"
```

### Build-Tools installieren

```bash
sudo apt update
sudo apt install linux-headers-$(uname -r) build-essential git dkms \
    libcurl4-openssl-dev libtbb-dev pybind11-dev python3-pybind11
```

## Schritt 1: xdna-driver Repository klonen

```bash
cd ~/sources
git clone https://github.com/amd/xdna-driver.git
cd xdna-driver
git submodule update --init --recursive
```

## Schritt 2: Abhängigkeiten installieren

```bash
sudo ./tools/amdxdna_deps.sh
```

## Schritt 3: XRT kompilieren

```bash
cd xrt/build
./build.sh -npu -opt
```

## Schritt 4: XRT-Pakete installieren

```bash
sudo apt reinstall ./Release/xrt_*-amd64-base.deb ./Release/xrt_*-amd64-npu.deb
```

## Schritt 5: XDNA-Treiber kompilieren

```bash
cd ~/sources/xdna-driver/build
./build.sh -release
```

## Schritt 6: XDNA-Plugin installieren

```bash
sudo apt reinstall ./Release/xrt_plugin.*-x86_64-amdxdna.deb
```

## Nach der Installation

### Speicherlimit erhöhen

```bash
sudo sh -c 'echo "* soft memlock unlimited" >> /etc/security/limits.conf'
sudo sh -c 'echo "* hard memlock unlimited" >> /etc/security/limits.conf'
```

**Neustart** erforderlich.

### XRT-Umgebung konfigurieren

```bash
echo 'source /opt/xilinx/xrt/setup.sh' >> ~/.bashrc
```

## Überprüfung

```bash
source /opt/xilinx/xrt/setup.sh
xrt-smi examine
xrt-smi validate
```

---

[← Startseite](index.html) | [Fehlerbehebung →](troubleshooting.html)
