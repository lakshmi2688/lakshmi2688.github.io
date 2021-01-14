---
layout: post
title: "Predict sentiment and analysis of Bias in data"
date: 2021-01-14
---

<h2><strong> Goal</strong></h2>
<p>The goal of this project is to predict the sentiment of Wikipedia discussion comments and identify any sources of bias that may exist in the datasets, and to develop testable hypotheses about how these biases might impact the behavior of machine learning models trained on the data extracted from these datasets, when those models are used for research purposes or to power data-driven applications. </p>

<p>The corpus we use for the project is called the Wikipedia Talk corpus, and it consists of three datasets. Each dataset contains thousands of online discussion posts made by Wikipedia editors who were discussing how to write and edit Wikipedia articles. Crowdworkers labelled these posts for three kinds of hostile speech: “toxicity”, “aggression”, and “personal attacks”. Many posts in each dataset were labelled by multiple crowdworkers for each type of hostile speech, to improve accuracy. Google data scientists used these <a href='https://figshare.com/projects/Wikipedia_Talk/16731'>annotated datasets</a> to train machine learning models as part of a project called <a href='https://conversationai.github.io/'>Conversation AI</a>. The models have been used in a variety of software products and made freely accessible to anyone through the Perspective API.</p>

<p>For the purpose of this analysis, we will be focusing on personal attacks dataset </p>

<p>There are currently two distinct types of data included:</p>
   <ol><li> A corpus of all 95 million user and article talk diffs made between 2001–2015 which can be scored by our personal attacks model.</li>
   <li> An annotated dataset of 1m crowd-sourced annotations that cover 100k talk page diffs (with 10 judgements per diff) for personal attacks, aggression, and toxicity.</li></ol>   

<h4>Analyze the personal attacks datasets and  answer some of the following questions</h4>
<ul><li>Predict sentiments of personal attack comments using Naive Bayes</li>
    <li>Explore relationships between worker demographics and labeling behavior</li>
    <li>How consistent are labelling behaviors among workers with different demographic profiles? For example, are female-identified labelers more or less likely to label comments as aggressive than male-identified labelers?</li>
    <li>If the labelling behaviors are different, what are some possible causes and consequences of this difference?</li></ul>

<h2>License</h2>
<p>All data collected or generated for this project is available under free licenses on <a href='https://figshare.com/projects/Wikipedia_Talk/16731'>Figshare</a>, per <a href='https://meta.wikimedia.org/wiki/Open_access_policy'>open access policy</a>. These datasets are released under a <a href='https://wiki.creativecommons.org/wiki/CC0'>CC0 public domain dedication.</a> If you're using this data in your research, please provide attribution via the recommended citation below. </p>
<h4>Citation</h4>
<p>This dataset can be cited as:
Wulczyn, Ellery; Thain, Nithum; Dixon, Lucas (2016): Wikipedia Detox. figshare. <a href='doi.org/10.6084/m9.figshare.4054689'>doi.org/10.6084/m9.figshare.4054689</a></p>

<h2>Packages Used</h2>

| Module       | Version    |
| :------------- | :----------  | 
|numpy | 1.18.2|
|pandas | 1.0.3|
|seaborn | 0.10.0|


<h2><strong>Links to all relevant API documentation:</strong></h2>

<h4>Due to the large size of the datasets, these datasets can be downloaded from the below links</h4>
<ul><li>https://figshare.com/articles/dataset/Wikipedia_Talk_Labels_Aggression/4267550</li>
<li>https://figshare.com/articles/dataset/Wikipedia_Talk_Labels_Toxicity/4563973</li>
<li>https://figshare.com/articles/dataset/Wikipedia_Talk_Labels_Personal_Attacks/4054689</li>
<li>https://figshare.com/articles/dataset/Wikipedia_Talk_Corpus/4264973</li></ul>

<h4>Other reference links</h4>
<ul><li><a href='https://meta.wikimedia.org/wiki/Research:Detox'>Overview of the research project Research:Detox</a></li>
<li><a href='https://meta.wikimedia.org/wiki/Research:Detox/Data_Release'>Dataset description and schemas</a></li> 
   <li><a href='https://conversationai.github.io/'>Overview of Google’s Conversation AI project</a></li>
   <li><a href='https://arxiv.org/abs/1610.08914'>Research Paper</li></ul>

<h4>Schema for attack_annotations dataset</h4>

| File       | Description    |
| :------------- | :----------  | 
|rev_id | MediaWiki revision id of the edit that added the comment to a talk page (i.e. discussion)|
|worker_id| Anonymized crowd-worker id|
|quoting_attack| Indicator for whether the worker thought the comment is quoting or reporting a personal attack that originated in a different comment|
|recipient_attack| Indicator for whether the worker thought the comment contains a personal attack directed at the recipient of the comment|
|third_party_attack| Indicator for whether the worker thought the comment contains a personal attack directed at a third party|
|other_attack| Indicator for whether the worker thought the comment contains a personal attack but is not quoting attack, a recipient attack or third party attack|
|attack| Indicator for whether the worker thought the comment contains any form of personal attack. The exact question we posed can be found . The annotation takes on value 0 if the worker selected the option "This is not an attack or harassment" and value 1 otherwise|

<h4>Schema for aggression_annotations dataset</h4>

| Columns        | Description    |
| :------------- | :----------  | 
|rev_id| MediaWiki revision id of the edit that added the comment to a talk page (i.e. discussion)|
|worker_id| Anonymized crowd-worker id|
|aggression_score| Categorical variable ranging from very aggressive (-2), to neutral (0), to very friendly (2)|
|aggression| Indicator variable for whether the worker thought the comment has an aggressive tone . The annotation takes on the value 1 if the worker considered the comment aggressive (i.e worker gave an aggression_score less than 0) and value 0 if the worker considered the comment neutral or friendly (i.e worker gave an aggression_score greater or equal to 0). Takes on values in {0, 1}|

<h4>Schema for toxicity_annotations dataset</h4>

| Columns        | Description    |
| :------------- | :----------  | 
|rev_id| MediaWiki revision id of the edit that added the comment to a talk page (i.e. discussion)|
|worker_id| Anonymized crowd-worker id|
|toxicity_score| Categorical variable ranging from very toxic (-2), to neutral (0), to very healthy (2)|
|toxicity| Indicator variable for whether the worker thought the comment is toxic. The annotation takes on the value 1 if the worker considered the comment toxic (i.e worker gave a toxicity_score less than 0) and value 0 if the worker considered the comment neutral or healthy (i.e worker gave a toxicity_score greater or equal to 0). Takes on values in {0, 1}|

<h4>Schema for all demographics datasets</h4>

| Columns        | Description    |
| :------------- | :----------  | 
|  worker_id | Anonymized crowd-worker id.  | 
| gender   | The gender of the crowd-worker. Takes a value in {'male', 'female', and 'other'}. | 
|  english_first_language | Does the crowd-worker describe English as their first language. Takes a value in {0, 1}. | 
| age_group   | The age group of the crowd-worker. Takes on values in {'Under 18', '18-30', '30-45', '45-60', 'Over 60'}. | 
| education | The highest education level obtained by the crowd-worker. Takes on values in {'none', 'some', 'hs', 'bachelors', 'masters', 'doctorate', 'professional'}. Here 'none' means no schooling, some means 'some schooling', 'hs' means high school completion, and the remaining terms indicate completion of the corresponding degree type. | 

<h4>Schema for all comments datasets</h4>

| Columns        | Description    |
| :------------- | :----------  | 
|  rev_id |  MediaWiki revision id of the edit that added the comment to a talk page (i.e. discussion).  | 
| comment   | Comment text. Consists of the concatenation of content added during a revision/edit of a talk page. MediaWiki markup and HTML have been stripped out. To simplify tsv parsing, \n has been mapped to NEWLINE_TOKEN, \t has been mapped to TAB_TOKEN and " has been mapped to ". | 
|  year | The year the comment was posted in | 
| logged_in   | Indicator for whether the user who made the comment was logged in. Takes on values in {0, 1} | 
| ns | Namespace of the discussion page the comment was made in. Takes on values in {user, article}. | 
|  sample | Indicates whether the comment came via random sampling of all comments, or whether it came from random sampling of the 5 comments around a block event for violating WP:npa or WP:HA. Takes on values in {random, blocked}. | 
| split   | For model building in our paper we split comments into train, dev and test sets. Takes on values in {train, dev, test}.| 

<h2><strong>Known issues/considerations</strong></h2>
<p>Impact of Harassment on User Retention uses observational data to study how newcomers behave after being harassed. In the future, the project will be extended to non-newcomers</p> 
<p>More details in the link <a href='https://meta.wikimedia.org/wiki/Research:Detox'>Research:Detox site</a></p>


