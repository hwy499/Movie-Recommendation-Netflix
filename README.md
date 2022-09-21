<br>
<img src="https://cdn.slidesharecdn.com/ss_thumbnails/netflixprize-170320014819-thumbnail-4.jpg?cb=1489978383" width='25%'>
<h1> Netflix Prize Challenge - Movie Recommendation </h1>
<h3> Developed by Wenyi Hu </h3>
<br>

## Problem Description
Netflix is all about connecting people to the movies they love. To help customers find those movies, they developed world-class movie recommendation system: CinematchSM. Its job is to predict whether someone will enjoy a movie based on how much they liked or disliked other movies. Netflix use those predictions to make personal movie recommendations based on each customer’s unique tastes. And while Cinematch is doing pretty well, it can always be made better.

Now there are a lot of interesting alternative approaches to how Cinematch works that netflix haven’t tried. Some are described in the literature, some aren’t. We’re curious whether any of these can beat Cinematch by making better predictions. Because, frankly, if there is a much better approach it could make a big difference to our customers and our business.

The challenge's goal is to develop a system that could beat the RMSE accuracy of 0.9514 from their in-house developed recommendation system (the Cinematch) by 10%. In 2009, the prize was awarded to team ”BellKor’s Pragmatic Chaos” with RMSE of 0.8567 or 10.06% improvement. 

## About the Project
1. Predict the rating that a user would give to a movie that he/she has not yet rated (Rating from 1 to 5).
2. Minimize the difference between predicted and actual rating (RMSE).

## Source of data
The Netflix prize challenge data can be download from kaggle: https://www.kaggle.com/datasets/netflix-inc/netflix-prize-data

## Table of Contents
1. [Import Libraries](#1.-Import-Libraries)
2. [Load Data](#2.-Load-Data)
3. [EDA](#3.-EDA)
4. [Feature Engineering](#4.-Feature-Engineering)
5. [Machine Learning](#5.-Machine-Learning)
    1. [Baseline Model](#5.1-Baseline-Model)
    2. [Parameter Tuning](#5.2-Parameter-Tuning)
    3. [Ensemble](#5.3-Ensemble)
    4. [NN Black Box](#5.4-NN-Black-Box)
6. [Deep Learning](#6.-Deep-Learning)
    1. [Data Preprocessing](#6.1-Data-Preprocessing)
    2. [Build Model Architecture](#6.2-Build-Keras-Model-Architecture)
    3. [Train Model](#6.3-Train-Model)
    4. [Model Evaluation](#6.4-Model-Evaluation)
