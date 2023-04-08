# Automated Feature Engineering

## Introduction: Automated Feature Engineering with Featuretools

Problem: we have a set of cutoff times and labels - in a label times table - and we need to build relevant features for each label using only data from before the cutoff time. Traditionally, we would do this by hand, a painstaking and error prone process that makes developing useable machine learning solutions extremely difficult.

Solution: Use automated feature engineering as implemented in Featuretools to build hundreds or thousands of relevant features from a relational dataset with a reusable framework that also automatically filters the data based on the cutoff times. This approach overcomes the limitations of manual feature engineering, letting us build better predictive models in a fraction of the time.

The general process of feature engineering is shown below:

![image](https://user-images.githubusercontent.com/86930309/230740271-ad0902e2-094b-4d4f-844c-089b737f93e4.png)

In this notebook, we'll work with Featuretools to develop an automated feature engineering workflow for the customer churn dataset. The end outcome is a function that takes in a dataset and label times for customers and builds a feature matrix that can be used to train a machine learning model

## 1. Import Libraries

## 2. Upload the 3 Datasets

## 3. Define Entities and EntitySet:

### - Members Table

a. The members table holds basic information about each customer.

### - Transaction Table 

a. The transactions table contains payments made by the customers. Each row records one payment.

![image](https://user-images.githubusercontent.com/86930309/230740641-299efdf8-81cd-42f9-8ff1-de01820e499b.png)

b. Many Customers paid $150 or $100.

![image](https://user-images.githubusercontent.com/86930309/230740705-c6fbbd42-7d3a-40af-a240-6981eaf280f6.png)

c. This the difference between the list and actual amount each customer paid when there was a difference.

### - Logs Table

a. The logs contain user listening behavior.

![image](https://user-images.githubusercontent.com/86930309/230740915-7aad4cc6-9167-4d4b-9bf8-8b0404961003.png)


![image](https://user-images.githubusercontent.com/86930309/230740962-f6c0b0ae-910c-4b2a-9ef2-7f391f2eb414.png)
 
b. Most of the songs were listend to the end by the customer.
 
c. Making features by hand may seem counterintuitive if we are using automated feature engineering, but the benefits of doing this before using Featuretools is that these features can be stacked on top of to build deep features.

### - Relationships

We use relationships to specify how examples in one table relate to examples in other tables. The entityset structure for this problem is fairly simple as there are only three entities with two relationships. Members is the parent of logs and transactions.

### - Cutoff Times

Featuretools automatically filters our data based on the cutoff times to ensure that all the features are valid for machine learning.

## 4. Deep Feature Synthesis

### - Featuretools has built 188 features.

### - Specify Primitives

### - Aggregation Primitives

### - Transform Primitives

### - Where Primitives

### - Custom Primitives

a. Custom Primitive Implementation

b. Deep Feature Synthesis with Specified Primitives. This will generate 255 features.

### - Run Deep Feature Synthesis

![image](https://user-images.githubusercontent.com/86930309/230742695-c266f486-0ada-4d4a-a7c3-b7b52f37c794.png)

Not many songs are listen to all the way to the end. We have a positively skewed distribution.

## 5. Conclusions

Automated feature engineering is a significant improvement over manual feature engineering in terms of both time and modeling performance. In this notebook, we implemented an automated feature engineering workflow with Featuretools for the customer churn problem. Given customer data and label times, we can now calculate a feature matrix with several hundred relevant features for predicting customer churn while ensuring that our features are made with valid data for each cutoff time.

Along the way, we implemented a number of Featuretools concepts:

An entityset and entities
Relationships between entities
Cutoff times
Feature primitives
Custom primitives
Deep feature synthesis

