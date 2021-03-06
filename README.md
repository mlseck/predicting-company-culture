# 7CCSMDPJ
# Predicting company culture from job postings content

This repo contains all datasets, python notebooks and models used to prepare the project report submitted previously

## Installation
No prior installation required. All code is provided in Notebooks prepared with Google Colab.

## Content
### Notebooks
#### Script A: Review Collection Script
*This notebook contains the script used to collect reviews from the Glassdoor job posting site. We use the python library Selenium to carry out the scraping. Note that this notebook's code was heavily inspired by the script written by Maria Vasilenko for Glassdoor scraping, published on Medium. However, this inspiration only appears in the structure of the code. The content of the code was written from scratch to serve our own scraping goals.*

---
*References: https://mashavasilenko.medium.com/scrape-your-way-to-thousands-of-interview-reviews-f6dba8063539*

#### Script B: Multi-label Text Classification with BERT and PyTorch Lightning, finetuned on GoEmotions
*This notebook contains the script used to build our first multi-label classification model, which recognizes emotions from reviews collected in Script A. In it, we build a BERTBase model using the PyTorch Lightning library. Note that this notebook's code was written following a tutorial on multi-label text classification for detection of toxic tweets published by Venelin Valkov. However, the content of the code was written to serve our own model goals.*

---
*References: https://curiousily.com/posts/multi-label-text-classification-with-bert-and-pytorch-lightning/*

#### Script C: Linking Postings to Recognized Emotions
*This script links emotions recognized in reviews made about companies, to job postings that were made by the same company within the same time range. Here, we pick time ranges of six months because companies tend to hold semi-annual reviews. At the end of this script, we get the top three emotions for each company and time range and drop all information related to the company and the time range. This results in the dataset that will be used to train our multi-label classification model in Script C*

#### Script D: Multi-label Text Classification Model based on BERT with CNN Classification layer. Trained on Posting Emotions Dataset
*This notebook contains the script used to build our main multi-label classification model, which recognizes emotions from job postings. In it, we build a BERTBase model with a CNN classification layer. Note that this notebook's code was written following a tutorial on multi-label text classification for tagging questions posted on Q&A sites such as Stack Overfllo. However, the content of the code was written to serve our own model goals.*

---
*References: https://github.com/Moradnejad/Bert-Based-Tag-Recommendation*

#### Script E: Job Posting Collection
*This notebook contains the script used to collect job postings from Glassdoor. This scraper was built upon an open-source Glassdoor job postings scraper posted on Github. This script makes a call to the open-source API for each company in our company list, and collects at least 100 job postings for them. The final output of this script is the Glassdoor Job Postings dataset.*

---
*References: https://github.com/kelvinxuande/glassdoor-scraper*

### Datasets
- reviews.csv : Collection of company reviews scraped from Glassdoor via Script A
- company_list.csv : Collection of companies with tech roles scraped from Glassdoor via Script A
- postings.csv : Collection of job postings from companies in company_list.csv, scraped from Glassdoor via Script E
- review_sentiments.csv : Collection of emotions recognized from reviews in reviews.csv, generated by Script B
- posting_sentiments.csv : Collection of job postings in postings.csv merged with emotions recognized from reviews in review_sentiments.csv, generated by Script C
- top_sentiments.csv : Collection of job listings along with the top 3 sentiments they are linked to, generated by Script C

### Models
- Emotion Recognition model: due to the size of the model, we are making it accessible via Google Drive using this link https://drive.google.com/file/d/1iupXk8hUeP3iEjn9_DtCdstw-ocb86D9/view?usp=sharing
- Text Tagging model: due to the size of the model, we are making it accessible via Google Drive using this link https://drive.google.com/drive/folders/1wYc79ozGEamaqA-LpEXMeYfVv2AdHrb9?usp=sharing
