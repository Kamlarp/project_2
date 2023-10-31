### Problem Statement

The problems we will address is "What should be the best home price?" and "how can increase value of my home? "

The audience of this problem is the sellers in Bangkok and sorrounding provinces. So they can sell the house at the best price by using the predicted price as the baseline for advertising and sales negotiation, and can improve their home for selling at better price.

We will address this problem by creating the model and evaluate it by R2 score, Root Mean Squared Error (RMSE), and result gap between train and test result.

We will use the linear regression model, Ridge model and Lasso model.

### Datasets

based on train data set which contain house data of 14,271 houses with 3 property types (condo, townhouse, detached house) and 3 provinces (bangkok, samutprakarn, nonthaburi) with 23 attributes below

    id                           int64
    province                    object
    district                    object
    subdistrict                 object
    address                     object
    property_type               object
    total_units                float64
    bedrooms                   float64
    baths                      float64
    floor_area                   int64
    floor_level                float64
    land_area                  float64
    latitude                   float64
    longitude                  float64
    nearby_stations              int64
    nearby_station_distance     object
    nearby_bus_stops           float64
    nearby_supermarkets        float64
    nearby_shops                 int64
    year_built                   int64
    month_built                 object
    facilities                  object
    price                        int64
    
    
### Data Processing

---------------import---------------------

Import the library
Load datasets to jupyter notebook

---------------train data ----------------

Check train data

    check shape
    check head
    check data type
    check descriptive statistics
    check mode
    check distribution
    check outliers
    check null values
    check descriptive statistics by propertype

clean & transform train data

    treat missing data
    treat outlier data
    treat wrong data type
    treat inaccurate data
    Extract categorical data into numerical data

EDA train data

    study of target price
    check features' relationship with target price
    check features' p value

build and evaluate the model on train data

    modeling appraoch
    feature engineering
    linear regression
    linear regression scaled
    ridge
    ridge scaled
    lasso
    lasso scaled
    modeling result comparison and summary
    
---------------test data ----------------

Check test data

    check shape
    check head
    check data type
    check descriptive statistics
    check mode
    check distribution
    check outliers
    check null values
    check descriptive statistics by propertype

clean & transform test data

    treat missing data
    treat outlier data
    treat wrong data type
    treat inaccurate data
    Extract categorical data into numerical data

predict target price on test data

    feature engineering
    selected model prediction

    
### Conclusion & Recommendation
 
#### Conclusion
based on house data of 13832 houses in the market within 3 provinces including bangkok, samutprakan, and nonthaburi, 100% of house prices are between 0.48 mil bht and 9.99 mil bht 50% of house prices are between 2.25 mil bht and 5.50 mil bht average price is at 4.30 mil bht median price is at 3.50 mil bht

we found that there are several factors that are highly related to house price including location (province, district, subdistrict) property type including condo, townhouse, and detached house size (floor levels, nbr of bothrooms, nbr of bedrooms) surrounding areas (nbr of nearby market place and public transport) extra facilities

based on these factors, we able to come up with price prediction tool that help predict the price for price seller which are able to explain 70% of the target price. We can use this tool to predict the price of bangkok and surrounding provinces in the future.

however for the other provinces, the tools need adjustment because some factors will be different such as public transports which do not exist in the other provinces.

Based on our Modeling approach

    1) we will input all features that are available except 3 following columns
            land area because it has too many null value and its null value not randomly missing; it only missing in condo property type
            year built because it has too many null value and it does not make sense to impute year value with mean, median, or mode data
            month built because month should not be useful with year built columsn
            
    2) after feature all available columns, we will tune the performance of the model by using regularization
    
    3) we will use 6 models including
            linear regression model
            linear regression model with scaling
            ridge model
            ridge model with scaling
            lasso model
            lasso model with scaling
            
    4) then we will evaluate each model with R2 and RMSE and select one the have best result
            test result have high R2 score
            test result have low RMSE
            test result have small gap from train result in term of R2 score
            test result have small gap from train result in term of RMSE
            
based on the appraoch, ridge with 𝛼=10 wihtout scaling provide the best R2 score, RMSE, gap with between train and test result
      the model have error that can generate price deviatopm at 1,171,893 bht 
      based on top coefficient in the result below, we recommend the following feature to add value to home price  
           - number of baht room add 6334k bht per room 
           - size of floor area add 633k bht per 1sqm
           - number of bed rooms add 458 bht per room 
           - being in klongtun nua subdistrict add 266k baht per room
           - being detached house add 314k bht 
           - increase 1 floor level add 261k bht

#### Business Recommendation

Which factors appear to be most significant to a home?

        size(number of bahtroom, number of bed room, floor area) location (bangkok central district such as klongton nua) and property type (detached house)

      
Which features appear to add the most value to a home?

       - number of baht room add 6334k bht per room 
       - size of floor area add 633k bht per 1sqm
       - number of bed rooms add 458 bht per room 
       - being in klongtun nua subdistrict add 266k baht per room
       - being detached house add 314k bht 
       
Which features hurt the value of a home the most?

       - prperty type = townhouse
       - high density (too many total units in the same place)
       - location in Nonthaburi province
 
What neighborhoods seem like they might be a good investment?

          in term of province, it is bangkok. 
          in term of district, it is wattana
          in term of subdistrict, it is klongton nua.