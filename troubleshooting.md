---
layout: default
title: Dépannage
---

<p align="right">
  <strong>🇫🇷</strong> |
  <a href="en/troubleshooting.html">🇬🇧</a> |
  <a href="de/troubleshooting.html">🇩🇪</a> |
  <a href="es/troubleshooting.html">🇪🇸</a> |
  <a href="pt/troubleshooting.html">🇵🇹</a> |
  <a href="it/troubleshooting.html">🇮🇹</a> |
  <a href="nl/troubleshooting.html">🇳🇱</a> |
  <a href="pl/troubleshooting.html">🇵🇱</a> |
  <a href="ru/troubleshooting.html">🇷🇺</a> |
  <a href="zh/troubleshooting.html">🇨🇳</a> |
  <a href="ja/troubleshooting.html">🇯🇵</a> |
  <a href="ko/troubleshooting.html">🇰🇷</a>
</p>

# Dépannage

Solutions aux problèmes courants lors de l'installation du driver AMD NPU.

## Erreur "mmap failed: Resource temporarily unavailable"

**Cause :** La limite de mémoire verrouillée est trop basse.

**Solution :**

```bash
sudo sh -c 'echo "* soft memlock unlimited" >> /etc/security/limits.conf'
sudo sh -c 'echo "* hard memlock unlimited" >> /etc/security/limits.conf'
```

Puis redémarrez.

## Le driver ne se charge pas

```bash
# Vérifier le statut DKMS
dkms status

# Recharger le module
sudo modprobe amdxdna

# Vérifier les erreurs
dmesg | grep -i amdxdna
```

## Le NPU n'est pas détecté

1. Vérifiez votre processeur :
```bash
cat /proc/cpuinfo | grep "model name" | head -1
```

2. Vérifiez le BIOS — le NPU pourrait être désactivé

## Erreurs apt "404 Not Found"

```bash
sudo rm -rf /var/lib/apt/lists/*
sudo apt update
```

## Erreur pip "externally-managed-environment"

Ignorez cette erreur. Installez via apt :

```bash
sudo apt install pybind11-dev python3-pybind11
```

## xrt-smi : command not found

```bash
source /opt/xilinx/xrt/setup.sh
```

---

[← Installation](installation.html) | [SDK Ryzen AI →](sdk.html)
