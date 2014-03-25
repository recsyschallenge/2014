---
title: Challenge
layout: default
---
#The task
Recommender systems are used in a wide variety of domains and applications. Classical recommendation approaches focus on recommending high-scoring items, whether in terms of ratings (rating prediction) or interest (top-n). This is also reflected in the way they are evaluated. However, recent research from academia as well as industry has pointed out flaws in current methods of evaluation, e.g. a low rating prediction error does not necessarily translate to a well-perceived recommendation. A similar analogy is true for top-n recommendation as well.

In this challenge, we intend to use a different means of evaluating recommendations. Instead on focusing on predictive qualities, our intention is to optimize recommendations on user engagement.
The challenge is based on an extended version of the [MovieTweetings dataset](http://recsyswiki.com/wiki/Movietweetings). The dataset contains movie ratings automatically tweeted by users who have connected their IMDb accounts to their Twitter accounts. In addition to the ratings, we have collected the interactions (retweets and favorites) performed on the tweets expressing the users’ ratings. 


#The evaluation
Instead of a traditional evaluation predicting ratings or relevant items, the participants are tasked with predicting which items generate the highest user engagement, i.e. favorites and retweets.

More specifically, participant's algorithms should generate a ranked list of tweets which are ranked based on the amount of interaction. The interaction is defined as the sum of retweet and favorite count.

###Metrics
The evaluation is based on nDCG@10. For each user in the test set, calculate nDCG@10. This is then to be averaged over all users.
Scripts for the evaluation will be provided further on.

#Weekly progress
The dataset is divided into three portions: a training set, a test set and a final evaluation set. Participants are provided with the training set and test set. Participants should train their model using the training set and can report their results on the test set on a weekly basis.


#Final evaluation
The final evaluation is done using the independent evaluation set. This portion of the data will not be published and will only be used for the final evaluation by organizers. The final algorithms of participants are tested against this set. The winners are selected based on their performance on the evaluation set.

<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','//www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-49358167-1', 'recsyschallenge.com');
  ga('send', 'pageview');

</script>
