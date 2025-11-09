🧬 Molecular Property Prediction — Radius of Gyration (Rg)

This repository contains code and methodology for predicting the Radius of Gyration (Rg) of molecules using multiple molecular representations and deep learning architectures.
The goal is to leverage both graph-based and text-based molecular encodings to learn structural relationships driving polymer conformations.

🚀 Project Overview

We predict the Radius of Gyration (Rg) — a structural descriptor computed using RDKit — by combining multiple feature extraction methods from molecular data:

Graph-based representation: CMPNN (Communicative Message Passing Neural Network)

Text-based representation: ChemBERTa (Transformer trained on SMILES)

Fingerprint-based representation: Morgan Fingerprints

Rule-based features: RDKit Descriptors

These features are integrated and trained using a neural model for property regression.

🧩 Methodology
1️⃣ Data Input

Each molecule is represented by its SMILES string.

Rg values are computed directly from RDKit for supervised training.

2️⃣ Feature Extraction
Feature Type	Method	Description
Graph	CMPNN	Captures molecular graph topology and atomic interactions.
Text	ChemBERTa	Encodes SMILES sequences using transformer embeddings.
Fingerprint	Morgan Fingerprints	Circular substructure-based molecular representation.
Rule-based	RDKit Descriptors	Physicochemical features such as MW, TPSA, HBA/HBD, etc.
3️⃣ Model Training

The extracted features are concatenated into a unified representation.

A neural regression head is trained to predict the Radius of Gyration (Rg).

Loss function: Mean Squared Error (MSE)

Optimizer: Adam

Training with K-Fold cross-validation to ensure robustness.

🧠 Model Architecture
          ┌──────────────────────┐
          │     CMPNN Encoder     │
          │  (Graph Embeddings)   │
          └──────────┬───────────┘
                     │
          ┌──────────▼──────────┐
          │    ChemBERTa Model   │
          │   (SMILES Encoding)  │
          └──────────┬──────────┘
                     │
          ┌──────────▼──────────┐
          │ Morgan Fingerprints  │
          └──────────┬──────────┘
                     │
          ┌──────────▼──────────┐
          │   RDKit Features     │
          └──────────┬──────────┘
                     │
          ┌──────────▼──────────┐
          │  Fully Connected NN  │
          │  → Predicts Rg       │
          └──────────────────────┘
