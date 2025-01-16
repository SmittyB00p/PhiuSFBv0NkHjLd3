# Potential Talents Overview

As a talent sourcing and management company, the goal is to identify and match talented individuals to technology companies. However, this task is challenging due to several factors:

1.) Understanding the Role: Accurately grasping the client’s needs and the requirements of the role.
2.) Identifying Candidate Qualities: Knowing what makes a candidate a good fit for the specific role.
3.) Locating Talent: Finding skilled individuals in the right places.

Currently, this process involves significant manual effort. Such as determining how fit a candidate is to a given role after a pre-ranking has been done and then re-ranking that list. The aim is to streamline the process by developing an automated system that saves time and improves candidate matching. Specifically, to build a machine learning-powered pipeline that:

1.) Identifies and ranks candidates based on their suitability for a given role.
2.) Utilizes role-specific keywords (e.g., "full-stack software engineer", "aspiring human resources", etc.) to guide the search process.

### Objectives

* Given a job title description, predict how 'fit' a candidate is for that job title, via a robust ranking algorithm.

### Challenges

* Is there a way to filter out candidates which in the first place should not be in the list?
* Is there a way to determine a cut-off point that would work for other roles without losing high potential candidates?

## About the Dataset
This dataset is comprised of a candidates unique index number, their job title, their location, number of connections they have, and a fit column that will be used to rank the candidate on how well their job title corresponds to the job title that the hiring personel are looking for.

## Exploratory Data Analysis
The eda.ipynb is comprised of two main sections:
* an exploratory look at the main three feature in the dataset - (job_title, connection, and location)
* techniques to use for representing the job titles via pre-trained word/sentence embeddings

Looking at the dataset in the first section of the notebook there are: 
* 52 unique job_titles in the dataset
* 41 different locations (because of the way that people have specified their location, there might be less uniqueness)
* over 40% of the candidates who have more than 500 connections

When looking at how to represent job titles via vector embeddings in the second section there were multiple techniques used:
* Tf-IDF (Term Frequency - Inverse Document Frequency)
* Word2Vec
* FastText
* GloVe
* BERT

Below, the word cloud represents the number of unique words in the job_title feature of this dataset. The larger the word is in the cloud the more times it shows up in candidates' job titles.

Certain stop words have been omitted from the job_title feature, such as numbers, articles such as 'a', 'an', and 'the', as well as some prepositions such as 'with' and 'without'.

![Word Cloud for visual purposes](https://github.com/SmittyB00p/PhiuSFBv0NkHjLd3/blob/af81b4cb19cc44a705e55f19e703cebe82ff1b2a/word-cloud.jpeg)

After looking at unique words in the job_title feature and doing feature engineering to strip the high frequency but low importance words and experimenting with different word/sentence embedding techniques, the BERT embeddings seemed to be the best way to capture most of the similarity/disimilarity of the job titles. 

- If you want, at the bottom of the eda.ipynb there is a heatmap of both the BERT and FastText cosine similarity scores that shows the difference in their representations.

## Modeling

The models.ipynb notebook is comprised of three main sections. The first two implementing different learning-to-rank algorithms. 
* RankNet (using PyTorch)
* LambdaRank (using LGBM and XGBoost)
* Prompt Engineering (using Phi3)

-- Note --
The two notebooks below require extra memory and a GPU. I was not able to run either of them more than once.

The RAG.ipynb notebook is used for implementing Retrieval-Augmented Generation via the small language model (SLM) Phi-3.

The Google Colab notebook is used for fine-tuning the Phi-3 model. Because of hardware issues (memory and GPU) it was the optimal way to fine-tune.

## Conclusion

In conclusion, the best way to implement a robust ranking algorithm is with the XGBRanker model

## Setup

Make sure to use Python --version 3.9.13. 

Then make sure to read in the requirements.txt file by running pip install -r 'requirements.txt' in the terminal
OR
if using the notebook setup you can run %pip install -r 'requirements.txt'