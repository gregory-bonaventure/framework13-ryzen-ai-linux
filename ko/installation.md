---
layout: default
title: 설치
---

<p align="right">
  <a href="../installation.html">🇫🇷</a> | <a href="../en/installation.html">🇬🇧</a> | <a href="../de/installation.html">🇩🇪</a> | <a href="../es/installation.html">🇪🇸</a> | <a href="../pt/installation.html">🇵🇹</a> | <a href="../it/installation.html">🇮🇹</a> | <a href="../nl/installation.html">🇳🇱</a> | <a href="../pl/installation.html">🇵🇱</a> | <a href="../ru/installation.html">🇷🇺</a> | <a href="../zh/installation.html">🇨🇳</a> | <a href="../ja/installation.html">🇯🇵</a> | <strong>🇰🇷</strong>
</p>

# 설치 가이드

## 필수 조건

```bash
sudo apt install linux-headers-$(uname -r) build-essential git dkms libcurl4-openssl-dev libtbb-dev pybind11-dev python3-pybind11
```

## 1단계: 저장소 복제

```bash
git clone https://github.com/amd/xdna-driver.git && cd xdna-driver
git submodule update --init --recursive
```

## 2단계: XRT 컴파일

```bash
cd xrt/build && ./build.sh -npu -opt
sudo apt reinstall ./Release/xrt_*-amd64-base.deb ./Release/xrt_*-amd64-npu.deb
```

## 3단계: XDNA 드라이버 컴파일

```bash
cd ../../build && ./build.sh -release
sudo apt reinstall ./Release/xrt_plugin.*-x86_64-amdxdna.deb
```

## 설치 후 구성

```bash
sudo sh -c 'echo "* soft memlock unlimited" >> /etc/security/limits.conf'
sudo sh -c 'echo "* hard memlock unlimited" >> /etc/security/limits.conf'
echo 'source /opt/xilinx/xrt/setup.sh' >> ~/.bashrc
```

변경 사항을 적용하려면 **재부팅**하세요.

---

[← 홈](index.html) | [문제 해결 →](troubleshooting.html)
