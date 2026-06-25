# Sentiment Analysis using LSTM, BiLSTM, BiRNN, and Attention

## Course Information

**Course:** AI 454 – Natural Language Processing

## Team Members

* Areen Alakaleek
* Huda Shqerat
* Lujain Toma

---

## Project Overview

This project investigates the effectiveness of different recurrent neural network architectures for sentiment classification. The study compares:

* LSTM
* BiLSTM
* BiRNN
* BiLSTM with Attention

The models were trained and evaluated on a sentiment analysis dataset using pre-trained GloVe word embeddings. Performance was measured using accuracy, F1-score, and confusion matrices.

---

## Objectives

* Compare LSTM and BiLSTM architectures.
* Analyze the impact of bidirectional sequence processing.
* Evaluate the effectiveness of attention mechanisms.
* Investigate model complexity versus performance.
* Visualize attention weights and model predictions.

---

## Word Embeddings

Pre-trained embeddings:

* GloVe 6B 100d

Out-of-vocabulary words were handled using a dedicated OOV token with randomly initialized vectors.

---

## Models

### 1. LSTM

A unidirectional Long Short-Term Memory network that processes text from left to right.

Features:

* Memory cells
* Input gate
* Forget gate
* Output gate

---

### 2. BiLSTM

A Bidirectional LSTM that processes text in both forward and backward directions.

Advantages:

* Captures past context
* Captures future context
* Better semantic understanding

---

### 3. BiRNN

A Bidirectional Recurrent Neural Network without gating mechanisms.

Advantages:

* Simpler architecture
* Faster training

Limitations:

* More vulnerable to vanishing gradients
* Less effective at long-term dependency learning

---

### 4. BiLSTM with Attention

Adds an additive attention mechanism on top of BiLSTM hidden states.

Benefits:

* Focuses on important words
* Improves interpretability
* Enhances classification performance

---

## Hyperparameters

| Parameter           | Value |
| ------------------- | ----- |
| Embedding Dimension | 100   |
| Hidden Size         | 128   |
| Dropout             | 0.5   |
| Optimizer           | Adam  |
| Learning Rate       | 0.001 |
| Batch Size          | 32    |
| Epochs              | 10    |

---

## Results

| Model              | Dev Accuracy | Test Accuracy | Macro F1 |
| ------------------ | ------------ | ------------- | -------- |
| LSTM               | 64.66%       | 59.97%        | 0.5478   |
| BiRNN              | 75.95%       | 75.95%        | 0.7571   |
| BiLSTM             | 83.58%       | 82.84%        | 0.8284   |
| BiLSTM + Attention | 84.07%       | 84.75%        | 0.8464   |

---

## Key Findings

### LSTM vs BiLSTM

* BiLSTM significantly outperformed LSTM.
* Bidirectional processing improved sentiment understanding.
* BiLSTM achieved more balanced classification across classes.

### BiRNN vs BiLSTM

* BiLSTM achieved higher accuracy and F1 scores.
* BiRNN trained faster but struggled with long-term dependencies.
* BiRNN showed signs of vanishing gradients.

### Effect of Attention

* Attention further improved performance.
* Better identification of sentiment-bearing words.
* Improved classification of difficult samples.

---

## Attention Visualization

### Correct Prediction

Sentence:

```text
Absolutely loved the food and service!
```

Important attention weights:

* loved
* food
* service

### Incorrect Prediction

Sentence:

```text
Not the worst movie I've ever seen
```

The model incorrectly focused on:

* worst
* seen

while failing to fully capture the negation "Not".

---

## Technologies Used

* Python
* PyTorch
* NumPy
* Pandas
* Matplotlib
* Scikit-learn
* GloVe Embeddings

---

## Project Structure

```text
project/
│
├── data/
├── embeddings/
├── models/
│   ├── lstm.py
│   ├── bilstm.py
│   ├── birnn.py
│   └── bilstm_attention.py
│
├── training/
├── evaluation/
├── visualizations/
├── notebooks/
├── requirements.txt
└── README.md
```

## Conclusion

The experiments demonstrate that bidirectional architectures significantly improve sentiment classification performance. The addition of an attention mechanism provided the best overall results, achieving the highest accuracy and macro F1-score while offering greater interpretability of model decisions.

The best-performing model was **BiLSTM with Attention**, achieving a test accuracy of **84.75%** and a macro F1-score of **0.8464**.
