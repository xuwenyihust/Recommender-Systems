![Python 3.5](https://img.shields.io/badge/python-3.5-blue.svg)

# Restaurant-Recommendation-System
My own solution to Harvard CS 109 HW4.
<br/>
### Data
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

### Goal

> Neighborhood-based CF recommender.

* **Reduce the sparsity** of the original dataset by filtering out business with <= 150 review or users with <= 60 review.
* Get the **common user support**(count of users who reviewed both) of each pair of restaurants.
* Calculate the **similarity** between each pair of restaurants by using **Pearson correlation**.
* Create a **DataBase** of similarities for each pair of restaurants using python class.
*  Write a function to get **K-Nearest** restaurants of a given restaurant. (shrink Pearson coefficients to control the effect of small common supports)
