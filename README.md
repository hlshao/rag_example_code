# rag_example_code
This repository provides a **ready-to-run Retrieval-Augmented Generation (RAG) example** for Google Colab,  
built with **llama-cpp-python** and a **lightweight quantized LLM** (e.g., TinyLLaMA 1.1B or Qwen 0.5B).  
It does **not** require a Hugging Face token, runs entirely on **free Colab CPU**, and supports **PDF/TXT document upload** for knowledge base construction.

## ✨ Features
- 🚀 **No Hugging Face token required**
- 🧠 **Small models (<1B) + quantization** → lightweight & low resource usage
- 🌏 **Supports both Chinese and English**
- 📄 **Upload PDF / TXT files to build a knowledge base**
- 🔍 **Integrated retrieval + generation**
- 🆓 **Runs on free Google Colab CPU**

---

## 📦 Installation & Usage

### 1. Run on Google Colab
1. Open [Google Colab](https://colab.research.google.com/)
2. Upload `RAG_TinyLLaMA_example.ipynb`
3. Execute each cell in order

### 2. Choose a Model
The default example uses **TinyLLaMA 1.1B Q4_K_M**.  
For better Chinese performance, use:

```python
# Qwen 0.5B Chat (smaller size, better Chinese capability)
!wget -q https://huggingface.co/Qwen/Qwen1.5-0.5B-Chat-GGUF/resolve/main/qwen1_5-0_5b-chat-q4_k_m.gguf -O model.gguf
```
#### Load it with:
```python
from llama_cpp import Llama
llm = Llama(model_path="model.gguf", n_ctx=2048, n_threads=4)
```
### 3. Upload Documents
When prompted, upload .pdf or .txt files.
They will be automatically parsed and stored in a ChromaDB vector database.

### 4. Ask Questions

```python
print(rag_query("Summarize the main points of this document."))
```

## Technical Details
Retrieval: chromadb + default embedding function
Generation: llama-cpp-python inference
Document Parsing: PyMuPDF (PDF) / built-in TXT loader
Quantized Models: GGUF format, Q4_K_M precision (good trade-off between speed & accuracy)

## License
This project is released under the MIT License.
Model usage follows the original model authors’ licenses and terms.

------------
correspondence: Hsuanlei Shao
