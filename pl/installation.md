---
layout: default
title: Instalacja
---

<p align="right">
  <a href="../installation.html">🇫🇷</a> | <a href="../en/installation.html">🇬🇧</a> | <a href="../de/installation.html">🇩🇪</a> | <a href="../es/installation.html">🇪🇸</a> | <a href="../pt/installation.html">🇵🇹</a> | <a href="../it/installation.html">🇮🇹</a> | <a href="../nl/installation.html">🇳🇱</a> | <strong>🇵🇱</strong> | <a href="../ru/installation.html">🇷🇺</a> | <a href="../zh/installation.html">🇨🇳</a> | <a href="../ja/installation.html">🇯🇵</a> | <a href="../ko/installation.html">🇰🇷</a>
</p>

# Przewodnik instalacji

## Wymagania wstępne

```bash
sudo apt install linux-headers-$(uname -r) build-essential git dkms libcurl4-openssl-dev libtbb-dev pybind11-dev python3-pybind11
```

## Krok 1: Klonowanie repozytorium

```bash
git clone https://github.com/amd/xdna-driver.git && cd xdna-driver
git submodule update --init --recursive
```

## Krok 2: Kompilacja XRT

```bash
cd xrt/build && ./build.sh -npu -opt
sudo apt reinstall ./Release/xrt_*-amd64-base.deb ./Release/xrt_*-amd64-npu.deb
```

## Krok 3: Kompilacja sterownika XDNA

```bash
cd ../../build && ./build.sh -release
sudo apt reinstall ./Release/xrt_plugin.*-x86_64-amdxdna.deb
```

## Konfiguracja po instalacji

```bash
sudo sh -c 'echo "* soft memlock unlimited" >> /etc/security/limits.conf'
sudo sh -c 'echo "* hard memlock unlimited" >> /etc/security/limits.conf'
echo 'source /opt/xilinx/xrt/setup.sh' >> ~/.bashrc
```

**Uruchom ponownie** aby zastosować zmiany.

---

[← Strona główna](index.html) | [Rozwiązywanie problemów →](troubleshooting.html)
