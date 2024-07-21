# Statistical modelling 
It is a form of mathematical modelling that involves statistics to estimate or predict real-world behaviours, trends, and future outcomes based on data. It involves the construction of a statistical model, which is a formal representation of relationships between variables, typically expressed in the form of mathematical equations. 

## What is Statistical Modelling? And How It’s Different From Machine Learning Model Training?
Statistical modelling is a mathematical framework used to describe the relationships between variables in the form of equations, usually involving stochastic elements (randomness). It is primarily focused on inference, which means understanding the relationships between variables and quantifying how certain factors influence outcomes.

Statistical models are built based on assumptions about the data distributions and the nature of the relationships between variables. Common examples include linear regression, logistic regression, and analysis of variance (ANOVA).

The difference between statistical modelling and machine learning model training is that statistical modelling is primarily concerned with inference. It seeks to understand the underlying relationships between variables and to quantify how predictors influence the response variable. It often tests hypotheses about these relationships.

Whereas Machine Learning model training focuses on prediction. The primary goal is to create models that can make accurate predictions on new, unseen data. Machine learning often cares less about the ‘why’ of the data relationships and more about the ‘how well’ it can predict the outcome.

## Statistical Modelling of music features using Python
Aim is to identify what music features determine the popularity of music tracks.

### Dataset:
Dataset using here is from 'Statso'.
Statso is a Data Science Community to Find Case Studies, Datasets and more!

### 1. Getting started
- Import necessary libraries
- Load the dataset

### 2. Let’s have a look at the column info and summary statistics before moving forward: 
- music_data.info()
- print(music_data.describe())
  
I noticed an unnamed column. Before removing it, let’s have a look at whether the data has null values or not:
- music_data.isnull().sum()

### 3. Data cleaning
- Dropping the 'Unnamed: 0' column
- Handling missing values by filling them with placeholder text

The data is now cleaned, and all missing values have been handled:

The unnecessary Unnamed: 0 column has been removed.
Missing values in the Track Name, Artists, and Album Name columns have been filled with “Unknown”.
Now, let’s examine the distribution of the Popularity score and then look at correlations between Popularity and other musical features. We’ll generate some plots to visualize these aspects:
- Plotting the distribution of popularity
!["Alt text"](music-popularity-1.webp)

The distribution of popularity scores shows a range mainly between 40 to 70, with peaks around the 50s and 60s. This indicates that most tracks in this dataset have moderate to high popularity.

Now, let’s have a look at the correlation matrix:
!["Alt text"](music-popularity-2.webp)

The heatmap provides insights into how various features are related to each other and the popularity of the tracks. Notably, Popularity seems to have some level of positive correlation with Loudness and Energy, while it has slight negative correlations with Acousticness. This suggests that louder and more energetic tracks tend to be more popular, while more acoustic tracks tend to be less popular.

Danceability and Valence (the musical positiveness conveyed by a track) also show some positive correlation with popularity, indicating that tracks that are more danceable and have a happier tone might be preferred by listeners.

Now, let’s delve into the individual feature impacts on the popularity of music tracks. We’ll focus on several key features based on our initial observations from the correlation matrix. Specifically, we’ll analyze:
- Danceability vs. Popularity
- Energy vs. Popularity
- Loudness vs. Popularity
- Acousticness vs. Popularity
- Valence vs. Popularity
  
For each of these features, we’ll create scatter plots to visualize their relationship with popularity. This will help us understand how each feature might influence the popularity of a track:
- Creating scatter plots for various feature

!["Alt text"](music-popularity-3.webp)

Here are the scatter plots visualizing the relationships between various musical features and the popularity of tracks:

- Danceability vs. Popularity: Higher danceability scores tend to correlate with moderate to high popularity. This suggests that more danceable tracks are generally more popular.
- Energy vs. Popularity: Similar to danceability, higher energy levels in tracks often correlate with higher popularity. This aligns with the trend that energetic tracks are preferred by listeners.
- Loudness vs. Popularity: There’s a trend showing that louder tracks tend to have higher popularity scores. This might reflect listener preference for more vibrant and powerful sound profiles.
- Acousticness vs. Popularity: Acousticness shows a somewhat inverse relationship with popularity, where tracks with lower acousticness tend to be more popular. This could suggest that highly acoustic tracks are less favoured in the dataset’s music genre context.
- Valence vs. Popularity: Tracks with higher valence, which indicates a happier or more positive tone, show a slight tendency towards higher popularity. This might imply that listeners prefer tracks that have a positive emotional tone.
  
Now, let’s have a look at how danceability, energy, and other features impact popularity differently when the track is explicit versus when it’s not. This can reveal whether explicit content has a modifying effect on the relationship between audio features and popularity:
- Creating plots for danceability vs. popularity and energy vs. popularity, segmented by explicit content
- Danceability vs. popularity
- Energy vs. popularity

!["Alt text"](music-popularity-4.webp)

The segmented scatter plots for Danceability vs. Popularity and Energy vs. Popularity, divided by whether tracks are explicit or not, show some interesting trends:

- Danceability vs. Popularity: Both explicit and non-explicit tracks show a positive trend between danceability and popularity. However, explicit tracks tend to cluster slightly higher on the popularity scale at similar levels of danceability compared to non-explicit tracks.
- Energy vs. Popularity: Similar to danceability, there’s a generally positive relationship between energy and popularity for both explicit and non-explicit tracks. Explicit tracks appear to achieve higher popularity at lower energy levels compared to non-explicit tracks, suggesting that the explicit content may appeal to certain listener groups more, irrespective of energy level.


## Statistical Modelling of Music Features
Now, let’s quantitatively assess the impact of various features on the popularity of music tracks using statistical modelling. We can use a regression model. This will allow us to understand which features are significant predictors of popularity, and quantify their impact.

For statistical modelling, we’ll use features that show promising relationships and convert categorical data (like Explicit) into a format suitable for regression analysis. We’ll also include the Key and Mode as they might carry additional information about the musical properties of the tracks.

Let’s start by preparing the features and setting up our dataset for statistical modelling using Linear Regression:
- Preparing the dataset for regression
- Convert 'Explicit' from boolean to integer (0 or 1)
- Selecting features and target for the model
- Standardizing the features
- Splitting the dataset into training and testing sets
- Initializing and training the linear regression model
- Predicting on the test set
- Evaluating the model
- Outputting the coefficients and performance metrics

The output above represents the coefficients from the regression model quantifying the impact of various musical features on track popularity. A positive coefficient indicates that an increase in the feature is associated with an increase in popularity, and vice versa for a negative coefficient.

For instance, Danceability (1.249640), Loudness (1.141456), Acousticness (2.469403), and Valence (2.125671) all have positive coefficients, suggesting that tracks with higher values in these features tend to be more popular.

On the contrary, Energy (-3.204815), Key (-3.189486), Mode (-5.859715), and Tempo (-1.865736) are negatively associated with popularity, indicating that higher values in these features could lead to lower popularity.

The coefficients for Explicit (1.620926e-14) and Speechiness (0.03398224) suggest a negligible impact on the popularity, with Explicit essentially having no effect. Instrumentalness (0.3390750) shows a minor positive influence.

## Summary
So, Statistical modelling is a mathematical framework used to describe the relationships between variables in the form of equations, usually involving stochastic elements (randomness). It is primarily focused on inference, which means understanding the relationships between variables and quantifying how certain factors influence outcomes.
