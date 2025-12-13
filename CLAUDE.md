# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a machine learning study repository following the "파이썬 머신러닝 완벽 가이드" (Python Machine Learning Perfect Guide) book. The repository contains Jupyter notebooks covering various ML topics from basic concepts to advanced techniques like ensemble learning, NLP, and recommender systems.

## Development Environment

- Python 3.9.6
- Virtual environment: `.venv/` (activated via `source .venv/bin/activate`)
- Primary tools: Jupyter notebooks for interactive ML experimentation
- Data science stack: scikit-learn, pandas, numpy, matplotlib

## Running Code

### Start Jupyter
```bash
source .venv/bin/activate
jupyter notebook
```

### Execute Notebooks
All notebooks are in the `perfect_guide/` directory organized by chapter number. Open and run them interactively in Jupyter.

## Repository Structure

### Root Level Notebooks
- `K-Nearst Neighbors.ipynb` - KNN algorithm implementation
- `Linear Regression.ipynb` - Linear regression examples
- `Unsuperviesd Learning.ipynb` - Clustering (KMeans) and dimensionality reduction (PCA)
- `test01.ipynb` - Experimental/scratch work

### perfect_guide/ - Book Chapter Exercises

Organized by chapter (1장-9장), each containing topic-specific notebooks:

**Chapter 2 (2장)**: Scikit-learn fundamentals
- Iris dataset classification example
- Model selection and cross-validation
- Data preprocessing techniques
- Titanic survival prediction

**Chapter 3 (3장)**: Evaluation metrics
- Accuracy, Precision, Recall, F1-Score, ROC-AUC
- Pima Indians diabetes prediction

**Chapter 4 (4장)**: Decision trees and ensemble methods
- Decision trees, Random Forest, GBM
- XGBoost and LightGBM implementations
- Bayesian hyperparameter optimization
- Stacking ensemble models
- Real-world applications: credit card fraud detection, customer satisfaction prediction

**Chapter 5 (5장)**: Regression
- Gradient descent implementation

**Chapter 6 (6장)**: Dimensionality reduction
- PCA (Principal Component Analysis)
- LDA (Linear Discriminant Analysis)

**Chapter 8 (8장)**: Natural Language Processing
- Text preprocessing and normalization
- Bag of Words (BOW) feature extraction
- Text classification (20 Newsgroups dataset)
- Sentiment analysis
- Topic modeling (LDA)
- Document clustering (Opinion Review dataset)

**Chapter 9 (9장)**: Recommender systems
- Content-based filtering (TMDB 5000 Movie Dataset)
- Uses cosine similarity and weighted voting for movie recommendations

### Data Directories

- `perfect_guide/4장/human_activity/` - Human activity recognition dataset
- `perfect_guide/9장/ml-latest-small/` - MovieLens dataset
- `bike-sharing-demand/` - Kaggle bike sharing dataset
- External datasets downloaded via kagglehub when needed

## Architecture Patterns

### Typical ML Workflow in Notebooks

1. **Data Loading**: Use pandas to read CSV files or kagglehub for Kaggle datasets
2. **Preprocessing**:
   - Handle missing values
   - Feature engineering (log transforms, outlier removal)
   - Text data: tokenization, vectorization (CountVectorizer, TfidfVectorizer)
3. **Train/Test Split**: `train_test_split` from sklearn.model_selection
4. **Model Training**: Fit various models (DecisionTree, RandomForest, GBM, XGBoost, LightGBM)
5. **Evaluation**: Multiple metrics (accuracy, precision, recall, F1, ROC-AUC)
6. **Hyperparameter Tuning**: GridSearchCV or Bayesian optimization
7. **Visualization**: matplotlib for plots, seaborn for statistical visualizations

### Content-Based Filtering Pattern (Chapter 9)

Uses weighted rating formula to balance popularity and quality:
```
WR = (v/(v+m)) * R + (m/(v+m)) * C
```
Where:
- R = movie's average rating
- v = vote count for the movie
- m = minimum votes required (typically 60th percentile)
- C = mean vote across all movies

Combines genre similarity (cosine similarity on CountVectorized genres) with weighted ratings to recommend similar high-quality content.

### Ensemble Stacking Pattern (Chapter 4)

Multi-level stacking approach:
- Level 1: Multiple base models (KNN, RandomForest, DecisionTree, AdaBoost)
- Level 2: Meta-model (LogisticRegression) trained on base model predictions
- Uses cross-validation to generate out-of-fold predictions for training the meta-model

### Text Processing Pattern (Chapter 8)

Standard NLP pipeline:
1. Text cleaning and normalization
2. Feature extraction using CountVectorizer or TfidfVectorizer
3. Classification using scikit-learn models
4. Topic modeling using LDA (LatentDirichletAllocation)
5. Clustering using KMeans on TF-IDF vectors

## Common Datasets

- **Iris**: Classic classification (sklearn.datasets)
- **Titanic**: Binary classification with feature engineering
- **Diabetes**: Binary classification with class imbalance
- **Human Activity**: Time-series classification from sensor data
- **Credit Card Fraud**: Highly imbalanced dataset, uses SMOTE
- **20 Newsgroups**: Text classification
- **IMDB Reviews**: Sentiment analysis
- **TMDB Movies**: Recommender systems

## Git Workflow

Recent commits use emoji prefixes:
- `:sparkles:` - New feature/topic implementation
- `:recycle:` - Refactoring

Branch: `develop` (main development branch)