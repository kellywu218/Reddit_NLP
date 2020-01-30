# Project 3: Web APIs & NLP

## Problem Statement
After a huge success from releaseing Mario Kart Tour, Nintendo is about to release another interation of Mario Kart and wants to utilize their social media presence to create buzz. The marketing department has come up with the use of a hashtag! However, the office has become split about what hashtag to use. Some say to just use "Mario Kart" because it's known, some are arguing that "Mario Kart" too general for this new release, others are just throwing random words to spice things up like "Luigi Kart," "Mushroom Race," and "Mario Drive." With a divided office, they managed to all agree on one thing: hire an analyst to help them decide. What word should be the marketing hashtag for the upcoming Mario Kart? 

## Executive Summary
We begin our process by going to the home of topic conversations: Reddit. There we decided to choose two popular Mario game subreddits: Mario Kart and Smash Bros Ultimate. From those two subreddits, we began by gathering our data through webscraping via 10 request pulls and converting all our findings into a nice data frame to work with in our analysis (which can be found in a separate notebook in the code folder). Afterwards, we saved and exportd our nicely converted data to be imported into a new notebook to begin a cleaning and exploratory data analysis to fix any immediately noticeable values that wouldn't be beneficial to us. 

Here we searched for any outliers and null values that we decided to drop from our dataset as they were only a minute number of rows in our overall collected data. In the end, we had abotu 1850 rows from the Mario Kart subreddit and 1450 rows from the Smash Bros Ultimate subreddit. Next we decided to focus on the titles as we figured that you always get grabbed by a title before actually reading the content. So we dived into lemmatizing-to pull root words from the title words- and count vectorizing to determine the frequency of certain words-single words and consecutive pair words. Afterwards, we looked at the frequency with consideration of an existing set of English stop words to reduce any "noise" (as we don't want common words like "the" or "a" showing up on our list). 

After discovering our potential hashtag words, we went on to a modeling process to see if we could find the best model in prediciting whether it can classify certain titles into the correct subreddit. Our goal here is that we want don't want to select a hashtag that is too ambiguous and won't have an immediate recognition to Mario Kart. Therefore, we have our second subreddit, which is slightly similar, to see how accurate our potential hashtag may be in representing the upcoming Mario Kart and not being confused for Smash Bros Ultimate. Through modeling we explore Naive Bayes and Classifier models and play with some of the hyperparameters to tune and find the best model and come to our conclusion.

## Conclusion and Recommendations
After exploring a few different models and tuning those models by playing with the hyperparameters, we discovered that our Tuned AdaBoost model is ideal in differentiating titles into the correct reddit as it is 92.14% accurate in classifying our training set and 89.98% accurate in classifying our testing set. As shown in the table below, we can see all the training and testing model accuracy scores. While our Tuned AdaBoost model doesn't necessarily have the highest scores, we care more about the two scores being as close together as possible because it shows that our model isn't overfit to our training data. For instance, if we look at the Multinomial NB model, the training score is quite high with a 95.49% accuracy, but the testing score is nearly 10 points lower at 84.54% accuracy, which means that this model is very overfit to the training data set and doesn't do well in classifying new titles into the correct subreddit. Overall, our Tuned AdaBoost model still does fairly well considering that it managed to predict 90% of our titles to the correct subreddit out of a sample of over 3000 rows (which means that it was inaccurate on about 300 rows). 

|Model|Training Score|Testing Score|
|---|---|---|
|Bernoulli NB|0.9669|0.8998|
|Multinomial NB|0.9549|0.8454|
|Logistic Regression|0.9694|0.9058|
|AdaBoost Classifier|0.9202|0.8937|
|Bernoulli NB Tuned|0.9702|0.9130|
|Multinomial NB Tuned|0.9609|0.8599|
|Logistic Regression Tuned|0.9694|0.9118|
|AdaBoost Classifier Tuned|0.9214|0.8998|

However, we do need to consider that this is still a relatively "surface level" model so there are downfalls to this model. Primarily, our model is only catered to two specific subreddits: Mario Kart and Smash Bros Ultimate. Therefore, we can't apply this model to other subreddits such as Mario Party or Super Mario Bros unless we make some modifications. In addition, we could also tune our hyperparameters further as we are only exploring four hyperparameters out of a myriad of possible combinations that could increase our model's accuracy so it can learn more and be capable of thinking more like a human. Furthermore, this data is also time based as recommendations made today may not be the same a year from now as these subreddits are constantly growing and topics may change. 

Overall, we suggest that Nintendo market their new Mario Kart game as essentially the title. For example, if the game is going to be called "Mario Kart Global" then our recommended hashtag is "#mariokartglobal" as the most common words we discovered in the Mario Kart subreddit to be "kart" (when looking at a single word option) or "mario kart" (when looking at a consecutive two word option). Building off of the consecutive two word option, the next couple most common word combinations are: "kart tour" and "kart deluxe" which refer to the latest, Mario Kart Tour, and Mario Kart Deluxe 8, respectively. Additionally, we recommend refraining from including numbers in the hashtag based on the sole foundation of what we discovered from Mario Kart 8 Deluxe being referred to as "mario kart deluxe" instead of "mario kart 8." 

## Sources
- [Mario Kart Subreddit](#https://www.reddit.com/r/mariokart/)
- [Smash Bros Ultimate Subreddit](#https://www.reddit.com/r/SmashBrosUltimate/)
- [Reddit](#https://www.redditinc.com/)