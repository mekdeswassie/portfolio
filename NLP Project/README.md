# Project 3: Medical Requests Classification: Diabetes Vs. Asthma

### Overview
Using Pushshift's API, we have collected data from two subreddit posts: Diabetes and Asthma. We used 5,000 posts from each subreddit, a total of 10,000 posts. We assumed the posts are a representation of the patient requests in medical apps. We then used NLP to train a classifier on which subreddit a given post came from. 

### Problem Statement:
A research institute has plans to conduct a research on medical apps for self-diagnosis of diabetes. 
They have collected requests made by patients with a description of basic information on their conditions. The data they are working with contains patient requests that were diagnosed as asthma and diabetes. 
Before the begin their work, they requested the technology department to come up with a solution for sorting patient requests based on their diagnosis. 


### Data Dictionary:
    
|Feature|Type|Dataset|Description|
|---|---|---|---|
|subreddit|object|Diabetes/Asthma|a forum on different topics|
|title|object|Diabetes/Asthma|title of each subreddit post|
|selftext|object|Diabetes/Asthma|the body of a subreddit post|
|created_utc|int|Diabetes/Asthma|epoch time (the number of seconds that have elapsed since January 1, 1970 at midnight UTC time minus the leap seconds)|


### Summary of Analysis:

- We considered two evaluation metrics when picking out the best classifer from four of the classifiers we trained.
    - knn with term frequency-inverse document frequency has a sensitivty of 15.5% and an accuracy of 55.7%
    - Multinomial Naive Bayes with count vectorizer has a sensitivty of 97.2% and an accuracy of 95.6%
    - Multinomial Naive Bayes with term frequency-inverse document frequency has a sensitivty of 95.3% and an accuracy of 95.4%
    - Random forest with count vectorizer has a sensitivity of 97.6% and an accuracy of 94.8% 


### Conclusion/Recommendation

- The best classifier is found to be the multinomial Naive Bayes (with countvectorizer) with an accuracy of 95.6% and sensitivity of 97.2%. 
- This classifier is performing very well, but it would be a good idea to make sure that we are not training the estimator obvious words such as 'asthma' and 'diabetes' which are in the top common words. 
- Also, including more stop words into the English stop words that are common across each subreddit such as 'doctor', 'like', and 'just', might help to increase the performance of the classfier. 
- Knn classifer has a sensitivty of 15.5%. This is very low comparing it with how the other models performed. Analyzing why there are many false positive predictions with the knn classifier will help to identify trends in the data. 

### Sources: 

- https://www.reddit.com/r/diabetes/
- https://www.reddit.com/r/Asthma/


