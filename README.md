## Project Title
### Forecast Future Sales
**Author** : Shirish Wate

#### Executive summary

The objective of this project is to predict monthly sales volumes for every shop-item pair using historical daily sales data. The dataset features comprehensive metadata—including shops, items, categories for a Russian retail chain. The problem carries high impact in retail operations, enabling better inventory and demand management.

My approach included data cleanup, data integration and time-series matrix creation. Feature engineering strategies included extracting features hidden inside existing features such as city, category type, when the item was first sold, number of transactions in a month, adding lag variables (e.g., past 3 months’ sales), aggregated metrics (e.g., shop/item mean sales) etc. My modeling options included Polynomial Regression, ARIMA time series model along with ensemble techniques such as XGBoost and LightGBM.

My findings suggest that strong feature engineering and ensemble modeling are pivotal in delivering accurate forecasts. As future extensions, experimentation with deep learning models and transformers could uncover further improvements and performance.

#### Business Understanding

It is important to have predictions for future sales (say a month in advance) for a store as it enables them to decide on resource allocation and inventory planing. A store can optimize their operations and plan for any potential issues there by improving their profitability and competitive edge.
* It helps with planning in following areas.
    * Managing inventory so the supply of items can fulfill the demand.
    * Staffing the stores sufficiently
    * Budgeting allocation for coming months
    * Identify areas for growth so the store can focus on it.
    * Setting sales goals that are achievable.
    * Assess the effectiveness of marketing campaigns.
    * Cash flow management and future investment planing by projecting revenue.
    * Attracting potential investor to secure funding for expansion.
    * Make proactive measures in case of sales decline.
    * Understand user trends and behavior and manage competition as well as invest to products that users like.

#### Research Question

what will be the total sale for every product in every store location of a retail chain next month?

#### Data Sources

A large Russian retail chain operating across about 60 stores provided provided daily sales data for a duration of 33 months from Jan 2013 till oct 2015.
[Sales Data](https://www.kaggle.com/competitions/competitive-data-science-predict-future-sales/data)

#### Directory Structure

The Github repository contains following folders
* data - Contains all the data files including test and training data files.
* images - Contains all the charts and graphs generated during EDA and model training and inferencing.
* presentation - Contains the powerpoint presentation for the Sales forecasting project.

Main folder (project root) contains following files
* README.md - Readme file with project details.
* Summary.docx - Word document version of the project summary
* capstone-project.ipynb - Main Jupyter notebook for the project.
  
#### Methodology

* EDA
   *	Since the data is for Russian stores, store names and product names are in Russian. I used a translation tool to get some sense of data patterns visually.
	*	Removed unwanted features
	*	Discarded nulls, if they do not add any values.
	*	Deleted duplicate records.
	*	Sales data is huge, so performed memory management by using smaller datatypes for some features.
	*	Merged Datasets, as there are multiple related data sets
	*	Visualizalized data using charts. This gives some sense of data patterns visually.
	*	Removed outliers and corrected data.
	*	Encoded Category Type and City  features.
	*	Split data in to training, validation and testing sets. I used last one month data as testing set and month 32 and33 for validation set.
	*	As a baseline model, used Polynomial Regression and performed GridSearchCV to find the best degree.
	*	Perform Time Series analysis using ARIMA model for each store and item combination. First iteration took a long ime, when i was aggregating monthly alecount for each store-item combination. Then I changed the logic to aggregate the monthly counts for the whole dataset and then looped through each store-item combinaiton. This made the training process drastically faster. 
    *   I also used LGBM and XGBRegressor and compare the RMSE of both these models to the Polynomial and ARIMA model.  
    *   I added mean and lag features of various cominations of features as part of the feature engineering, along with the mean and standard deviations of the lag features and the change in the lag features. This was done to capture trend and momentum of the trend for the monthly sales counts.

#### Data Understanding

##### Data Summary
There are five data files available.
* Shops.csv - This file contains detals for each shop , such as shop_id, shop_name. There are 59 stores for the retail chain.
* item_categories.csv - This file contains details about the item categories such as item_category_id, item_category_name. There are 83 categorys available.
* items.csv - This file contains details of each item that is available for sale at the stores such as item_name, item_category_id and item_id. There are around 22K items available for sale across all the 59 stores.
* sales_train.csv - This file contain the data available for training. It has information such as daily sales counts for each item in each store and their price.
* test.csv - this file only contains store_id and item_id and is suppose to be used for testing forecasting the sale for next month for each  store-item combination in the file.

##### Observations 

* There seems to be a over all declining trend in the number of items sold.
![Monthly Item Sale](images/bar_monthly_items_sold.png) 
  
* There are couple of months where the sales have gone up and it could related to some promotions or events during those months.
* Most of the shops have similar sales overall.
* Few shops are selling below average
* couple of shops are are rockstars such as shop-ids 25, 28, 31, 42, and 54
* Total sale amount by each shop more or less follows the trend of number of items sold, with exception of couple of shops. This indicates these shops tend to sale costlier items.
* "MockBa" which is Russian for Moscow, seems to be the city where shops are selling the most.
* All other citys are selling way lower but are close to each other, with couple of cities shining a bit.
* This indicates, majority of the sell is happening in Big city , Moscow in this case.
* Four category types are prominent, Игры i.e "Game", Кино i.e "Movies", Музыка i.e "Music" and Подарки i.e "Gifts"
* Most of the category items are selling in very low range, whith just a handfull outshining.
* This indicates that a handfull of category item sell significantly more than others.

#### Results


#### Next steps

So far I have perofrmed the Data cleaning, initial feature engineering and EDA. As next step, I will be performing part two of Feature engineering, to get the data ready for ensemble models like LGBM and XGBoost. This includes adding mean and lag feature over three months moving period (since the goal is to forecast monthly sales). Then using this engineered data , I will pefrform trainig nand predictions based on these models, and compare the MSE for all the models considered so far to arrive at the best model with least MSE.

Beyond the scope of this project, some deep learning models and transformers can be considered to further improve on the accuracy.

#### Outline of project

- [Project Notebook](https://github.com/shirishswate/CapstoneProject-StoreSalesForecast/blob/main/project.ipynb)



##### Contact and Further Information

- [Github](https://github.com/shirishswate)
- [LinkedIn](https://www.linkedin.com/in/shirishwate/)
- [wshirish@hotmail.com](mailto:wshirish@hotmail.com)
