---
layout: default
title: Inicio
---

<p align="right">
  <a href="../">🇫🇷</a> |
  <a href="../en/">🇬🇧</a> |
  <a href="../de/">🇩🇪</a> |
  <strong>🇪🇸</strong> |
  <a href="../pt/">🇵🇹</a> |
  <a href="../it/">🇮🇹</a> |
  <a href="../nl/">🇳🇱</a> |
  <a href="../pl/">🇵🇱</a> |
  <a href="../ru/">🇷🇺</a> |
  <a href="../zh/">🇨🇳</a> |
  <a href="../ja/">🇯🇵</a> |
  <a href="../ko/">🇰🇷</a>
</p>

# Framework Laptop 13 - AMD Ryzen AI NPU en Linux

Guía completa para hacer funcionar la **NPU AMD XDNA 2** en un **Framework Laptop 13** con procesador **AMD Ryzen AI 9 HX 370** en **Debian 13 (Trixie)**.

## 🚀 Resultados

| Prueba | Resultado |
|--------|-----------|
| **Rendimiento** | 51 TOPS |
| **Latencia** | 56 µs |
| **Throughput** | 81.442 ops/s |
| **Estado** | ✅ Funcional |

## 📋 Configuración probada

| Componente | Detalles |
|------------|----------|
| Laptop | Framework Laptop 13 (AMD Ryzen AI 300) |
| Procesador | AMD Ryzen AI 9 HX 370 |
| NPU | XDNA 2 (Strix) - 50 TOPS |
| RAM | 96 GB DDR5 |
| SO | Debian 13 (Trixie) |
| Kernel | 6.12.48 |

## 📚 Documentación

- [**Instalación completa**](installation.html) — Guía paso a paso
- [**Solución de problemas**](troubleshooting.html) — Soluciones a problemas comunes
- [**SDK Ryzen AI**](sdk.html) — Ejecutar modelos IA en la NPU

## ⚡ Inicio rápido

```bash
# Clonar el driver
git clone https://github.com/amd/xdna-driver.git
cd xdna-driver
git submodule update --init --recursive

# Compilar XRT
cd xrt/build
./build.sh -npu -opt
sudo apt reinstall ./Release/xrt_*-amd64-base.deb ./Release/xrt_*-amd64-npu.deb

# Compilar e instalar driver XDNA
cd ../../build
./build.sh -release
sudo apt reinstall ./Release/xrt_plugin.*-x86_64-amdxdna.deb

# Configurar entorno
source /opt/xilinx/xrt/setup.sh
xrt-smi validate
```

## 🔗 Enlaces útiles

- [AMD XDNA Driver (GitHub)](https://github.com/amd/xdna-driver)
- [Documentación Ryzen AI](https://ryzenai.docs.amd.com/en/latest/linux.html)
- [Framework Laptop 13](https://frame.work/laptop13)

---

*Guía creada el 30 de noviembre de 2025 por Gregory Bonaventure*
