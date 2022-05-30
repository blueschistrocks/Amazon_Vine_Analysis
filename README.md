# Amazon Vine Analysis

The purpose of the Challenge was to analyze Amazon Vine reviews written by members of the paid Amazon Vine program and non-Vine members.  Amazon Vine is a service that allows manufacturers and publishers to receive reviews of their products and determine if there are any biases among the Vine members and non-Vine members reviews.  Companies will sometimes provide free products to Vine members who are expected to publish a review.  I used the furniture reviews for my analysis:

[Link to Data Set](https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Furniture_v1_00.tsv.gz)

## Deliverable 1 - Perform ETL on Amazon Product Reviews 
I created an AWS RDS database with tables in pgAdmin and extracted the above referenced dataset into a DataFrame. Then transform the DataFrame into four separate DataFrames that match the table schema I used in pgAdmin. Then I upload the transformed data into the appropriate tables and run queries in pgAdmin to confirm that the data has been properly uploaded. See the link and images below:

[Link to "Amazon_Review__ETL.ipynb"](https://github.com/blueschistrocks/Amazon_Vine_Analysis/blob/80db3887602d99bd63ce57bf9eb98071f1625579/Amazon_Reviews_ETL_starter_code.ipynb)

[Link to "Amazon_Review__ETL.ipynb - Colaboratory.pdf"](https://github.com/blueschistrocks/Amazon_Vine_Analysis/blob/80db3887602d99bd63ce57bf9eb98071f1625579/Amazon_Reviews_ETL.ipynb%20-%20Colaboratory.pdf)

### "review_id_table"
![image](https://github.com/blueschistrocks/Amazon_Vine_Analysis/blob/6a5677c565b27a715fe2803f1e804764aff90ca2/Images/Screen%20Shot%202022-05-28%20at%202.29.50%20PM.png)<br>

### "products_table"
![image](https://github.com/blueschistrocks/Amazon_Vine_Analysis/blob/6a5677c565b27a715fe2803f1e804764aff90ca2/Images/Screen%20Shot%202022-05-28%20at%202.35.39%20PM.png)<br>

### "vine_table"
![image](https://github.com/blueschistrocks/Amazon_Vine_Analysis/blob/6a5677c565b27a715fe2803f1e804764aff90ca2/Images/Screen%20Shot%202022-05-28%20at%202.36.03%20PM.png)<br>

### "costumer_table"
![image](https://github.com/blueschistrocks/Amazon_Vine_Analysis/blob/6a5677c565b27a715fe2803f1e804764aff90ca2/Images/Screen%20Shot%202022-05-28%20at%202.34.59%20PM.png)<br>

## Deliverable 2 - Determine Bias of Vine Reviews

To determine if there is bias from Vine members vs non-Vine members the data was filtered to only use rows where the “total_votes” count is equal to or greater than 20 in order to pick reviews that are more likely to be helpful and to avoid having division by zero errors later on in the analysis. The data was further filtered to retrieve all the rows where the number of “helpful_votes” divided by “total_votes” is equal to or greater than 50%.  The data below was extracted from the data frame, paid indicates a verified purchase. 

#### Helpful
- Total Number of Helpful Vine and Non-Vine Reviews Paid and Not Paid: 18,155
- Total Number of Helpful Vine Reviews Paid: 3
- Total Number of Helpful Vine Reviews Not Paid: 133
- Total Number of Helpful Non-Vine Reviews Paid: 15,080
- Total Number of Helpful Non-Vine Reviews Not Paid: 2,939

#### Five Star
- Total Number of Helpful Five Star Reviews: 8,556
- Total Number of Helpful Five Star Vine Reviews Paid: 2
- Total Number of Helpful Five Star Vine Reviews Not Paid: 72
- Total Number of Helpful Five Star Non-Vine Reviews Paid: 7,323
- Total Number of Helpful Five Star Non-Vine Reviews Not Paid: 1,159

#### Five Star Percentage
- Percent of Five Star Vine Reviews Paid: 67
- Percent of Five Star Vine Reviews Not Paid: 54
- Percent of Five Star Vine Reviews Paid: 49
- Percent of Five Star Vine Reviews Not Paid: 39

#### Review Totals
- Total Number of Reviews: 792,113
- Total Number of 'Helpful' Reviews: 18,155
- Total Number of Five Star Reviews: 447,716

The counts of Vine and non-Vine reviews were placed in a new data frame using Pandas and plotted on a bar graph using Matplotlib. 

#### Vine and Non-Vine Reviews
![image](https://github.com/blueschistrocks/Amazon_Vine_Analysis/blob/8702ec1eeafafdf8b6191f417b639a3bcb9d261c/Images/Screen%20Shot%202022-05-29%20at%203.10.14%20PM.png)<br>

![image](https://github.com/blueschistrocks/Amazon_Vine_Analysis/blob/8702ec1eeafafdf8b6191f417b639a3bcb9d261c/Images/Screen%20Shot%202022-05-29%20at%203.10.55%20PM.png)<br>

The percentage of Vine and non-Vine reviews were placed in a new data frame using Pandas and plotted on a bar graph using Matplotlib. 

#### Percentage of Vine and Non-Vine Reviews
![image](https://github.com/blueschistrocks/Amazon_Vine_Analysis/blob/8702ec1eeafafdf8b6191f417b639a3bcb9d261c/Images/Screen%20Shot%202022-05-29%20at%203.11.09%20PM.png)<br>

![image](https://github.com/blueschistrocks/Amazon_Vine_Analysis/blob/8702ec1eeafafdf8b6191f417b639a3bcb9d261c/Images/Screen%20Shot%202022-05-29%20at%203.10.31%20PM.png)<br>

## Summary

- A vast majority of the helful reviews for Furniture are made by non-Vine customers.
- Vine customers appeared to provide a higher percentage of Five-star rating, therefore some bias from Vine members vs non-Vine members is likely. However, given that they provide fewer that 1% of the overall reviews the potential bias would have a negligible impact.     


## Recommendations
I recommend additional analysis overall product types to see if the Vine reviews are similar to the Furniture data set or vary depending on the product type.

# Tools Used

The following were used to complete the analysis:
-	Spark 
-	PySpark
-	Python
-	Pandas
-	Matplotlib
-	Google Colaboratory



