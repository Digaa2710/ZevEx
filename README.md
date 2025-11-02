# ZevEx 
### Zero-Shot Cross-Lingual Event Extraction using XLM-RoBERTa-Large (SQuAD2)

---

## Overview

**ZevEx** is a research project that investigates **zero-shot cross-lingual transfer learning** for **event extraction** using the **`xlm-roberta-large-squad2`** model.  
The model, originally fine-tuned on the **SQuAD2 (Question Answering)** dataset, is repurposed to extract event information by answering **three event-specific questions** for each sentence.  
Testing was performed on **Gujarati** and **Marathi** event datasets without any fine-tuning — demonstrating the zero-shot capability of multilingual transformers.

---

## Research Objective

- To perform **event extraction** through a **Question Answering (Q&A)** approach.  
- To test the **cross-lingual generalization** ability of **`xlm-roberta-large-squad2`** for **Gujarati** and **Marathi** languages.  
- To evaluate and compare the performance of **XLM-RoBERTa** and **IndicBERT** models for zero-shot event understanding.

---

## Experimental Setup

### Task
Each input sentence was transformed into **three Q&A pairs**, asking the model:

1. **Event Actor** → *Who performed the event?*  
2. **Event Type** → *What kind of event occurred?*  
3. **Event Reason** → *Why did the event occur?*

---

### Training Data

- **Language:** English  
- **Base Model:** `xlm-roberta-large-squad2`  
- **Dataset:** Custom Q&A-style **event extraction** dataset derived from English event texts.  

**Example:**

| Question | Context | Answer |
|-----------|----------|--------|
| Who is the actor in the event? | "Prime Minister inaugurated a new hospital in Delhi." | Prime Minister |
| What type of event occurred? | "Prime Minister inaugurated a new hospital in Delhi." | Inauguration |
| Why did the event occur? | "Prime Minister inaugurated a new hospital in Delhi." | To improve healthcare facilities |

---

### Testing Data

- **Languages Tested:** Gujarati, Marathi  
- **Dataset Type:** Custom, event-based Q&A dataset  
- **Evaluation:** Zero-shot — no fine-tuning on target languages  

---

## Models Evaluated

| Model Name | Type | Parameters | Purpose |
|-------------|------|-------------|----------|
| `xlm-roberta-base` | Multilingual Transformer | ~270M | Baseline |
| **`xlm-roberta-large-squad2`** | Multilingual QA Transformer | ~550M | ✅ Best Performing Model |
| `indic-bert` | Indic Language Transformer | ~120M | Comparative baseline |

---

##  Results

| Language | Model | Exact Match (EM) | F1 Score | Remarks |
|-----------|--------|------------------|-----------|----------|
| Gujarati | XLM-RoBERTa Base | 45.8 | 76.3 | Moderate performance |
| **Gujarati** | **XLM-RoBERTa-Large (SQuAD2)** | **54.4** | **80.7** | ✅ Best Results |
| Gujarati | IndicBERT | 39.2 | 68.5 | Weak cross-lingual generalization |
| **Marathi** | **XLM-RoBERTa-Large (SQuAD2)** | **64.33** | **82.95** | Strong performance in Devanagari script |

---

##  Key Findings

- **`xlm-roberta-large-squad2`** performed best across Gujarati and Marathi datasets.  
- **Zero-shot transfer** successfully extracted event-related details (actor, type, reason) from regional language texts.  
- **IndicBERT** showed lower F1, indicating less effective transfer without fine-tuning.  
- The **Q&A-based formulation** made event extraction intuitive and language-independent.

---

##  Conclusion

This study confirms that **multilingual QA-based transformers** like `xlm-roberta-large-squad2` can effectively generalize **event extraction tasks** to **low-resource Indian languages** through **zero-shot transfer learning**.  
Despite some accuracy loss due to linguistic and script differences, the approach offers a promising foundation for **multilingual event understanding**.

---

##  Future Work

- Create and fine-tune on manually annotated Gujarati and Marathi event datasets.  
- Extend experiments to **Hindi**, **Tamil**, and **Bengali**.  
- Explore **chunk-based extraction** for long paragraphs.  
- Use **multilingual summarization** before extraction to handle long contexts.

---

##  Tech Stack

- **Model:** `xlm-roberta-large-squad2` (Hugging Face Transformers)  
- **Framework:** PyTorch + Transformers  
- **Evaluation Metrics:** Exact Match (EM), F1 Score  
- **Languages:** English (training), Gujarati & Marathi (testing)  
- **Type:** Zero-Shot Cross-Lingual Transfer  



