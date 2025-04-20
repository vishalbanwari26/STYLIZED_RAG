# Stylized Retrieval-Augmented Generation (RAG)

This personal project implements a **Retrieval-Augmented Generation (RAG)** pipeline designed for **text style transfer**, with a strong emphasis on modularity, stylistic control, and enhanced retrieval using an ensemble approach.

## 🎯 Project Objective

To generate contextually relevant and stylistically tailored responses by:
- Integrating multiple retrieval strategies.
- Leveraging a powerful instruction-tuned LLM.
- Structuring prompt input with precision.
- Dynamically fetching and parsing relevant web content.

## 🧠 Key Features

- **Ensemble Retriever**: Combines dense and sparse retrieval methods:
  - **Chroma (vector-based)** for semantic similarity.
  - **BM25** for keyword-based relevance.
- **Large Language Model**: Uses [`mistralai/Mistral-7B-Instruct-v0.3`](https://huggingface.co/mistralai/Mistral-7B-Instruct-v0.3) for high-quality, instruction-following generation.
- **Prompt Engineering**: Uses `PromptTemplate` to format retrieved documents for optimal input to the LLM.
- **Web Scraping and Parsing**: Uses `BeautifulSoup` (BS) to fetch and clean online content to populate the retrieval index.

## 🧪 Pipeline Overview

1. **Web Data Collection**: Dynamically scrapes relevant text data using BeautifulSoup.
2. **Index Construction**: Documents are embedded and stored in a Chroma DB, with BM25-based indexing for sparse retrieval.
3. **Query Handling**:
   - Query is passed through both retrievers.
   - Results are merged into a unified context.
4. **Prompt Formatting**:
   - Retrieved documents are inserted into a structured prompt using `PromptTemplate`.
5. **Stylized Generation**:
   - The prompt is passed to `Mistral-7B-Instruct`, which returns a response tailored to the desired writing style.

## 🔧 Technologies Used

- **LLM**: `mistralai/Mistral-7B-Instruct-v0.3`
- **Retrievers**: Chroma (dense), BM25 (sparse)
- **Prompting**: `PromptTemplate` from LangChain
- **Web Scraping**: `BeautifulSoup`
- **Indexing**: FAISS / Chroma
- **Frameworks**: Python, Jupyter Notebook, LangChain, Hugging Face Transformers

## 🚀 How to Use

1. Clone this repo and install dependencies:
   ```bash
   pip install langchain chromadb beautifulsoup4
   ```
2. Run the notebook `STYLIZED_RAG.ipynb`.
3. Input your query and desired style.
4. Review the stylized response generated using retrieved documents.

## 💡 Future Work

- Add multi-style support and presets (e.g., Shakespearean, News, Twitter-style).
- Integrate with a UI for interactive exploration.
- Evaluate generation quality and relevance with metrics like BLEU and ROUGE.

## 📄 License

This project is open-source under the MIT License.
