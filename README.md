Recently I ran into single-column structured datasets at work- it is a set of survey questions responded by shoppers; many question allow "check-all-that-apply". The multiple reponses to each survey question by the shoppers are recorded as a string seperated by comma (for example, What are your favorite fruits? the answer is recorded as: `apple, mango, banana, lemon`) To further analyze these responses, I would need to transform those values into multiple-column structure, and then into Boolean datatype. Here are two key questions:

- How to do that in Pyspark?
- How to process multiple questions at once?

We will use foreveralone dataset from Reddit for demo, as this dataset contains multiple check-all-that-apply questions. Here are the 7 steps of the flow:

1. Exploration of the data set: identify the columns (number of columns = N. In this demo, N=3) that record check-all-that-apply values.
2. Convert N columns into a list.
3. Clean up the strings with a for loop, in order to collect all the unique cateogorical answers in columns into lists.
4. Write a function that renames all new columns in a systematic way.
5. Write THE function `Check_All_That_Apply()`. This is the key of this notebook!
6. Run `Check_All_That_Apply()` for column list to generate N new dataframes.
7. Join all N dataframes, and we are all set!


This notebook will focus on feature engineering techniques in Pyspark, instead of analytics. 
