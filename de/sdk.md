---
layout: default
title: Ryzen AI SDK
---

<p align="right">
  <a href="../sdk.html">🇫🇷</a> |
  <a href="../en/sdk.html">🇬🇧</a> |
  <strong>🇩🇪</strong> |
  <a href="../es/sdk.html">🇪🇸</a> |
  <a href="../pt/sdk.html">🇵🇹</a> |
  <a href="../it/sdk.html">🇮🇹</a> |
  <a href="../nl/sdk.html">🇳🇱</a> |
  <a href="../pl/sdk.html">🇵🇱</a> |
  <a href="../ru/sdk.html">🇷🇺</a> |
  <a href="../zh/sdk.html">🇨🇳</a> |
  <a href="../ja/sdk.html">🇯🇵</a> |
  <a href="../ko/sdk.html">🇰🇷</a>
</p>

# Ryzen AI SDK

Anleitung zur Installation des AMD Ryzen AI SDK und Ausführung von KI-Modellen auf der NPU.

## Voraussetzungen

- ✅ XDNA-Treiber installiert und funktionsfähig
- ✅ `xrt-smi validate` besteht alle Tests
- ✅ Genehmigtes AMD-Konto

## SDK-Zugang erhalten

1. Konto erstellen auf [AMD Ryzen AI Software Early Access Lounge](https://account.amd.com/en/member/ryzenai-sw-ea.html)
2. Auf Genehmigung warten (~2 Werktage)
3. `ryzen_ai-1.6.1.tgz` herunterladen

## Installation

```bash
mkdir ~/ryzen_ai-1.6.1
cd ~/ryzen_ai-1.6.1
tar -xvzf ryzen_ai-1.6.1.tgz
./install_ryzen_ai.sh -a yes -p ~/ryzen-ai-env
source ~/ryzen-ai-env/bin/activate
```

## Überprüfung

```bash
cd ~/ryzen-ai-env/quicktest
python quicktest.py
```

## Verwendung mit ONNX Runtime

```python
import onnxruntime as ort

session = ort.InferenceSession(
    "model.onnx",
    providers=['VitisAIExecutionProvider', 'CPUExecutionProvider']
)

result = session.run(None, {"input": input_data})
```

## Unterstützte Modelltypen

| Typ | Format | Unterstützung |
|-----|--------|---------------|
| CNN | INT8 | ✅ |
| CNN | BF16 | ✅ |
| NLP (BERT) | BF16 | ✅ |
| LLM | - | ✅ |

---

[← Fehlerbehebung](troubleshooting.html) | [Startseite](index.html)
