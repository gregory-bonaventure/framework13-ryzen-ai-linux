---
layout: default
title: Ryzen AI SDK
---

<p align="right">
  <a href="../sdk.html">🇫🇷</a> |
  <strong>🇬🇧</strong> |
  <a href="../de/sdk.html">🇩🇪</a> |
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

Guide to install the AMD Ryzen AI SDK and run AI models on the NPU.

## Prerequisites

- ✅ XDNA driver installed and working
- ✅ `xrt-smi validate` passes all tests
- ✅ Approved AMD account

## Get SDK Access

1. Create an account on [AMD Ryzen AI Software Early Access Lounge](https://account.amd.com/en/member/ryzenai-sw-ea.html)
2. Wait for approval (~2 business days)
3. Download `ryzen_ai-1.6.1.tgz`

## Installation

```bash
mkdir ~/ryzen_ai-1.6.1
cd ~/ryzen_ai-1.6.1
tar -xvzf ryzen_ai-1.6.1.tgz
./install_ryzen_ai.sh -a yes -p ~/ryzen-ai-env
source ~/ryzen-ai-env/bin/activate
```

## Verification

```bash
cd ~/ryzen-ai-env/quicktest
python quicktest.py
```

## Using with ONNX Runtime

```python
import onnxruntime as ort

session = ort.InferenceSession(
    "model.onnx",
    providers=['VitisAIExecutionProvider', 'CPUExecutionProvider']
)

result = session.run(None, {"input": input_data})
```

## Supported Model Types

| Type | Format | Support |
|------|--------|---------|
| CNN | INT8 | ✅ |
| CNN | BF16 | ✅ |
| NLP (BERT) | BF16 | ✅ |
| LLM | - | ✅ |

## Resources

- [Ryzen AI Documentation](https://ryzenai.docs.amd.com/en/latest/)
- [RyzenAI-SW GitHub](https://github.com/amd/RyzenAI-SW)

---

[← Troubleshooting](troubleshooting.html) | [Home](index.html)
