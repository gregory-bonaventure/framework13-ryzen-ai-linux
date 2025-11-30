---
layout: default
title: Solución de problemas
---

<p align="right">
  <a href="../troubleshooting.html">🇫🇷</a> |
  <a href="../en/troubleshooting.html">🇬🇧</a> |
  <a href="../de/troubleshooting.html">🇩🇪</a> |
  <strong>🇪🇸</strong> |
  <a href="../pt/troubleshooting.html">🇵🇹</a> |
  <a href="../it/troubleshooting.html">🇮🇹</a> |
  <a href="../nl/troubleshooting.html">🇳🇱</a> |
  <a href="../pl/troubleshooting.html">🇵🇱</a> |
  <a href="../ru/troubleshooting.html">🇷🇺</a> |
  <a href="../zh/troubleshooting.html">🇨🇳</a> |
  <a href="../ja/troubleshooting.html">🇯🇵</a> |
  <a href="../ko/troubleshooting.html">🇰🇷</a>
</p>

# Solución de problemas

## Error "mmap failed: Resource temporarily unavailable"

```bash
sudo sh -c 'echo "* soft memlock unlimited" >> /etc/security/limits.conf'
sudo sh -c 'echo "* hard memlock unlimited" >> /etc/security/limits.conf'
```

Luego reiniciar.

## El driver no carga

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

[← Instalación](installation.html) | [SDK Ryzen AI →](sdk.html)
