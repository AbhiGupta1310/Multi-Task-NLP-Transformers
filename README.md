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

1. Takes a list of customer email reviews as input  
2. For each text:
   - Detects sentiment and confidence score
   - Extracts named entities (e.g., customer name)
   - Classifies the topic using zero-shot learning
   - Generates a concise summary
3. Stores all results in a structured Pandas DataFrame

---

## Usage Example
ai = Assistant()

email = [

"""Subject: Issue with Order #1234
Hi, I placed an order last week and it still hasn't arrived. Can you please look into this and let me know what's going on? I've tried tracking it but it says it's still in transit. I've checked my email and didn't see any updates from you guys, so I'm getting a bit worried. Could you please check on the status of my order and let me know when I can expect it to arrive?
My order number is #1234.
Regards, John Rick"""
]

df = ai.organize(email)
print(df)

| index | customer_name | sentiment | sentiment_conf | topic | topic_conf | summary |
|------:|---------------|-----------|----------------|-------|------------|---------|
| 0 | John Rick | NEGATIVE | 0.9987 | complaint | 0.5408 | Subject: Issue with Order #1234. I placed an order last week and it still hasn't arrived. I've tried tracking it but it says it's still in transit. |

