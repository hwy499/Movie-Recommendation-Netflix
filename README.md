<br>
<img src="https://cdn.slidesharecdn.com/ss_thumbnails/netflixprize-170320014819-thumbnail-4.jpg?cb=1489978383" width='25%'>
<h1> Netflix Prize Challenge - Movie Recommendation </h1>
<h3> Developed by Wenyi Hu </h3>
<br>

## Table of Contents
1. [Recommendation System](#Recommendation-System)
2. [Problem Description](#Problem-Description)
3. [Source of Data](#Source-of-Data)
4. [Goals of This Project](#Goals-of-This-Project)
5. [About the Project](#About-the-Project)
6. [Notebook Details](#Notebook-Details)

## Recommendation System
A recommendation system is a subclass of Information filtering Systems that seeks to predict the rating or the preference a user might give to an item. In simple words, it is an algorithm that suggests relevant items to users. For example, the system recommends which movie to watch in Netflix website, suggests which product to buy in e-commerce platform, and proposes which people to connect in Linkedin. Almost any business can benefit from a recommendation system, because a good recommendation can increase user’s satisfaction, thus increase profits, loyalty, and decreases churn.

There are two types of recommendation system: content-based filtering and collaborative based filtering. The content-based filtering shows relevant items using the content of the previously searched items by the users. The collaborative-based filtering is based on the interest and preference of other similar users and items. Most of movie recommendation system is collaborative-based filtering which also has two classes: one is user-based collaborative filtering by using the rating of similar users; the other is item-based collaborative filtering using the user's own rating on similar items. 

Implementation of recommendation systems is of two types: model-based and memory-based. Model-based approach builds a model of users to learn their preferences and is created using Machine Learning techniques like regression, clustering, classification, etc. Memory-based approach uses the entire user-tiem dataset to generate a recommendation using statistical techniques like Pearson Correlation, Euclidean distance, Cosine Similarity, etc.

Depending on the type of recommendation systems, the matrix used for evaluation is different. Mean Absolute Error (MAE) and Root Mean Squared Error (RMSE) give the average of the difference between actual values and predicted values in a model-based recommendation system. They remove the negative sign by squaring the predictions. RMSE also normalizes the mean result to the same scale and is better at dealing with outliers. Some similarity metrics, like Cosine, Mean Square Difference (MSD), and Pearson, compute the similarity between all pairs of users(or items) in a memory-based recommendation system.

## Problem Description
Netflix is all about connecting people to the movies they love. To help customers find those movies, they developed world-class movie recommendation system: CinematchSM. Its job is to predict whether someone will enjoy a movie based on how much they liked or disliked other movies. Netflix use those predictions to make personal movie recommendations based on each customer’s unique tastes. And while Cinematch is doing pretty well, it can always be made better.

Now there are a lot of interesting alternative approaches to how Cinematch works that netflix haven’t tried. Some are described in the literature, some aren’t. The challenge's goal is to develop a system that could beat the RMSE accuracy of 0.9514 from their in-house developed recommendation system (the Cinematch) by 10%. In 2009, the prize was awarded to team "BellKor's Pragmatic Chaos" with RMSE of 0.8567 or 10.06% improvement. 

## Source of Data
This dataset was constructed to support participants in the Netflix Prize. The datails of Netflix prize challenge data can be found in kaggle: https://www.kaggle.com/datasets/netflix-inc/netflix-prize

The movie rating files contain over 100 million ratings from 480 thousand randomly-chosen, anonymous Netflix customers over 17 thousand movies, and over 100 million records in total. The data were collected between November 1999 and December 2005 and reflect the distribution of all ratings received during this period. The ratings are on a scale from 1 to 5 (integral) stars. To protect customer privacy, each customer id has been replaced with a randomly-assigned id. The date of each rating and the title and year of release for each movie id are also provided.

## Goals of This Project
1. Predict the rating that a user would give to a movie that he/she has not yet rated (Rating from 1 to 5).
2. Minimize the difference between predicted and actual rating (RMSE).

## About the Project
All provided moving rating records (100,480,507 rows) were loaded for exploratory data analysis (EDA), presenting the distribution of ratings, the rating trends over years, months, and weeks, and the density of ratings per user or per movie. 

Due to the limit of memory and storage, a smaller dataset whose users gave the most rates on most movies was choosen for modelling, with 1000 top rated movies and 10,000 top users. The 12% of the rating records are retained from the whole data. 

Matrix factorization techniques are commonly used in a model-based collaborative filtering recommendation system. During machine learning, the SVD algorithm from scikit-Surprise package (source: https://surprise.readthedocs.io/en/stable/index.html) was used for matrix factorization of the recommendation system. SVD decreases the dimensions of the user-movie interaction matrix by using the latent factor which captures the similarity between users and movies. A list of SVD hyperparameters was tuned in GridSearchCV to get the best estimator by minimizing RMSE score. The performance of model was measured on predicting the ratings of an item for a user by RMSE: biased RMSE = 0.7053, unbiased RMSE = 0.7704.

![image](https://user-images.githubusercontent.com/112957640/192361276-5cf8a5c1-a935-45db-a5c3-c3f84bcc9452.png)

A deep learning model was also applied on the small dataset by using matrix factorization to predict the rating based on a sparse user-movie interaction matrix. The model architecture was built on the top of Keras (source: https://keras.io/api/). Embadding layer was used for building user matrix and movie matrix. Dot and Concatenate layers were used for building rating matrix. Dense layers were used for output. Model was compiled with the loss function = 'mean_squared_error', optimizer = Adam, and metrics = RootMeanSquaredError. Model was fit on the train set and valided on the valid set. The predicted result was evaluated by RMSE = 0.80.

![image](https://user-images.githubusercontent.com/112957640/191597383-37f61234-0ed2-4af8-9128-9616fe1b59fb.png)

## Notebook Details
1. Load Data and EDA
    - All movie rating files with movie_id, user_id, rating, date were loaded with EDA.
2. Machine Learning
    - SVD algorithm tuned in GridSearchCV was used.
3. Deep Learning
    - Keras architecture network was built.
