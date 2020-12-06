### Introduction

The first Pokemon game was dropped in 1996. The main series of the Pokemon is now into its 8th generation and the platforms these games are played on have evolved over the years as well. Including other spin-offs as well as mobile apps and PC games, there are likely to be a few hundred Pokemon games today. The Pokemon Company would like to understand what gamers that play the different Pokemon games are discussing online on various forums. The analysis of these discussions can help to further improve updates to the games or the development of future games. The first step in this analysis would be the successful classification of online posts with regards to the correct Pokemon game that the post is talking about. This project aims to study reddit posts associated with two of these games, Pokemon GO and Pokken, with the goal of developing a classification model to decide which game the posts are associated with.

___

### Overview

975 posts are scrapped from each of the respective sub-reddits for Pokemon Go and Pokken and stored. The relevant python libraries were imported into the jupyter notebook file. The dataset underwent exploration and cleaning to be made suitable for model fitting. Count Vectorizer and Tfidf Vectorizer were used with Naive Bayes classifier in a pipeline to Gridsearch for the best parameters. The best performing Vectorizer was then used to compare the Naive Bayes classifier against the Support Vector classifier to develop an overall best model.

___

#### Data Cleaning, Exploration, Visualization

All features except for the title and selftext were dropped for both dataframes from each of the sub-reddits. Nulls were found in the selftext column for the Pokken posts. These were imputed with a "." to allow for the combination of the title and selftext columns into a single text column. Post length and the most popular words from both dataframes were checked. Results of these checks gave some additional words that had to be removed prior to building the model in addition to standard stopwords from the natural language toolkit. The two dataframes were combined into one with a identifier column indicating which sub-reddit each post belongs to. A cleaning function was implemented removing html characters, non-letters, stopwords and the additional words that were found during EDA. All words were also converted to lower case and lemmatized. After dropping duplicates, the baseline accuracy was found to be 51.6%. 

___

#### Modeling

The combined dataframe underwent a train test split. The data from the split was then vectorized using both the Count Vectorizer and Tfidf Vectorizer followed by the building of a Naive Bayes classification model. The Naive-Bayes classifier was then compared against a Support Vector classifier. Pipeline and Gridsearch were used to find the optimum parameters. All models gave very high scores indicating that the majority of the posts were correctly classified. The best performing model would be the SVC classifier developed using the Tfidf Vectorizer with the results as follows: 

|True Negatives|False Positives|False Negatives|True Positives|
|---|---|---|---|
|178|5|4|191|

It was observed that misclassified posts are likely to have been caused by the contents of the post being rather general in nature and containing words that are likely associated with the wrong sub-reddit.
___

#### Conclusions and recommendations

On the whole, it can be said that this classifier has shown to be largely successful in classifying posts to the correct sub-reddit with a score of 99.1% on train data and 97.6% on test data as compared to the baseline score of 51.6%. The extremely high scores indicate that the contents of the two sub-reddits have features that are easily distinguishable from one another. While both games are based on Pokemon, it is likely that the different natures of the games contributed to the posts being easily distinguishable.

Since the classifier is largely successful in distinguishing posts from the two sub-reddits, it has fulfilled its purpose of being the first step in helping game developers separate posts for further analysis to provide insights that can aid game updates and the development of future games. Further analysis of the classified posts for improvements on game updates and development are not within the scope of this project.

The classifier model built may be useful to classify posts from other forums outside of reddit that may be talking about these games as well. Posts and user feedback from other forums that can be found online may provide additional insights. One limitation of this model is that it is a binary classifier. A new model that is able to classify posts into the various Pokemon game titles across the various generations and platforms would be a lot more useful as it can be used in forums such as the main Pokemon sub-reddit: https://www.reddit.com/r/pokemon/. For the purpose of this project, words associated with the title of the sub-reddits were removed. In an actual classifier model, it would be better to keep such words since they would be the clearest identifiers possible.