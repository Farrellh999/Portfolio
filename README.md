
# Data Science Project: Dog Breed Popularity vs Genetic Ailments


## Overview

This project uses a publicly available dataset which examines each dog breed, providing scores on popularity, size, intelligence, suitability for children (score for kids), lifetime cost, intelligence, longevisty, genetic ailments, purchase price, annual food costs, and grooming frequency. I wish to use a linear regression model to examine if there is a relationship between the number of genetic ailments commonly associated with the breed and the popularity of said breed.

### Positive Impact


### Negative Impact
Public perception and opinion, breeds becoming extinct.

## Conclusion

##  Bibliography


# Data Sources
The dataset can be found at https://www.kaggle.com/datasets/jainaru/dog-breeds-ranking-best-to-worst. This a public dataset, readily available to download to anyone who has a free Kaggle account.

# Contents

[Introduction](#introduction)

[Project Background](#project-background)

# Project Background
Dogs are notoriously know as man's best friend, with the vast displays on social media of 'doggos' further illustrating this point. However, with the emergence of social media, in addition to the displays of love and affection these animals bring, it is becoming more common to bare witness to the public debates surrounding the ethics of dog breeding and the health of certain dog breeds. This project aims to examine the relationship between popularity ranking and the number of genetic ailments. 

If there is a positive relationship between the number of genetic ailments and popularity, this could raise an issue surrounding more dogs being born with a higher risk of illness, and therefore it could open up discussion surrounding the drivers for owning such dogs and exploring owner knowledge of the breeds and potential health ailments.

If there is a negative relationship between the number of genetic ailments and popularing, this could indicate that knowledge surrounding dog health is widely understood in the public and people are actively considering avoiding owning dogs with certain genetic ailments.

If no relationship is discovered, then it indicates that either:
* The public have little awareness of genetic ailments in dog breeds; or
* The public do not hold the possibility of genetic ailments as a strong enough deterrent to buying certain dog breeds.

# Project Summary

## Question
Are dogs with more genetic ailments becoming more popular?

## Solution

## Outcome


## Preparing the data
The datasets are imported into Jupyter notebooks with the pandas, numpy, and matplotlib libraries imported.

import pandas as pd  
import numpy as np  
import matplotlib.pyplot as plt  

### import the datasets and identify each one
dogs_file = r'C:\Users\HannahFarrell\Greater Manchester GP Federations Toolkit\GMTHFiles - Documents\GM Training Hub\Information Analysis\.ipynb_checkpoints\dogs-ranking-dataset.csv'
dogs_data= pd.read_csv(dogs_file)

### Check the top 5 rows of the table
dogs_data.head()  

![image](https://github.com/user-attachments/assets/96048de0-e306-47bf-9d9a-8a804dd34e15)  

The data appears to have imported correctly.

### Check Data Quality

dogs_data.info()  
![image](https://github.com/user-attachments/assets/51af1835-6374-460d-ad41-1670de7a30be)  

There are a few categories which will require the data type changing if we decide to perform analysis on them e.g., lifetime cost, food costs per year. 

The dataset is completed, with no columns containing null values. All columns are present. 

There are several spelling errors within the column headers to be mindful of, and consider renaming.

### Observe the summary statistics of the data
print(dogs_data.describe())  
![image](https://github.com/user-attachments/assets/6bbd1fb4-3ed2-47c7-aeba-f00cb4537a35)

### Observe popularity ranking by type category
sns.boxplot(x='type', y='popularity ranking',data=dogs_data)  
plt.xticks(rotation = 45) # rotate the x labels to improve visibility  
plt.show()  

![image](https://github.com/user-attachments/assets/9ddd84e4-7b45-4d1b-88ee-5dcc9142b1bc)


### Choose the specific columns to analyse
For this project we will be focusing on the columns: popularity ranking, and number of genetic ailments.  
selected_columns = dogs_data[['popularity ranking','NUMBER OF GENETIC AILMENTS']]  
print(selected_columns.head())  

![image](https://github.com/user-attachments/assets/321054c1-ce2a-4c4a-89b7-428d0b3e06aa)

### Check for null values
null_counts = selected_columns.isnull().sum()  
print(null_counts)  

![image](https://github.com/user-attachments/assets/d4d08d8b-74c8-49bf-9752-afb466ff633b)

## Explore the Data
### Observe the summary statistics of the data
print(selected_columns.describe())  
![image](https://github.com/user-attachments/assets/97cbc5fb-6791-4bb2-835e-8c16350528c3)  
This identifies that there are 87 records, indicating the 87 different dog breeds. The average number of genetic ailments is 1.69; some breeds have zero and other breeds have up to 9 genetic ailments.

### Analyse the distribution of the data
selected_columns.hist(figsize=(10,8), bins=20)  
plt.show()  
![image](https://github.com/user-attachments/assets/303a2a9a-ebb0-4009-b3c8-7d295ae13809)  
The histogram reveals that most dogs have only 1 genetic ailment. But how popular is this breed?

### Observe the distribution of the data in a scattergraph
sns.scatterplot(x='NUMBER OF GENETIC AILMENTS', y = 'popularity ranking', data = selected_columns)  
plt.show()  
![image](https://github.com/user-attachments/assets/f691ace7-f398-4ebd-9315-e091e119a135)  
The scattergraph identifies that there is a high concentration of breeds who have 0 - 1 genetic ailments who also score high in popularity ranking. However, there are still a sizeable number of breeds with a high population ranking with more than 1 genetic ailment. 

## Train the Model
### Identify the variables
The dependent variable is the popularity ranking of the dog breed. The independent variable is the number of genetic ailments. I.e., we wish to explore how the popularity of a dog breed is influenced by it's number of genetic ailments.

### Split the data into test and training groups
from sklearn.model_selection import train_test_split  

x = selected_columns['NUMBER OF GENETIC AILMENTS']  
y = selected_columns['popularity ranking']  
x_train, x_test, y_train, y_test = train_test_split(x, y, test_size = 0.2, random_state=42)  

## Apply the Model


### Applying Business Logic



### Bringing it all Together



### Validating the Outputs



### Displaying Results to the User


# Conclusion

## Outline



## Considerations



#  Bibliography

