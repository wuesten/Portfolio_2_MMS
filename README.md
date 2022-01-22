<h1><center>«Portfolio-Exam Part II» </center></h1>
<h2><center>MADS-MMS </center></h2>
<h3><center>Author: Tom Wüsten </center></h3>

### Abstract

This paper deals with the customer segmentation of an online shop. The data set [1] contains all the transactions occurring for a UK-based and registered, non-store online retail between 01/12/2009 and 09/12/2011.The company mainly sells unique all-occasion gift-ware. Many customers of the company are wholesalers. The first step was a general data exploration, looking at when products are bought, which country has the most customers, how many product are returned, and a product analysis. New features were created from the findings of the data exploration using the RFM (Recency, Frequency, Monetary) method. For the subsequent customer segmentation, a data model was created that distinguishes customer types based on characteristics. Based on the new features created by RFM, various methods of clustering were carried out and evaluated using the Silhouette score. <br>

### Introduction
In today's world, companies are increasingly competing through globalisation. Companies need to have clear strategies to retain their existing customers. To do this, it is imperative to know the different types of customers. For successful implementation, it is imperative to pursue an individual marketing strategy for each type of customer. <br>
One approach for customer segmentation is offered by data mining methods. Data mining is a part of knowledge
discovery data which is an information extraction process that
is useful, not known before, and hidden from data [4]. Clustering is one of the methods of data mining and is particularly suitable for identifying groupings and patterns. Clustering is in the group of unsupervised learning that menas there are no target variables to predict. For customer segmentation, it means that segmentations can be created based on interactions and transactions with the customers. In this paper, clustering refers to a dataset of an online shop registered in the UK. The dataset was taken from the UCI Machine Learning Repository[1]. The data record depicts customer invoices. A good and useful method to get more information from invoice data is RFM (Recency, Frequency, Monetary). With this method, the customer's transaction data is transformed and grouped. From this, the recency: last visit by the customer, frequency: frequency of the purchase and the monetary: sales per one purchase can be determined. The RFM method offers a simple way of presenting the information obtained in an understandable manner. <br>
The aim of the paper is to create a customer segmentation using the RFM method in order to create specially tailored marketing campaigns and thus increase the sales of the online shop.[2][3]

### Licence Dataset
CC BY 4.0 <br>

### Attribute Information: <br>

InvoiceNo: Invoice number. Nominal. A 6-digit integral number uniquely assigned to each transaction. If this code starts with the letter 'c', it indicates a cancellation. <br>
StockCode: Product (item) code. Nominal. A 5-digit integral number uniquely assigned to each distinct product. <br>
Description: Product (item) name. Nominal. <br>
Quantity: The quantities of each product (item) per transaction. Numeric. <br>
InvoiceDate: Invice date and time. Numeric. The day and time when a transaction was generated. <br>
UnitPrice: Unit price. Numeric. Product price per unit in sterling (Â£). <br>
CustomerID: Customer number. Nominal. A 5-digit integral number uniquely assigned to each customer. <br>
Country: Country name. Nominal. The name of the country where a customer resides. <br>

### Data Exploration
#### Time of product purchase
In order to create an analysis of the point of purchase, additional information must be obtained from the feature InvoiceDate. <br>
The year, month, day of the week and hour are used for further analysis. In the following, we will examine how the online shop has developed over the years 2009-2011. <br>
The number of orders is used for this purpose. Furthermore, we want to find out in which month, on which day of the week and in which hours most orders are placed.
<br>
<img src="/output/time_product_buy.png" alt="Alt text" title="Optional title">
The plot "Distribution of invoices per weekday" shows the number of bills over the weekdays. <br>
A peak in orders can be seen on Thursday. A constant level of incoming goods can be seen on Monday, Tuesday, Wednesday and Sunday. <br>
On Friday, a decrease of 20% in purchases can be seen. But the most interesting thing is that there are no orders on Saturday. <br>
This seems very unusual and one would have to ask the person responsible for the data why there is no data or no orders on Saturday. <br>
The plot "Distribution of invoices per hour" shows the number of bills over the hours. <br>
The plot behaves like a gaussian distribution. With the assumption that most customers are wholesalers,  can assume that most purchases are made during business hours.
<br>
<img src="/output/time_product_buy_week.png" alt="Alt text" title="Optional title">

#### Sales by country
To measure sales by country, the sales volume per order must first be determined. To do this, the features Quantity and Price are multiplied. This result is in the new feature Cost per Invoice. <br>
The most turnover is made in the UK with 82.93%. The online shop also has small turnovers in EIRE (Irland), Netherland, <br> Germany and France. This countries come to a turnover of 11,21%. The rest 6% of the turnover is made around the world.
<br>
<img src="/output/sales_country.png" alt="Alt text" title="Optional title">

#### Return Rate
The two graphs show the most recalled products and the return rate across all orders. The return rate of 2.3% for all products is very low. <br>
Returned orders are no longer taken into account for the further investigations because they affect the subsequent market segmentation.
<br>
<img src="/output/return_rate.png" alt="Alt text" title="Optional title">

#### Best selling products
When analysing the products, I first checked whether the number of stock codes was the same as the number of labels. <br>
This revealed that some products have different descriptions. This could be improved in the online shop. That's why I only use the stock codes for product analysis. <br>
The online shop has 4631 products, where none of the products take the biggest part in the sale.<br>
This can be seen in the following diagram, where I show the 10 best-selling products. <br>
In this plot, the number of products sold is compared with the sales revenue per product of the 10 best-selling products. <br>
You can see that, for example, the product with the stock code 84077 is responsible for 1% of the number of goods sold, but only for 0.14% of the turnover per product. <br>
This shows that the number of products sold does not equal the turnover per product.
<br>
<img src="/output/bestselling_product.png" alt="Alt text" title="Optional title">

#### Customer Analysis
The online shop has 5881 customers. The 10 best customers alone are responsible for 15.93% of the turnover. <br>
In this analysis, only an overview of the customers is to be gained. The clustering will then go into detail about types of customers.
<br>
<img src="/output/customer.png" alt="Alt text" title="Optional title">

### Result
The best customer segmentation was achieved for K-Mean clustering with a cluster size of 5. It has only the 4th highest silhouette score compared to the other clustering methods. But compared to the previous places, it offers a more precise customer segmentation due to a higher number of cluster sizes. <br>
The customer segmentation has identified 5 different customer types for the online shop: <br>
1. active customer (cluster 0) <br>
2. occasional customer (cluster 1) <br>
3. growth customer (cluster 2) <br>
4. lost customer (cluster 3) <br>
5. top customer (cluster 4). <br>
<br>
<img src="/output/result_boxplots.png" alt="Alt text" title="Optional title">
The distribution of customer segments clearly shows that two thirds of the customers are classified as either lost customers or occasional customer. Lost customers can be won back through "reach out" campaigns. Occasionally customers can be encouraged to buy again more frequently with regular offers. The remaining 35% of customers are Active Customer (5%), Top Customer (10%) and Growth Customer (20%). Most of the potential lies in the Growth Customers. With these customers, the goal must be to build a strong customer relationship. Active customers can be sent special offers via e-mails or newsletters, which they can buy with their next regular purchase. Top customers should be highly valued by providing special offers and more service to maintain customer satisfaction.
<br>
<img src="/output/result.png" alt="Alt text" title="Optional title">

### References

[1]     Dua, D. and Graff, C. (2019). UCI Machine Learning Repository [https://archive.ics.uci.edu/ml/datasets/Online+Retail+II](https://archive.ics.uci.edu/ml/datasets/Online+Retail+II) <br> Irvine, CA: University of California, School of Information and Computer Science <br>
[2]     Maryani, Ina, et al. "Customer segmentation based on RFM model and clustering techniques with K-means algorithm." 2018 Third International Conference on Informatics and        Computing (ICIC). IEEE, 2018. <br>
[3]     Shirole, Rahul, Laxmiputra Salokhe, and Saraswati Jadhav. "Customer Segmentation using RFM Model and K-Means Clustering." (2021). <br>

[4]     Ramamohan, Y, K Vasantharao, C Kalyana Chakravarti,and a S KRatnam. 2012. “A Study of Data Mining Tools in Knowledge Discovery Process.” International Journal of
        Soft Computing and Engineering 2 (3):191–94. <br>
[5]     Murtagh, Fionn, and Pedro Contreras. "Algorithms for hierarchical clustering: an overview." Wiley Interdisciplinary Reviews: Data Mining and Knowledge Discovery 2.1 (2012): 86-97. <br>
[6]     Jarman, Angur Mahmud. "Hierarchical Cluster Analysis: Comparison of Single linkage, Complete linkage, Average linkage and Centroid Linkage Method." (2020). <br>
[7]     Biggio, Battista, et al. "Poisoning complete-linkage hierarchical clustering." Joint IAPR International Workshops on Statistical Techniques in Pattern Recognition (SPR) and     Structural and Syntactic Pattern Recognition (SSPR). Springer, Berlin, Heidelberg, 2014. <br>
[8]     Sasirekha, K., and P. Baby. "Agglomerative hierarchical clustering algorithm-a." International Journal of Scientific and Research Publications 83 (2013): 83. <br>
[9]     Safari, Fariba, Narges Safari, and Gholam Ali Montazer. "Customer lifetime value determination based on RFM model." Marketing Intelligence & Planning (2016). <br>
[10]    Bholowalia, P., & Kumar, A. (2014). EBK-means: A clustering technique based on elbow method and k-means in WSN. International Journal of Computer Applications, 105(9). <br>
