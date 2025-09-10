## Project Title
### Forecast Future Sales
**Author** : Shirish Wate

#### Executive summary

The objective of this project is to predict monthly sales volumes for every shop-item pair using historical daily sales data. The dataset features comprehensive metadata—including shops, items, categories for a Russian retail chain. The problem carries high impact in retail operations, enabling better inventory and demand management.

My approach included data cleanup, data integration and time-series matrix creation. Feature engineering strategies included extracting features hidden inside existing features such as city, category type, when the item was first sold, number of transactions in a month, adding lag variables (e.g., past 3 months’ sales), aggregated metrics (e.g., shop/item mean sales) etc. Lag and aggregation metric will be added in part 2 of the project. My modeling options included ARIMA time series model along with ensemble techniques such as XGBoost and LightGBM.

My findings suggest that strong feature engineering and ensemble modeling are pivotal in delivering accurate forecasts. As future extensions, experimentation with deep learning models and transformers could uncover further improvements and performance.

#### Rationale

It is important to have predictions for future sales (say a month in advance) for a store as it enables them to decide on resource allocation and inventory planing. A store can optimize their operations and plan for any potential issues there by improving their profitability and competitive edge.
	◦	It helps with planning in following areas.
    	▪	Managing inventory so the supply of items can fulfill the demand.
    	▪	Staffing the stores sufficiently
    	▪	Budgeting allocation for coming months
    	▪	Identify areas for growth so the store can focus on it.
    	▪	Setting sales goals that are achievable.
    	▪	Assess the effectiveness of marketing campaigns.
    	▪	Cash flow management and future investment planing by projecting revenue.
    	▪	Attracting potential investor to secure funding for expansion.
    	▪	Make proactive measures in case of sales decline.
    	▪	Under user trends and behavior and manage competition as well as invest to products that users like.

#### Research Question

what will be the total sale for every product in every store location of a retail chain next month?

#### Data Sources

I will be using the sales data for the Russian retail chain provided at kaggle for a duration od 33 months from Jan 2013 till oct 2015.
[Sales Data](https://www.kaggle.com/competitions/competitive-data-science-predict-future-sales/data)

#### Methodology

◦	EDA
	▪	Data cleanup
	▪	Since the data is for Russian stores, store names and product names are in Russian. I am thinking of using some kind of translation (ay be offline) to get some sense of data patterns visually.
	▪	Removing unwanted features
	▪	Discarding nulls, if they do not add any values.
	▪	Sales data is huge, so might need some memory management  including using smaller datatypes for some features.
	▪	Merging of Datasets, as there are multiple related data sets
	▪	Data Visualization
	▪	Removing outliers and correcting data if required.
	▪	Feature encoding for Category Type, City etc
	▪	Split data in to training and testing sets. I will use last one month data as testing set.
	▪	Perform Time Series analysis using ARIMA model as baseline for each store and item combination.
    ▪   I also plan to use LGBM and XGBRegressor and compare the RMSE of both these models to the ARIMA model and use the best one to forecast the  future sales. 
    ▪   In order to use the XGB and LGBM models, I will be adding mean and lag features of various means for cominations of features as part of the feature engineering. 
	▪	Forecast the results.

#### Results

* There seems to be a over all declining trend in the number of items sold
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
#### Next steps

So far I have perofrmed the Data cleaning, initial feature engineering and EDA. As next step, I will be performing part two of Feature engineering, to get the data ready for ensemble models like LGBM and XGBoost. This includes adding mean and lag feature over three months moving period (since the goal is to forecast monthly sales). Then using this engineered data , I will pefrform trainig nand predictions based on these models, and compare the MSE for all the models considered so far to arrive at the best model with least MSE.

Beyond the scope of this project, some deep learning models and transformers can be considered to further improve on the accuracy.

#### Outline of project

- [Project Notebook](https://github.com/shirishswate/CapstoneProject-StoreSalesForecast)



##### Contact and Further Information

- [Github](https://github.com/shirishswate)
- [LinkedIn](https://www.linkedin.com/in/shirishwate/)
- [wshirish@hotmail.com](mailto:wshirish@hotmail.com)
