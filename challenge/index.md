---
title: Challenge
layout: default
---
#The task
Recommender systems are used in a wide variety of domains and applications. Classical recommendation approaches focus on recommending high-scoring items, whether in terms of ratings (rating prediction) or interest (top-n). This is also reflected in the way they are evaluated. However, recent research from academia as well as industry has pointed out flaws in current methods of evaluation, e.g. a low rating prediction error does not necessarily translate to a well-perceived recommendation. A similar analogy is true for top-n recommendation as well.

In this challenge, we intend to use a different means of evaluating recommendations. Instead on focusing on predictive qualities, our intention is to optimize recommendations on user engagement.
The challenge will be based on an extended version of the MovieTweetings dataset (http://recsyswiki.com/wiki/Movietweetings). The dataset contains movie ratings automatically tweeted by users who have connected their IMDb accounts to their Twitter accounts. In addition to the ratings, we have collected the interactions (retweets and favorites) performed on the tweets expressing the users’ ratings. Furthermore, the dataset will contain ratings and interactions on data from other services such as YouTube, Spotify, Last.fm, etc.


#The evaluation
Instead of a traditional evaluation predicting ratings or relevant items, the participants will be tasked with predicting which items generate the highest user engagement, i.e. favorites and retweets.

More specifically, participant's algorithms should generate a ranked list of tweets which are ranked based on the amount of interaction. The interaction is defined as the sum of retweet and favorite count. The official evaluation metrics would be NDCG, MAP and MRR.

#Weekly progress
The dataset is divided into three portions: a training set, a test set and a final evaluation set. Participants are provided with the training set and test set. Participants should train their model using the training set and can report their results on the test set on a weekly basis.


#Final evaluation
The final evaluation is done using the independent evaluation set. This portion of data will be published without ground truth (i.e. without retweet and favorite count). The final algorithm of participants are tested against this set. The winners are selected based on their performance on the evaluation set.
