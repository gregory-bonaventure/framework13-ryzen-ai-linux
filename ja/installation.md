---
layout: default
title: インストール
---

<p align="right">
  <a href="../installation.html">🇫🇷</a> | <a href="../en/installation.html">🇬🇧</a> | <a href="../de/installation.html">🇩🇪</a> | <a href="../es/installation.html">🇪🇸</a> | <a href="../pt/installation.html">🇵🇹</a> | <a href="../it/installation.html">🇮🇹</a> | <a href="../nl/installation.html">🇳🇱</a> | <a href="../pl/installation.html">🇵🇱</a> | <a href="../ru/installation.html">🇷🇺</a> | <a href="../zh/installation.html">🇨🇳</a> | <strong>🇯🇵</strong> | <a href="../ko/installation.html">🇰🇷</a>
</p>

# インストールガイド

## 前提条件

```bash
sudo apt install linux-headers-$(uname -r) build-essential git dkms libcurl4-openssl-dev libtbb-dev pybind11-dev python3-pybind11
```

## ステップ1：リポジトリのクローン

```bash
git clone https://github.com/amd/xdna-driver.git && cd xdna-driver
git submodule update --init --recursive
```

## ステップ2：XRTのコンパイル

```bash
cd xrt/build && ./build.sh -npu -opt
sudo apt reinstall ./Release/xrt_*-amd64-base.deb ./Release/xrt_*-amd64-npu.deb
```

## ステップ3：XDNAドライバのコンパイル

```bash
cd ../../build && ./build.sh -release
sudo apt reinstall ./Release/xrt_plugin.*-x86_64-amdxdna.deb
```

## インストール後の設定

```bash
sudo sh -c 'echo "* soft memlock unlimited" >> /etc/security/limits.conf'
sudo sh -c 'echo "* hard memlock unlimited" >> /etc/security/limits.conf'
echo 'source /opt/xilinx/xrt/setup.sh' >> ~/.bashrc
```

変更を適用するには**再起動**してください。

---

[← ホーム](index.html) | [トラブルシューティング →](troubleshooting.html)
