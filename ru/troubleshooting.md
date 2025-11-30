---
layout: default
title: Устранение неполадок
---

<p align="right">
  <a href="../troubleshooting.html">🇫🇷</a> | <a href="../en/troubleshooting.html">🇬🇧</a> | <a href="../de/troubleshooting.html">🇩🇪</a> | <a href="../es/troubleshooting.html">🇪🇸</a> | <a href="../pt/troubleshooting.html">🇵🇹</a> | <a href="../it/troubleshooting.html">🇮🇹</a> | <a href="../nl/troubleshooting.html">🇳🇱</a> | <a href="../pl/troubleshooting.html">🇵🇱</a> | <strong>🇷🇺</strong> | <a href="../zh/troubleshooting.html">🇨🇳</a> | <a href="../ja/troubleshooting.html">🇯🇵</a> | <a href="../ko/troubleshooting.html">🇰🇷</a>
</p>

# Устранение неполадок

## Ошибка "mmap failed: Resource temporarily unavailable"

```bash
sudo sh -c 'echo "* soft memlock unlimited" >> /etc/security/limits.conf'
sudo sh -c 'echo "* hard memlock unlimited" >> /etc/security/limits.conf'
```

Затем перезагрузите.

## Драйвер не загружается

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

[← Установка](installation.html) | [SDK →](sdk.html)
