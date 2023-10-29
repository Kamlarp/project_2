### Problem Statement

The problems we will address is "What should be the housing price (y) giving the variables (X) such as

    location features (province, district, subdistrict, address, latitude, longtitude)
    housing features (property type, total units, bedrooms, baths, floor area, floor level, land area)
    neighborhood features (nearby stations, nearby bus stops, nearby super markets)
    time features (year and month built)"

The audience of this problem is the house/condo/apartment sellers in Bangkok and sorrounding provinces. So they can sell the house at the best price by using the predicted price as the baseline for advertising and sales negotiation.

We will address this problem by creating the model that predict price with low errors (or biases), evaluated by Root Mean Squared Error (RMSE), yet have the low variance, so it can be used for other different cases as well.

We will use the linear regression model, Ridge model and Lasso model.


### Conclusion & Recommendation
 
based on house data of 13832 houses in the market within 3 provinces including bangkok, samutprakan, and nonthaburi, 
        100% of house prices are between 0.48 mil bht and 9.99 mil bht 
        50% of house prices are between 2.25 mil bht and 5.50 mil bht 
        average price is at 4.30 mil bht 
        median price is at 3.50 mil bht

we found that there are several factors that are highly related to house price including 
        location (province, district, subdistrict) 
        size (floor levels, nbr of bothrooms, nbr of bedrooms) 
        surrounding areas (nbr of nearby market place and public transport) extra facilities

based on these factors, we able to come up with price prediction tool that help predict the price for price seller which are able to explain 70% of the target price. We can use this tool to predict the price of bangkok and surrounding provinces in the future. And for the other province, the tool is still be usable but need adjustment because some factors will be different such as public transports which do not exist in the other provinces
    
Which factors appear to be most significant to a home?

    location and property type
        location
            based on number below, we can see that there are huge difference between top 3 and bottom 3 subdistrict
            top 3 includes
                 M Silom                             9900000.0
                 StarView Rama 3                     8962000.0
                 Chimphli                            8900000.0
            bottom 3 include
                 624 Condolette Ladprao              1370000.0
                 Smart Condo Rama 2                  1435000.0
                 Khok Faet                           1550000.0
        Property type
            based on number below, we can see that there are also sizable difference between property type
                  Detached House                      5568336.0
                  Condo                               3923175.0 
                  Townhouse                           3331694.0
Which features appear to add the most value to a home?
        
        size (= floor area) and number of bathrooms  

Which features hurt the value of a home the most?
        
        density (total units), number of public transport (bus and train) 
        which might be applied that the homeowners still use the public transports instead of cars. 
 
What neighborhoods seem like they might be a good investment?
            
        in term of province, it is bangkok. in term of district, it is bangrank. in term of subdistrict, it is silom.    
---

### Datasets

based on train data set which contain house data of 13832 houses in the market within 3 provinces including bangkok, samutprakan, and nonthaburi 
    train = pd.read_json('data/train.json')
    test = pd.read_json('data/test.json')

---

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

    feature engineering
    linear regression
    linear regression scaled
    ridge
    ridge scaled
    lasso
    lasso scaled
    
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
    linear regression
    linear regression scaled
    ridge
    ridge scaled
    lasso
    lasso scaled