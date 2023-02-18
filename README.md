# OTTO-Multi-Objective-Recommender-System
This solution got a silver medal from the Kaggle competition: OTTO-Multi-Objective Recommender System
https://www.kaggle.com/competitions/otto-recommender-system

1. This competition is based on user's historical clicks, favorites, and order behaviors, and
predicts the results of user clicks, favorites, and orders in the next 7 days. This competition uses
the recall of the top 20 products as the evaluation index, which is a typical product
recommendation problem.

2. Firstly, we used multiple recall methods to identify potential item IDs. Specific recall methods
include:
• The ID of the product with the most clicks/favorites/orders in history
• Similar products: Based on the user's click behavior sequence, a word2vec model is
established, the products are vectorized and coded, and a product similarity matrix is
established
• Co-visitation matrix of click/cart/order to cart/order with type weighting
• Co-visitation matrix of cart/order to cart/order
By recall，we can determine the top 200 items that are most likely to be
clicked/favorite/purchased.

3. Based on these recalled items, we constructed a series of characteristics of items, users, and
item-user dimensions:
1) Item dimension: click/collection/purchase volume in the past 1 and 4 weeks, calculate the
rate of product addition to shopping cart and product purchase rate in the past 1 week and 4
weeks
2) User dimension: user clicks/favorites/purchases in the past week
3) User-Item dimension:
• Based on the user's historical behavior, we can vectorize the user and calculate the similarity
between the user and the product
• Calculate the similarity between the item clicked by the user in the past 1/3/5/10/15 times
and the recalled product
According to the historical click/shopping difference/purchased product data, we can label the
recalled data with 0 or 1. Then we established the LGB binary classification model, and selected
the 20 product IDs with the highest prediction probability as the submission. Our final
leaderboard score is 0.585, ranking in the top 4%.

4. In this competition, we reasonably controlled the rhythm of the competition according to the
competition time, actively discussed, reasonably formulated the iterative tasks of the
competition model, organized brainstorming to advance the competition, and started the
development of the model
