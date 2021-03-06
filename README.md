# Clothes Recommendation System
## [DataSet](https://www.kaggle.com/rmisra/clothing-fit-dataset-for-size-recommendation)
* Began with data attributed on customers fit and rating, a data-set that was collected from “ModCloth” and “RentTheRunWay” provided on Kaggle.
* The dataset includes User’s measurements, items purchased, and ratings for the purchased items.
* Items though did not include names, hence basing prediction on item id numbers.
* Dataset is highly sparse, with most products and customers having only a single transaction.

## Exploratory Data Analysis
1. Dealing with highly sparse data originally, but primarily looking at at the main three factors for the recommendation system; usernames, item ids, and ratings.
2. Removed 68 NaNs from our ratings column.
3. Number of customers: 32,399  Number of products: 1,376 Number of transactions: 82,790
![Screen Shot 2019-09-05 at 1.02.00 PM](https://github.com/klemma14/Clothes-Recommendation-System/blob/master/Data-Visuals/Screen%20Shot%202019-09-05%20at%201.02.00%20PM.png)
* Average amount of times an item is bought is around 60 times.
* Average amount of items an individual bought was close to 3 items.
* Most customers seem to be happier with their purchases, rather than being disappointed.

## Recommendation System Plan
1. The best choice was a Model-Based Collaborative Filtering method using Surprise.
2. Memory-Based; Can Use multiple different similarity metrics to find out out which performs best: Pearson, Cosine, Jaccard.
3. Model-Based; Using Singular Value Decomposition (SVD) to decrease the dimensions of our utility matrix and extract latent factors.
SVD essentially turning our Recommendation problem into an Optimization one.
4. Root Mean Square Error (RMSE) is our metric for performance.
5. Using Model-Based (Matrix factorization) rather than Memory-Based collaborative filtering to make faster predictions with less data than the original.

## Results
* Memory-Based: Cosine similarity outperformed the Pearson method
Best Model performance using Neighbor-Based methods was KNN_Baseline with Cosine similarity.
![Screen Shot 2019-09-05 at 1.02.20 PM](https://github.com/klemma14/Clothes-Recommendation-System/blob/master/Data-Visuals/Screen%20Shot%202019-09-05%20at%201.02.20%20PM.png)
* Model-Based Approach: GridSearch to find best parameters for SVD, changing our n_factors (10, 20, 30, 50, 100) and reg_all (0.2, 0.4, 0.6, 0.7).
Using different Optimal Parameters from the GridSearch to train SVD.

![Screen Shot 2019-09-05 at 1.02.34 PM](https://github.com/klemma14/Clothes-Recommendation-System/blob/master/Data-Visuals/Screen%20Shot%202019-09-05%20at%201.02.34%20PM.png)

## Future Steps
* Since the dataset only included item id numbers, not item names themselves, I plan to use NLP on the reviews column to search for key words for the name of the items. I may also just scrape the online item ids from websites the data was found on, then just match ids with name of item, which will allow the ability to see what the recommendation system is suggesting.
