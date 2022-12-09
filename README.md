# The NHANES program Data Analysis
### EXPLORING THE CORRELATION BETWEEN DIET, LIFESTYLE AND HEALTH

## Table of Contents

1. [Project Description](#description)
- 1.1 [Background: The NHANES program](#background)
- 1.2 [Problem statement: Health and diet](#problem)
- 1.3 [Data exploration](#exploration)
- 1.4 [Data Modeling](#modeling)
- 1.5 [Conclusions](#conclusions)
2. [Installation and Libraries](#installation)
3. [Files List](#files)


## Project Description<a name = "description"></a>

**This is an an indepentent project.** 

## Approach
### Background: The NHANES program<a name = "background"></a>

The **National Health and Nutrition Examination Survey (NHANES)** is a program of studies designed to assess the health and nutritional status of adults and children in the United States. The survey is unique in that it combines interviews and physical examinations. 

NHANES is a major program of the National Center for Health Statistics (NCHS). NCHS is part of the Centers for Disease Control and Prevention (CDC) and has the responsibility for producing vital and health statistics for the Nation. 

The NHANES program began in the early 1960s and has been conducted as a series of surveys focusing on different population groups or health topics. In 1999, the survey became a continuous program that has a changing focus on a variety of health and nutrition measurements to meet emerging needs. The survey examines a nationally representative sample of about 5,000 persons each year. These persons are located in counties across the country, 15 of which are visited each year.

The NHANES **interview** includes demographic, socioeconomic, dietary, and health-related questions. The **examination** component consists of medical, dental, and physiological measurements.

### Problem statement: Health and diet<a name = "background"></a>
A McKinsey & Co. [survey](https://www.mckinsey.com/industries/consumer-packaged-goods/our-insights/feeling-good-the-future-of-the-1-5-trillion-wellness-market) about the wellness market, published in 2021, states that “a rise in consumer interest and purchasing power presents opportunities across markets, especially as consumer spending rebounds.” The growth of the wellness industry is estimated to be between **5 to 10%.**

An important role in wellness marked is played by nutrition and idealistic lifestyle habits.

> *Are those mainstream diets and lifestyle advices really healthy?*

To answer this question, I analyzed the information collected in the NHANES studies by following this approach:
1. Select three of the most currently trendy diets, and consider the proportion of macronutrients (carbohydrates, fats, proteins) specific of each diet.
2. Consider the NHANES participants' demographic, dietary, and lifestyle (including physical activity and alcohol and drugs abuse) habits.
3. Investigate how participants' health condition (**High Blood Pressure, High Cholesterol Level, Diabetes**) is related to the above-mentioned factors through an exploratory data analysis.
4. Predict which factor, or factors influences participants' health.

The three diets type I considered are: 

**Dash**  
The DASH (Dietary Approaches to Stop Hypertension) eating plan is an acceptable eating pattern for people who have diabetes. In addition to promoting blood pressure control, this eating pattern has been shown to improve insulin resistance, hyperlipidemia, and even overweight/obesity. This balanced approach promotes consumption of a variety of foods (whole grains, fat-free or low-fat dairy products, fruits, vegetables, poultry, fish, and nuts) and is appropriate for the entire family. __[Source](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5439361/)__.

**Mediterranean**  
The Mediterranean diet is a way of eating that mimics the diets of people along the Mediterranean Sea. It emphasizes whole foods and is high in vitamins, minerals, and healthy fats. It has been shown to promote heart health, manage weight, and even lower the risks of Alzheimer's and metabolic diseases. __[Source](https://www.mindbodygreen.com/articles/mediterranean-diet-macros#:~:text=What%20are%20the%20typical%20macros,Isabel%20Smith%2C%20R.D.%2C%20CDN)__.

**Paleo**  
The Paleolithic or “Paleo” diet seeks to address 21st century ills by revisiting the way humans ate during the Paleolithic era more than 2 million years ago. Paleo proponents state that because our genetics and anatomy have changed very little since the Stone Age, we should eat foods available during that time to promote good health. Our predecessors used simple stone tools that were not advanced enough to grow and cultivate plants, so they hunted, fished, and gathered wild plants for food. If they lived long enough, they were believed to experience less modern-day diseases like diabetes, cancer, and heart disease because of a consistent diet of lean meats and plant foods along with a high level of physical activity from intensive hunting.__[Source](https://www.hsph.harvard.edu/nutritionsource/healthy-weight/diet-reviews/paleo-diet/#:~:text=%5B7%5D%20The%20Paleo%20diet%20provided,%2C%20avocado%2C%20and%20olive%20oil)__.

**Balanced diet as reccomended by the USDA**  
The 2015–2020 Dietary Guidelines was designed to help Americans eat a healthier diet. Intended for policymakers and health professionals, this edition of the Dietary Guidelines outlines how people can improve their overall eating patterns — the complete combination of foods and drinks in their diet. I used the USDA nutrition guidline as a reference for the other three diets. __[Source](https://health.gov/our-work/nutrition-physical-activity/dietary-guidelines/previous-dietary-guidelines/2015)__.



Macronutrients by diet: (% of daily calories intake):

| Diet type     | Carbohydrates        | Fats        | Proteins     | Source |
| :- | :- | :- | :- | :- |
| DASH          | 55%                  | 27%         | 18%          | __[link](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5439361/)__ |
| Mediterranean | 50%                   |35%         | 15%          | __[link](https://www.mindbodygreen.com/articles/mediterranean-diet-macros#:~:text=What%20are%20the%20typical%20macros,Isabel%20Smith%2C%20R.D.%2C%20CDN)__ |
| Paleo         | 35%                  | 35%         | 30%          | __[link](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8004139/)__ |
| USDA Balanced | 45-65%               | 25-35%      | 10-30%       | __[link](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8004139/)__ |


### Data exploration<a name = "exploration"></a>

Data exploration has been performed by using Tableau Desktop.
The Tableau Dashboards can be found [here](https://public.tableau.com/app/profile/francesca.scipioni/viz/Healthnutritionlifestyle/OVERVIEWDB).

### Data Modeling<a name = "modeling"></a>

There are three health conditions I considered here: **High Blood Pressure, High Cholesterol Level, and Diabetes.** These conditions are highly correlated with nutrition habits and lifestyle. The goal is to understand which factor, or factors, influences their development the most. 

Each condition has been considered individually.  
Because a participant has a condition or not, this is a **binary classification problem.**

The best unsupervised algorithms to apply to a binary classification problem are (__[Source 1](https://en.wikipedia.org/wiki/Binary_classification)__, __[Source 2](https://machinelearningmastery.com/types-of-classification-in-machine-learning/)__, __[Source 3](https://towardsdatascience.com/top-10-binary-classification-algorithms-a-beginners-guide-feeacbd7a3e2)__):
- Logistic Regression
- Support Vector Machines
- Decision Tree
- Random Forest Classifier
- Naive Bayes

I used the function **GridSearchCV** to span across the models's hyper-parameters to search for the parameters’ combination that maximizes the models' performance. I initialized the models again, using the best hyper-parameters, and make predictions on the data.
**Naive Bayes algorithm** doeasn't have parameters to to tune and I didn't use the GridSearchCV for it. 
The modeling is divided in two parts.

#### Part 1.
The models has been implemented considering all the features in the DataFrame, so to understand which are the factors mostly influencing the three health conditions.

#### Part 2.
The DataFrame features have been groupped into Demographic, Dietary, and Lifestyle. The models predicted the factors of each category mostly influencing the three health conditions.

### Conclusions<a name = "conclusions"></a>

When considering all the features as equal (Part 1) the best performing models are **Logistic Regression** and **Random Forest Classifiers.** 
Old age, above 60 years old, is predicted to be the most important factor influencing the onset of high blood pressure and high cholesterol level. 
For diabetes, young age (18 to 29 years old) is predicted to be the most important factor, followed by older age ranges. The difference in percentage importance is small, the first factor having 7% of importance, the following factors having a percentage ranging between 5 to 4%.
Besides age, the amount of money spent for eating out and the total sugars intake are also considered important factors. This can justify, or be related with, the onset of diabetes in joung subjects.

When considering the features groupped in categories (Part 2), there are the main onservations:

**Demographic category.** Old age is again the most important feature related to the health conditions.

**Dietary category.** The most important features differs for each condition: Total sugars and the amount of water intake for HBP; the amount of water intake and obesity for HCL; the amount of water intake and the total sugars for Diabetes.

**Lifestyle - Daily habits category.** The most important daily habits factors for the conditions are the intake of dietary supplements, the amount of physical activity, and the amount of money spent on eating out or for purchasing food at grocery stores.

**Lifestyle - Substances use category.** Alcohol is the main factor influencing HBP, while drug consumption is related to HCL. None of the models considered predicts a connection between Diabetes and substances use. 


## Installation and Libraries<a name = "installation"></a>

The code should run with no issues using Python versions 3.* 
The libraries used are are:

- pandas
- numpy
- json
- functools
- seaborn
- matplotlib
- random
- sklearn


## Files List<a name = "files"></a>

- README.md
	The readme file

- Codes
	Directory containing the Jupyter notebooks files needed to run code, and described below
	- 01 - NHANES_Data_cleaning.ipynb. 
		The Jupiter notebook with the code to clean the raw datasets.
	- 02 - NHANES_Exploratory_Data.ipynb
		The Jupiter notebook with the code to preprocess the cleaned DataFrames.
	- 03 - NHANES_Modeling.ipynb	
		The Jupiter notebook with the code to model the cleaned and preprocessed DataFrames.

- Original Datasets
	Directory containing the original files downloaded from the [NHANES webpage](https://www.cdc.gov/nchs/nhanes/about_nhanes.htm) in .XPT format.

	- DEMOGRAPHYCS_ORIGINAL 
	 	Directory containing the original Demographic dataframe, groupped by year: 
	 		- 2013-2014
	 			DEMO_H.XPT
	 		- 2015-2016
	 			DEMO_I.XPT
	 		- 2017-2018
	 			DEMO_J.XPT

	 - DIETARY_ORIGINAL
	 	Directory containing the original Dietary dataframes, groupped by year:
	 		- 2013-2014  
	 			DSQTOT_H.XPT
				DSQIDS_H.XPT
				DR2TOT_H.XPT
				DR1TOT_H.XPT
	 		- 2015-2016
	 			DSQTOT_I.XPT
				DSQIDS_I.XPT
				DR2TOT_I.XPT
				DR1TOT_I.XPT
	 		- 2017-2018
	 			DSQTOT_J.XPT
				DSQIDS_J.XPT
				DR2TOT_J.XPT
				DR1TOT_J.XPT

	- EXMINATIONS_ORIGINAL
		Directory containing the original Examination dataframes, groupped by year:
		- 2013-2014
	 		BPX_H.XPT
			BMX_H.XPT
	 	- 2015-2016
	 		BPX_I.XPT
			BMX_I.XPT
	 	- 2017-2018
	 		BPX_J.XPT
			BMX_J.XPT

	- QUESTION_ORIGINAL
		Directory containing the original Questionnaire dataframes, groupped by year:
		- 2013-2014
	 		ALQ_H
			BPQ_H.XPT
			CDQ_H.XPT
			CBQ_H.XPT
			HSQ_H.XPT
			DIQ_H.XPT
			DBQ_H.XPT
			DUQ_H.XPT
			PAQ_H.XPT
			SMQ_H.XPT
	 	- 2015-2016
	 		ALQ_I.EXP
			BPQ_I.EXP
			CDQ_I.EXP
			CBQ_I.EXP
			HSQ_I.EXP
			DIQ_I.EXP
			DBQ_I.EXP
			DUQ_I.EXP
			PAQ_I.EXP
			SMQ_I.EXP
	 	- 2017-2018
	 		ALQ_J.EXP
			BPQ_J.EXP
			CDQ_J.EXP
			CBQ_J.EXP
			HSQ_J.EXP
			DIQ_J.EXP
			DBQ_J.EXP
			DUQ_J.EXP
			PAQ_J.EXP
			SMQ_J.EXP
