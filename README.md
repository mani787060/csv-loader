# LangChain CSV Document Loader
[![LangChain](https://img.shields.io/badge/Framework-LangChain-green)](https://www.langchain.com/)
[![Python](https://img.shields.io/badge/Python-3.9%2B-blue)](https://www.python.org/)
[![Data Processing](https://img.shields.io/badge/Data-Tabular%20Ingestion-orange)](https://python.langchain.com/docs/modules/data_connection/document_loaders/csv)

## 🏗️ Project Overview
This repository focuses on **Structured Data Ingestion** for Retrieval-Augmented Generation (RAG) systems. While LLMs excel at unstructured text, enterprises run on tabular data. This project demonstrates how to use LangChain's **`CSVLoader`** to parse Comma-Separated Values, converting discrete rows of data into rich, semantic `Document` objects that an AI can query, summarize, and analyze.

---

## 🛠️ Key Technical Implementations

### 1. Row-to-Document Transformation
* **`CSVLoader` Integration:** Automatically parsing `.csv` files so that each row becomes a standalone piece of context. The loader neatly formats the columns into key-value pairs within the `page_content`.
* **Delimiter & Encoding Management:** Handling real-world messy data by configuring `csv_args` to support custom delimiters (like tabs or semicolons) and specific text encodings.

### 2. Strategic Metadata Mapping
* **Source Column Designation:** By default, every row points to the CSV file as its source. This project demonstrates using the `source_column` argument to map a specific unique identifier (like a "Transaction ID" or "User ID") as the document's source.
* **Granular Traceability:** Ensuring that when the LLM answers a question based on a specific row, the downstream application can trace the answer back to the exact primary key in the original database.

### 3. Pipeline Readiness
* **Structured Context:** Preparing tabular data to be embedded into a vector database, allowing for semantic searches over traditionally rigid datasets (e.g., finding "high-risk behavior" in a transaction log without writing complex SQL).

---

## 💻 Tech Stack
* **Language:** Python 3.9+
* **Framework:** LangChain Community (`langchain-community`)
* **Environment:** `python-dotenv`

---

## 🚀 Getting Started

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/your-username/langchain-csv-loader-tabular-data.git](https://github.com/your-username/langchain-csv-loader-tabular-data.git)


2. **Install Dependencies:**
   ```bash
   pip install -U langchain-community python-dotenv

3. **Add a Sample CSV:**

   Place a sample dataset (e.g., dataset.csv) in the root directory.

5. **Run the Implementation:**
   ```bash
   python csv_loader.py   
