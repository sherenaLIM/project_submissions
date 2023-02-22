#  ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 2 - Singapore Housing Data and Kaggle Challenge

### Overview

Welcome to Project 2! You have been tasked with creating a regression model based on Singapore Housing Dataset. This model will predict the price of a house at sale. This Dataset is an exceptionally detailed one with over 70 columns of different features relating to houses.

The project required you to utilise and demonstrate the following skills:
- Basic statistics and probability
- Many Python programming concepts
- Programmatically interacting with files and directories
- Visualizations
- Exploratory Data Analysis
- Working with Jupyter notebooks for development and reporting
- Pre-processing and Modelling

### Problem Statement

Over the years, Singapore has seen the puzzling rise of public housing in the resale market with million dollar price tags, supporting the theory that “decent gains” can still be acquired, especially for HDB flats bought at subsidised prices from the Government. There are many macro and micro, demand and supply factors contributing to high upside potential for these units. 

You are part of the Research & Consultancy team in PropNext. Propnext would like to ride on the wave and increase the number of high-value sales and purchase transactions intermediated by PropNext agents. The company is looking to develop an in-house mobile application that is able to predict the selling price of HDB resale flats. The application would help real estate agents detect and look out for units with huge upside potential, so as to rake in higher commissions per sale. The team has to identify high-yield features that contribute to the appreciation of units and report their findings to the software development team in 2 weeks' time. The software developers will then communicate the requirements to the software engineers who would then build the application with the embedded predictive function in collaboration with data scientists. 

Include the following business recommendations within your research report.
- What aspect of location matters to whom? 
- Which features appear to add the most value to a home?
- Which features hurt the value of a home the most?
- What are things that homeowners could improve in their homes to increase the value?
- What neighborhoods seem like they might be a good investment?
- Do you feel that this model will generalize to other cities? How could you revise your model to make it more universal OR what date would you need from another city to make a comparable model?


**Citations:**
- Kwek S C, Hoh D, et al. (2017). Commentary - Determining the value of leasehold land: A closer look at “Bala’s Table”. Centre for Liveable Cities Singapore. https://www.clc.gov.sg/docs/default-source/commentaries/balas-table.pdf .
- Rottke, N., Wernecke, M., & Schwartz, A. L. (2003). Real Estate Cycles in Germany—Causes, Empirical Analysis and Recommendations for the Management Decision Process. Journal of Real Estate Literature, 11(3), 327–345. http://www.jstor.org/stable/44103477
- Yuen, B., Yeh, A., Appold, S. J., Earl, G., Ting, J., & Kwee, L. K. (2006). High-rise Living in Singapore Public Housing. Urban Studies, 43(3), 583–600. http://www.jstor.org/stable/43198351

---

### Datasets

#### Provided Data

There are 3 housing datasets provided in the [`data`](./data/) folder for this project. 

* [`train.csv`](./data/train.csv): Contains all of the training data for your model with the following format (150634, 77). There is a total of 77 variables, 76 of which are feature variables. The target variable (resale_price) is also included within the dataset. 
* [`test.csv`](./data/test.csv): Contains the test (unseen) data for your model with the following format (16737, 76). You will feed this data into your regression model to make predictions. There is a total of 76 variables, all of which are feature variables. The target variable (resale_price) has been removed from the test set!
* [`sample_sub_reg.csv`](./data/sample_sub_reg.csv): An example of a correctly formatted submission for the DSI-SG Project 2 Regression Challenge (HDB Price). A random number has been provided as prediction for resale_price. Please ensure that your submission to Kaggle matches this format (16737, 2).

#### Datasets for Kaggle Submission
* [`kaggle_baseline_submission.csv`](./data/kaggle_baseline_submission.csv): Predicted values made up of the mean resale price from the training dataset. 
* [`kaggle_prediction_submission.csv`](./data/kaggle_prediction_submission.csv): Predicted values from the test (unseen) dataset. 

---

### Data Dictionary

| Feature | Type | Description |
|---|---|---|
|resale_price| numeric (float64)|the property's sale price in Singapore dollars|
|id|categorical (nominal)|identification number of each resale unit|
|tranc_yearmonth|datetime64|year and month of the resale transaction, e.g. 2015-02| 
|town|categorical (nominal)|HDB township where the flat is located, e.g. TANJONG PAGAR|
|flat_type|categorical (ordinal)|type of the resale flat unit, e.g. 3 ROOM|
|block|categorical (nominal)|block number of the resale flat, e.g. 454|
|street_name|categorical (nominal)|street name where the resale flat resides, e.g. TAMPINES ST 42|
|storey_range|categorical (ordinal)|floor level (range) of the resale flat unit, e.g. 07 TO 09|
|floor_area_sqm|numeric (float64)|floor area of the resale flat unit in square metres|
|flat_model|categorical (nominal)|HDB model of the resale flat, e.g. Multi Generation|
|lease_commence_date|numeric (int64)|commencement year of the flat unit's 99-year lease|
|tranc_year|datetime64|year of resale transaction|
|tranc_month|datetime64|month of resale transaction|
|mid_storey|numeric (int64)|*median value of storey_range*|
|lower|numeric (int64)|*lower value of storey_range*|
|upper|numeric (int64)|*upper value of storey_range*|
|mid|numeric (int64)|*middle value of storey_range*|
|full_flat_type|categorical (nominal)|combination of flat_type and flat_model|
|address|categorical (nominal)|*combination of block and street_name*|
|floor_area_sqft|numeric (float64)|floor area of the resale flat unit in square feet|
|hdb_age|numeric (int64)|number of years from lease_commence_date to present year|
|max_floor_lvl|numeric (int64)|highest floor of the resale flat|
|year_completed|numeric (int64)|year which construction was completed for resale flat|
|residential|categorical (boolean)|boolean value if resale flat has residential units in the same block|
|commercial|categorical (boolean)|boolean value if resale flat has commercial units in the same block|
|market_hawker|categorical (boolean)|boolean value if resale flat has a market or hawker centre in the same block|
|multistorey_carpark|categorical (boolean)|boolean value if resale flat has a multistorey carpark in the same block|
|precinct_pavilion|categorical (boolean)|boolean value if resale flat has a pavilion in the same block|
|total_dwelling_units|numeric (int64)|total number of residential dwelling units in the resale flat|
|1room_sold|numeric (int64)|number of 1-room residential units in the resale flat|
|2room_sold|numeric (int64)|number of 2-room residential units in the resale flat|
|3room_sold|numeric (int64)|number of 3-room residential units in the resale flat|
|4room_sold|numeric (int64)|number of 4-room residential units in the resale flat|
|5room_sold|numeric (int64)|number of 5-room residential units in the resale flat|
|exec_sold|numeric (int64)|number of executive type residential units in the resale flat block|
|multigen_sold|numeric (int64)|number of multi-generational type residential units in the resale flat block|
|studio_apartment_sold|numeric (int64)|number of studio apartment type residential units in the resale flat block|
|1room_rental|numeric (int64)|number of 1-room rental residential units in the resale flat block|
|2room_rental|numeric (int64)|number of 2-room rental residential units in the resale flat block|
|3room_rental|numeric (int64)|number of 3-room rental residential units in the resale flat block|
|other_room_rental|numeric (int64)|number of "other" type rental residential units in the resale flat block|
|postal|categorical (nominal)|postal code of the resale flat block|
|latitude|numeric (float64)|latitude based on postal code|
|longitude|numeric (float64)|longitude based on postal code|
|planning_area|categorical (nominal)|government planning area that the flat is located|
|mall_nearest_distance|numeric (float64)|distance (in metres) to the nearest mall|
|mall_within_500m|numeric (float64)|number of malls within 500 metres|
|mall_within_1km|numeric (float64)|number of malls within 1 kilometre|
|mall_within_2km|numeric (float64)|number of malls within 2 kilometres|
|hawker_nearest_distance|numeric (float64)|distance (in metres) to the nearest hawker centre|
|hawker_within_500m|numeric (float64)|number of hawker centres within 500 metres|
|hawker_within_1km|numeric (float64)|number of hawker centres within 1 kilometre|
|hawker_within_2km|numeric (float64)|number of hawker centres within 2 kilometres|
|hawker_food_stalls|numeric (int64)|number of hawker food stalls in the nearest hawker centre|
|hawker_market_stalls|numeric (int64)|number of hawker and market stalls in the nearest hawker centre|
|mrt_nearest_distance|numeric (float64)|distance (in metres) to the nearest MRT station|
|mrt_name|categorical (nominal)|name of the nearest MRT station|
|bus_interchange|categorical (boolean)|boolean value if the nearest MRT station is also a bus interchange|
|mrt_interchange|categorical (boolean)|boolean value if the nearest MRT station is a train interchange station|
|mrt_latitude|numeric (float64)|latitude (in decimal degrees) of the the nearest MRT station|
|mrt_longitude|numeric (float64)|longitude (in decimal degrees) of the nearest MRT station|
|bus_stop_nearest_distance|numeric (float64)|distance (in metres) to the nearest bus stop|
|bus_stop_name|categorical (nominal)|name of the nearest bus stop|
|bus_stop_latitude|numeric (float64)|latitude (in decimal degrees) of the the nearest bus stop|
|bus_stop_longitude|numeric (float64)|longitude (in decimal degrees) of the nearest bus stop|
|pri_sch_nearest_distance|numeric (float64)|distance (in metres) to the nearest primary school|
|pri_sch_name|categorical (nominal)|name of the nearest primary school|
|vacancy|numeric (int64)|number of vacancies in the nearest primary school|
|pri_sch_affiliation|categorical (boolean)|boolean value if the nearest primary school has a secondary school affiliation|
|pri_sch_latitude|numeric (float64)|latitude (in decimal degrees) of the the nearest primary school|
|pri_sch_longitude|numeric (float64)|longitude (in decimal degrees) of the nearest primary school|
|sec_sch_nearest_dist|numeric (float64)|distance (in metres) to the nearest secondary school|
|sec_sch_name|categorical (nominal)|name of the nearest secondary school|
|cutoff_point|numeric (int64)|PSLE cutoff point of the nearest secondary school|
|sec_sch_affiliation|categorical (boolean)|boolean value if the nearest secondary school has an primary school affiliation|
|sec_sch_latitude|numeric (float64)|latitude (in decimal degrees) of the the nearest secondary school|
|sec_sch_longitude|numeric (float64)|longitude (in decimal degrees) of the nearest secondary school|

---

### Brief Summary of Analysis

#### Key Takeaways


1. The following features are included in your predictive model:

| Feature of Importance | Datatype | Proposed Relationship wth Target Variable based on EDA |
|---|---|---|
|`hdb_age`|numeric (int64)|inversely proportionate - as hdb age increases/ remaining lease period decreases, causing the value of the flat to depreciate |
|`max_floor_lvl`|numeric (int64)|directly proportionate - as the maximum floor level of the project increases, the value of the units within the development appreciates |
|`floor_area_sqft`|numeric (float64)|directly proportionate - as the floor area (sqft) increase the value of the unit increases|
|`mall_nearest_distance`|numeric (float64)|inversely proportionate - the nearer you are to the mall, the higher the value of your property|
|`hawker_nearest_distance`|numeric (float64)|proximity to hawker has no apparent effect on resale price|
|`mrt_nearest_distance`|numeric (float64)|inversely proportionate - the nearer you are to a transportation node, the higher the value of your property|
|`bus_stop_nearest_distance`|numeric (float64)|directly proportionate - the further you are from a bus stop, the higher the value of the property |
|`pri_sch_nearest_distance`|numeric (float64)|inversely proportionate - the nearer you are to a primary school, the higher the value of your property|
|`sec_sch_nearest_dist`|numeric (float64)|directly proportionate - the further you are from a secondary school, the higher the value of your property|
|`flat_type_cat`|numeric (int8)|label encoded - the larger the flat type, the higher the value of the unit|
|`storey_range_cat`|numeric (int8)|label encoded - the higher the storey range of the unit, the higher the value of the unit|
|'flat_model_Apartment', 'flat_model_Maisonette', 'flat_model_Model A', 'flat_model_Multi Generation', 'flat_model_New Generation', 'flat_model_Specia' |numeric (uint8)|dummy encoded - no apparent trend for resale price of different flat models|
|'planning_area_west', 'planning_area_north_east', 'planning_area_east', 'planning_area_north' |numeric (uint8)|dummy encoded - flats located in the central region were priced the highest, followed by flats in the west, north-east, and the east, with flats in the north region commanding the lowest resale prices|

<br> 

2. Model Selection (Equation): 𝑦̂ =𝛽0+𝛽1𝑥1+⋯+𝛽𝑁𝑥𝑁

3. Optimization Algorithm Selection: Linear Algebra (Direct Solution)

4. Loss Function Selection: $$RMSE = \sqrt{\frac{1}{n}\sum_{i=1}^n(y_i-\hat{y}_i)^2}$$

---

#### Business Recommendations
<details> <summary> 1.  Which features appear to add the most value to a home? </summary>
    <br>
Based on the coefficients of the first trial model, the following features are as follows:
    - `flat_model_Special` (141k per unit increase), 
    <br>
    - `flat_model_Multi Generation` (120k per unit increase), 
    <br>
    - `floor_area_sqft` (77k per unit increase), 
    <br> 
    - `flat_model_Maisonette` (68k per unit increase),
    <br>
    - `flat_model_New Generation` (41k per unit increase),
    <br>
    - `max_floor_lvl` (23k per unit increase), 
    <br>
    - `flat_type_cat` (21k per unit increase),
    <br> 
    - `storey_range_cat` (19k per unit increase),
    <br>
    - `flat_model_Apartment` (14k per unit increase),
    <br>
    - `flat_model_Model A` (13k per unit increase). 

</details> 
    <br> 
    
<details><summary> 2. Which features hurt the value of a home the most? </summary>
    <br>
Based on the coefficients of the first trial model, the following features are as follows:
    <br>
    - `planning_area_north` (-162k per unit increase), 
    <br>
    - `planning_area_west` (-126k per unit increase), 
    <br>
    - `planning_area_north_east` (-91k per unit increase), 
    <br> 
    - `planning_area_east` (-79k per unit increase),
    <br>
    - `hdb_age` (-32k per unit increase),
    <br>
    - `hawker_nearest_distance` (-23k per unit increase), 
    <br>
    - `mrt_nearest_distance` (-21k per unit increase),
    <br> 
    - `mall_nearest_distance` (-5k per unit increase).

</details> 
    
---   

#### Limitations of the Project

- Aspects that homeowners could improve in their homes to increase the value such as interior design, maintainence fees, have not been taken into consideration. 
- The model is unlikely able to generalize to other cities. 


