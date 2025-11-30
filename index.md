---
layout: default
title: Accueil
---

<p align="right">
  <strong>🇫🇷</strong> |
  <a href="en/">🇬🇧</a> |
  <a href="de/">🇩🇪</a> |
  <a href="es/">🇪🇸</a> |
  <a href="pt/">🇵🇹</a> |
  <a href="it/">🇮🇹</a> |
  <a href="nl/">🇳🇱</a> |
  <a href="pl/">🇵🇱</a> |
  <a href="ru/">🇷🇺</a> |
  <a href="zh/">🇨🇳</a> |
  <a href="ja/">🇯🇵</a> |
  <a href="ko/">🇰🇷</a>
</p>

# Framework Laptop 13 - AMD Ryzen AI NPU sur Linux

Guide complet pour faire fonctionner le **NPU AMD XDNA 2** sur un **Framework Laptop 13** équipé d'un processeur **AMD Ryzen AI 9 HX 370** sous **Debian 13 (Trixie)**.

## 🚀 Résultats obtenus

| Test | Résultat |
|------|----------|
| **Performances** | 51 TOPS |
| **Latence** | 56 µs |
| **Débit** | 81 442 ops/s |
| **Status** | ✅ Fonctionnel |

## 📋 Configuration testée

| Composant | Détail |
|-----------|--------|
| Laptop | Framework Laptop 13 (AMD Ryzen AI 300) |
| Processeur | AMD Ryzen AI 9 HX 370 |
| NPU | XDNA 2 (Strix) - 50 TOPS |
| RAM | 96 Go DDR5 |
| OS | Debian 13 (Trixie) |
| Kernel | 6.12.48 |

## 📚 Documentation

- [**Installation complète**](installation.html) — Guide pas à pas pour compiler et installer le driver
- [**Dépannage**](troubleshooting.html) — Solutions aux problèmes courants
- [**SDK Ryzen AI**](sdk.html) — Exécuter des modèles IA sur le NPU

## ⚡ Démarrage rapide

```bash
# Cloner le driver
git clone https://github.com/amd/xdna-driver.git
cd xdna-driver
git submodule update --init --recursive

# Compiler XRT
cd xrt/build
./build.sh -npu -opt
sudo apt reinstall ./Release/xrt_*-amd64-base.deb ./Release/xrt_*-amd64-npu.deb

# Compiler et installer le driver XDNA
cd ../../build
./build.sh -release
sudo apt reinstall ./Release/xrt_plugin.*-x86_64-amdxdna.deb

# Configurer l'environnement
source /opt/xilinx/xrt/setup.sh
xrt-smi validate
```

## 🔗 Liens utiles

- [AMD XDNA Driver (GitHub)](https://github.com/amd/xdna-driver)
- [Ryzen AI Documentation](https://ryzenai.docs.amd.com/en/latest/linux.html)
- [Framework Laptop 13](https://frame.work/fr/fr/laptop13)

## 📄 Licence

Ce guide est fourni "tel quel" sans garantie. Libre de distribution et modification.

---

*Guide créé le 30 novembre 2025 par Gregory Bonaventure*
