# Multilingual RAG Retrieval and Evaluation

## Project Overview

This project implements a multilingual Retrieval-Augmented Generation (RAG) pipeline for retrieving information from an English document using queries in multiple languages.

The system extracts content from a PDF document, creates section-based chunks, generates multilingual embeddings, and retrieves relevant information using semantic similarity. It also includes a multilingual evaluation framework for assessing generated answers and their factual support against retrieved evidence.

The project demonstrates queries and evaluation in Hindi, Marathi, and Marwari.

## Key Features

- PDF document processing and text extraction.
- Text cleaning and section-based document chunking.
- Multilingual semantic embeddings using LaBSE.
- Query conversion to English for retrieval.
- Multilingual query support.
- Semantic retrieval using cosine similarity.
- Context-grounded answer generation.
- Multilingual evaluation of answer quality and factual support.
- Support for numerical facts and numerical ranges across languages.

## How the System Works

The pipeline follows this process:

**Multilingual User Query → Query Conversion → Multilingual Semantic Retrieval → Retrieved Context → Grounded Answer → Multilingual Evaluation**

### 1. Document Processing

The system uses `pypdf` to extract text from a PDF document. The extracted text is cleaned and organized into section-based chunks.

Each chunk stores information such as:

- Chunk ID
- Page number
- Section heading
- Text content

### 2. Multilingual Embeddings

The project uses the following embedding model:

`sentence-transformers/LaBSE`

LaBSE converts document chunks and queries into multilingual vector representations. The embeddings are normalized and compared using cosine similarity for semantic retrieval.

### 3. Query Conversion

The project loads the NLLB translation model:

`facebook/nllb-200-distilled-600M`

Multilingual queries can be converted to English to support retrieval from the English source document.

### 4. Context Retrieval

The system retrieves the most relevant document chunks based on semantic similarity.

The retrieved results include:

- Chunk ID
- Section heading
- Retrieval score
- Retrieved context

### 5. Multilingual Evaluation

The project includes custom evaluation functions for analysing generated answers across languages.

The evaluation considers:

- Semantic similarity
- Factual agreement
- Numerical fact matching
- Numerical range matching
- Atomic fact coverage
- Text similarity
- Evidence alignment
- Answer completeness

The project also includes custom evaluation approaches inspired by:

- FactCC-style factual consistency
- SummaC-style claim and evidence comparison
- QAGS-style factual agreement
- DAE-style evidence support
- BLEURT-style answer similarity

## Supported Languages Demonstrated

The notebook includes examples using:

- English
- Hindi
- Marathi
- Marwari

## Technologies Used

- Python
- PyPDF
- Sentence Transformers
- Hugging Face Transformers
- PyTorch
- NumPy
- Pandas
- scikit-learn
- Google Colab

## Models Used

### Multilingual Embedding Model

`sentence-transformers/LaBSE`

Used to generate multilingual embeddings for document chunks and semantic similarity calculations.

### Translation Model

`facebook/nllb-200-distilled-600M`

Used for multilingual query conversion to English.

## Evaluation Approach

The evaluation framework combines multiple signals rather than relying only on exact text matching.

### Multilingual Semantic Score

Measures semantic similarity between multilingual text using LaBSE embeddings and cosine similarity.

### Multilingual Fact Matching

Compares factual information, including numerical values and numerical ranges.

### Answer Similarity

Combines:

- Semantic similarity
- Factual similarity
- Atomic fact coverage
- Normalized text similarity

### Evidence Support

Measures how well a generated answer is supported by the retrieved context using factual and semantic evidence.

### Completeness

Measures expected fact coverage, semantic coverage, and evidence alignment.

## Project Workflow

```text
PDF Document
     ↓
Text Extraction and Cleaning
     ↓
Section-Based Chunking
     ↓
LaBSE Multilingual Embeddings
     ↓
Multilingual User Query
     ↓
Query Conversion to English
     ↓
Semantic Retrieval
     ↓
Retrieved Evidence
     ↓
Grounded Answer
     ↓
Multilingual Evaluation
```

## Installation

Install the required libraries:

```bash
pip install pypdf sentence-transformers transformers accelerate scikit-learn sentencepiece
```

## Running the Project

1. Upload the source PDF document to Google Colab.
2. Run the text extraction and cleaning cells.
3. Create section-based document chunks.
4. Load the LaBSE embedding model.
5. Generate embeddings for the document chunks.
6. Load the NLLB translation model.
7. Submit a multilingual query.
8. Retrieve relevant document chunks.
9. Generate or provide a grounded answer.
10. Run the multilingual evaluation functions.

## Repository Structure

```text
Multilingual-RAG-Retrieval-and-Evaluation/
│
├── Multilingual_RAG_Retrieval_and_Evaluation.ipynb
├── README.md
└── Educational_Loan_Scheme.pdf
```

> Note: The source PDF should only be uploaded if you have permission to share it publicly.

## Author

**Harshita Sharma**  
AI/ML Engineer

GitHub: github.com/harshitasharma891  
LinkedIn: linkedin.com/in/harshita-sharma-b843031b5
