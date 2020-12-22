---
layout: post
title: "Analysis of COVID impact on US households"
date: 2020-12-14
---

<h3>Abstract</h3> 
<p>The goal of this analysis is to gauge the impact of the pandemic on overall household characteristics such as employment status, housing, education disruptions, and dimensions of physical and mental wellness. There is a large amount of emotionally negative stimuli related to the COVID-19 pandemic. How do people prepare themselves in difficult times like this? Analyzing and exploring people's response to pandemic can provide useful insights into people's perspective about COVID and the challenges they face.</p>

<p>As we all know,the impacts of the pandemic and the economic fallout have been widespread, but are particularly prevalent among Black, Latino, Indigenous, and immigrant households. There is also an impact on gender. This analysis will  deep dive into some of the impacts of covid by Age group, race and ethinicity and gender. We also try to compare the impacts in Washington state versus all other states in terms of certain indicators and understand the different groups of people based on various characteristics pertaining to COVID. The research questions will target specific variables. Below are some references: </p>
<li><a href='https://www.cbpp.org/research/poverty-and-inequality/tracking-the-covid-19-recessions-effects-on-food-housing-and'>Covid Recession effects</a></li>
<li><a href='https://www.cdc.gov/nchs/covid19/pulse/mental-health.htm'>Covid data from NCHS</a></li>

<h3>Data Source</h3>
<p>The <a href='https://www2.census.gov/programs-surveys/demo/technical-documentation/hhp/2020_HPS_Background.pdf'>Household Pulse Survey</a> provides timely data to help understand the experiences of American households during the coronavirus pandemic. Data for this research comes from the Phase 1 Household Pulse Survey that began on April 23 and ended on July 21, 2020 spanning 12 weeks. The dataset is very rich and informative. It dataset has 105 variables, 1088314 observations and includes employment status, food security, housing, physical and mental health, access to health care, and educational disruption. In order to support the nation’s recovery, we need to know the ways this pandemic has affected people’s lives and livelihoods. Data from these datasets will show the widespread effects of the coronavirus pandemic on individuals, families, and communities across the country. </p>

<p>The survey was conducted by an internet questionnaire, with invitations to participate sent by email and text message. Housing units linked to one or more email addresses or cell phone numbers were randomly selected to participate, and one respondent from each housing unit was selected to respond.</p>

<h4> Links to Data set and Data dictionary</h4>
<ul><li>The datasets are available for public use under <a href='https://www.census.gov/programs-surveys/household-pulse-survey/datasets.html'>census.gov</a> website as weekly files.</li>
<li>Data dictionary is available in the census.gov website under the link <a href='https://www.census.gov/programs-surveys/household-pulse-survey/technical-documentation.html#phase1'>Phase 1 Household Pulse Survey Technical Documentation.</a> It has also been added to the repository. Please refer to repository structure for pulse2020_data_dictionary.xlsx</li></ul>

<h4>Download data</h4>
<p>Data is directly downloaded from census website using python modules. Refer to the data_cleaning.ipynb for detailed downloading steps<p>
  
<h4>Terms of use of census data </h4>
<p>The Census Bureau is committed to open government by sharing its public data as open data. Census data continues to be a key national resource, serving as a fuel for entrepreneurship and innovation, scientific discovery, and commercial activity.  We continuously identify and publish datasets and Application Programming Interface’s (API’s) to Data.gov in accordance with the Office of Management and Budget (OMB) Memorandum M-10-06, the Executive Order 13642 on open data, and the overall principles outlined in the Digital Government Strategy.  In
 accordance with the Open Data Policy, M-13-13, the Census Bureau publishes its information in machine-readable formats while also safeguarding privacy and security.</p>


<h3>Research Questions</h3>
<ul>
    <li>Understand the impacts of COVID in terms of employment loss, income loss, food insufficiency, education interruptions, inability to meet housing expenses and how does this vary by Race/Ethnicity or gender? </li>
    <li>What is the impact on Mental health status (Anxiety and depression)? Is there a correlation between Mental health status (Anxiety and depression) and factors such as age, number of household members, gender, income, health status, race? How does the anxiety levels vary between first and last week of survey?</li>
    <li>How does employment loss, income loss, food insufficiency, education interruptions, inability to meet housing expenses in Washington differ as compared  to national average?</li>
    <li>How do different groups based on age, race and ethnicity differ in their behavior or attitude towards COVID. Are there any patterns observed in the population based on certain characteristics pertaining to COVID?</li> 
</ul>

<h3>Methodology</h3>
<ul><li>For <strong>question 1</strong>, Logistic regression has been used as the response indicator variables are binary in nature, all the data points are independent and the sample size is large enough. Also, chi's square test of independence has been used to compare 2 categorical varaibles which is the case here. Overall likelihood ratio test has been used to verify if the full model that includes gender, race/ethnicity tell us more about the outcome (or response) variable than a model that does not include these 2 variables. </li>
   
<p></p>
<li>For <strong>question 2</strong> , ordinal logistic regression has been used because the response variable is categorical and ordered in nature, all the data points are independent and the sample size is large enough. Also, chi's square test of independence has been used to compare 2 categorical variables which is the case here.  We also used Random features feature importance to identify the top 10 features impacting Anxiety/depression.  Overall likelihood ratio test has been used to verify if the full model that includes the predictors in question namely gender, worry, interest, income loss, food insufficiency, Age group, number of household members, income level, health status, race/ethnicity tell us more about Anxiety/depression than a model that does not include these variables. </li>
<p></p>

<p></p>
<li>For <strong>question 3</strong>, Logistic regression has been used as the response indicator variables are binary in nature, all the data points are independent and the sample size is large enough. Also, chi's square test of independence has been used to compare 2 categorical variables which is the case here. Overall likelihood ratio test has been used to verify if the full model that includes state tell us more about the outcome (or response) variable than a model that does not include this variable</li>

<p></p>
<li>For <strong>question 4</strong>, Principal component Analysis and K-means clustering have been used to identify any patterns and classify groups of people based on similar characteristics</li>

<p></p>
<li><strong>Results: </strong>The results will be presented as intepretation of coefficients, significance of hypothesis tests and comprehensive compilation of visualizations.</li></ul>


<h3>Link to source code in Github</h3> 
<a href= "https://github.com/lakshmi2688/COVID_Impact_on_US_Households/tree/master">Source code</a>
