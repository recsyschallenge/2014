---
title: Dataset
layout: default
---
#MovieTweetings extended

The dataset is an extended version of the [MovieTweetings dataset](https://github.com/sidooms/MovieTweetings). So data originates from users of the IMDb iOS app that rate movies and share the rating on Twitter. By querying the Twitter API on a daily basis for tweets containing the keywords *I rated #IMDb* tweets are collected and relevant information is extracted. For more information on the MovieTweetings dataset see [this github website](https://github.com/sidooms/MovieTweetings), [this slideshare presentation](http://www.slideshare.net/simondooms/movie-tweetings-a-movie-rating-dataset-collected-from-twitter) or [this paper](http://crowdrec2013.noahlab.com.hk/papers/crowdrec2013_Dooms.pdf).

In its basic form MovieTweetings contains only user ids, item ids, ratings and timestamps similar to the well-known MovieLens dataset. For this challenge however, all of the metadata of the tweets (as provided by the [Twitter API](https://dev.twitter.com/docs/api/1.1/get/statuses/show/%3Aid)) is provided, allowing us to focus on the *engagement* of the ratings in the form of *retweet* and *favorites* counts. The goal of the challenge is to rank the tweets (for each user) by engagement. 

[Register](...) as participant of this challenge to obtain a download link to the dataset. 

#Statistics

The dataset contains **xxx** tweets by **xxx** unique Twitter users. All tweets were originally posted between **xxx** and **xxx**.

#The Data files

For this challenge, the dataset was chronologically split up in three subsets: training set, test set and evaluation set, as illustrated in the following figure.

**TODO: Include figure here**

The training set consists of the first 80% tweets and can be used as input for the training of models and predictive algorithms. The test and evaluation sets both contain 10% of the remaining tweets and are used for the weekly evaluation by participants themselves (test set) or for the final evaluation by the organizers (evaluation set).

##The training set
Consists of 1 file: **training.dat**. The file is CSV formatted with every line containing the following information:

scraping timestamp**,**rating**,**tweet data

- *Scraping timestamp*: a linux timestamp indicating the moment the Twitter API was queried for the tweet information. So it is not the posting time of the tweet itself but rather the moment at which the data of the tweet was collected. This may be important to take into account since it reflects how long the tweet has been *online* and may therefore influence the number of retweets or favorites (the longer a tweet has been online, the more exposure it has).
- *Rating*: The numeric rating on a scale 10-star scale, extracted from the tweet text.
- *Tweet data*: The tweet metadata in JSON format. Includes all data available through the Twitter API except for the tweet text itself. 

The following is an example of one line of the training dataset:

    1391030896,8,{"contributors": null, "truncated": false, "text": "", "in_reply_to_status_id": null, "id": 307139025897152512, "favorite_count": 0, "source": "<a href=\"http://itunes.apple.com/us/app/imdb-movies-tv/id342792525?mt=8&uo=4\" rel=\"nofollow\">IMDb Movies & TV on iOS</a>", "retweeted": false, "coordinates": null, "entities": {"symbols": [], "user_mentions": [], "hashtags": [{"indices": [48, 53], "text": "IMDb"}], "urls": [{"url": "http://t.co/oSoACtR7Pb", "indices": [25, 47], "expanded_url": "http://www.imdb.com/title/tt0444778", "display_url": "imdb.com/title/tt0444778"}]}, "in_reply_to_screen_name": null, "id_str": "307139025897152512", "retweet_count": 0, "in_reply_to_user_id": null, "favorited": false, "user": {"follow_request_sent": false, "profile_use_background_image": true, "id": 296041028, "verified": false, "profile_text_color": "333333", "profile_image_url_https": "https://pbs.twimg.com/profile_images/3635577628/2fded110fafbe2389f074fc50831a59e_normal.jpeg", "profile_sidebar_fill_color": "EFEFEF", "is_translator": false, "geo_enabled": true, "entities": {"description": {"urls": []}}, "followers_count": 114, "protected": false, "location": "\u0e17\u0e35\u0e48\u0e40\u0e14\u0e34\u0e21~", "default_profile_image": false, "id_str": "296041028", "lang": "en", "utc_offset": 25200, "statuses_count": 47133, "description": "They said I could be anything.. So I became your Friend.// Mr.149", "friends_count": 474, "profile_link_color": "000000", "profile_image_url": "http://pbs.twimg.com/profile_images/3635577628/2fded110fafbe2389f074fc50831a59e_normal.jpeg", "notifications": false, "profile_background_image_url_https": "https://si0.twimg.com/profile_background_images/810193743/85c3b06e5a58288065117440931884a3.jpeg", "profile_background_color": "FFFFFF", "profile_banner_url": "https://pbs.twimg.com/profile_banners/296041028/1367973819", "profile_background_image_url": "http://a0.twimg.com/profile_background_images/810193743/85c3b06e5a58288065117440931884a3.jpeg", "name": "\u0e21\u0e34\u0e2a\u0e40\u0e15\u0e2d\u0e23\u0e4c\u0e1a\u0e25\u0e39\u0e02\u0e2d\u0e1a\u0e32\u0e22\u0e2a\u0e4c\u2667", "is_translation_enabled": false, "profile_background_tile": true, "favourites_count": 679, "screen_name": "Nat_ta_gun", "url": null, "created_at": "Tue May 10 03:03:19 +0000 2011", "contributors_enabled": false, "time_zone": "Bangkok", "profile_sidebar_border_color": "000000", "default_profile": false, "following": false, "listed_count": 2}, "geo": null, "in_reply_to_user_id_str": null, "possibly_sensitive": false, "lang": "en", "created_at": "Thu Feb 28 14:43:44 +0000 2013", "in_reply_to_status_id_str": null, "place": null}

##The test set

Consists of 3 files: **test.dat**, **test_empty.dat**, **test_solution.dat**

###test.dat
The same structure as the training set, so CSV formatted, one line per tweet and the datafields: scraping time, rating and tweet data. This file contains the 10% tweets chronologically occuring after the 80% training tweets. 

###test_empty.dat
Again similarly structured as the **test.dat** and **training.dat** files, but here the important tweet data fields *favorite_count* and *retweet_count* have been cleared (i.e., set to empty string). This file is the task file i.e., it contains all tweets and users for which the engagement (=favorite\_count \+ retweet\_count) must be ranked.


###test_solution.dat
The solution file for the **test_empty.dat** file. It reflects what the result should be given the **test_empty.dat** file. The file is CSV formatted with every line containing the following information:

userid**,**tweetid**,**engagement

- *Userid*: The Twitter userid. This id can be found in the tweet data in the *user* array (e.g., 296041028 in the previous example tweet JSON data).
- *Tweetid*: The id of the tweet itself. Can be found in the tweet data as the *id* field (e.g., 307139025897152512 in the previous example tweet JSON data).
- *Engagement*: The sum of the two fields: *favorite_count* and *retweet_count*, indicating the engagement of the tweet.

The file is sorted on userid (descending), then on engagement (descending), then on tweetid (descending). It contains all users contained in the **test_empty.dat** file and ranks all contained tweets by engagement. The weekly evaluation score is calculated by comparing this file with your own solution using the nDCG ranking metric.

##The evaluation set
The evaluation set consists of the final 10% of the tweets used in this challenge. Its tweets were posted chronologically after the ones contained in the training and test sets. At the end of the challenge, particpants will be provided with an **evaluation_empty.dat** file (structured similarly as the **test_empty.dat** file) and requested to generate a solution file (structured as **test_solution.dat**) which will be evaluated against the **evaluation_solution.dat** by the organizers to calculate the final challenge score. The **evaluation_solution.dat** file is of course kept private.

#Python example code

Some Python code to help you with the processing the dataset. It reads the **training.dat** file and creates a List structure that contains the information.

    import json
    def read_the_dataset(the_dataset_file):
        tweets = list()
        with file(the_dataset_file,'r') as infile:
            for line in infile:
                line_arr = line.strip().split(',')
                scraping_time = int(line_arr[0])
                rating = (line_arr[1])
                tweet = ','.join(line_arr[1:]) # The json format also contains commas (,)
                json_obj = json.loads(tweet)
                #use the json_obj to easy access the tweet data
                #e.g. the tweet id: json_obj['id']
                tweets.append((scraping_time,rating,tweet))
        return tweets
