---
layout: default
title: SDK Ryzen AI
---

<p align="right">
  <strong>🇫🇷</strong> |
  <a href="en/sdk.html">🇬🇧</a> |
  <a href="de/sdk.html">🇩🇪</a> |
  <a href="es/sdk.html">🇪🇸</a> |
  <a href="pt/sdk.html">🇵🇹</a> |
  <a href="it/sdk.html">🇮🇹</a> |
  <a href="nl/sdk.html">🇳🇱</a> |
  <a href="pl/sdk.html">🇵🇱</a> |
  <a href="ru/sdk.html">🇷🇺</a> |
  <a href="zh/sdk.html">🇨🇳</a> |
  <a href="ja/sdk.html">🇯🇵</a> |
  <a href="ko/sdk.html">🇰🇷</a>
</p>

# SDK Ryzen AI

Guide pour installer le SDK AMD Ryzen AI et exécuter des modèles IA sur le NPU.

## Prérequis

- ✅ Driver XDNA installé et fonctionnel
- ✅ `xrt-smi validate` passe tous les tests
- ✅ Compte AMD approuvé

## Obtenir l'accès au SDK

1. Créez un compte sur [AMD Ryzen AI Software Early Access Lounge](https://account.amd.com/en/member/ryzenai-sw-ea.html)
2. Attendez l'approbation (~2 jours ouvrés)
3. Téléchargez `ryzen_ai-1.6.1.tgz`

## Installation

```bash
mkdir ~/ryzen_ai-1.6.1
cd ~/ryzen_ai-1.6.1
tar -xvzf ryzen_ai-1.6.1.tgz
./install_ryzen_ai.sh -a yes -p ~/ryzen-ai-env
source ~/ryzen-ai-env/bin/activate
```

## Vérification

```bash
cd ~/ryzen-ai-env/quicktest
python quicktest.py
```

## Utilisation avec ONNX Runtime

```python
import onnxruntime as ort

session = ort.InferenceSession(
    "model.onnx",
    providers=['VitisAIExecutionProvider', 'CPUExecutionProvider']
)

result = session.run(None, {"input": input_data})
```

## Types de modèles supportés

| Type | Format | Support |
|------|--------|---------|
| CNN | INT8 | ✅ |
| CNN | BF16 | ✅ |
| NLP (BERT) | BF16 | ✅ |
| LLM | - | ✅ |

## Ressources

- [Documentation Ryzen AI](https://ryzenai.docs.amd.com/en/latest/)
- [RyzenAI-SW GitHub](https://github.com/amd/RyzenAI-SW)

---

[← Dépannage](troubleshooting.html) | [Accueil](index.html)
