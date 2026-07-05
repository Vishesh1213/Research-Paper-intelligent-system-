# 🧠 AI Research Paper Intelligent System

An NLP-based intelligent research paper search system that retrieves relevant research papers using **semantic search** instead of traditional keyword matching. The project leverages **Sentence Transformers**, **FAISS**, **BART Summarization**, **KeyBERT**, and **Google Gemini API** to search, summarize, and explain research papers.

---

## 📌 Project Overview

Traditional keyword-based search often fails to retrieve semantically relevant research papers. This project addresses that problem by converting research papers into dense vector embeddings and performing similarity search using FAISS.

The system also summarizes retrieved papers, extracts important keywords, and generates detailed explanations for technical terms using the Google Gemini API.

---

## 🚀 Features

- Load research papers from the Hugging Face dataset
- Preprocess paper titles and abstracts
- Generate semantic embeddings using Sentence Transformers
- Store embeddings in a FAISS vector database
- Perform semantic similarity search
- Retrieve Top-K relevant research papers
- Summarize research paper abstracts using BART
- Extract important keywords using KeyBERT
- Explain technical keywords using Google Gemini
- Save generated entity information as JSON

---

## 📚 Dataset

The project uses the **ML-ArXiv-Papers** dataset from Hugging Face.

Only the following fields are used:

- **Title**
- **Abstract**

Both columns are combined into a single text field (`paper_text`) for embedding generation.

---

## 🛠️ Technologies Used

| Category | Library |
|----------|----------|
| Programming Language | Python |
| Data Processing | Pandas, NumPy |
| Dataset | Hugging Face Datasets |
| Embedding Model | Sentence Transformers (`all-MiniLM-L6-v2`) |
| Vector Database | FAISS |
| Similarity Metric | Cosine Similarity |
| Summarization | Facebook BART (`facebook/bart-large-cnn`) |
| Keyword Extraction | KeyBERT |
| LLM | Google Gemini API |

---

# 📦 Installation

Clone the repository

```bash
git clone https://github.com/your-username/AI-Research-Paper-Intelligent-System.git

cd AI-Research-Paper-Intelligent-System
```

Install the required dependencies

```bash
pip install datasets
pip install sentence-transformers
pip install faiss-cpu
pip install transformers==4.46.3
pip install keybert
pip install google-generativeai
```

---

# ▶️ How to Run

Open the notebook and run all cells sequentially.

```text
Research_Paper_Intelligent_System.ipynb
```

The notebook automatically

- Loads the dataset
- Generates embeddings
- Creates the FAISS index
- Performs semantic search
- Summarizes retrieved papers
- Extracts keywords
- Generates keyword explanations using Gemini

---

# 🔄 Workflow

## 1. Load Dataset

The project downloads the **ML-ArXiv-Papers** dataset from Hugging Face.

```python
dataset = load_dataset("CShorten/ML-ArXiv-Papers")
```

---

## 2. Data Preparation

The dataset is converted into a Pandas DataFrame.

Only the following columns are retained:

- Title
- Abstract

Both are merged into a new column

```python
paper_text = title + abstract
```

---

## 3. Generate Sentence Embeddings

Each research paper is converted into a semantic vector using

```
SentenceTransformer("all-MiniLM-L6-v2")
```

Generated embeddings are saved locally as

```
embedding.npy
```

If the file already exists, it is loaded instead of generating embeddings again.

---

## 4. Build FAISS Index

The embeddings are normalized and stored inside a FAISS vector database.

Generated index

```
paper_faiss.index
```

If the index already exists, it is loaded automatically.

---

## 5. Semantic Search

A user query is converted into an embedding.

The embedding is searched against the FAISS index to retrieve the most relevant research papers.

Returned information includes

- Similarity Score
- Paper Title
- Paper Abstract

---

## 6. Research Paper Summarization

The retrieved paper abstracts are summarized using

```
facebook/bart-large-cnn
```

This generates concise summaries of the retrieved papers.

---

## 7. Keyword Extraction

Important keywords are extracted from the abstract using **KeyBERT**.

Both single-word and multi-word key phrases are generated.

Example

```
Deep Learning

Medical Imaging

CNN

Transformer
```

---

## 8. Keyword Explanation using Google Gemini

Each extracted keyword is sent to the Gemini API.

Gemini returns structured information including

- Entity
- Category
- Definition
- Importance
- Applications
- Related Terms

The generated information is stored in

```
paper_entities.json
```

---

# 📁 Generated Files

| File | Description |
|------|-------------|
| `embedding.npy` | Saved sentence embeddings |
| `paper_faiss.index` | FAISS vector database |
| `paper_entities.json` | Gemini-generated keyword explanations |

---

# 🔍 Example

```python
search_and_summarize(
    "Deep learning in medical imaging",
    k=5
)
```

Output includes

- Similarity Score
- Research Paper Title
- Abstract
- Generated Summary

---

# 📂 Project Structure

```
AI-Research-Paper-Intelligent-System/

│── Research_Paper_Intelligent_System.ipynb
│── embedding.npy
│── paper_faiss.index
│── paper_entities.json
│── README.md
```

---

# 📌 Current Status

✔ Dataset Loading

✔ Semantic Embedding Generation

✔ FAISS Vector Search

✔ Semantic Paper Retrieval

✔ Research Paper Summarization

✔ Keyword Extraction

✔ Gemini-based Keyword Explanation

---

## 👨‍💻 Author

**Vishesh Raijada**

Data Analyst | Data Scientist | Machine Learning & NLP Enthusiast

---

⭐ **If you found this project helpful, consider giving it a star on GitHub!**
