![Python 3.5](https://img.shields.io/badge/python-3.5-blue.svg)

# Restaurant-Recommendation-System
My own solution to Harvard CS 109 HW4.
<br/>
## Data
The data set was extracted from the Yelp Phoenix restaurant dataset. 

Joint information about users & business.

| Column | Descriptions |
| -------|--------------|
| user_id | Unique user id |
| business_id | Unique restaurant id |
| date | The date of review |
| review_id | Unique review id |
| stars | Star rating |
| usefulvotes_review | Votes for this review |
| user_name | Name of the user |
| categories | Classiication of this restaurant |
| biz_name | The full business name |
| latitude | Latitude |
| longitude | Longitude |
| business_avg | Average stars over all users reviews for business |
| business_review_count | Review count for this restaurant |
| user_avg | Average rating for this user over all businesses |
| user_review_count | Review count for this user |

## Goal

### 1. Neighborhood-based CF(collaborative filtering) recommender

* **Reduce the sparsity** of the original dataset by filtering out business with <= 150 review or users with <= 60 review.
* Get the **common user support** *(count of users who reviewed both)* of each pair of restaurants.
* Calculate the **similarity** between each pair of restaurants by using **Pearson correlation** *(similarity measurement)* based on common user support *(if the common user support == 0, set similarity to 0, otherwise, calculate pearson's r)*.
* Create a **DataBase** of similarities for each pair of restaurants *(global similar restautants)* using python class.
*  Write a function to get **K-Nearest** restaurants of a given restaurant. *(shrink Pearson coefficients to control the effect of small common supports)*

 #### Flow of calculating similarity between restaurants in a pair & K nearset restaurants
<p align="justify">
  <img src="https://cloud.githubusercontent.com/assets/7127935/16394991/a6ff77c4-3c6c-11e6-9d83-d5b916c9d0b0.JPG" width="350"/>
  <img src="https://cloud.githubusercontent.com/assets/7127935/16396281/d66d9f30-3c72-11e6-82bb-4ebce2dd13e2.JPG" width="400"/>
</p>

### 2. User based recommender with predicted ratings

### 3. Bayesian Chocolates: Model based recommendations
