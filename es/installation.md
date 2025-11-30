---
layout: default
title: Instalación
---

<p align="right">
  <a href="../installation.html">🇫🇷</a> |
  <a href="../en/installation.html">🇬🇧</a> |
  <a href="../de/installation.html">🇩🇪</a> |
  <strong>🇪🇸</strong> |
  <a href="../pt/installation.html">🇵🇹</a> |
  <a href="../it/installation.html">🇮🇹</a> |
  <a href="../nl/installation.html">🇳🇱</a> |
  <a href="../pl/installation.html">🇵🇱</a> |
  <a href="../ru/installation.html">🇷🇺</a> |
  <a href="../zh/installation.html">🇨🇳</a> |
  <a href="../ja/installation.html">🇯🇵</a> |
  <a href="../ko/installation.html">🇰🇷</a>
</p>

# Guía de instalación

## Requisitos previos

```bash
sudo apt update
sudo apt install linux-headers-$(uname -r) build-essential git dkms \
    libcurl4-openssl-dev libtbb-dev pybind11-dev python3-pybind11
```

## Paso 1: Clonar repositorio

```bash
git clone https://github.com/amd/xdna-driver.git
cd xdna-driver
git submodule update --init --recursive
```

## Paso 2: Compilar XRT

```bash
cd xrt/build
./build.sh -npu -opt
sudo apt reinstall ./Release/xrt_*-amd64-base.deb ./Release/xrt_*-amd64-npu.deb
```

## Paso 3: Compilar driver XDNA

```bash
cd ~/sources/xdna-driver/build
./build.sh -release
sudo apt reinstall ./Release/xrt_plugin.*-x86_64-amdxdna.deb
```

## Configuración post-instalación

```bash
sudo sh -c 'echo "* soft memlock unlimited" >> /etc/security/limits.conf'
sudo sh -c 'echo "* hard memlock unlimited" >> /etc/security/limits.conf'
echo 'source /opt/xilinx/xrt/setup.sh' >> ~/.bashrc
```

**Reiniciar** para aplicar cambios.

---

[← Inicio](index.html) | [Solución de problemas →](troubleshooting.html)
