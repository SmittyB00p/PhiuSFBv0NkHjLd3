# Potential Talents Overview




## About the Dataset
This dataset is comprised of a candidates unique index number, their job title, their location, number of connections they have, and a fit column that will be used to rank the candidate on how well their job title corresponds to the job title that the hiring personel are looking for.

Below, the word cloud represents the number of unique words in the job_title feature of this dataset. The larger the word is in the cloud the more times it shows up in candidates' job titles.

Certain stop words have been omitted from the feature, such as numbers, articles such as 'a', 'an', and 'the', as well as some prepositions such as 'with' and 'without'.

![Word Cloud for visual purposes](https://github.com/SmittyB00p/PhiuSFBv0NkHjLd3/blob/af81b4cb19cc44a705e55f19e703cebe82ff1b2a/word-cloud.jpeg)


### Objectives




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

In the end, BERT's embeddings seemed to be the best way to capture most of the similarity/disimilarity of the job titles. 

- If you want, at the bottom of the eda.ipynb there is a heatmap of both the BERT and FastText cosine similarity scores that shows the difference in their representations.

## Modeling



## Conclusion


## Setup

Make sure to use Python --version 3.9.13. Then make sure to read in the requirements.txt file by running pip install -r 'requirements.txt'