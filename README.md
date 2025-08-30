# 🔐 DuoCrypt: PII Encryption Pipeline for AI Privacy

## 📌 Overview
As AI systems such as ChatGPT become widely integrated into sensitive domains such as healthcare, finance, and defense, **privacy leakage** is a growing concern.  
Current solutions often **redact personally identifiable information (PII)** before sending text to LLMs, but redaction is **one-way**: once removed, the data cannot be recovered.

Our solution takes a different approach:  
👉 Instead of redacting PII, we **encrypt it with AES-256** before sending it to the LLM. This enables organisations to:

- 🔒 Prevent privacy leakage when using generative AI  
- 🔑 Restore original sensitive data when needed (reversible, unlike redaction)  
- 📄 **Empower shared access to documents** — authorized personnel can securely share documents without exposing sensitive details, since encrypted placeholders protect the underlying data  
- 🤝 Balance **security and usability**, ensuring that LLMs still receive enough context to be useful without risking data breaches
  

---

## ✨ Features
- **PII Detection**: Uses a pre-trained HuggingFace model to automatically detect sensitive information in text.  
- **AES-256 Encryption**: Quick encryption utilsiing only the detected PII (not the whole document) for maximum efficiency and security.  
- **Reversible Process**: Unlike redaction, encrypted PII can be decrypted later with the right keys.  
- **Context Preservation**: The LLM still receives meaningful input, allowing it to generate accurate responses.  

---

## 🛠 Development Tools
- **Python 3.10+** – Core programming language  
- **Google Colab** – Development & testing environment  
- **Git + GitHub** – Version control and collaboration  

---

## 🌐 APIs / Models Used
- **[Piiranha v1](https://huggingface.co/iiiorg/piiranha-v1-detect-personal-information)** – Pretrained NLP model for PII detection (via HuggingFace Transformers)  

---

## 📦 Libraries Used
- [**transformers**](https://github.com/huggingface/transformers) – For loading the pretrained PII detection model  
- [**torch**](https://pytorch.org/) – Backend for running the NLP model  
- [**pycryptodome**](https://www.pycryptodome.org/) – For AES-256 encryption & decryption  
- **re (Regex)** – For handling text replacements and restoration  
- **os** – For secure random key/IV generation  

---

## 📜 Problem Statement
As AI technologies rapidly integrate into our daily lives, concerns about **privacy and security** have become more urgent than ever. With the rise of powerful generative AI models, large-scale data collection, and cloud-based deployment, users face increasing risks such as **sensitive data leakage and identity theft**.  

This hackathon challenge focuses on:
- Enhancing the privacy of AI systems themselves (**Privacy of AI**), and/or  
- Using AI to defend user privacy and security (**AI for Privacy**)  

Our project addresses this by:
- Preventing privacy leakage when using generative AI  
- Building an app that detects **PII in prompts** and encrypts it before sending to LLMs  
- Enabling organizations to safely adopt AI without fear of data leaks, while still being able to recover sensitive information when needed  

---

## 🚀 How It Works (Quick Demo)
```python
# Input text
"My name is John Doe and my credit card number is 1234-5678-9012-3456."

# → PII detected: "John Doe", "1234-5678-9012-3456"
# → Encrypted with AES-256
"My name is [a91bcf...] and my credit card number is [f7d23a...]"

# LLM processes the context safely
# → After authorized decryption
"My name is John Doe and my credit card number is 1234-5678-9012-3456."
