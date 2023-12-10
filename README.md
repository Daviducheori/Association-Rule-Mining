# Market-Basket-Analysis
Data from a supermarket's sales were used in the study

### Table of Contents
- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Preparation of Dataset](#preparation-of-dataset)
- [Implementation in Python](#implementation-in-python)
- [Visualisations](#visualisations)
- [Result and Discussion](#result-and-discussion)
- [Conclusion](#conclusion)

### Project Overview
This research was done to create a Market Basket Analysis, identify consumer buying trends, and identify the items that are combined utilising Association Rules. Data from a supermarket's sales were used in the study.

### Programming Language
- Python

### Dataset
The groceries_unpivot dataset was used for this study and was obtained from Data World which is a widely recognized leading enterprise data catalogue. The dataset contains 3 features and 29,063 rows. The features include a “PuchaseID” attribute, which shows the ID of every distinct customer, the “Date” attribute, it shows the sales transaction from 1 January 2000 until 26 February 2002 and an “Item” attribute which displays the product that was purchased by a particular customer.

### Preparation of Dataset

- Installing Packages: MLxtend package was installed through the Python Package Index (PyPi) by running pip install mlxtend.
- Importing the Required Libraries:The relevant Python libraries were imported, including MLxtend for using the Apriori algorithm and association rules, Pandas for data manipulation, Matplotlib, and Seaborn for visualisation.
- Importing the Dataset: The next step was to load the data into pandas. The dataset was saved in the same directory as the jupyter note-book file after being obtained from its source so that I could easily read the datasets using pandas. Since we’re dealing with a csv file, the dataset was imported using the read_csv() method in pandas.
- Examining the Dataset Structure:The dataset's structure was examined using the info() method to determine the number of rows and columns, the names, and data types of each column, and whether or not any of the columns had null values. It was discovered that the dataset contained 3 attributes and 29,063 rows.
- Exploring the Missing Values in the Dataset:
The dataset was examined for missing values, it was discovered that the dataset did not contain any missing values.
- Removing Blanks Spaces and Rows Lacking a PurchaseID: The blank spaces in the item column and the rows lacking PurchaseID

### Implementation in Python

- Apriori Algorithm: Apriori algorithm is used for frequent item set mining and association rule learning. Apriori algorithm utilises a level-wise approach, in which n-item sets are used to explore (n+1)- item sets. The candidate generation phase is the stage where the Apriori technique expands frequent subsets one item at a time. The data is then checked against groups of candidates. Apriori uses a hash tree structure and the breadth-first search approach to efficiently enumerate candidate item sets.
- Selecting Only Required Variables for Modelling: The PurchaseID and Item attributes were used for the analysis and assigned into a new data frame.
- Creating a Basket: The transaction (PurchaseID) and the products were grouped to generate a basket matrix. The values of the quantities of each item purchased were displayed. After that the value was counted and un-stacked. Lastly, the index was changed to the PurchaseID, the data frame contains the quantity of each item bought per PurchaseID. This data frame is basically the ‘basket’ that the customers ‘carry’s on’ to the cashier in the shop. It shows us how much this customer / transaction (PurchaseID) bought a par-ticular item. If the number is 0, then this customer didn’t buy that particular item.
- Encoding:
The total number of each item purchased is not particularly significant in market basket analysis. The decisive factor is whether or not an item is purchased. Because we just want to know how purchasing some products is related to purchasing other items. Therefore, we must convert the data from the shopping cart into a binary format that indicates whether an item was purchased (1) or not (0).
Generating Frequent Item Sets: Now that the data is correctly organised. The next step was to apply the Apriori algorithm. The first parameter was the list of lists that the rules need to be extracted from. The second parameter is the min_support parameter. A frequent item sets with at least 7% support was generated (this number was chosen so that I could get enough useful examples).
- Generating Association Rules: The rules and their related lift, confidence, and support were generated at the final stage. This displays the antecedents and consequent items along with their parameter values.
- Estimating the Number of Rules Generated: A total of 22,556 rules were generated from the predefined parameters in the previous step.

### Visualisations

![image](https://github.com/Daviducheori/Market-Basket-Analysis/assets/76125377/ecfaefc0-50d5-463e-9119-b8813014dabb)

Fig 2.1 Descriptive Statistics of the Rules



![Visualising the Top 10 Sold Items](https://github.com/Daviducheori/Market-Basket-Analysis/assets/76125377/fa06ee60-3e1e-4e68-bdab-22124f9d6e09)

Fig 2.2 Visualising the Top 10 Sold Items



![Visualising the Least 10 Sold Items](https://github.com/Daviducheori/Market-Basket-Analysis/assets/76125377/3af5c69b-d0c3-4665-b4d7-67a949c79947)


Fig 2.3 Visualising the Least 10 Sold Items


![image](https://github.com/Daviducheori/Market-Basket-Analysis/assets/76125377/341ba717-7a74-49d1-8b6a-442e4d7823e8)

Fig 2.4 Top 10 Rules with the Largest Lift

![image](https://github.com/Daviducheori/Market-Basket-Analysis/assets/76125377/a3ad82b2-ba63-4b6c-ac38-8cafab12fea7)

Fig 2.5 Top 10 Rules with the Largest Confidence

![image](https://github.com/Daviducheori/Market-Basket-Analysis/assets/76125377/f898e52c-a743-491e-ac46-4e0381a13411)


Fig 2.6 Visualisation of Rules with Highest Life and Confidence


![image](https://github.com/Daviducheori/Market-Basket-Analysis/assets/76125377/36bd2caa-50c3-4ecd-b596-2a250546a19b)

Fig 2.7 Filtering for Hand Soap as A Consequent with Specified Lift and Confidence Thresholds

![image](https://github.com/Daviducheori/Market-Basket-Analysis/assets/76125377/94e07da0-3b04-4c47-8180-694a9881b136)

Fig 2.8 Filtering for Ketchup as A Consequent with Specified Lift and Confidence Thresholds

![Scatterplot of Confidence Against Support](https://github.com/Daviducheori/Market-Basket-Analysis/assets/76125377/1044fe99-e339-4f87-9604-62e197db0dc2)


Fig 2.9 Scatterplot of Confidence Against Support

### Result and Discussion
A total of 22,556 rules were generated from the analysis setting a min_support threshold of 0.05. This value was chosen to obtain many useful examples. The descriptive statistics of the rules which is shown in Fig 2.1, it can be seen that a typical rule has a lift of 1.21 and the lift values range from 1.00 to 1.63. The mean value of confidence is 0.35 and in the confidence values range from 0.09 to 0.93. The graphical representation in Fig 2.2 indicates that vegetables, poultry, and soda are the three highest sold items in the shop. Fig 2.3 indicates that hand soap, ketchup and sandwich bags are the least sold items in the shop. Lift shows the strength of association. Lift explains how much more frequently the antecedent and consequent occur together than they do independently. The table in Fig 2.4, the first rule indicates that customers who purchased vegetables and juice are 1.63 times more likely to buy yogurt and shampoo. The table in Fig 2.5, The first rule indicates that of all the transactions where eggs, dishwashing liquid/detergent, and poultry were purchased, 93% of them included vegetables. The other rules in the tables also show a high confidence level for the purchase of vegetables alongside combination of the other items in the antecedent column.

#### Making Recommendations
- Filtering Rules with High Confidence and Lift:
As we already know, the significance of the relationship between the elements increases with the lift ratio. Also, the higher the confidence, the more reliable are the rules. So, we are looking for rules with high confidence (>=0.90) and high lift (>=1.25). For this we filter the records as shown in Fig 2.6 The result is giving us a lot of information about item grouping such as customers are 92% likely to buy vegetables if they have already bought eggs, dinner rolls and cheeses. The items in this table are very likely to be purchased in association and should be positioned together.

- Filtering for Hand Soap as A Consequent with Specified Lift and Confidence Thresholds: As shown in Fig 2.7, setting the values of the lift to be greater than 1 and a 45% confidence value. The revenue generated form hand soap, being the least sold item in the shop is likely to be increased if it is placed alongside (all-purpose and mixes), (waffles and spaghetti sauce), and (poultry and spaghetti sauce).

- Filtering for Ketchup as A Consequent with Specified Lift and Confidence Thresholds: As shown in Fig 2.8, setting the values of the lift to be greater than 1 and a confidence of 0.45, the set of rules is filtered to suggest combinations that can improve the revenue generated from ketchup.

### Conclusion 
Numerous fields, including market basket analysis, website navigation analysis, medical diagnosis and research, and others, can benefit from association rule mining. The typical association rules discovery algorithm consists of two phases. The first stage yields all frequent item sets. In the second stage, the association rules are constructed with a confidence level of at least minimum confidence. More association rules are generated but with lower accuracy values when the minimal support and confidence values are lowered. In a case study, 29,063 entries from a grocery store's database were analysed to find the association rules and accompanying metrics. The Apriori function was used for this process. A set of recommendations were also made that can improve the sales of some of the least purchased products in the store. According to this investigation, market basket analysis could benefit from the use of association rule mining algorithms to improve the classification of the enormous amount of data. The greater the set of frequently occurring item sets, the higher the number of rules, many of which are replicated. This is valid even for small datasets, but for large datasets, mining all conceivable frequent item sets, let alone producing rules, is just not viable. This is due to the fact that they frequently produce an increasing number of frequent item sets. This study proved that applying the Apriori method to generate and apply market basket analysis to transaction data is advantageous. It is also applicable across a wide range of fields and can help address a number of issues more effectively and efficiently.






