---
layout: post
title: "Predict sentiment and analysis of Bias in data"
date: 2021-01-14
---

<h2><strong> Goal</strong></h2>
<p>The goal of this project is to predict the sentiment of Wikipedia discussion comments and identify any sources of bias that may exist in the datasets, and to develop testable hypotheses about how these biases might impact the behavior of machine learning models trained on the data extracted from these datasets, when those models are used for research purposes or to power data-driven applications. </p>

<p>The corpus we use for the project is called the Wikipedia Talk corpus, and it consists of three datasets. Each dataset contains thousands of online discussion posts made by Wikipedia editors who were discussing how to write and edit Wikipedia articles. Crowdworkers labelled these posts for three kinds of hostile speech: “toxicity”, “aggression”, and “personal attacks”. Many posts in each dataset were labelled by multiple crowdworkers for each type of hostile speech, to improve accuracy. Google data scientists used these <a href='https://figshare.com/projects/Wikipedia_Talk/16731'>annotated datasets</a> to train machine learning models as part of a project called <a href='https://conversationai.github.io/'>Conversation AI</a>. The models have been used in a variety of software products and made freely accessible to anyone through the Perspective API.</p>

<p>For the purpose of this analysis, we will be focusing on personal attacks dataset </p>

<p>There are currently two distinct types of data included:
   <ol><li> A corpus of all 95 million user and article talk diffs made between 2001–2015 which can be scored by our personal attacks model.</li>
   <li> An annotated dataset of 1m crowd-sourced annotations that cover 100k talk page diffs (with 10 judgements per diff) for personal attacks, aggression, and toxicity.</li></ol>   </p>
   
<h4>Analyze the personal attacks datasets and  answer some of the following questions</h4>
<ul><li>Predict sentiments of personal attack comments using Naive Bayes</li>
    <li>Explore relationships between worker demographics and labeling behavior</li>
    <li>How consistent are labelling behaviors among workers with different demographic profiles? For example, are female-identified labelers more or less likely to label comments as aggressive than male-identified labelers?</li>
    <li>If the labelling behaviors are different, what are some possible causes and consequences of this difference?</li></ul>


<h3>Link to source code in Github</h3> 
<a href= "https://github.com/lakshmi2688/Sentiment-Analysis-and-understand-Bias-in-Data">Source code</a>



