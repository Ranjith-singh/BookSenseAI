# **BookSenseAI – Intelligent Book Recommendation System**

*A Semantic, LLM-Powered, Emotion-Aware Book Recommender*

---

## 🖼️ **Project Logo**

```
██████╗  ██████╗  ██████╗ ██╗  ██╗███████╗██████╗ ███████╗ █████╗ ███╗   ██╗
██╔══██╗██╔═══██╗██╔════╝ ██║ ██╔╝██╔════╝██╔══██╗██╔════╝██╔══██╗████╗  ██║
██████╔╝██║   ██║██║  ███╗█████╔╝ █████╗  ██████╔╝█████╗  ███████║██╔██╗ ██║
██╔═══╝ ██║   ██║██║   ██║██╔═██╗ ██╔══╝  ██╔══██╗██╔══╝  ██╔══██║██║╚██╗██║
██║     ╚██████╔╝╚██████╔╝██║  ██╗███████╗██║  ██║███████╗██║  ██║██║ ╚████║
╚═╝      ╚═════╝  ╚═════╝ ╚═╝  ╚═╝╚══════╝╚═╝  ╚═╝╚══════╝╚═╝  ╚═╝╚═╝  ╚═══╝
                BookSenseAI – Vector + LLM Powered Book Discovery
```

*(If you want an actual image logo, I can generate it too.)*

---

# 🏷️ **Badges**

<p align="center">

<img src="https://img.shields.io/badge/OpenAI-Embeddings-blue?logo=openai&logoColor=white" />
<img src="https://img.shields.io/badge/HuggingFace-Transformers-yellow?logo=huggingface&logoColor=white" />
<img src="https://img.shields.io/badge/Python-3.10+-blue?logo=python&logoColor=white" />
<img src="https://img.shields.io/badge/Gradio-Dashboard-orange?logo=python" />
<img src="https://img.shields.io/badge/Kaggle-Datasets-blue?logo=kaggle" />
<img src="https://img.shields.io/badge/Pandas-Dataframe-green?logo=pandas&logoColor=white" />
<img src="https://img.shields.io/badge/LangChain-Text%20Processing-purple?logo=chainlink" />
<img src="https://img.shields.io/badge/Chroma-VectorDB-green?logo=google" />

</p>

---

# 📚 **Project Overview Diagram**

```
┌────────────────────────────────────────┐
│            Kaggle Dataset              │
└───────────────┬────────────────────────┘
                │ (CSV files)
                ▼
       ┌─────────────────────┐
       │  Data Cleaning      │
       └───────┬────────────┘
               │
               ▼
      ┌──────────────────────┐
      │ Vector Embeddings     │ ← OpenAI
      └────────┬─────────────┘
               │
               ▼
      ┌───────────────────────┐
      │    Chroma VectorDB     │
      └─────────┬──────────────┘
                │
                ▼
        ┌─────────────────┐
        │ Similarity Search│
        └──────────────────┘
                │
                ▼
     ┌────────────────────────────┐
     │ BookSenseAI Recommendations│
     └────────────────────────────┘
```

---

# 🧪 **Dataset Extraction & Cleaning Workflow**

## 🔽 1. **Extract Kaggle Data**

```
Kaggle → Cache → CSV → pandas.DataFrame
```

---

## 🧹 2. **Data Cleaning Workflow**

### **Pipeline Diagram**

```
┌───────────────┐
│ Missing Values │──────────────┐
└───────┬───────┘              │
        │                      ▼
        ▼             ┌─────────────────┐
  Correlation Check → │ Remove Null Rows│
                      └─────────────────┘
        │                      │
        ▼                      ▼
 Category Cleaning ─────────→ Fix Fake Categories
        │
        ▼
Remove Short Descriptions
        │
        ▼
Combine Title + Subtitle
        │
        ▼
Drop Unnecessary Columns
```

---

## 📊 **Visualizations**

You generate:

* Missing value heatmaps
* Category count plots
* Correlation plots

(using Seaborn + Matplotlib)

---

# 🤖 **LLM Theory (Simplified with Diagram)**

## Transformer Architecture

```
        ┌─────────────┐
Input → │   Encoder    │ → Context Vectors
        └──────┬──────┘
               │
               ▼
        ┌─────────────┐
        │   Decoder    │ → Generated Text
        └─────────────┘
```

### GPT-style LLMs

```
Only Decoder Block
```

### How Self-Attention Works

```
Token → Vector  
Vectors → Similarity Scores  
Scores → Weighted Representation  
```

---

# 🔍 **Semantic Book Recommendation Pipeline**

## 🧩 Diagram

```
┌──────────────────────────┐
│ taggedDescription.txt     │
└───────────┬──────────────┘
            │
            ▼
  LangChain TextReader
            │
            ▼
CharacterTextSplitter
            │
            ▼
  OpenAI Embeddings
            │
            ▼
 Chroma Vector DB
            │
            ▼
User Query → Embedding
            │
            ▼
Similarity Search → Recommended Books
```

---

# 🗂️ **Category Classification using HuggingFace**

## Diagram

```
Raw Categories
       │
       ▼
 Top-K Categories
       │
       ▼
 Zero-Shot Classifier (HF Model)
       │
       ├──────────► Fiction
       │
       └──────────► Non-Fiction
```

Accuracy is measured between:

* Predicted labels
* Actual dataset labels

Remaining categories (n–top–k) → classified & saved to CSV.

---

# 🎭 **Emotion Detection on Descriptions**

## Diagram

```
Long Description
       │
       ▼
Split into Chunks
       │
       ▼
Emotion Classifier (HF)
       │
       ▼
Emotion % per Chunk
       │
       ▼
Compute Mean Emotion
       │
       ▼
Append to Books CSV
```

---

# 🖥️ **Gradio Dashboard**

Gradio is used to create:

* Search bar
* Dropdown menus
* Display book metadata
* Show emotion categories
* Interactive recommendation UI

---

# 🚀 **Run Locally**

```bash
git clone https://github.com/Ranjith-singh/BookSenseAI.git
```

Run the dashboard:

```bash
python GradioBasedDashboard.py
```
