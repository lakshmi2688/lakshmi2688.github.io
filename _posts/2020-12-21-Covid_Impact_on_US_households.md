---
layout: post
title: "COVID Impact on US households"
date: 2020-12-14
---


<h1>Analysis of COVID impact on US households</h1>

<p>Lakshmi Venkatasubramanian </p>
<p>12/14/2020</p>

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

<h3>Repository structure</h3>

```
├── README.md
├── LICENSE
├── assets
│   └── pictures
├── clean_data
│   ├── covid_clean_data.csv
├── data_dictionary
│   ├── pulse2020_data_dictionary.xlsx
├── sample_raw_data
│   └── pulse2020_raw_data.csv
└── src
    ├── analysis.ipynb
    ├── data_cleaning.ipynb
```

| File       | Description    |
| :------------- | :----------  | 
|LICENSE | Code license |
|README.md | This readme |
|assets/pictures/ | Directory containing the various images displayed in the analysis notebook |
|clean_data/covid_clean_data.csv | CSV file containing a cleaned version of covid dataset. This has the data of all the 12 weekly files cleaned up. This file is used as input to analysis.ipynb file |
|data_dictionary/pulse2020_data_dictionary.xlsx | Data dictionary for all 12 weeks of raw data downloaded from the url |
|sample_raw_data/pulse2020_raw_data.csv | Sample data obtained by parsing week 1 survey data from the census url that can be used as the input to data_cleaning.ipynb|
|src/analysis.ipynb | Contains the report and analysis code/visualizations and takes the input covid_clean_data.csv which is the output of data_cleaning.ipynb |
|src/data_cleaning.ipynb| Contains the logic to clean all the 12 weeks of data downloaded directly from the url|

<h3>Research Questions</h3>
<ul>
    <li>Understand the impacts of COVID in terms of employment loss, income loss, food insufficiency, education interruptions, inability to meet housing expenses and how does this vary by Race/Ethnicity or gender? </li>
    <li>What is the impact on Mental health status (Anxiety and depression)? Is there a correlation between Mental health status (Anxiety and depression) and factors such as age, number of household members, gender, income, health status, race? How does the anxiety levels vary between first and last week of survey?</li>
    <li>How does employment loss, income loss, food insufficiency, education interruptions, inability to meet housing expenses in Washington differ as compared  to national average?</li>
    <li>How do different groups based on age, race and ethnicity differ in their behavior or attitude towards COVID. Are there any patterns observed in the population based on certain characteristics pertaining to COVID?</li> 
</ul>


<h3>Methodology</h3>
<ul><li>For <strong>question 1</strong>, Logistic regression has been used as the response indicator variables are binary in nature, all the data points are independent and the sample size is large enough. Also, chi's square test of independence has been used to compare 2 categorical varaibles which is the case here. Overall likelihood ratio test has been used to verify if the full model that includes gender, race/ethnicity tell us more about the outcome (or response) variable than a model that does not include these 2 variables. </li>

<p align="left" width="100%">
    <img width="40%" src="/assets/pictures/CovidImpactByGender.jpg"> 
    <img width="40%" src="/assets/pictures/CovidImpactByRaceEthnicity.jpg"> 
</p>
    
<p></p>
<li>For <strong>question 2</strong> , ordinal logistic regression has been used because the response variable is categorical and ordered in nature, all the data points are independent and the sample size is large enough. Also, chi's square test of independence has been used to compare 2 categorical variables which is the case here.  We also used Random features feature importance to identify the top 10 features impacting Anxiety/depression.  Overall likelihood ratio test has been used to verify if the full model that includes the predictors in question namely gender, worry, interest, income loss, food insufficiency, Age group, number of household members, income level, health status, race/ethnicity tell us more about Anxiety/depression than a model that does not include these variables. </li>
<p></p>

<p align="left" width="100%">
    <img width="60%" src="/assets/pictures/AnxietyByRaceAndGender.jpg"> 
    <img width="60%" src="/assets/pictures/AnxietyByAgeAndIncome.jpg"> 
    <img width="40%" src="/assets/pictures/SelectedMentalIndicators.jpg">
</p>

<p></p>
<li>For <strong>question 3</strong>, Logistic regression has been used as the response indicator variables are binary in nature, all the data points are independent and the sample size is large enough. Also, chi's square test of independence has been used to compare 2 categorical variables which is the case here. Overall likelihood ratio test has been used to verify if the full model that includes state tell us more about the outcome (or response) variable than a model that does not include this variable</li>

<p align="left" width="100%">
    <img width="40%" src="/assets/pictures/CovidImpactByState.jpg"> 
</p>

<p></p>
<li>For <strong>question 4</strong>, Principal component Analysis and K-means clustering have been used to identify any patterns and classify groups of people based on similar characteristics</li>

<p align="left" width="100%">
    <img width="40%" src="/assets/pictures/PCA.jpg"> 
</p>

<p></p>
<li><strong>Results: </strong>The results will be presented as intepretation of coefficients, significance of hypothesis tests and comprehensive compilation of visualizations.</li></ul>

<h3>How to run the notebook</h3>

<li>Install Anaconda</li>
<li>Using a terminal or cmd, navigate to the src folder.</li>
<li>Launch jupyter by running: jupyter notebook</li>
<li>Select the notebook of interest. (Start at data_cleaning.ipynb for the full process or analysis.ipynb for the final report.)</li>

<h3>Schema of the files created</h3>
<p>There is one CSV file extracted and compiled as part of this analysis which is clean_data/covid_clean_data.csv. Below is its schema</p>

| Columns        | Description    | Data type |
| :------------- | :----------  | :----------  |
| WEEK | Wee k of the survey | numeric |
| EGENDER   | The gender of the respondent. Takes a value in {'MALE', 'FEMALE'}. | string| 
| THHLD_NUMPER | The number of members in the household. Takes a value between 1 and 10 |  numeric |
| HLTHSTATUS  | Overall health status of the respondent. Takes on values in {'POOR', 'FAIR', 'EXCELLENT'| string |
| WORRY | Worry level of the respondent. Takes on values in {'NONE','MODERATE','VERY HIGH'} | string |
| INTEREST | Interest level of the respondent. Takes on values in {'NONE','MODERATE','VERY HIGH'} | string |
| RACE_ETHNICITY | Race or Ethnicity of the respondent. Takes on values in {'Hispanic','White alone','Black alone','Asian alone','Other races'} | string |
| EMP_STATUS | Employment status of the respondent. Takes on values in {0,1} | numeric |
| EMPLOSSCOVID | Employment loss due to covid. Takes on values in {0,1} | numeric |
| FOOD_INSUFF | Food insufficiency due to covid. Takes on values in {0,1} | numeric |
| RENT_DEBT | Inability to pay the rent due to covid. Takes on values in {0,1} | numeric |
| RENT_DEBT | Inability to pay the rent due to covid. Takes on values in {0,1} | numeric |
| INCOMELOSS| Income loss due to covid. Takes on values in {0,1} | numeric |
| AGE_GROUP | Age group of the respondent. Takes on values in {'18 - 24','25 - 39','40 - 54','55 - 64','65 and above'} | string |
| EDUC | Worry level of the respondent. Takes on values in {'Less than a high school diploma','High school diploma or GED','Some college/associate's degree','Bachelor's degree or higher'} | string |
| INCOME_LEV | Income level of the respondent. Takes on values in {'Less than $25,000','$25,000 - $74,999','$75,000 - $149,999','$150,000 and above'} | string |


<h3>Source of Bias</h3>
<p> Nonsampling errors can also occur and are more likely for surveys that are implemented quickly, achieve low response rates, and rely on online response.  Nonsampling errors for the Household Pulse Survey may include:</p>

<ul><li><strong>Measurement error:</strong> The respondent provides incorrect information, or an unclear survey question is misunderstood by the respondent. The Household Pulse Survey schedule offered only limited time for testing questions. </li>
<li><strong>Coverage error: </strong>Individuals who otherwise would have been included in the survey frame were missed. The Household Pulse Survey only recruited households for which an email address or cell phone number could be identified.</li>
<li><strong>Nonresponse error:</strong> Responses are not collected from all those in the sample or the respondent is unwilling to provide information. The response rate for the Household Pulse Survey was substantially lower than most federally sponsored surveys.</li>
<li><strong>Processing error: </strong>Forms may be lost, data may be incorrectly keyed, coded, or recoded. The real-time dissemination of the Household Pulse Survey provided limited time to identify and fix processing errors.</li></ul>
 
<p>The Census Bureau employs quality control procedures to minimize these errors.  However, the potential bias due to nonsampling errors has not yet been evaluated.</p>


<h3>Resources used</h3>

This analysis was prepared using Python 3.8 running in a Jupyter Notebook environment.  
Documentation for Python can be found here: https://docs.python.org/3.8/  
Documentation for Jupyter Notebook can be found here: http://jupyter-notebook.readthedocs.io/en/latest/  

The following Python packages were used and their documentation can be found at the accompanying links:

* [pandas](https://pandas.pydata.org/)
* [numpy](https://numpy.org/)
* [IPython](https://ipython.org/)
* [matplotlib](https://matplotlib.org/)
* [seaborn](https://seaborn.pydata.org/)

<h3>Unknowns and dependencies</h3>
<p>These data are experimental and samples may not be representative of the population. </p>




