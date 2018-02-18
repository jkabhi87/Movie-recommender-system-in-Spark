# Movie-recommender-system-in-Spark
Movie recommender system using utility matrix in Spark

Observations:
The recommender system I built works pretty well for the new user that I added. I based the new user's ratings on my personal preferences.
I saw that there were certain movies in the dataset that were not hollywood movies. I was able to locate a few Indian movies in the dataset. 
So, I incorporated them in the new user ratings and to my surprise, I saw a hindi movie name "Kahaani" in the recommended list of movies.
There is more to this. At first, I was not considering the number of ratings a movie has received in my final recommendations. This led to 
recommendations of movies that I had not even heard of (extremely rarely rated movies). I figured that the predicted rating for these movie depends on the item to item similarity.
So, I eliminated the movies that had less than 25 user ratings and then I started seeing movies that were familiar to me. This is when I saw "Kahaani" in my recommendations.
I then increased the rating count from 25 to 100 and finally to 500. This is when i started seeing really popular movies in the recommendations. This is obvious because, if a movie is popular,
it is bound to have more ratings. But still, the predicted ratings for these movies were still very much on the lines of my linking.
I tend to rate drama, Scifi higher than comedies as I like them better. And in the final output, the top 5 recommended movies were either drama or scifi. The ratings predicted were in line with my ratings as well.
Also, for the 5 movies for which the recommender system predicts the ratings, you can see that "Bruce Almighty" which is a comedy gets a score of 3.02 while the rest of the movies which are drama or scifi are predicted a higher rating.

One final observation is, for movies with more than 500 ratings, the recommender system never predicted a rating of more than 4.

Cross validation:
I learnt that the shell script used to split the dataset into 5 fold CV files that used to be the part of the movie lens dataset is not being shipped with the standard dataset any more.
However, I was able to download the files from the github repo of movielens. I had to download "split_ratings.sh" and "allbut.pl" files and slightly modify them.
I got it working and it generated 5 test and 5 train files (like r1.test, r2.test, r1.train, r2.train and so on).
I used these files to implement my own cross validation program. I felt comfortable writing my own CV program instead of using the standard library code.
I tried running 5 fold CV with multiple combinations of rank (latent factors) and lambda (learning rate) values.
I used the following values for rank (2,3,4,5). 
I used the following values for lambda (0.01,0.05,0.08,0.1,0.15). 
I found that the error values were the least for rank=2 and lambda=0.1 which i have used in my final model.


All tasks have been implemented in python.
1. The zipped file contains one folder which contains 3 folders : Code, Pseuodocode  and Output
2. The output folder contains the sample output files.
3. The folder named "Code" has 2 files
    a. CV.py is the code I wrote for 5 fold cross validation.
    b. ALS.py is the recommender system code in python that bases the recommender system on the utility matrix generated using the movielens dataset of 20m size.
3. The folder named "Pseudocode" has 2 files
    a. The file Cross_validation.docx contains pseudocode for the python script for cross validation.
    b. The folder ALS.docx contains pseudocode for the python script for the recommender system.
