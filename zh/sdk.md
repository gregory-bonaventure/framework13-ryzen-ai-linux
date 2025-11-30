---
layout: default
title: Ryzen AI SDK
---

<p align="right">
  <a href="../sdk.html">🇫🇷</a> | <a href="../en/sdk.html">🇬🇧</a> | <a href="../de/sdk.html">🇩🇪</a> | <a href="../es/sdk.html">🇪🇸</a> | <a href="../pt/sdk.html">🇵🇹</a> | <a href="../it/sdk.html">🇮🇹</a> | <a href="../nl/sdk.html">🇳🇱</a> | <a href="../pl/sdk.html">🇵🇱</a> | <a href="../ru/sdk.html">🇷🇺</a> | <strong>🇨🇳</strong> | <a href="../ja/sdk.html">🇯🇵</a> | <a href="../ko/sdk.html">🇰🇷</a>
</p>

# Ryzen AI SDK

## 获取访问权限

1. 在 [AMD Ryzen AI Early Access](https://account.amd.com/en/member/ryzenai-sw-ea.html) 创建账户
2. 等待审批（约2个工作日）
3. 下载 `ryzen_ai-1.6.1.tgz`

## 安装

```bash
mkdir ~/ryzen_ai-1.6.1 && cd ~/ryzen_ai-1.6.1
tar -xvzf ryzen_ai-1.6.1.tgz
./install_ryzen_ai.sh -a yes -p ~/ryzen-ai-env
source ~/ryzen-ai-env/bin/activate
```

## 使用ONNX Runtime

```python
import onnxruntime as ort

session = ort.InferenceSession(
    "model.onnx",
    providers=['VitisAIExecutionProvider', 'CPUExecutionProvider']
)
result = session.run(None, {"input": input_data})
```

---

[← 故障排除](troubleshooting.html) | [首页](index.html)
