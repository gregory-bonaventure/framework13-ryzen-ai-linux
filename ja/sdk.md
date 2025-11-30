---
layout: default
title: Ryzen AI SDK
---

<p align="right">
  <a href="../sdk.html">🇫🇷</a> | <a href="../en/sdk.html">🇬🇧</a> | <a href="../de/sdk.html">🇩🇪</a> | <a href="../es/sdk.html">🇪🇸</a> | <a href="../pt/sdk.html">🇵🇹</a> | <a href="../it/sdk.html">🇮🇹</a> | <a href="../nl/sdk.html">🇳🇱</a> | <a href="../pl/sdk.html">🇵🇱</a> | <a href="../ru/sdk.html">🇷🇺</a> | <a href="../zh/sdk.html">🇨🇳</a> | <strong>🇯🇵</strong> | <a href="../ko/sdk.html">🇰🇷</a>
</p>

# Ryzen AI SDK

## アクセス権の取得

1. [AMD Ryzen AI Early Access](https://account.amd.com/en/member/ryzenai-sw-ea.html) でアカウントを作成
2. 承認を待つ（約2営業日）
3. `ryzen_ai-1.6.1.tgz` をダウンロード

## インストール

```bash
mkdir ~/ryzen_ai-1.6.1 && cd ~/ryzen_ai-1.6.1
tar -xvzf ryzen_ai-1.6.1.tgz
./install_ryzen_ai.sh -a yes -p ~/ryzen-ai-env
source ~/ryzen-ai-env/bin/activate
```

## ONNX Runtimeでの使用

```python
import onnxruntime as ort

session = ort.InferenceSession(
    "model.onnx",
    providers=['VitisAIExecutionProvider', 'CPUExecutionProvider']
)
result = session.run(None, {"input": input_data})
```

---

[← トラブルシューティング](troubleshooting.html) | [ホーム](index.html)
