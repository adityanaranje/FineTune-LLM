# 📘 Fine-Tuning LLMs — Complete Guide

## 🔍 What Is Fine-Tuning?

Fine-tuning is the process of taking a pretrained Large Language Model (LLM) and training it further on a **specific dataset** so it adapts to a domain, task, or writing style.

A pretrained model already understands:
- Language  
- World knowledge  
- Reasoning  
- Grammar  
- Common patterns  

But it may not perfectly handle **your** domain or **your** output structure.  
Fine-tuning adjusts internal weights so the model behaves exactly how you want.

---

## ❓ Why Fine-Tune If RAG Already Exists?

**RAG (Retrieval-Augmented Generation)** retrieves external documents and feeds them into the model during inference.  
But RAG does **not** change the model’s internal behavior.

| Capability | RAG | Fine-Tuning |
|------------|-----|-------------|
| Add external knowledge | ✅ | ❌ |
| Teach structure, style, tone | ❌ | ✅ |
| Improve reasoning | ⚠️ | ✅ |
| Reduce hallucinations | ⚠️ | ⚠️ |
| Requires vector DB | Yes | No |
| Knowledge stored inside model | No | Yes |
| Output consistency | Low | High |

### RAG is not enough when:
- You need consistent output formats  
- You expect domain-specific reasoning  
- You want internalized rules  
- You want task-specific models  
- You want independence from retrieval pipelines  

### Fine-Tuning + RAG works best when:
- RAG provides **knowledge**  
- Fine-tuning provides **behavior + structure**  

---

# 🧩 Types of Fine-Tuning

## 1️⃣ **Full Fine-Tuning**

Updates **all** model parameters.

\[
	heta_{new} = 	heta_{old} - \eta \cdot 
abla_	heta L(x,y)
\]

---

## 2️⃣ **Parameter-Efficient Fine-Tuning (PEFT)**

Only updates a **small fraction** of weights.

Types:
- LoRA  
- QLoRA  
- Prefix / Prompt Tuning  
- Adapters  

---

# ⚙ LoRA (Low-Rank Adaptation)

\[
W' = W + BA
\]

LoRA injects small trainable matrices into transformer layers instead of modifying full weights.

---

# ⚡ QLoRA (Quantized LoRA)

\[
W' = D(W_q) + BA
\]

QLoRA quantizes the base model to **4-bit NF4** to drastically reduce memory usage.

---

# 🏎 LoRA vs QLoRA

| Feature | LoRA | QLoRA |
|---------|------|-------|
| Precision | FP16 | 4-bit |
| Memory | Medium | Very Low |
| GPU | 24GB+ | 8–12GB |
| Accuracy | High | Near full |

---

# 📐 Math Behind Fine-Tuning

\[
\hat{y} = f(x; 	heta)
\]
\[
L = - \sum y \log(\hat{y})
\]
\[
	heta = 	heta - \eta 
abla_	heta L
\]

---

# 🧾 Summary

| Problem | Best Method |
|---------|-------------|
| Add knowledge | RAG |
| Improve behavior | Fine-Tuning |
| Low GPU | QLoRA |
| Specialization | LoRA/QLoRA |
