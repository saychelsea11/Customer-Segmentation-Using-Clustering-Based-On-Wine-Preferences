# Title

Customer Segmentation Using Clustering Based On Wine Preferences

# Data

The dataset contains information on marketing newsletters/e-mail campaigns (e-mail offers sent to customers) and transaction level data from customers. The transactional data shows which offer customers responded to, and what the customer ended up buying. The data is presented as an Excel workbook containing two worksheets. Each worksheet contains a different dataset.

# Methodology

We're trying to learn more about how our customers behave, so we can use their behavior (whether or not they purchased something based on an offer) as a way to group similar minded customers together. We can then study those groups to look for patterns and trends which can help us formulate future offers.

The first thing we need is a way to compare customers. To do this, we're going to create a matrix that contains each customer and a 0/1 indicator for whether or not they responded to a given offer. This is done below by merging the two datasets.

Next we transform the dataset into a 2D sparse matrix for clustering. This is done by first grouping the data by the customer name and offer_id based on the frequency of each combination. Then the dataset is unstacked to create a 2D representation.

# Strategies for choosing the optimal K (number of clusters):
- Elbow Method
- Silhouette Method
- Gap Statistic

# Visualizing Clusters using PCA

How do we visualize clusters? If we only had two features, we could likely plot the data as is. But we have 100 data points each containing 32 features (dimensions). Principal Component Analysis (PCA) will help us reduce the dimensionality of our data from 32 to something lower. For a visualization on the coordinate plane, we will use 2 dimensions.

This is only one use of PCA for dimension reduction. We can also use PCA when we want to perform regression but we have a set of highly correlated variables. PCA untangles these correlations into a smaller number of features/predictors all of which are orthogonal (not correlated). PCA is also used to reduce a large set of variables into a much smaller one.

# Results

Visually, the scatterplot with K=3 provides the best result despite not having the best silhouette score. For K=7, clusters 0 and 1 are distinct but the others tend to overlap making the distinction blurry.

# Analyzing clusters
In order to differentiate between the clusters, we need to create a mapping between the customer names and the cluster labels

# Observations

Above, we have grouped the dataframe by each cluster to observe the differences in mean. The offer_id column does not provide much useful information since it's simply an identification feature.

The min_qty column indicates that cluster 0 has the highest average value at 80.229 followed by cluster 1 at 65.581 whereas cluster 2 is significantly lower at 14.51. This tells us that on average, customers in cluster 0 tend to respond to offers where the min_qty is higher. That's one indication of customer behavior.

Customers in cluster 0 also tend to respond to higher discounts on average whereas cluster 1 has the lowest discount value. Clusters 0 and 2 are similar when it comes to the past peak values, 0.207 and 0.193 respectively whereas cluster 1 shows a value of 0. Hence customers in cluster 1 always tend to respond to offers where the wines are never past their peak. For clusters 0 and 2, while the values are higher, they are still leaning more towards 0 than 1.

What we've done is we've taken those columns of 0/1 indicator variables, and we've transformed them into a 2-D dataset. We took one column and arbitrarily called it x and then called the other y. Now we can throw each point into a scatterplot. We color coded each point based on it's cluster so it's easier to see them.

![alt text](https://github.com/saychelsea11/Customer-Segmentation-Using-Clustering-Based-On-Wine-Preferences/blob/master/K_means_elbow.JPG)
