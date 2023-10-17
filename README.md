# data-512-homework_2

# Overview
This project explores the concept of bias in data by analyzing Wikipedia articles about cities in different US states. The aim is to understand how the coverage of US cities on Wikipedia varies among states and how the quality of articles differs.

# Datasets
data/us_cities_by_state_SEPT.2023.csv: A dataset listing Wikipedia article pages about US cities from each state.
data/NST-EST2022-POP.xlsx: Population estimates for every US state.
data/US States by Region - US Census Bureau.xlsx: Listing of states in each US census regional division.

# Dependencies
Python 3
Jupyter Notebook
Pandas
Requests

# Code
I have used this Google Colab to write my code for data acquisition and analysis: DATA512 HW2-Analysing Wikipedia Page reviews.ipynb

# Procedure to follow to reproduce the project
1) Data Collection and Preprocessing: A Wikimedia API was used to scrape data from Wikipedia using the us_cities_by_state_SEPT.2023.csv file to read the URLs of all the articles that we need. The API call takes about 2 hours to retrieve data for about 20,000+ articles.
2) After the initial city data acquisition, it was found that there were many duplicates. I stored this data into a dictionary which automatically dropped duplicates.
3) Acquired population data from the US Census Bureau for each state. We found the data on this website- https://www.census.gov/data/tables/time-series/demo/popest/2020s-state-total.html
4) Extracted regional divisions as defined by the US Census Bureau. The file name for this data is US States by Region - US Census Bureau. You can also find it at https://docs.google.com/spreadsheets/d/14Sjfd_u_7N9SSyQ7bmxfebF_2XpR8QamvmNntKDIQB0/edit?usp=sharing
5) For each last changed revision ID we hit an API that gives us the ORES prediction for the quality of the article. ORES is a machine learning algorithm that rates the quality of the articles.

The quality scores range from "FA" (Featured article) to "Stub" (Stub-class article).
The API call for 20,000+ articles took about 5 hours to complete. The initial round of calls produced about 4,000 rows with errored predictions.
These errors were then resolved in the second round of API calls. All this data was appended to a dictionary after each API call.

# Data Integration

Combined Wikipedia data, population data, and regional division data using state names as the key.
Handled data inconsistencies and discrepancies during this merge.
We finally produce a final consolidated dataframe: merged_region_data.

# Analysis

Calculated "articles-per-population" and "high-quality-articles-per-population" for each state.
Displayed the top 10 and bottom 10 states according to the aforementioned metrics.
Defined "high quality" articles as those predicted by ORES to be either "FA" or "GA".

#Results Visualization

Produced tables highlighting states and census divisions based on their coverage and quality on Wikipedia.
Top and bottom 10 US states by coverage and quality.
Census divisions are ranked by coverage and quality.

#Research Implications

I tried to answer 3 questions that I found are important in this analysis.

Q) What biases did you expect to find in the data (before you started working with it), and why?

Ans. 
I was expecting that the larger states/cities would automatically have the highest-rated articles but upon my analysis, I found that to be untrue. The quality of articles did not seem to have a direct correlation with the size/population of the states.

Anyone can contribute to Wikipedia and hence it can be influenced by its editors' demographics. If certain demographic groups are overrepresented among Wikipedia editors, topics of interest to those groups might be covered more extensively.

I also thought that some articles might be biased towards events or facts that have received more media attention historically. For example, cities that have been historically significant or have seen major events might have more detailed articles.

Q) Can you think of a realistic data science research situation where using these data (to train a model, perform hypothesis-driven research, or make business decisions) might create biased or misleading results, due to the inherent gaps and limitations of the data

Ans.

Wikipedia has been criticized for gender bias in its biographical articles. There are typically fewer biographies of women compared to men. If a data science study relies on Wikipedia to analyze gender-related trends or achievements, it may inadvertently reinforce gender bias.

Q) Can you think of a realistic data science research situation where using these data (to train a model, perform hypothesis-driven research, or make business decisions) might still be appropriate and useful, despite its inherent limitations and bias

Ans. 
Wikipedia has a plathora of data. Generally, factual pieces on Wikipedia are something which are consistant with reality and hence I believe that we can use that data for getting an initial understanding of the problem we are working on. Wikipedia is generally up-to-date with the latest happenings around the world and hence some articles can act as a great way to train models on. 

Time series models can also be trained on Wikipedia data as it generally has a well documented series of events which have happened related to a particuar event.

The way articles are written, the topics that are covered, and the details that are emphasized can sometimes(but not always) provide cultural or societal insights.

# License

This project is licensed under the MIT License. Please see the LICENSE file for more details.

# Acknowledgements

Wikipedia for the dataset about US cities.
US Census Bureau for the population and regional division data.
ORES for providing the article quality predictions.

# Contact Information
For any additional questions or feedback, please contact [Harshit Rai] at [vriteshg@uw.edu]
