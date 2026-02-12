# GenAI_DirectMultimoda_LLM

# 🧠 Direct Multimodal LLM System  
### Enterprise-Scale Multimodal Reasoning (Without RAG)

---

## 📌 Project Overview

This capstone project implements a **Direct Multimodal Large Language Model (LLM) pipeline** that enables users to ask natural language questions over multiple input modalities — without a separate retrieval (RAG) step.

The system directly processes and reasons over:

- 📄 Text documents (reports, manuals, notes)
- 🖼️ Images (charts, diagrams)
- 🎙️ Audio recordings (meetings, lectures)
- 📑 PDFs (digital and scanned)

The objective is to simulate an enterprise AI assistant capable of reasoning across multimodal internal company data.

---

## 🏗️ System Architecture

### 🔹 1. Data Ingestion
Supports:
- Text files (.txt)
- Image files (.png, .jpg)
- Audio files (.wav, .mp3)
- PDF documents

### 🔹 2. Preprocessing

| Modality | Tool Used | Purpose |
|-----------|------------|------------|
| Text | Python | Cleaning & formatting |
| Image | PIL | Resizing, RGB conversion |
| Audio | Whisper | Speech-to-text transcription |
| PDF | PyMuPDF / pdfplumber | Text extraction |

---

## 🤖 Multimodal LLM

**Model Used:** Qwen-VL (Open-Source Multimodal LLM)

### Why Qwen-VL?
- Strong text + image reasoning
- Instruction-following capability
- HuggingFace ecosystem compatibility
- Open-source & locally deployable

Alternative models explored:
- LLaVA
- MiniGPT-4

---

## 🔄 Processing Flow

User Query  
⬇  
Multimodal Inputs Preprocessed  
⬇  
Structured Prompt Construction  
⬇  
Direct Multimodal LLM Reasoning  
⬇  
Natural Language Response  

---

## 🧠 Prompt Engineering Strategy

To reduce hallucinations and improve grounding:

- Explicit instruction to use only provided inputs
- Clear separation of modalities in prompt
- Instruction to state when information is unavailable
- Optional step-by-step reasoning guidance

### Example Prompt Template

```text
You are an enterprise AI assistant.
Use ONLY the provided multimodal inputs.
If information is not present, clearly state it.

Text Context:
{extracted_text}

Image Context:
{image_input}

Audio Transcript:
{transcribed_audio}

User Question:
{query}
```

---

## 🧪 Example Queries Demonstrated

### 1️⃣ Revenue Drop Analysis  
**Modalities:** Text + Image  
**Query:** Why did revenue drop in Q3?  
**Observation:** Successfully linked chart decline with textual explanation.

---

### 2️⃣ Meeting Confirmation  
**Modalities:** Audio Transcript  
**Query:** Was the product launch confirmed?  
**Observation:** Accuracy dependent on transcription quality.

---

### 3️⃣ Architecture Diagram Explanation  
**Modalities:** Image  
**Query:** What is the role of the API gateway?  
**Observation:** Minor hallucination when diagram text was unclear.

---

### 4️⃣ Budget Approval Validation  
**Modalities:** Text + Audio  
**Query:** Is the budget approved?  
**Observation:** Model struggled when modalities contained conflicting signals.

---

### 5️⃣ Risk Identification  
**Modalities:** Text + Image + Audio  
**Query:** What risks were identified in the presentation?  
**Observation:** Structured prompting improved grounding.

---

## ⚠ Challenges Encountered

- Audio transcription noise affecting reasoning
- OCR inaccuracies in scanned PDFs
- Context length limitations
- Occasional visual hallucinations
- Need for strong prompt constraints

---

## 📊 Evaluation Summary

| Metric | Performance |
|--------|------------|
| Cross-modal reasoning | Good |
| Hallucination control | Moderate |
| Visual reasoning | Strong on clear diagrams |
| Audio robustness | Dependent on transcription |

---

## 🛠️ Tech Stack

- Python
- HuggingFace Transformers
- Qwen-VL
- OpenAI Whisper
- PIL
- PyMuPDF / pdfplumber
- Jupyter Notebook

---

## 📂 Repository Structure

```
├── multimodal_pipeline.py
├── data.zip
├── requirements.txt
└── README.md
```

---

## 🚀 How to Run

### 1️⃣ Install Dependencies

```bash
pip install -r requirements.txt
```

### 2️⃣ Extract Input Files

```bash
unzip data.zip
```

### 3️⃣ Run the Pipeline

```bash
python multimodal_pipeline.py
```

---

## 💡 Future Improvements

- Add modality confidence scoring
- Improve OCR robustness
- Compare with RAG-based architecture
- Build interactive UI (Streamlit/Gradio)
- Add visual attention explanation

---

## 👩‍💻 Author

Sirisha Rompicherla  
Software Engineer | AI & GenAI Practitioner  
Full Stack Developer | ML Enthusiast
