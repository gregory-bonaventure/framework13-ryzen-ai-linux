---
layout: default
title: Ryzen AI SDK
---

<p align="right">
  <a href="../sdk.html">🇫🇷</a> | <a href="../en/sdk.html">🇬🇧</a> | <a href="../de/sdk.html">🇩🇪</a> | <a href="../es/sdk.html">🇪🇸</a> | <a href="../pt/sdk.html">🇵🇹</a> | <a href="../it/sdk.html">🇮🇹</a> | <a href="../nl/sdk.html">🇳🇱</a> | <strong>🇵🇱</strong> | <a href="../ru/sdk.html">🇷🇺</a> | <a href="../zh/sdk.html">🇨🇳</a> | <a href="../ja/sdk.html">🇯🇵</a> | <a href="../ko/sdk.html">🇰🇷</a>
</p>

# Ryzen AI SDK

## Uzyskanie dostępu

1. Utwórz konto na [AMD Ryzen AI Early Access](https://account.amd.com/en/member/ryzenai-sw-ea.html)
2. Poczekaj na zatwierdzenie (~2 dni robocze)
3. Pobierz `ryzen_ai-1.6.1.tgz`

## Instalacja

```bash
mkdir ~/ryzen_ai-1.6.1 && cd ~/ryzen_ai-1.6.1
tar -xvzf ryzen_ai-1.6.1.tgz
./install_ryzen_ai.sh -a yes -p ~/ryzen-ai-env
source ~/ryzen-ai-env/bin/activate
```

## Użycie z ONNX Runtime

```python
import onnxruntime as ort

session = ort.InferenceSession(
    "model.onnx",
    providers=['VitisAIExecutionProvider', 'CPUExecutionProvider']
)
result = session.run(None, {"input": input_data})
```

---

[← Rozwiązywanie problemów](troubleshooting.html) | [Strona główna](index.html)
