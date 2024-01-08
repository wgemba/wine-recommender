# Wine Recommender System Using Unsupervised Content-Based Filtering

This project created a sophisticated recommendation engine designed to offer personalized wine suggestions to users based on their individual taste preferences. Leveraging a comprehensive dataset of wine reviews, the system employs natural language processing (NLP) techniques to extract qualitative features from wine descriptions, creating detailed taste profiles. The heart of the system lies in neural network models that generate user and item vectors, facilitating accurate predictions of user ratings. Users can interact with the system by providing taste preferences, enabling the recommender to deliver tailored wine recommendations. With a focus on scalability and user interactivity, the project demonstrates a seamless integration of machine learning and user-friendly functionalities to enhance the wine discovery experience.

## Table of Contents
- [About](#about)
- [Dataset](#dataset)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Usage](#usage)
- [Results](#results)

## About

This project explores the use of unsupervised machine learning methods, namely content-based filtering, to derive an accurate way of predicting wine preferences and provide wine recommendations to different tasters in the world of oenology. Leveraging natural language processing (NLP) techniques, the system deciphers the intricate descriptions of wines, translating them into quantitative features for analysis. The neural network models employed in this project form user and item vectors, enabling accurate predictions of user ratings based on individual taste preferences.

The primary goal of this project is to provide users with a tailored and enjoyable wine discovery experience. By understanding the unique palate of each user, the system can recommend wines that align with their preferences, creating a more engaging and satisfying exploration of the world of wines. The project addresses the challenge of information overload, making it easier for users to navigate the vast array of available wines and discover new favorites.

Significantly, this project goes beyond the conventional collaborative filtering approach by incorporating content-based filtering, ensuring that recommendations are not only based on user similarities but also on the inherent characteristics of the wines themselves. This hybrid approach enhances the precision of recommendations, offering users a more personalized and relevant selection.

In essence, the Wine Recommender System caters to both wine enthusiasts seeking new discoveries and novices navigating the complex landscape of wines. By providing tailored recommendations and promoting a deeper understanding of individual taste preferences.

<b>*Note:</b>The project in its current form only predicts the rating that a new taster, previously unseen to the training data, would give to a each wine based on the their input for a select number of taster profile features (i.e., aged,fruity,earthy, etc.)

## Dataset

Briefly describe the dataset used in the project. Include information about the source, size, and any preprocessing steps performed.
The source dataset was derived from [Kaggle](https://www.kaggle.com/datasets/zynicide/wine-reviews) and contains approximately 129,971 reviews and 13 features. Preprocessing involved extracting relevant features such as taste profiles from textual descriptions, cleaning and organizing the data, and handling missing values to ensure the dataset's quality and coherence. From this data set, I was able to engineer two separte data sets - one for the taster that includes averages for each taste feature for each wine reviewed, and one for the wines that included one-hot binary values that indicate which features are present in each wine.

## Features

The source data set includes the following features:

Data columns (total 13 columns):<br>
 No. &nbsp;  Column    &nbsp;             Non-Null Count &nbsp;  Dtype <br> 
--- &nbsp; ------        &nbsp;         --------------  &nbsp; -----  <br>
 0  &nbsp; country      &nbsp;          129908 non-null &nbsp; object <br>
 1  &nbsp; description    &nbsp;        129971 non-null  &nbsp;object <br>
 2  &nbsp; designation    &nbsp;        92506 non-null  &nbsp; object <br>
 3  &nbsp; points        &nbsp;         129971 non-null  &nbsp; int64  <br>
 4  &nbsp; price           &nbsp;       120975 non-null &nbsp; float64<br>
 5  &nbsp; province        &nbsp;       129908 non-null &nbsp; object <br>
 6  &nbsp; region_1           &nbsp;    108724 non-null &nbsp; object <br>
 7  &nbsp; region_2         &nbsp;      50511 non-null  &nbsp; object <br>
 8  &nbsp; taster_name       &nbsp;     103727 non-null &nbsp; object <br>
 9   &nbsp;taster_twitter_handle &nbsp; 98758 non-null   &nbsp;object <br>
 10 &nbsp; title            &nbsp;      129971 non-null &nbsp; object <br>
 11  &nbsp;variety          &nbsp;      129970 non-null  &nbsp;object <br>
 12  &nbsp;winery            &nbsp;     129971 non-null  &nbsp;object <br>
dtypes: &nbsp;float64(1), &nbsp;int64(1), &nbsp;object(11)<br>

Following and inital exploratory data analysis of the data set, only 'description', 'points', 'price', 'taster_name', 'title', and 'variety' were chosen to be used. It is the feature 'description' that formed the basis for deriving the taste palette profile of each wine. Using ChatGPT 3.5 I generate a list of 200 frequently used words to describe the taste palette of wine. Using natural language processing, I extracted the unique set of words from each wine review and then took the union set across all wines. With this union set I one-hot encoded each 'description' to derive and additional 183 binary features. Similar encoding technique was applied to the 'variety' attribute. 

## Technologies Used

 - Python,
 - Pandas,
 - NumPy,
 - Scikit-Learn,
 - TensorFlow 2.0,
 - Keras,
 - Natural Language Processing Toolkit (NLTK)

## Usage

Included in this repository are three files: exploratory_data_analysis.ipynb, feature_engineering_preprocessing.ipynb, and neuralnetwork_filtering.ipynb. Assumeing one has downloaded the data set from the Kaggle source (one only needs the csv file named 'winemag-data_130k-v2.csv'), one can run each file sequentially. 
- exploratory_data_analysis.ipynb is simply a data exploration that takes the raw data and performs an EDA.
- feature_engineering_preprocessing.ipynb takes the source data and outputs three processed datasets: one wine dataset (item), one taster dataset (user), and one observered/actual ratings given by each taster for each wine.
- neuralnetwork_filtering.ipynb takes the three outputs from the feature_engineering_preprocessing.ipynb file and, after performing some additional table manipulation, creates a the neural network architecture that trains on the data sets and ultimately performs a prediction.

## Results

![image](https://github.com/wgemba/wine-recommender/assets/134420287/1cf3550d-c23c-4363-8e14-6e4fc8b4b269)

Final test loss: 0.0070
