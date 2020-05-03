Project 2: Ames Iowa Housing Prices Analysis 

by: Elton Yeo

### Context and Problem Statement

To predict housing prices in Ames, Iowa, by understanding the relationships among various variables such as lot area, neighbourhood etc., and using linear regression models to predict the prices. 

This will allow prospective home-owners to better manage their cashflow when preparing to buy a house, current home-owners to know how to best add value to their houses, and policy-makers to better monitor and regulate housing prices. 


### Executive Summary

In this analysis, we considered 80 different variables and their effects on housing prices in Ames, Iowa. We broke down the variables into categorical, numerical, and ordinal. We analysed and cleaned the data to impute missing values and change wrong data types. We conducted feature engineering by combining variables and log-transforming sale prices. We also dropped categorical variables with mode >80%.

We used linear regression, Ridge and Lasso models on our cleaned data, and chose Ridge based on the highest r-squared score and lowest root mean squared error. Our predicted housing prices based on the test set generated a Kaggle score of 35118, which is within the top 60 on the leaderboard. 

### Data Analysis, Cleaning and Feature Engineering

We considered whether any of the data was of the wrong type, and also the number of missing values in each variable. 
- Data of the wrong type was amended. 
- For missing values, we assumed in the case of cateogrical variables that none of those features were found in the houses i.e. missing values were filled with "none". In the case of numerical variables, we assumed that none of those features were found in the house i.e missing values were filled with "0".

For variables which were similar, we combined them e.g. there was no need to differentiate among the different types of porches, what was important was whether or not the house had a porch.

Looking at the distribution of saleprice (which is only found in the train set), we saw that it was a unimodal distribution with a right skew. Since this was our target variable, we log-transformed it to fit it into a normal distribution. This corrected the skewness of the distribution and allowed it to be modelled more easily later. 

Based on visualisations of the data, we saw that most numerical variables had multimodal distributions. Scatterplots of the numerical variable also allowed us to identify an impossible outlier i.e. year the garage was built was 2207 - this was amended to 2007. Boxplots of the categorical data against sale price showed that most of these variables were found within the lower end of sale prices i.e. less than $300,000. 

We also dropped categorical variables with mode >80%. This is because there is much less variance and hence such categorical variables will not have significant impact on the model.


### Modelling

We used linear regression, Ridge and Lasso models on our cleaned data and compared r-squared and root mean squared error figures to determine the best model to predict housing prices from our test set. Our chosen model was Ridge. Our predicted housing prices generated a Kaggle score of 35118, which is within the top 60 on the leaderboard. 


### Conclusion and Recommendations

The features which added the most value to housing prices were: 
- Overall quality (rates the overall material and finish of the house)
- Ground living area (Above ground living area square feet)
- Total square feet (combination of first floor, second floor and basement area square feet)

The features which hurt the value of housing prices the most were: 
- Misc val (the value of miscellaneous features)
- Being in the Edwards neighborhood
- Being in a commercial zone

In order to increase the value of their houses, owners could consider improving the overall quality of the house by commencing renovation and upgrading works. This could include waterproofing, new coats of paint, stronger materials etc. Owners could also consider building additional floors if permitted, to increase the above total sqaure feet of the home across all levels and thereby increase space to live, work and play in. 

Buying houses in the Northridge Heights neighbourhood or Stone Brook neighbourhood would be good investments as being in those neighbourhoods added value to the houses. 

This model would likely generalise to other cities as overall quality, and total sqaure feet of the house across all room types, would be important to most homebuyers even in different cities. In order to make the model even more universal, we could consider removing features which are specific to Ames, Iowa such as the specific neighbourhoods. In order to make a comparable model for another city, we could collect more data on race, income, age, occupation, political affiliation, neighbourhood etc. to consider how these various factors might affect the prices of houses across neighbourhoods in the other city. 
