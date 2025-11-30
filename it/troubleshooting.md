---
layout: default
title: Risoluzione problemi
---

<p align="right">
  <a href="../troubleshooting.html">🇫🇷</a> | <a href="../en/troubleshooting.html">🇬🇧</a> | <a href="../de/troubleshooting.html">🇩🇪</a> | <a href="../es/troubleshooting.html">🇪🇸</a> | <a href="../pt/troubleshooting.html">🇵🇹</a> | <strong>🇮🇹</strong> | <a href="../nl/troubleshooting.html">🇳🇱</a> | <a href="../pl/troubleshooting.html">🇵🇱</a> | <a href="../ru/troubleshooting.html">🇷🇺</a> | <a href="../zh/troubleshooting.html">🇨🇳</a> | <a href="../ja/troubleshooting.html">🇯🇵</a> | <a href="../ko/troubleshooting.html">🇰🇷</a>
</p>

# Risoluzione problemi

## Errore "mmap failed: Resource temporarily unavailable"

```bash
sudo sh -c 'echo "* soft memlock unlimited" >> /etc/security/limits.conf'
sudo sh -c 'echo "* hard memlock unlimited" >> /etc/security/limits.conf'
```

Poi riavviare.

## Il driver non si carica

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

[← Installazione](installation.html) | [SDK →](sdk.html)
