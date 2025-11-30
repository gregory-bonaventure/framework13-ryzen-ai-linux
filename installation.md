---
layout: default
title: Installation
---

<p align="right">
  <strong>🇫🇷</strong> |
  <a href="en/installation.html">🇬🇧</a> |
  <a href="de/installation.html">🇩🇪</a> |
  <a href="es/installation.html">🇪🇸</a> |
  <a href="pt/installation.html">🇵🇹</a> |
  <a href="it/installation.html">🇮🇹</a> |
  <a href="nl/installation.html">🇳🇱</a> |
  <a href="pl/installation.html">🇵🇱</a> |
  <a href="ru/installation.html">🇷🇺</a> |
  <a href="zh/installation.html">🇨🇳</a> |
  <a href="ja/installation.html">🇯🇵</a> |
  <a href="ko/installation.html">🇰🇷</a>
</p>

# Guide d'installation

Guide complet pour installer le driver AMD XDNA et faire fonctionner le NPU sur Framework Laptop 13 avec Debian 13.

## Spécifications matérielles

### Processeur AMD Ryzen AI 9 HX 370

| Spécification | Détail |
|---------------|--------|
| Architecture | Zen 5 (4 cœurs) + Zen 5c (8 cœurs) |
| Threads | 24 |
| GPU intégré | Radeon 890M (16 CUs RDNA 3.5) |
| NPU | XDNA 2 (Strix) - 50 TOPS |
| TDP | 28W |

### NPU (Neural Processing Unit)

| Spécification | Détail |
|---------------|--------|
| Architecture | AMD XDNA 2 |
| Nom de code | Strix |
| Performances | 50 TOPS (INT8) |
| PCI ID | c2:00.1 |

## Prérequis

### Vérifier la détection du NPU

```bash
lspci | grep -i "Processing"
```

Sortie attendue :

```
c2:00.1 Signal processing controller: Advanced Micro Devices, Inc. [AMD] Strix/Krackan/Strix Halo Neural Processing Unit (rev 10)
```

### Installer les outils de compilation

```bash
sudo apt update
sudo apt install linux-headers-$(uname -r) build-essential git dkms \
    libcurl4-openssl-dev libtbb-dev pybind11-dev python3-pybind11
```

## Étape 1 : Cloner le dépôt xdna-driver

```bash
cd ~/sources
git clone https://github.com/amd/xdna-driver.git
cd xdna-driver
git submodule update --init --recursive
```

## Étape 2 : Installer les dépendances

```bash
sudo ./tools/amdxdna_deps.sh
```

## Étape 3 : Compiler XRT (Xilinx Runtime)

```bash
cd xrt/build
./build.sh -npu -opt
```

## Étape 4 : Installer les paquets XRT

```bash
sudo apt reinstall ./Release/xrt_*-amd64-base.deb ./Release/xrt_*-amd64-npu.deb
```

## Étape 5 : Compiler le driver XDNA

```bash
cd ~/sources/xdna-driver/build
./build.sh -release
```

## Étape 6 : Installer le plugin XDNA

```bash
sudo apt reinstall ./Release/xrt_plugin.*-x86_64-amdxdna.deb
```

## Configuration post-installation

### Augmenter la limite de mémoire verrouillée

```bash
sudo sh -c 'echo "* soft memlock unlimited" >> /etc/security/limits.conf'
sudo sh -c 'echo "* hard memlock unlimited" >> /etc/security/limits.conf'
```

**Redémarrez** pour appliquer les changements.

### Configurer l'environnement XRT

```bash
echo 'source /opt/xilinx/xrt/setup.sh' >> ~/.bashrc
```

## Vérification

```bash
source /opt/xilinx/xrt/setup.sh
xrt-smi examine
xrt-smi validate
```

---

[← Accueil](index.html) | [Dépannage →](troubleshooting.html)
