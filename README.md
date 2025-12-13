# LLM-Based Generative AI Systems: Hallucination Reduction & Multi-Agent Reasoning

**Course:** COMSE6998-015 – Introduction to LLM-Based Generative AI Systems  
**Focus:** Hallucination mitigation, retrieval grounding, and multi-agent reasoning  
**Execution Environment:** Google Colab (Preferred: A100 GPU)

---

## Project Overview
This repository contains a collection of **LLM-based system implementations and experiments** focused on improving **factuality, safety, and reliability** in generative AI systems.

The project explores **three complementary approaches** to hallucination reduction and reasoning quality:

1. **Retrieval-Augmented Generation (RAG)**
2. **Contrastive Decoding**
3. **Multi-Agent Role-Aligned Reasoning**

Together, these components study how both **training-time assumptions** and **inference-time system design** affect LLM reliability.

---


---

## 1. Retrieval-Augmented Generation (RAG) Experiments

**Notebook:** `Hallucination_eval.ipynb`

### Objective
Evaluate how **retrieval-augmented generation** reduces hallucinations compared to generation without retrieval.

---

### Methodology
- Relevant documents are retrieved based on semantic similarity
- Retrieved passages are injected into the model prompt
- Outputs are evaluated for:
  - factual consistency
  - hallucination frequency
  - answer completeness

---

### Key Insight
Grounding model responses in retrieved external context significantly reduces unsupported claims and improves factual reliability, especially for domain-specific queries.

---

## 2. Contrastive Decoding Experiments

**Notebook:** `Hallucination_eval_Contrastive_Decoding.ipynb`

### Objective
Analyze how **contrastive decoding** can reduce hallucinations at inference time without modifying model weights.

---

### Methodology
- Compare standard decoding against contrastive decoding
- Penalize token trajectories likely to produce hallucinations
- Evaluate factual accuracy across structured prompts

---

### Key Insight
Contrastive decoding provides a **lightweight, inference-time hallucination mitigation strategy** that complements retrieval-based approaches.

---

## 3. Multi-Agent Medical QA & Case Analysis System

**Notebook:** `multi_agent_documented.ipynb`

### Motivation
Single-model systems often struggle to balance:
- expert-level medical reasoning
- safe, patient-friendly communication

This system addresses that limitation using **role-aligned multi-agent architecture**.

---

### Agent Roles

#### Cardiology Agent
- Performs cardiology-specific reasoning
- Uses only retrieved cardiology documents
- Avoids answering outside its domain

#### Dermatology Agent
- Performs skin-related analysis and differential reasoning
- Uses dermatology-specific retrieved documents
- Restricts output to dermatology scope

#### Doctor Agent (Clinical Synthesizer)
- Integrates outputs from specialist agents
- Produces a coherent, medically grounded response
- Resolves conflicts and summarizes findings

#### Nurse Agent (Patient-Facing Interpreter)
- Converts the doctor’s output into clear, non-technical language
- Emphasizes safety and empathy
- Does **not** introduce new diagnoses

---

### Multi-Agent Pipeline
1. User submits a question or clinical case
2. Input is routed to Cardiology and Dermatology agents
3. Specialist outputs are synthesized by the Doctor agent
4. Final response is rewritten by the Nurse agent
5. Nurse-facing answer is returned to the user

---

## How to Run

### Run on Google Colab (Preferred: A100 GPU)
This project is designed to run on **Google Colab**, preferably using an **A100 GPU** for best performance.

1. Upload all repository files to your Colab environment.
2. Set the runtime to **GPU (A100 if available)**.
3. **Do not forget to add your Hugging Face access token**, required for loading models:
   - Store it as an environment variable (`HF_TOKEN`), or
   - Add it securely using Colab secrets.
4. Run the notebooks or Python scripts sequentially.

---

### User Interface (Gradio)
For the multi-agent system:

- In the **final code cell**, a **Gradio web interface** is launched.
- A public **Gradio link** will appear in the output.
- Click the link to interact with the system through a browser-based UI.

---

## Evaluation Criteria
Evaluation across all components focuses on:
- hallucination reduction
- grounding to external context
- multi-step reasoning quality
- safety and clarity of outputs

---

## Technologies Used

- **Python** – Core implementation language  
- **Google Colab** – GPU-based execution environment (A100 preferred)  
- **HuggingFace Transformers & Hub** – Model loading, tokenization, and inference  
- **Retrieval-Augmented Generation (RAG)** – Document-grounded generation  
- **Contrastive Decoding** – Inference-time hallucination reduction  
- **Multi-Agent Prompt Engineering** – Role-aligned specialist, doctor, and nurse agents  
- **LangChain / LangGraph–style Orchestration** – Structured multi-step agent pipelines (conceptually inspired)  
- **Gradio** – Web-based user interface  

---

## Limitations
- Results depend on document quality and retrieval accuracy
- Contrastive decoding requires careful tuning
- Intended for **research and educational use only**

---

## Summary
This repository demonstrates how **retrieval, decoding strategies, and multi-agent architectures** can work together to improve the reliability and safety of LLM-based generative AI systems.
