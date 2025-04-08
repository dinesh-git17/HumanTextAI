# 📘 Research Notes — Phase 1: Detection Mechanisms

## 🎯 Objective
Understand the internal mechanisms used by modern AI content detectors such as GPTZero, Turnitin, and QuillBot to identify machine-generated text. These insights will guide the design of our humanization engine to effectively bypass detection systems while preserving semantic integrity.

---

## 🧠 Detectors Overview

| Detector     | Detection Focus                          | Description |
|--------------|------------------------------------------|-------------|
| GPTZero      | Perplexity & Burstiness                  | GPTZero evaluates how predictable and structurally uniform a piece of text is. AI-generated content tends to have low perplexity and low burstiness. |
| Turnitin     | Structured Language Patterns              | Turnitin flags consistently structured, overly formal, or logically “perfect” writing—hallmarks of AI-generated text. |
| QuillBot AI  | Syntactic Uniformity & Word Choice       | Focuses on repetitive syntax and unnatural vocabulary that often emerge from AI paraphrasing. |

---

## 🔍 Core Detection Features

### 1. Perplexity
- Measures how *predictable* the text is for a language model.
- Lower perplexity → high likelihood of AI generation.
- Human writing often includes errors, unpredictability, or “messiness”.

### 2. Burstiness
- Captures *variation* in sentence lengths and structures.
- AI tends to use uniform sentence patterns.
- Human writing shows high burstiness — short, punchy lines mixed with long, complex ones.

### 3. Syntactic Patterns
- AI tends to avoid:
  - Passive voice
  - Idioms/slang
  - Rhetorical questions
- Human writing is often rich in these elements.

### 4. Redundancy & Repetition
- AI-generated content may repeat ideas, rephrase the same point, or use similar sentence starters.
- Humans tend to use more contextual transitions.

---

## 🧠 Known Techniques for Bypassing Detection

| Technique                   | Description |
|----------------------------|-------------|
| Lexical Variety            | Use synonyms and alter vocabulary to increase perplexity. |
| Sentence Restructuring     | Rearrange sentence order, length, and punctuation for burstiness. |
| Stylistic Noise            | Introduce controlled randomness (rhetorical questions, informal tone, idioms). |
| Semantic Preservation      | Use cosine similarity to ensure meaning is unchanged post-transformation. |

---

## 🧪 Example Detection Metrics

| Metric         | Human Sample | AI Sample |
|----------------|--------------|-----------|
| Perplexity     | High (~80+)  | Low (~10–20) |
| Burstiness     | High         | Low       |
| Detection Conf.| < 10%        | > 80%     |

---

## 🧬 Implications for Engine Design

Our rewriter must:
- **Increase perplexity** without harming grammar
- **Boost burstiness** with sentence-level variety
- **Mimic human style** with randomness and nuance
- **Maintain meaning** through semantic vector comparisons

---

## 📌 References

- [GPTZero Docs](https://gptzero.me)
- [Originality.ai Blog](https://originality.ai/blog/perplexity-and-burstiness-in-writing)
- [Turnitin AI Writing Detection](https://www.turnitin.com/products/ai-writing-detection)
- [Medium - Perplexity Explained](https://medium.com/the-generator/the-dummy-guide-to-perplexity-and-burstiness-in-ai-generated-content-1b4cb31e5a81)

---

## ✅ Next Steps

- Collect a dataset of real AI vs. human text samples for benchmarking
- Design our detection bypass strategy (`strategy.md`)

