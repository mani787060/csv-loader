# LangChain CSV Loader | Structured Data Ingestion

A practical implementation of **LangChain's CSVLoader** for loading structured tabular data and converting CSV rows into LangChain Document objects.

This project demonstrates how CSV datasets can be ingested into a LangChain application, making structured information easier to prepare for downstream workflows such as Retrieval-Augmented Generation (RAG).

## Project Overview

CSV files are commonly used to store structured information in rows and columns. However, when building LLM-powered applications, this information often needs to be converted into a format that LangChain can process.

LangChain provides `CSVLoader` to handle this transformation.

In this project, the `Social_Network_Ads.csv` dataset is loaded using `CSVLoader`. The loader converts individual CSV records into LangChain Document objects containing textual content and metadata.

## Project Objectives

- Understand how LangChain Document Loaders work.
- Load structured CSV data using `CSVLoader`.
- Convert CSV records into LangChain Document objects.
- Explore the `page_content` and metadata of loaded documents.
- Understand how structured data ingestion fits into a RAG pipeline.

## How CSVLoader Works

`CSVLoader` is a document loader available through the `langchain-community` package.

It reads a CSV file and converts its rows into individual Document objects.

Each Document generally contains two important components:

### 1. page_content

Contains the textual representation of a CSV row.

For example, a record containing:

```text
Age: 35
EstimatedSalary: 20000
Purchased: 0
```

is represented as textual content that can be processed by downstream LangChain components.

### 2. metadata

Contains additional information associated with the document, such as its source file.

Metadata helps identify where a particular document originated and supports traceability in document-processing workflows.

## Project Implementation

The current implementation follows these steps:

### Step 1: Import CSVLoader

Import `CSVLoader` from LangChain Community:

```python
from langchain_community.document_loaders import CSVLoader
```

### Step 2: Initialize the Loader

Specify the CSV file that needs to be loaded:

```python
loader = CSVLoader(file_path="Social_Network_Ads.csv")
```

### Step 3: Load the CSV File

Use the `load()` method to read the CSV file and create Document objects:

```python
docs = loader.load()
```

### Step 4: Inspect the Loaded Documents

Check how many documents were created and inspect an individual document:

```python
print(len(docs))
print(docs[1])
```

This helps understand how CSV records are represented inside LangChain.

## Dataset

This project uses the `Social_Network_Ads.csv` dataset.

The dataset contains information related to social network advertising and customer purchasing behaviour.

| Column | Description |
|---|---|
| `Age` | Age of the customer |
| `EstimatedSalary` | Estimated salary of the customer |
| `Purchased` | Indicates whether the customer purchased the product |

The dataset is used here to demonstrate structured CSV ingestion, not to train a machine learning model.

## Technologies Used

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| LangChain Community | CSV document loading |
| CSVLoader | Converting CSV rows into Document objects |
| Pandas / NumPy | Not required by the current implementation |

## Repository Structure

```text
csv-loader/
│
├── csv_loader.py
├── Social_Network_Ads.csv
└── README.md
```

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/mani787060/csv-loader.git
```

### 2. Navigate to the Project Directory

```bash
cd csv-loader
```

### 3. Create a Virtual Environment (Recommended)

```bash
python -m venv .venv
```

Activate it on Windows:

```bash
.venv\Scripts\activate
```

Activate it on macOS/Linux:

```bash
source .venv/bin/activate
```

### 4. Install Dependencies

Install LangChain Community:

```bash
pip install -U langchain-community
```

### 5. Run the Python File

```bash
python csv_loader.py
```

The program loads `Social_Network_Ads.csv`, creates LangChain Document objects, prints the total number of documents, and displays the second document.

## Understanding the Role of CSVLoader in RAG

CSVLoader can be used as an initial data-ingestion component in a RAG workflow.

A typical workflow looks like this:

```text
CSV Dataset
     |
     v
CSVLoader
     |
     v
LangChain Documents
     |
     v
Text Processing / Chunking
     |
     v
Embeddings
     |
     v
Vector Database
     |
     v
Retriever
     |
     v
LLM
     |
     v
Generated Response
```

This project focuses on the **CSV ingestion and Document creation stage**. It does not currently implement embeddings, vector storage, retrieval, or an LLM-powered question-answering system.

## Key Learning Outcomes

By completing this project, you can understand:

- How to use LangChain document loaders.
- How CSVLoader reads structured tabular data.
- How CSV rows are converted into Document objects.
- The difference between `page_content` and metadata.
- How document ingestion contributes to RAG applications.

## Future Improvements

The current implementation provides a basic introduction to CSV ingestion. It can be extended with:

- Custom delimiters and encoding using `csv_args`.
- Custom metadata mapping using `source_column`.
- Loading CSV files from different directories.
- Handling larger CSV datasets.
- Splitting and embedding loaded documents.
- Integrating a vector database for semantic retrieval.
- Building a complete CSV-based RAG application.

---

If you find this project useful, consider giving the repository a ⭐ on GitHub.
