---
layout: default
title: Troubleshooting
---

<p align="right">
  <a href="../troubleshooting.html">🇫🇷</a> |
  <strong>🇬🇧</strong> |
  <a href="../de/troubleshooting.html">🇩🇪</a> |
  <a href="../es/troubleshooting.html">🇪🇸</a> |
  <a href="../pt/troubleshooting.html">🇵🇹</a> |
  <a href="../it/troubleshooting.html">🇮🇹</a> |
  <a href="../nl/troubleshooting.html">🇳🇱</a> |
  <a href="../pl/troubleshooting.html">🇵🇱</a> |
  <a href="../ru/troubleshooting.html">🇷🇺</a> |
  <a href="../zh/troubleshooting.html">🇨🇳</a> |
  <a href="../ja/troubleshooting.html">🇯🇵</a> |
  <a href="../ko/troubleshooting.html">🇰🇷</a>
</p>

# Troubleshooting

Solutions to common issues when installing the AMD NPU driver.

## Error "mmap failed: Resource temporarily unavailable"

**Cause:** Locked memory limit is too low.

**Solution:**

```bash
sudo sh -c 'echo "* soft memlock unlimited" >> /etc/security/limits.conf'
sudo sh -c 'echo "* hard memlock unlimited" >> /etc/security/limits.conf'
```

Then reboot.

## Driver Not Loading

```bash
# Check DKMS status
dkms status

# Reload module
sudo modprobe amdxdna

# Check errors
dmesg | grep -i amdxdna
```

## NPU Not Detected

1. Check your processor:
```bash
cat /proc/cpuinfo | grep "model name" | head -1
```

2. Check BIOS — NPU might be disabled

## apt "404 Not Found" Errors

```bash
sudo rm -rf /var/lib/apt/lists/*
sudo apt update
```

## pip "externally-managed-environment" Error

Ignore this error. Install via apt:

```bash
sudo apt install pybind11-dev python3-pybind11
```

## xrt-smi: command not found

```bash
source /opt/xilinx/xrt/setup.sh
```

---

[← Installation](installation.html) | [Ryzen AI SDK →](sdk.html)
