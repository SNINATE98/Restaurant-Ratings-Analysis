# Restaurant Ratings Analysis

## Table of Contents

- [Case Study](#case-study)
- [Dataset Description](#dataset-description)
- [ER Diagram](#er-diagram)
- [Data Cleaning](#data-cleaning)
- [Data Analysis](#data-analysis)
- [Dashboard](#dashboard)

---

## Case Study

Restaurant ratings in Mexico by real consumers from 2012, including additional information about each restaurant and their cuisines, and each consumer and their preferences.

---

## Dataset Description

Our dataset consists of the following observations:

### Consumers

- **Consumer_ID** – Unique identifier for each consumer
- **City** – City where the consumer lives
- **State** – State where the consumer lives
- **Country** – Country where the consumer lives
- **Latitude** – Latitude of residence
- **Longitude** – Longitude of residence
- **Smoker** – Whether the consumer smokes or not
- **Drink_Level** – Abstemious, casual, or social drinker
- **Transportation_Method** – On foot, public transport, or car
- **Marital_Status** – Single or married
- **Children** – Dependent/independent children
- **Age** – Consumer’s age
- **Occupation** – Student, employed, or unemployed
- **Budget** – Low, medium, high

### Consumer_Preferences

- **Consumer_ID** – Unique identifier
- **Preferred_Cuisine** – Types of preferred food

### Ratings

- **Consumer_ID** – Unique identifier
- **Restaurant_ID** – Unique identifier
- **Overall_Rating** – 0 = Unsatisfactory, 1 = Satisfactory, 2 = Highly Satisfactory
- **Food_Rating** – 0 = Unsatisfactory, 1 = Satisfactory, 2 = Highly Satisfactory
- **Service_Rating** – 0 = Unsatisfactory, 1 = Satisfactory, 2 = Highly Satisfactory

### Restaurants

- **Restaurant_ID** – Unique identifier
- **Name** – Restaurant name
- **City** – City
- **State** – State
- **Country** – Country
- **Zip_Code** – Zip code
- **Latitude** – Latitude
- **Longitude** – Longitude
- **Alcohol_Service** – None, wine & beer, full bar
- **Smoking_Allowed** – Smoking policy
- **Price** – Low, medium, high
- **Franchise** – Yes or No
- **Area** – Open or closed area
- **Parking** – None, yes, public, valet

### Restaurant_Cuisines

- **Restaurant_ID** – Unique identifier
- **Cuisine** – Type of cuisine served

---

## ER Diagram

<img width="1391" height="636" alt="image" src="https://github.com/user-attachments/assets/66ad99e1-ab7c-45aa-9ee1-9eb5a740dabb" />

---

## Data Cleaning

### Steps to Import Data as a Folder

1. Get Data → More → All → Folder → Connect
2. Select dataset folder path → Click OK
3. Click Transform Data
4. Duplicate the file
5. Click on Binary to expand the dataset
6. Repeat for each dataset
7. Create calculated fields

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
```

#### Service Rating Category

```DAX
Service_Rating_Category = 
SWITCH(
    TRUE(),
    ratings[Service_Rating] = 0, "Unsatisfactory",
    ratings[Service_Rating] = 1, "Satisfactory",
    "Highly Satisfactory"
)
```

#### Overall Rating Category

```DAX
Overall_Rating_Category = 
SWITCH(
    TRUE(),
    ratings[Overall_Rating] = 0, "Unsatisfactory",
    ratings[Overall_Rating] = 1, "Satisfactory",
    "Highly Satisfactory"
)
```

#### Food Rating Category

```DAX
Food_Rating_Category = 
SWITCH(
    TRUE(),
    ratings[Food_Rating] = 0, "Unsatisfactory",
    ratings[Food_Rating] = 1, "Satisfactory",
    "Highly Satisfactory"
)
```

---

## Data Analysis

### Local Insights

- Most of the population is from San Luis Potosí, followed by Cuernavaca, Morelos.
- Young adults under 30 form the majority.
- Most consumers are non-smokers.
- Most restaurants across cities lack parking facilities.

### Dining Insights

- Among 16 high-priced restaurants, most offer parking.
- San Luis Potosí has 84 restaurants.
- Most restaurants are non-franchises.
- Mexican cuisine is the most preferred.

### Hospitality Insights

- 66.92% of restaurants do not offer alcohol.
- 26.15% offer wine and beer.
- 6.93% offer a full bar.
- 61% of consumers use public transportation.
- 73% of restaurants maintain smoke-free policies.

### Behavior Insights

- Most consumers are students.
- Drink level varies by state.
- Most students have a medium budget.

### Review Insights

#### Top 5 Restaurants by Food Rating

- Tortas Locas Hipocampo
- Puesto de Tacos
- Cafeteria y Restaurante El Pacífico
- Gorditas Doña Gloria
- La Cantina Restaurante

#### Top 5 Restaurants by Service Rating

- Tortas Locas Hipocampo
- Puesto de Tacos
- Cafeteria y Restaurante El Pacífico
- Gorditas Doña Gloria
- La Cantina Restaurante

#### Top 5 Restaurants by Overall Rating

- Tortas Locas Hipocampo
- Puesto de Tacos
- Cafeteria y Restaurante El Pacífico
- La Cantina Restaurante
- Restaurant la Chalita

---

## Dashboard

<img width="2075" height="1200" alt="image" src="https://github.com/user-attachments/assets/be749377-9ac8-4f1b-b88e-154eaa2c1f56" />
<img width="2075" height="1200" alt="image" src="https://github.com/user-attachments/assets/bdab4b7d-d5c3-4197-ae2d-663a2ca07e29" />
<img width="2075" height="1200" alt="image" src="https://github.com/user-attachments/assets/7491ee1f-60fa-4050-8a87-6bac2649e478" />
<img width="2075" height="1200" alt="image" src="https://github.com/user-attachments/assets/7f66e390-f51d-4fe3-b019-bf6896fa3685" />
<img width="2075" height="1200" alt="image" src="https://github.com/user-attachments/assets/9264bf43-fa29-425c-beab-1565eb91ac9b" />






