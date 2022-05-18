# Health Insurance Cross Sell Prediction

![Logo](/images/cross_sell_img.png)

In this project, the client is a Insurance Company that has provided Health Insurance to its clients. Now it's needed to create a model that predict if the 
clients that already has Health Insurance will be interested in a Car Insurance either. An insurance policy is an arrangement by which a company 
undertakes to provide a guarantee of compensation for specified loss, damage, illness, or death in return for the payment of a specified premium. A premium is a 
sum of money that the customer needs to pay regularly to an insurance company for this guarantee.

Just like medical insurance, there is vehicle insurance where every year customer needs to pay a premium of certain amount to insurance provider company so that in 
case of unfortunate accident by the vehicle, the insurance provider company will provide a compensation (called ‘sum assured’) to the customer.

Building a model to predict whether a customer would be interested in Vehicle Insurance is extremely helpful for the company because it can then accordingly plan its 
communication strategy to reach out to those customers and optimise its business model and revenue.

All data and more detailed description of the dataset can be found at: https://www.kaggle.com/datasets/anmolkumar/health-insurance-cross-sell-prediction

## Data Description

There are two files that can be used to train and test the model performance: **Train data** and **Test data**. For this project, it will be used only 
the train data, and the model will be tested on randomly generated data.

**Train Data**

- Id - Unique ID for the customer.
- Gender - Gender of the customer.
- Age - Age of the customer.
- Driving_License - 0 : Customer does not have DL, 1 : Customer already has DL.
- Region_Code - Unique code for the region of the customer.
- Previously_Insured - 1 : Customer already has Vehicle Insurance, 0 : Customer doesn't have Vehicle Insurance
- Vehicle_Age - Age of the Vehicle.
- Vehicle_Damage - Yes : Customer got his/her vehicle damaged in the past. No : Customer didn't get his/her vehicle damaged in the past.
- Annual_Premium - The amount customer needs to pay as premium in the year.
- PolicySalesChannel - Anonymized Code for the channel of outreaching to the customer ie. Different Agents, Over Mail, Over Phone, In Person, etc.
- Vintage - Number of Days, Customer has been associated with the company.
- Response - 1 : Customer is interested, 0 : Customer is not interested.

## Feature Engineering
The dataset is clean and has not ***null*** values. So it was not needed to clean any data. I've made just some changes in some categorical variables facilitate
some analysis.

- Vehicle_Damage: Yes and No variables were changed to 0 and 1.
- Gender: Male and Female were changed to 0 and 1.

## Exploratory Data Analysis
### Univariate Analysis
At this analysis, we can see the behavior of each variable in terms of frequency.
#### Response Variable

![Response Variable Univariate](/images/univariate_analysis_response.png)

As we can see, that's an unbalanced dataset. The number of not interested customers represents 87.74% of the total dataset.

#### Numerical Variables

![Numerical Variable Univariate](/images/univariate_analysis_numerical)

#### Categorical Variables

![Categorical Variable Univariate](/images/univariate_analysis_categorical.png)

### Bivariate Analysis
At this analysis, we can compare all independent variables to the dependent one.
#### Numerical Variables

![Numerical Variable Bivariate](/images/bivariate_analysis_numerical.png)

**Age**

![Age](/images/bivariate_analysis_age.png)

#### Categorical Variables

![Categorical Variable Bivariate](/images/bivariate_analysis_categorical.png)

### Multivariate Analysis
At this analysis, we can see the behavior of each variable compared to other variables.

![Multivariate Analysis](/images/bivariate_analysis_categorical.png)

### Top Insights
1. People that has vehicle older than 2 years has the highest proportion that wants to have the health insurance.
2. People who had vehicle accident has more interest in having health insurance.
3. Older people (40-50 years) has more interst in having health insurance.
4. previously_insured and vehicle_damage has high negative correlation (-0,82).
5. policy_sales_channel and age has considerable negative correlation (-0,58).

## Data Preparation
After all this analysis, it's time to prepare all data to train machine learning models.
### Split train and validation set
The dataset was splited in validation and train set, with the proportions of 20% and 80%.
### Standardization
- annual_premium was standardized due to its distribution.
### Rescalling
- age and vintage were transformed using MinMaxScaler() function.
### Enconding
- region_code, vehicle_age, policy_sales_channel were encoded.

## Feature Selection
At first, Boruta was used to try to find the best features to train the models, but it was unefective. So, it was used another method using decision trees.

**Features Importance by Decision Trees**

The choosen features by importance were:

-img

## Machine Learning
The choosen method to train the model was LightGBM, to use Gradient Boosting Decision Trees.

-img

This is the cumulative gain plot, which shows the amount of dataset needed to select all of the desired dependent variables.

## Deploy
After selecting the model, it was created an API and hosted at heroku to predict the score of any data given as an input. This API was linked to
a Google Sheet to predict the data shown.

-img






