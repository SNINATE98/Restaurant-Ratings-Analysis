# Restaurant Ratings Analysis

## Table of Contents

- [Project Overview](#project-overview)
- [Case Study](#case-study)
- [Dataset Description](#dataset-description)
  - [Consumers](#consumers)
  - [Consumer Preferences](#consumer-preferences)
  - [Ratings](#ratings)
  - [Restaurants](#restaurants)
  - [Restaurant Cuisines](#restaurant-cuisines)
- [ER Diagram](#er-diagram)
- [Data Cleaning](#data-cleaning)
  - [Importing Data as Folder](#importing-data-as-folder)
  - [Calculated Fields](#calculated-fields)
- [Data Analysis](#data-analysis)
  - [Local Insights](#local-insights)
  - [Dining Insights](#dining-insights)
  - [Hospitality Insights](#hospitality-insights)
  - [Behavior Insights](#behavior-insights)
  - [Review Insights](#review-insights)
- [Dashboard](#dashboard)
- [Tools & Technologies](#tools--technologies)
- [How to Use This Project](#how-to-use-this-project)
- [Future Improvements](#future-improvements)

---

## Project Overview

This project analyzes restaurant ratings in Mexico using real consumer reviews from 2012.  
It explores how consumer demographics, preferences, and behaviors relate to restaurant characteristics such as price, alcohol service, smoking policy, and parking availability.

The analysis is structured around four main perspectives:

- **Local** (cities, states, locations)  
- **Dining** (price, cuisines, franchises)  
- **Hospitality** (alcohol, smoking, parking, service)  
- **Behavior** (age, occupation, drink level, marital status)

---

## Case Study

> Restaurant ratings in Mexico by real consumers from 2012, including additional information about each restaurant and their cuisines, and each consumer and their preferences.

The goal is to understand:

- Who the consumers are  
- How they behave and what they prefer  
- How restaurants perform in terms of ratings  
- Which restaurant characteristics drive higher satisfaction

---

## Dataset Description

The dataset is composed of five main tables.

### Consumers

- **Consumer_ID** – Unique identifier for each consumer  
- **City** – City where the consumer lives  
- **State** – State where the consumer lives  
- **Country** – Country where the consumer lives  
- **Latitude** – Latitude where the consumer lives  
- **Longitude** – Longitude where the consumer lives  
- **Smoker** – Whether the consumer smokes or not  
- **Drink_Level** – Abstemious, casual, or social drinker  
- **Transportation_Method** – On foot, public transport, or car  
- **Marital_Status** – Single or married  
- **Children** – Dependent/independent children or none  
- **Age** – Consumer’s age  
- **Occupation** – Student, employed, or unemployed  
- **Budget** – Low, medium, or high  

### Consumer Preferences

- **Consumer_ID** – Unique identifier for each consumer  
- **Preferred_Cuisine** – Types of food the consumer prefers  

### Ratings

- **Consumer_ID** – Unique identifier for each consumer  
- **Restaurant_ID** – Unique identifier for each restaurant  
- **Overall_Rating** – 0 = Unsatisfactory, 1 = Satisfactory, 2 = Highly Satisfactory  
- **Food_Rating** – 0 = Unsatisfactory, 1 = Satisfactory, 2 = Highly Satisfactory  
- **Service_Rating** – 0 = Unsatisfactory, 1 = Satisfactory, 2 = Highly Satisfactory  

### Restaurants

- **Restaurant_ID** – Unique identifier for each restaurant  
- **Name** – Restaurant name  
- **City** – Restaurant city  
- **State** – Restaurant state  
- **Country** – Restaurant country  
- **Zip_Code** – Zip code  
- **Latitude** – Restaurant latitude  
- **Longitude** – Restaurant longitude  
- **Alcohol_Service** – No alcohol, wine & beer, or full bar  
- **Smoking_Allowed** – No, bar only, sections, or allowed  
- **Price** – Low, medium, high  
- **Franchise** – Franchise or not  
- **Area** – Open or closed area  
- **Parking** – None, yes, public, valet  

### Restaurant Cuisines

- **Restaurant_ID** – Unique identifier for each restaurant  
- **Cuisine** – Types of food the restaurant serves  

---

## ER Diagram
<img width="1391" height="636" alt="image" src="https://github.com/user-attachments/assets/d857d946-cf01-48a1-9c6a-8fd83588de12" />

The data model is based on a star-like schema:

- **Consumers** and **Restaurants** are dimension tables  
- **Ratings** is the central fact table  
- **Consumer_Preferences** and **Restaurant_Cuisines** enrich the model with many-to-one relationships



---

## Data Cleaning

### Importing Data as Folder

1. **Get Data** → **More** → **All** → **Folder** → **Connect**  
2. Select the **folder path** containing all CSV files → **OK**  
3. In Power Query:
   - **Transform Data**
   - **Duplicate** the file query for each dataset
   - Click on **Binary** to expand each dataset
4. Repeat for all tables: Consumers, Consumer_Preferences, Ratings, Restaurants, Restaurant_Cuisines.

### Calculated Fields

#### Age Group

```DAX
AgeGroup = 
SWITCH(
    TRUE(),
    consumers[Age] <= 18, "Children and Adolescents",
    consumers[Age] <= 30, "Young Adults",
    consumers[Age] <= 45, "Adults",
    consumers[Age] <= 60, "Middle-aged Adults",
    "Seniors"
)
#### Service Rating Category
Service_Rating_Category = 
SWITCH(
    TRUE(),
    ratings[Service_Rating] = 0, "Unsatisfactory",
    ratings[Service_Rating] = 1, "Satisfactory",
    "Highly Satisfactory"
)

<img width="2075" height="1200" alt="image" src="https://github.com/user-attachments/assets/f1cbda3b-7f5a-432f-bc4b-b4af70ad813d" />

