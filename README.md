![Python 3.5](https://img.shields.io/badge/python-3.5-blue.svg)

# Recommender-Systems
Different implementations of recommender system.
<br/>

## Implementations
* [Havard CS 09 HW4](https://github.com/xuwenyihust/Restaurant-Recommendation-System/tree/master/harvard_cs%20_09_hw4)
* [User-Based Collaborative Filtering](https://github.com/xuwenyihust/Recommendation-Systems/tree/master/user_based_cf)
* [Item-Based Collaborative Filtering](https://github.com/xuwenyihust/Recommendation-Systems/tree/master/item_based_cf)

## Data
* [Yelp Phoenix restaurant dataset](https://github.com/xuwenyihust/Restaurant-Recommendation-System/blob/master/data/bigdf.csv)

  | Column | Descriptions |
  | -------|--------------|
  | user_id | Unique user id |
  | business_id | Unique restaurant id |
  | stars | Star rating |
  | ... | ... |
  | business_avg | Average stars over all users reviews for business |
  | business_review_count | Review count for this restaurant |
  | user_avg | Average rating for this user over all businesses |
  
  ```python
  >>> print(fulldf.shape)
  (149319, 15)
  ```

* [Amazon Fine Food Reviews](https://www.kaggle.com/snap/amazon-fine-food-reviews)

### Data Sparsity

**Yelp Dataset**:
<p align="justify">
  <img src="https://github.com/xuwenyihust/Recommendation-Systems/blob/master/images/yelp_sparsity_user.JPG" width="350"/>
  <img src="https://github.com/xuwenyihust/Recommendation-Systems/blob/master/images/yelp_sparsity_restaurant.JPG" width="340"/>
</p>
```python
>>> fulldf=pd.read_csv("https://raw.githubusercontent.com/xuwenyihust/Recommendation-Systems/master/data/bigdf.csv")
>>> print(fulldf.shape)
(149319, 15)
>>> print(fulldf['user_id'].unique().shape)
(34789,)
>>> print(fulldf['business_id'].unique().shape)
(4503,)
```
Most users reviewed on less than 20 item. And most items have less than 20 reviews. Need to reduce the sparsity.

**Amazon Dataset**:
<p align="justify">
  <img src="https://github.com/xuwenyihust/Recommendation-Systems/blob/master/images/amazon_sparsity_user.JPG" width="350"/>
  <img src="https://github.com/xuwenyihust/Recommendation-Systems/blob/master/images/amazon_sparsity_item.JPG" width="340"/>
</p>
```python
>>> fulldf=pd.read_csv("https://raw.githubusercontent.com/xuwenyihust/Recommendation-Systems/master/data/amazon-fine-foods.csv")
>>> fulldf = fulldf[:20000]
>>> print(fulldf.shape)
(20000, 10)
>>> print(fulldf['UserId'].unique().shape)
(17677,)
>>> print(fulldf['ProductId'].unique().shape)
(2657,)
```
The Amazon dataset is even more sparse than the Yelp dataset, and have much more users than items. Not fitted for the collaborative filtering.

## Systems
### User Based Collaborative Filtering
* Pre-processing
    * Reduce the **sparsity** of the original dataset.
    * Split the **train/test** data.
* Find **Similar** Users
    * Define the function to compute **user-to-user similarity** (*Pearson coefficient correlation*).
    * Add **'regularization'** parameter to improve the similarity.
    * Define the function to pick out **K nearest users** to a user.

* **Predict Ratings** for these recommendations
    * Define a new function which returns K nearest users that have rated this item given a user & a item as parameters.
    * Weighted average of the neighboring user's ratings.
    
      ![equation](http://www.sciweavers.org/tex2img.php?eq=%20P_%7Bu%2Ci%7D%20%3D%20%20%20P%5E%7Bbaseline%7D_%7Bu%2Ci%7D%20%2B%20%20%5Cfrac%7B%20%5Csum%20s_%7Bj%7D%20%2A%20%28P_%7Bu%2Cj%7D%20-%20P%5E%7Bbaseline%7D_%7Bu%2Ci%7D%29%20%7D%7B%20%5Csum%20s_%7Bj%7D%20%7D%20&bc=White&fc=Black&im=jpg&fs=12&ff=arev&edit=0)

    * Baseline prediction.
    
      Baseline = all_mean + (user_mean - all_mean) + (item_mean - all_mean)
      
* **Error** Analysis
    * Pick a number of random users and items we have the ratings in test dataset.
    * Calculate the **RMSE**.

<br/>
### Item Based Collaborative Filtering
  Can be better extended to large user bases than user-based CF.
  > Item–item CF generates predictions by using the user’s own ratings for other items  combined with 
  > those items’ similarities to the target item, rather than other users’ ratings and user similarities as in user–user CF.
  
* Pre-processing
    * Reduce the **sparsity** of the original dataset.
    * Split the **train/test** data.

* Compute item-to-item similarities
    * Define a function to compute common user support.
    * Define a function to use Pearson's r to compute similarity.
    * Build a **Database** in **sqlite** to store the item-to-item similarity matrix.

* Find the K Nearest items
* Predict Ratings
* Error Analysis

## Comparison
Compare the different implemntations.
* Build the ROC curves.
* The curve with the highest AUC value will show the best implementation.

## Libraries Used
* [pandas](http://pandas.pydata.org/)
* [matplotlib](http://matplotlib.org/)
* [sklearn](http://scikit-learn.org/stable/)
* [numpy](http://www.numpy.org/)
* [scipy](https://www.scipy.org/)
* [operator](https://docs.python.org/3/library/operator.html) 


## Resources

* [Official content for Harvard CS109](https://github.com/cs109/content)
* [Recommender systems](http://www.ibm.com/developerworks/library/os-recommender2/index.html)
* [J. McAuley and J. Leskovec. From amateurs to connoisseurs: modeling the evolution of user expertise through online reviews. WWW, 2013.](http://i.stanford.edu/~julian/pdfs/www13.pdf)
* [GroupLens](http://files.grouplens.org/papers/FnT%20CF%20Recsys%20Survey.pdf)
