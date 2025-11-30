---
layout: default
title: SDK Ryzen AI
---

<p align="right">
  <a href="../sdk.html">🇫🇷</a> | <a href="../en/sdk.html">🇬🇧</a> | <a href="../de/sdk.html">🇩🇪</a> | <a href="../es/sdk.html">🇪🇸</a> | <a href="../pt/sdk.html">🇵🇹</a> | <strong>🇮🇹</strong> | <a href="../nl/sdk.html">🇳🇱</a> | <a href="../pl/sdk.html">🇵🇱</a> | <a href="../ru/sdk.html">🇷🇺</a> | <a href="../zh/sdk.html">🇨🇳</a> | <a href="../ja/sdk.html">🇯🇵</a> | <a href="../ko/sdk.html">🇰🇷</a>
</p>

# SDK Ryzen AI

## Ottenere l'accesso

1. Creare un account su [AMD Ryzen AI Early Access](https://account.amd.com/en/member/ryzenai-sw-ea.html)
2. Attendere l'approvazione (~2 giorni lavorativi)
3. Scaricare `ryzen_ai-1.6.1.tgz`

## Installazione

```bash
mkdir ~/ryzen_ai-1.6.1 && cd ~/ryzen_ai-1.6.1
tar -xvzf ryzen_ai-1.6.1.tgz
./install_ryzen_ai.sh -a yes -p ~/ryzen-ai-env
source ~/ryzen-ai-env/bin/activate
```

## Utilizzo con ONNX Runtime

```python
import onnxruntime as ort

session = ort.InferenceSession(
    "model.onnx",
    providers=['VitisAIExecutionProvider', 'CPUExecutionProvider']
)
result = session.run(None, {"input": input_data})
```

---

[← Risoluzione problemi](troubleshooting.html) | [Home](index.html)
