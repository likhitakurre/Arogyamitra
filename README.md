🏥 Telugu Healthcare Chatbot (RAG + GPT-2 Fine-Tuning)

A medical assistant chatbot for Telugu & Code-Mixed Telugu users, powered by GPT-2 LoRA fine-tuning, RAG retrieval, and translation models.

🚀 Project Overview

This project builds an intelligent healthcare chatbot that can answer medical queries in:

Code-mixed Telugu (Telugu + English Romanized)

Pure Telugu (using translation model)

The system is powered by:

Fine-tuned GPT-2 (LoRA) on a 10K healthcare dataset

RAG retrieval using FAISS + Sentence-BERT

A hybrid UI built using Gradio

A Telugu translation Seq2Seq model for pure Telugu responses

This chatbot is designed to help elderly Telugu speakers, providing easy-to-understand medical advice.

✨ Key Features
🔹 1. GPT-2 Fine-Tuned Medical Chatbot

Fine-tuned on 15,000 healthcare Q/A pairs

LoRA configuration:

r=8

alpha=32

dropout=0.1

Optimized for code-mixed Telugu medical dialogue

🔹 2. RAG (Retrieval-Augmented Generation)

Uses FAISS for fast nearest-neighbor search

Knowledge base built from curated medical text (translated + expanded)

Embeddings generated using Indic Sentence-BERT (SBERT)

🔹 3. Dual-Language Output

Code-mixed Telugu response from fine-tuned model

Pure Telugu response translated using:

aryaumesh/english-to-telugu (Seq2Seq model)

🔹 4. Modern Chat UI

Gradio chat interface

Dark UI theme (ChatGPT-like feeling)

Displays:

Generated answer

Telugu translation

Retrieved RAG context (English + Telugu)

🧠 Architecture
User Query
     ↓
Encoder (Sentence-BERT)
     ↓
FAISS Retrieval → Top-K Relevant Medical Info
     ↓
GPT-2 LoRA (Fine-Tuned)
     ↓
Generated Code-Mixed Telugu Response
     ↓
Translation Model → Pure Telugu Output
     ↓
Gradio UI

🗂 Dataset
📌 1. Fine-Tuning Dataset

15K JSONL samples

Each sample contains:

{"prompt": "...", "completion": "..."}

Codemixed Telugu targeted towards common medical queries.

📌 2. RAG Knowledge Base

Curated & expanded from medical instruction dataset

Cleaned into structured, human-readable format

Stored in:

kb_docs_rich.txt

📊 Model Performance
Metric	Score
BERTScore (F1)	0.86
Semantic Similarity	0.64
Perplexity	31.5

These metrics indicate high fluency, relevance, and coherence for Telugu medical responses.

🧪 How to Run the Project (Colab)
1️⃣ Install Dependencies
pip install transformers sentence-transformers faiss-cpu gradio

2️⃣ Load Fine-Tuned GPT-2
generator = pipeline("text-generation", model="./output", tokenizer="./output", device_map="auto")

3️⃣ Load FAISS RAG Index
index = faiss.read_index("faiss_index.index")
with open("kb_texts.json") as f:
    kb_texts = json.load(f)

4️⃣ Run the Chat UI
import gradio as gr
chatbot.launch()

💬 Example Interaction
User: Naku headache undi. Em cheyyali?

Code-Mixed Response:
→ Please try mild headache ki rest and hydration maintain cheyyandi.

Pure Telugu:
→ తలనొప్పి ఉంటే కాసేపు విశ్రాంతి తీసుకుని నీళ్లు ఎక్కువగా తాగండి.

Retrieved Context:
→ headache vunte: rest teesukoni water maintain cheyyandi...

📦 Project Structure
├── output30epochs.zip              # Fine-tuned GPT-2 model
├── kb_docs_rich.txt                # Human-cleaned medical KB
├── clean_healthcare_15k.jsonl      # Fine-tuning dataset
├── code.py                          # Full RAG + Translator + UI code

🎯 Future Improvements

✔ Add Speech-to-Text for elderly users
✔ Add symptom classifier for structured tagging
✔ Deploy on Flask or FastAPI
✔ Add voice output in Telugu

🧑‍💻 Author
Kurre Likhita
AI/ML Developer
📍Hyderabad,India
