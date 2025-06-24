
# Fungal Metabolite Bioactivity Prediction

## Overview

This project implements a machine learning pipeline for predicting the bioactivity of fungal metabolites using multi-modal data. It integrates features derived from fungal biosynthetic gene clusters (BGCs) and mass spectrometry (MS) data to classify metabolites into bioactivity categories such as antibacterial, antifungal, or inactive. The goal is to simulate a computational approach for natural product drug discovery, where machine learning models help prioritize compounds for experimental testing.

The codebase also provides an example of how agentic workflows (using LangChain) can be incorporated to support literature mining and data enrichment, assisting in hypothesis generation and experiment planning.

## Features

- Dual-input neural network model implemented in TensorFlow combining BGC domain features and binned mass spectra features
- Custom data generator for efficient loading and batching of large datasets
- Training pipeline with early stopping, learning rate scheduling, and validation monitoring
- Evaluation using classification reports and confusion matrix visualization
- Example agent workflow using LangChain for retrieval-augmented literature mining

## Data

The project simulates a dataset to demonstrate the architecture:
- BGC features: integer counts of biosynthetic domains (e.g., PKS, NRPS)
- MS features: normalized intensity values across binned m/z ranges
- Labels: bioactivity classes (antibacterial, antifungal, inactive)

In a real-world application, these features would be derived from public and proprietary sources such as MIBiG for gene clusters and GNPS for mass spectra.

## Model Architecture

The model is composed of:
- A BGC input branch: fully connected layers processing domain count features
- An MS input branch: fully connected layers processing mass spectral features
- A merged layer: concatenation of both branches followed by dense layers and a softmax classifier

The architecture is modular, allowing easy replacement or extension of individual branches.

## How to Use

1. Install required libraries:
   ```
   pip install tensorflow scikit-learn seaborn matplotlib langchain faiss-cpu sentence-transformers
   ```

2. Run the Python script to:
   - Generate synthetic data
   - Build and train the model
   - Evaluate model performance
   - Visualize results

3. (Optional) Use the LangChain agent example to experiment with text-based data mining for fungal literature.

## Example Experiment Plan

- Baseline: train the dual-input model on simulated data and evaluate accuracy and confusion matrix
- Architecture tuning: explore dropout, batch normalization, or different layer sizes
- Modal fusion strategies: test concatenation vs. attention-based merging
- External validation: simulate external data to test generalization

## Extensions

Possible extensions to improve and adapt the project:
- Replace synthetic data with real MIBiG and GNPS datasets
- Incorporate additional features such as molecular descriptors or docking scores
- Implement multi-task learning to predict multiple properties simultaneously
- Build more advanced agent workflows to automate data integration and prioritization

## Purpose

This project is designed to demonstrate practical skills in:
- Building, fine-tuning, and evaluating machine learning models in TensorFlow
- Designing scalable pipelines for multi-modal biological data
- Integrating AI agent frameworks for data enrichment and hypothesis support
- Planning computational experiments relevant to bioactive small molecule discovery
