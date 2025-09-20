Semantic Retrieval on Psychology-6k

This project implements a semantic retrieval system using the Psychology-6k dataset.
The pipeline includes:

Light or lemmatized text preprocessing with SpaCy

Embedding generation with thenlper/gte-small (SentenceTransformers)

Semantic similarity ranking with cosine similarity

Evaluation with Mean Reciprocal Rank (MRR)

An interactive Gradio interface to explore questions and compare pipelines

Results: The system achieves high accuracy (≈0.97 MRR with light preprocessing).
