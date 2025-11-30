---
layout: default
title: 문제 해결
---

<p align="right">
  <a href="../troubleshooting.html">🇫🇷</a> | <a href="../en/troubleshooting.html">🇬🇧</a> | <a href="../de/troubleshooting.html">🇩🇪</a> | <a href="../es/troubleshooting.html">🇪🇸</a> | <a href="../pt/troubleshooting.html">🇵🇹</a> | <a href="../it/troubleshooting.html">🇮🇹</a> | <a href="../nl/troubleshooting.html">🇳🇱</a> | <a href="../pl/troubleshooting.html">🇵🇱</a> | <a href="../ru/troubleshooting.html">🇷🇺</a> | <a href="../zh/troubleshooting.html">🇨🇳</a> | <a href="../ja/troubleshooting.html">🇯🇵</a> | <strong>🇰🇷</strong>
</p>

# 문제 해결

## 오류 "mmap failed: Resource temporarily unavailable"

```bash
sudo sh -c 'echo "* soft memlock unlimited" >> /etc/security/limits.conf'
sudo sh -c 'echo "* hard memlock unlimited" >> /etc/security/limits.conf'
```

그 다음 재부팅하세요.

## 드라이버가 로드되지 않음

```bash
dkms status
sudo modprobe amdxdna
dmesg | grep -i amdxdna
```

## xrt-smi: command not found

```bash
source /opt/xilinx/xrt/setup.sh
```

---

[← 설치](installation.html) | [SDK →](sdk.html)
