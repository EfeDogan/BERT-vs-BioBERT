
# 🧬 BERT vs. BioBERT: Biomedical Information Retrieval

This repository contains a Proof of Concept (PoC) / term project designed to evaluate and compare the performance of a general-purpose language model (**Standard BERT**) against a domain-specific model (**BioBERT**) in biomedical information retrieval tasks.

## 📌 Project Objective

Traditional search engines rely on lexical matching (keyword overlap), whereas BERT-based models utilize **semantic search**. However, because standard BERT's vocabulary lacks highly specific medical terminology, it often breaks these terms into meaningless subwords, losing the crucial clinical context.

This project practically demonstrates how a domain-specific model like BioBERT (pre-trained on PubMed and PMC corpora) successfully maps layman's terms or symptomatic descriptions to complex medical jargon, significantly outperforming standard BERT in retrieving the correct medical literature.

## 🚀 Key Features

- **Side-by-Side Comparison:** A Gradio-based interactive web interface allows users to input a query and instantly compare the retrieval results of both models simultaneously.
- **Dense Retrieval:** Both the document corpus and the user queries are dynamically encoded into vector embeddings using the `sentence-transformers` library.
- **Cosine Similarity:** The semantic relevance between the query vector and document vectors is calculated using the Cosine Similarity metric:
  $\text{Cosine Similarity}(A, B) = \frac{A \cdot B}{\|A\| \|B\|}$
- **In-Memory Optimization:** To ensure millisecond response times, the document corpus embeddings are computed only once at startup and stored in memory.

## 📊 Dataset

To test the models' capacity to understand diverse medical jargon, a mini-corpus of **14 abstract excerpts** from the **PubMed** database was created. The corpus spans various medical disciplines, including oncology, endocrinology, toxicology, neurology, and advanced epigenetics.

## 🛠️ Installation and Setup

To run this project on your local machine, follow the steps below:

### 1. Install Dependencies
Ensure you have Python installed, then install the required libraries:

```bash
pip install torch transformers sentence-transformers gradio numpy
```

### 2. Run the Application
Execute the main Python script from your terminal:

```bash
python app.py
```

*Note: Upon the first execution, the models will be downloaded from the Hugging Face Hub, which may take a few moments depending on your internet connection.*

### 3. Access the Web Interface
Once the models are loaded and the server starts, open your web browser and navigate to the local address provided in the terminal (typically `http://127.0.0.1:7860/`).

## 🧪 Sample Queries for Testing

To observe the stark difference in context mapping between the two models, try using the following queries in the interface:

1. *"Treatments for progressive movement disorders characterized by severe shaking and slowness of movement."* (Target: Parkinson's Disease)
2. *"A condition causing extreme continuous thirst and excessive production of highly dilute urine due to hormone issues."* (Target: Central Diabetes Insipidus)
3. *"Acute kidney failure and renal dysfunction requiring hemodialysis after eating poisonous fungi."* (Target: Nephrotoxic Mushroom Poisoning)

## 👨‍💻 Author

**Efe Emirhan Doğan** *Information Retrieval Term Project*
```
