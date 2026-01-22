# 🧠 Multi-Task NLP System using Hugging Face Transformers

This project implements a **multi-task Natural Language Processing (NLP) pipeline** using **Hugging Face Transformers**.  
It performs **Sentiment Analysis**, **Text Summarization**, **Named Entity Recognition (NER)**, and **Topic Classification** on customer text data.

The goal is to demonstrate how multiple pre-trained transformer models can be combined into a single, reusable system.

---

## 🚀 Features

- Sentiment Analysis (Positive / Negative)
- Text Summarization
- Named Entity Recognition (NER)
- Topic Classification using Zero-Shot Learning
- Structured output using a Pandas DataFrame
- Modular and reusable class-based design

---

## 🧠 Models Used

| Task | Pipeline | Model |
|-----|--------|-------|
| Sentiment Analysis | sentiment-analysis | distilbert-base-uncased-finetuned-sst-2-english |
| Summarization | summarization | sshleifer/distilbart-cnn-12-6 |
| Named Entity Recognition | ner | dbmdz/bert-large-cased-finetuned-conll03-english |
| Topic Classification | zero-shot-classification | facebook/bart-large-mnli |

---

## How It Works

1. Takes a list of customer text reviews as input  
2. For each text:
   - Detects sentiment and confidence score
   - Extracts named entities (e.g., customer name)
   - Classifies the topic using zero-shot learning
   - Generates a concise summary
3. Stores all results in a structured Pandas DataFrame

---

## Usage Example
ai = Assistant()

texts = [
    "John really loved the product but delivery was slow.",
    "The service was terrible and I want a refund."
]

df = ai.organize(texts)
print(df)
### Sample Output

|customer_name|	sentiment|	sentiment_conf|	topic|	topic_conf|	summary|
|-----|--------|-------|
|John|	POSITIVE|	0.98|	compliment|	0.87|	John liked the product but delivery was slow|
