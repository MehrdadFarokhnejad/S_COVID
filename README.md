
# S_COVID

## A Search Engine to Explore COVID-19 Scientific Literature. Do you want to easily find related COVID-19 articles? Do you want to find important sentnces regarding your query in the papers? Do you have a specific research question and want to discover relevant articles? S_COVID can help you with all of your queries

**Approach**:
We, as a multi-disciplinary research group (three program developers, a biologist, and a physician), conducted lots of surveys on the Coronavirus-related family on Kaggle provided articles. We designed an efficient search engine, to find the most related answers to questions of the Kaggle’s competition. Our biologist and physician members use questions of the competition to evaluate and score our search engine.
As a final survey, we compare our results by another models on this competition to fix our possible errors. fortunately, we are happy to announce that our results were meaningfully much more accurate compare to similar search engines. 
___

**WORD2VEC-**
* For each of the paper present, we used three column of the dataset- Title, Abstract and Body text and combined them to form a ‘complete text’  containing all the text present in each of the paper.
*Then we performed pre-processing on the ‘complete text’.  We used scispaCy,  a Python package containing spaCy models for processing biomedical, scientific or clinical text. We removed the stop words and perform word lemmatization on the text data. We also removed some common unnecessary words such as author, figure, copyrights, license, fig. Etc from the  ‘complete text’. 
* We used ‘Gensim’ Python library to train our word2vec model on the  ‘complete text’ for each of the paper present in the dataset. We then save the word2vec model for the future uses.
---
**LDA TOPIC MODELING and FINDING ANSWERS TO THE QUERY-**

* We trained a LDA(Latent Dirichlet Allocation) model for topic modeling on the given dataset. In topic modeling each topic is a distribution over words and each document/paper is a mixture of topics  We discovered 50 as optimum number of topics.
*Each paper was assigned a set of topic that is, Each paper is a mixture of topics / a distribution. We have a LDA space, a simplex. The dimensionality of the space depends on the number of topics. .I.e. 50. Each paper is close to the most strong topics that represent it.  
* We then used Jensen-Shannon distance to measure the similarity between two probability distribution.
* Now, for the given query we used the Jensen-Shannon distance between the user query and the papers present in the topic space to find the top  relevant paper which is closest to the user query and might contain the answer to the query. As a similarity measure we use 1 - Jensen-Shannon distance. Higher the similarity score more close the paper is to the query.
* We then convert each paper into a set of sentences. We combine all the sentences in a list that is generated from the relevant papers. Using our word2vec model to generate a vector representation of each sentence. 
* We also form a query vector from the user query. Finally using Cosin similarity score, out of all the generated sentences from the  relevant papers, based on the similarity sore we take top sentences as the most probable answer to the query.
* We then group the sentences based on the paper they belong to. We take maximum of top 10 best sentence for each paper and present it to the user. 

___

**Features**
* Select a **time range** to limit the articles that are considered (you can decide if you want to find the latest publications or search for insights in past research)
* Option to only suggest **COVID-19-papers** (those that contain COVID-19, SARS-CoV-2, 2019-nCov, SARS Coronavirus 2 or 2019 Novel Coronavirus in the text body)


**Pros**:
* Doesn't only use the title or meta-data, but the actual content (text body) of the articles 
* Once trained, the model is easy and fast to apply
* Helps to discover latent relationships between articles that might drive innovation
* Finding related sentences to the questions in articles.

**Cons**:
* Unsupervised learning of topics is hard to verify

---
**Quickstart possible**: You don't have to train the model yourself, you can simply load it from below link!

- Data -  [A Neural Probabilistic Language Model(2003)](http://www.jmlr.org/papers/volume3/bengio03a/bengio03a.pdf)
- Colab - [main_git.ipynb](https://colab.research.google.com/drive/1TYYaqKBsTfZkEuF5Hqvvk5-7aMQ2Ably?usp=sharing)



**Dependencies**

* Python 3.6+

**Author**

* Mehrdadfarokhnejad
* Author Email : Mehrdadfarokhnejad@gmail.com 

