---
layout: default
title: SDK Ryzen AI
---

<p align="right">
  <a href="../sdk.html">🇫🇷</a> |
  <a href="../en/sdk.html">🇬🇧</a> |
  <a href="../de/sdk.html">🇩🇪</a> |
  <strong>🇪🇸</strong> |
  <a href="../pt/sdk.html">🇵🇹</a> |
  <a href="../it/sdk.html">🇮🇹</a> |
  <a href="../nl/sdk.html">🇳🇱</a> |
  <a href="../pl/sdk.html">🇵🇱</a> |
  <a href="../ru/sdk.html">🇷🇺</a> |
  <a href="../zh/sdk.html">🇨🇳</a> |
  <a href="../ja/sdk.html">🇯🇵</a> |
  <a href="../ko/sdk.html">🇰🇷</a>
</p>

# SDK Ryzen AI

## Obtener acceso

1. Crear cuenta en [AMD Ryzen AI Software Early Access Lounge](https://account.amd.com/en/member/ryzenai-sw-ea.html)
2. Esperar aprobación (~2 días hábiles)
3. Descargar `ryzen_ai-1.6.1.tgz`

## Instalación

```bash
mkdir ~/ryzen_ai-1.6.1
cd ~/ryzen_ai-1.6.1
tar -xvzf ryzen_ai-1.6.1.tgz
./install_ryzen_ai.sh -a yes -p ~/ryzen-ai-env
source ~/ryzen-ai-env/bin/activate
```

## Uso con ONNX Runtime

```python
import onnxruntime as ort

session = ort.InferenceSession(
    "model.onnx",
    providers=['VitisAIExecutionProvider', 'CPUExecutionProvider']
)
result = session.run(None, {"input": input_data})
```

---

[← Solución de problemas](troubleshooting.html) | [Inicio](index.html)
