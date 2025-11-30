---
layout: default
title: 故障排除
---

<p align="right">
  <a href="../troubleshooting.html">🇫🇷</a> | <a href="../en/troubleshooting.html">🇬🇧</a> | <a href="../de/troubleshooting.html">🇩🇪</a> | <a href="../es/troubleshooting.html">🇪🇸</a> | <a href="../pt/troubleshooting.html">🇵🇹</a> | <a href="../it/troubleshooting.html">🇮🇹</a> | <a href="../nl/troubleshooting.html">🇳🇱</a> | <a href="../pl/troubleshooting.html">🇵🇱</a> | <a href="../ru/troubleshooting.html">🇷🇺</a> | <strong>🇨🇳</strong> | <a href="../ja/troubleshooting.html">🇯🇵</a> | <a href="../ko/troubleshooting.html">🇰🇷</a>
</p>

# 故障排除

## 错误 "mmap failed: Resource temporarily unavailable"

```bash
sudo sh -c 'echo "* soft memlock unlimited" >> /etc/security/limits.conf'
sudo sh -c 'echo "* hard memlock unlimited" >> /etc/security/limits.conf'
```

然后重启。

## 驱动无法加载

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

[← 安装指南](installation.html) | [SDK →](sdk.html)
