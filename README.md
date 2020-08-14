# Capstone Project: Multiclass Text Classification of Contract Clauses
by Graham James Lim

Capstone Project Repository for General Assembly's DSI15 Machine Learning Course.

<img src="/images/displacy_sample.png">

## Problem Statement 
In this project, we will take a deep dive into legal corpora in the form of contractual clauses. 

Contracts can be dense, verbose and inaccessible. This is because it is written in legalese, or techno-legal language that people have no choice but to have to make sense of in commerce. This can become very unruly when one has multiple contracts and hundreds of clauses to pour over, not just for lawyers, but for compliance professionals and business stakeholders generally.

Thus, the classification of legal clauses via machine learning can be very useful to trawl through what is often seen as a necessary evil. Are we able to utilize machine learning to classify contract clauses easily? The short answer is yes.

## Web Scraping
Our first task is to scrape enough contract clauses from Lawinsider.com. This is a website that functions like a "wikipedia" of contract clauses, categorized by clause type. To achieve this, I wrote blocks of code using Selenium that would scrape clauses from infinitely scrolling web pages in the parent site.

## EDA
We observed the basic textual characteristics of contracts by analyzing word counts, clause types and top words and bigrams. 

We then explored common conceptual topics in contracts using spaCy, Blackstone, and LDA topic modelling. We found that some contractual clauses, like warranties and support obligations, can overlap. On the other hand, clauses like compliance clauses can be written with enough distinct word vectors that they are unique enough to be topics unto themselves.

We also realized that Bag-of-Words models are still strong enough to classify multiclass text problems, including legal corpora. Our SVC model outperformed every other sklearn-type model at `0.947` accuracy.

## The Limitations of Bag-of-Words vs Dependency Parsing and Sequences
However, we highlighted its drawback as being unnatural and not intuitive in terms of how people actually read documents. In the case of highly correlated word vectors in legal corpora, we underlined the mutual dependency that words have with each other. For this, we utilized displaCy to visualize this relationship through Dependency Parsing.

We concluded the project by exploring a Bi-directional Neural Network Model utilizing Transformers specifically developed for these types of NLP problems called `BERT`, which was even more accurate than the SVC Model at `0.965`, and seems to come very close to what humans do in terms of comprehending words contextually and interdependently.

* Law Insider - source of contract clauses (premium membership required): https://www.lawinsider.com
* BERT explanation: https://towardsdatascience.com/bert-explained-state-of-the-art-language-model-for-nlp-f8b21a9b6270
* BERT visualization: https://github.com/jessevig/bertviz
* spaCy: https://spacy.io
* Blackstone - NLP Legal Project by The Incorporated Council of Law Reporting for England and Wales: 
https://research.iclr.co.uk/blackstone
* Topic Modelling metrics explanation:
https://towardsdatascience.com/evaluate-topic-model-in-python-latent-dirichlet-allocation-lda-7d57484bb5d0
