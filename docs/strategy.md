
# 🧠 Detection Bypass Strategy — HumanTextAI

## 🎯 Objective
Design a modular and scalable humanization engine that transforms AI-generated text into human-like writing with the following constraints:

- **Detection Confidence**: Reduce AI detection scores to **< 20%**
- **Semantic Integrity**: Preserve **≥ 90%** of original meaning
- **Performance**: Processing time **< 10s per 1000 words**
- **Deployment-Ready**: Usable via CLI and API (FastAPI)

---

## 🔍 Core Problem

Modern AI detectors (GPTZero, Turnitin, QuillBot) identify machine-generated text using patterns such as:
- Low perplexity (predictability)
- Low burstiness (uniform sentence structures)
- Repetitive phrasing and unnatural flow

---

## 🧩 Transformation Pipeline Overview

[ Input Text ]
      ↓
[ Cleaning & Preprocessing ]
      ↓
[ Modular Rewriting Engine ]
      ↓
[ Semantic Validation ]
      ↓
[ Final Humanized Output ]

---

## 🧰 Transformation Modules

| Module | Purpose | Key Actions |
|--------|---------|-------------|
| **Lexical Substitution** | Increase lexical diversity | Synonym replacement, paraphrase noun/adjective phrases |
| **Sentence Restructuring** | Enhance burstiness | Flip clause order, change passive ↔ active, combine/split sentences |
| **Stylistic Noise Injection** | Mimic human unpredictability | Insert rhetorical phrases, idioms, randomness in tone |
| **Semantic Similarity Validation** | Maintain meaning | Use sentence-transformers + cosine similarity threshold |
| **Readability Tuner** | Balance complexity | Use `textstat` to keep writing readable but less robotic |

---

## 🎛️ Humanization Level (1–10)

| Level | Description |
|-------|-------------|
| 1–3   | Light: Subtle paraphrasing, high fidelity |
| 4–7   | Balanced: Mid-level rewrites with tone shifts |
| 8–10  | Aggressive: Max burstiness + complete sentence refactoring |

---

## 🧪 Quality Control Metrics

| Metric           | Threshold          | Tooling |
|------------------|--------------------|---------|
| AI Detection Score | < 20%             | GPTZero API, Turnitin trials |
| Semantic Similarity | ≥ 90% cosine sim | `sentence-transformers` |
| Grammar Quality    | High (no loss)    | `language-tool-python` |
| Readability Index  | 50–70 Flesch      | `textstat` |

---

## 🔄 Feedback Loop

If detection score ≥ 20%:
- Re-run pipeline with higher intensity level
- Swap paraphrasing templates
- Adjust randomness parameters

---

## 📌 Implementation Notes

- All modules are **independent and testable**
- Final transformation passes are scored before writing output
- Intermediate outputs are logged for rollback or debugging
- CLI + FastAPI support baked in from the start

---

## 🧱 Dependencies (Initial)

- `spacy` for parsing and structure detection
- `nltk`, `textstat` for lexical/sentence analysis
- `sentence-transformers` for semantic checks
- `parrot-paraphraser` or T5-based paraphrasing for rewriting
- `language-tool-python` for grammar QA

---

## ✅ Next Steps

- [ ] Collect AI vs. Human text samples into `data/examples/`
- [ ] Design core rewriter modules inside `rewriter.py`
- [ ] Build evaluation harness to test bypass success
