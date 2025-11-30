---
layout: default
title: Ryzen AI SDK
---

<p align="right">
  <a href="../sdk.html">🇫🇷</a> | <a href="../en/sdk.html">🇬🇧</a> | <a href="../de/sdk.html">🇩🇪</a> | <a href="../es/sdk.html">🇪🇸</a> | <a href="../pt/sdk.html">🇵🇹</a> | <a href="../it/sdk.html">🇮🇹</a> | <strong>🇳🇱</strong> | <a href="../pl/sdk.html">🇵🇱</a> | <a href="../ru/sdk.html">🇷🇺</a> | <a href="../zh/sdk.html">🇨🇳</a> | <a href="../ja/sdk.html">🇯🇵</a> | <a href="../ko/sdk.html">🇰🇷</a>
</p>

# Ryzen AI SDK

## Toegang verkrijgen

1. Account aanmaken op [AMD Ryzen AI Early Access](https://account.amd.com/en/member/ryzenai-sw-ea.html)
2. Wachten op goedkeuring (~2 werkdagen)
3. `ryzen_ai-1.6.1.tgz` downloaden

## Installatie

```bash
mkdir ~/ryzen_ai-1.6.1 && cd ~/ryzen_ai-1.6.1
tar -xvzf ryzen_ai-1.6.1.tgz
./install_ryzen_ai.sh -a yes -p ~/ryzen-ai-env
source ~/ryzen-ai-env/bin/activate
```

## Gebruik met ONNX Runtime

```python
import onnxruntime as ort

session = ort.InferenceSession(
    "model.onnx",
    providers=['VitisAIExecutionProvider', 'CPUExecutionProvider']
)
result = session.run(None, {"input": input_data})
```

---

[← Probleemoplossing](troubleshooting.html) | [Home](index.html)
