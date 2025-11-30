---
layout: default
title: Startseite
---

<p align="right">
  <a href="../">🇫🇷</a> |
  <a href="../en/">🇬🇧</a> |
  <strong>🇩🇪</strong> |
  <a href="../es/">🇪🇸</a> |
  <a href="../pt/">🇵🇹</a> |
  <a href="../it/">🇮🇹</a> |
  <a href="../nl/">🇳🇱</a> |
  <a href="../pl/">🇵🇱</a> |
  <a href="../ru/">🇷🇺</a> |
  <a href="../zh/">🇨🇳</a> |
  <a href="../ja/">🇯🇵</a> |
  <a href="../ko/">🇰🇷</a>
</p>

# Framework Laptop 13 - AMD Ryzen AI NPU unter Linux

Vollständige Anleitung zur Inbetriebnahme der **AMD XDNA 2 NPU** auf einem **Framework Laptop 13** mit **AMD Ryzen AI 9 HX 370** Prozessor unter **Debian 13 (Trixie)**.

## 🚀 Ergebnisse

| Test | Ergebnis |
|------|----------|
| **Leistung** | 51 TOPS |
| **Latenz** | 56 µs |
| **Durchsatz** | 81.442 ops/s |
| **Status** | ✅ Funktioniert |

## 📋 Getestete Konfiguration

| Komponente | Details |
|------------|---------|
| Laptop | Framework Laptop 13 (AMD Ryzen AI 300) |
| Prozessor | AMD Ryzen AI 9 HX 370 |
| NPU | XDNA 2 (Strix) - 50 TOPS |
| RAM | 96 GB DDR5 |
| OS | Debian 13 (Trixie) |
| Kernel | 6.12.48 |

## 📚 Dokumentation

- [**Vollständige Installation**](installation.html) — Schritt-für-Schritt-Anleitung
- [**Fehlerbehebung**](troubleshooting.html) — Lösungen für häufige Probleme
- [**Ryzen AI SDK**](sdk.html) — KI-Modelle auf der NPU ausführen

## ⚡ Schnellstart

```bash
# Treiber klonen
git clone https://github.com/amd/xdna-driver.git
cd xdna-driver
git submodule update --init --recursive

# XRT kompilieren
cd xrt/build
./build.sh -npu -opt
sudo apt reinstall ./Release/xrt_*-amd64-base.deb ./Release/xrt_*-amd64-npu.deb

# XDNA-Treiber kompilieren und installieren
cd ../../build
./build.sh -release
sudo apt reinstall ./Release/xrt_plugin.*-x86_64-amdxdna.deb

# Umgebung konfigurieren
source /opt/xilinx/xrt/setup.sh
xrt-smi validate
```

## 🔗 Nützliche Links

- [AMD XDNA Driver (GitHub)](https://github.com/amd/xdna-driver)
- [Ryzen AI Dokumentation](https://ryzenai.docs.amd.com/en/latest/linux.html)
- [Framework Laptop 13](https://frame.work/de/de/laptop13)

## 📄 Lizenz

Diese Anleitung wird "wie besehen" ohne Gewährleistung bereitgestellt.

---

*Anleitung erstellt am 30. November 2025 von Gregory Bonaventure*
