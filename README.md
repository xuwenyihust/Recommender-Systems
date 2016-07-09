![Python 3.5](https://img.shields.io/badge/python-3.5-blue.svg)

# Recommendation-Systems
Different implementations of recommender system.
<br/>

## Implementations
* [Havard CS 09 HW4](https://github.com/xuwenyihust/Restaurant-Recommendation-System/tree/master/harvard_cs%20_09_hw4)
* [User-Based Collaborative Filtering](https://github.com/xuwenyihust/Recommendation-Systems/tree/master/user_based_cf)
* [Item-Based Collaborative Filtering](https://github.com/xuwenyihust/Recommendation-Systems/tree/master/item_based_cf)

## Data
* [Yelp Phoenix restaurant dataset](https://github.com/xuwenyihust/Restaurant-Recommendation-System/blob/master/data/bigdf.csv)
* [Amazon Fine Food Reviews](https://www.kaggle.com/snap/amazon-fine-food-reviews)

### Data Sparsity

**Yelp Dataset**:

**Amazon Dataset**:
<p align="justify">
  <img src="https://github.com/xuwenyihust/Recommendation-Systems/blob/master/images/amazon_sparsity_user.JPG" width="350"/>
  <img src="https://github.com/xuwenyihust/Recommendation-Systems/blob/master/images/amazon_sparsity_item.JPG" width="340"/>
</p>
'''python
>>>print(fulldf.shape)
(20000, 10)
>>>print(fulldf['UserId'].unique().shape)
(17677,)
>>>print(fulldf['ProductId'].unique().shape)
(2657,)
'''
The Amazon dataset is even more sparse than the Yelp dataset, and have much more users than items. Not fitted for the collaborative filtering.

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
