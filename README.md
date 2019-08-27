# Capstone
Samuel Leadley | 08-26-19 | General Assembly
*Author: Samuel Leadley*
## Problem Statement
Publicly traded companies release annual reports outlining how the company has performed over a given period. The information contained in this report includes financial data as well as a letter from the CEO or chairman. The reports are relied heavily upon to value and assess companies in the investment management industry. While many investment analysts focus on the financial data and metrics within these reports, letters to shareholders also offer interesting insights and explanations as to why the company performed the way it did. Leveraging natural language processing I intend to determine whether or not the company had a positive or negative year. Given time restraints I cannot read each letter so I will use the change in reported net income as a proxy to determine if the company had a positive or negative year and use those determinations to train my model. Net income is a good proxy of how well a company perfromed as it measures the profit of a company after all expenses are taken into account. I hope to be able to utilize this analyzer for other text based financial data like management commentaries and transcripts of earnings calls.  
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
