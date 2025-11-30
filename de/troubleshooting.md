---
layout: default
title: Fehlerbehebung
---

<p align="right">
  <a href="../troubleshooting.html">🇫🇷</a> |
  <a href="../en/troubleshooting.html">🇬🇧</a> |
  <strong>🇩🇪</strong> |
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

# Fehlerbehebung

Lösungen für häufige Probleme bei der Installation des AMD NPU-Treibers.

## Fehler "mmap failed: Resource temporarily unavailable"

**Ursache:** Gesperrtes Speicherlimit ist zu niedrig.

**Lösung:**

```bash
sudo sh -c 'echo "* soft memlock unlimited" >> /etc/security/limits.conf'
sudo sh -c 'echo "* hard memlock unlimited" >> /etc/security/limits.conf'
```

Dann neu starten.

## Treiber wird nicht geladen

```bash
# DKMS-Status prüfen
dkms status

# Modul neu laden
sudo modprobe amdxdna

# Fehler prüfen
dmesg | grep -i amdxdna
```

## NPU wird nicht erkannt

1. Prozessor überprüfen:
```bash
cat /proc/cpuinfo | grep "model name" | head -1
```

2. BIOS prüfen — NPU könnte deaktiviert sein

## apt "404 Not Found" Fehler

```bash
sudo rm -rf /var/lib/apt/lists/*
sudo apt update
```

## xrt-smi: command not found

```bash
source /opt/xilinx/xrt/setup.sh
```

---

[← Installation](installation.html) | [Ryzen AI SDK →](sdk.html)
