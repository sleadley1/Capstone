# Capstone
Samuel Leadley | 08-26-19 | General Assembly
*Author: Samuel Leadley*
## Problem Statement
Publicly traded companies release quarterly and annual reports outlining how the company has performed over that period. The information contained in these reports include financial data as well text commentary. The reports are relied heavily upon to value and assess companies in the investment management industry. While many investment analysts focus on the financial data and metrics within these reports, the text also provides valuable insights. The text portions of the reports are often verbose and jargon heavy. I intend to develop a document analysis tool that can determine whether or not a company has had a positive or negative year within seconds rather than having someone read all the disclosures. For this project, as a result of time constraints, I will only be using the letters to shareholders to create my model. Additionally, I will use the change in reported net income as a proxy to determine if the company had a positive or negative year and use those determinations to train my model. Net income is a good proxy of how well a company performed as it measures the profit of a company after all expenses are taken into account. I hope this tool can be generalized enough to be used across industries and disclosures.
## Project Files
Below are a list of notebooks and datasets that will be found in the repo: <br>

### Notebooks 
- **1 - Cleaning_and_EDA:** Notebook detailing methods necessary to clean and expore the data. 
- **2 - Preprocessing_Modeling_and_Evaluation:** Notebook describing the process of fitting multiple classification models to the cleaned data and evaluating the best performing model.

### Data Sets
- **clean_df.csv:** Cleaned letter to shareholders
- **leadsheet.csv:** Raw letter to shareholders
- **ni_data.csv:** Net income data for each ticker
- **words_to_remove.csv:** Dataframe of words to remove

### Data Dictionary
|Column|Description|
|---|---|
|**company**|Company name|
|**ticker**|Company ticker|
|**sector**|S&P 500 sector|
|**year**|Year of data|
|**letter_to_shareholder**|Full letter to shareholders|
|**net_income**|Net income|
|**target**|Binary classification|

## Executive Summary
To create my document analysis tool, I needed many shareholder letters to train the model that the tool would utilize. Note I would have liked to use the management commentary or earnings call transcripts, but they were too long to fit into an excel file cell (I created my own data frame in excel because there was no preexisting data available). I chose to take data from various sectors, as defined by the S&P 500, over a 18 year period (2000-2018). The sectors I chose were financials, health care, energy, and info tech because they had interesting fluctuations within that time period and those are the sectors, I am most interested in. Collecting the data was not easy. Many of the historical reports were difficult to find or did not include a letter to shareholders because they were less common in the early 2000 so not every company, I chose to gather data on had the full 18 years of letters available. I got my data from the annual reports of each company I chose. In total I was able to get 166 documents. As mentioned above I could not read through each letter to determine if it was positive or negative, so I used the change in net income from one year to the next as a proxy. Net income data was taken from Y-charts. 

Almost no data cleaning was necessary because I was the person who created the database and had ensured that the data was already properly formatted, unique, and complete. I then conducted my exploratory data analysis. I used CountVectorizer to review the most common words and word pairs in each class, but no useful information was gleaned for it because almost the exact same words and word pairs were in both classes. I then checked to see if the length of the letter had any indication as to whether is was positive or negative but again no real conclusion could be reached. Sector specific EDA did provide some interesting insights like financial services companies tend to have very long-winded letter to their shareholders while the energy sector likes to keep it concise. I was also interested in which sectors performed the best over the time period. Unsurprisingly the health care sector fared the best over the 18 years while the energy sector fared the worst.

Before modeling I decided to lemmatize the words in each letter and create a custom stop words list as I saw various versions of the same word and common words between both classes during my EDA. The balance of my class was around 69% positive and 31% negative meaning that my baseline score is around 69%. I started my modeling process with a logistic regression model using both TF-IDF and CountVectorizer both of which had the exact same result. The logistic regression had a training score of 0.694% and a testing score of 0.690. I decided to try a more complex model to see if it would provide better results so I ran a decision tree. However, the decision tree was tremendously overfit. In an attempt to reduce overfitting, I also ran a random forest classifier which resulted in a training score of 0.879 and a testing score of 0.690. It seemed that my models could not break my baseline score significantly. I also noticed that the predictions from the models where all of the majority class so I thought I would try to rebalance the classes and rerun my models. Sadly, this led to poorer results but at least the predictions were not all one class. 

Overall, I believe my models failed. However, I think given more data or more prudent data, like management commentary, the models would have performed better. 

## Conclusions and Recommendations
As stated above the models failed. Given the nature of letters to shareholders (they try to paint a rosy picture in any circumstance) and the tiny amount of data I was able to collect I believe this is the best performance I could have gotten from my models. Given the arduous data collection method used in this project a tool that could locate and extract certain sections of text should be developed before attempting to create a document analysis tool. 
