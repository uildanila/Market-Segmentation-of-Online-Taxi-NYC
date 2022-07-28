# Market Segmentation : The Segmentation of Online Taxi's Customers Using K-Means

<img src='https://www.gannett-cdn.com/-mm-/56a47e3d9d848ce5dfbc1fdb5a813da89bde51d6/c=0-528-3000-2220/local/-/media/USATODAY/USATODAY/2014/04/14//1397524769000-Opposing-view-Uber.jpg?width=3000&height=1692&fit=crop&format=pjpg&auto=webp' style='width:100%; height:20%;'>

**About the Project**
<br>
This project is used to apply market segmentation, there is dataset that was provided as known as Online Taxi Transaction’s history. The dataset contains details of more than 200.000 online taxi customer's transactions in New York City.  Its features allows us to using the customer behavior from various features: from taxi provider, trip distance, fare amount, tip amount, tolls amount, rate code, pickup and dropoff location id, etc. We also using the shapefile geolocation data from external to get the details information about taxi zone, so we can get the detail information about location name for the focus area to increase the profit and offering the promos to the customers which have amount based on the customer's segment. 

In this project, I will apply K-Means clustering to segment customers into different clusters based on their behavioral characteristics. PCA and the best feature combination search technique will be used to reduce the number of features used in later models.

**List of Content**
1. Business Problem Understanding
1. Data Understanding & Data Preprocessing
1. Modeling
1. Cluster Visualization
1. Conclusion and Recommendation

## Business Problem Understanding
**Business Context**

In recent years, the daily travel of urban residents and the city's public transportation are closely linked and mutually influenced. Taxi is one of the critical transportation tools for urban residents to travel daily. With the rapid development of technology, now we can order taxi fast and safe ride to our destination anytime. 


**Problem Statement**

Due to the low operating efficiency of urban taxis, the total size of passenger traffic decrease and there are many taxi's online competitor exist so they have a chance to take our customes. Even, the total size of passengger traffic decrease at least we can maintain our customers to make sure the business still running. So the Taxi Online's Company need the ability to know more about number customers cluster. 


**Goal**

By knowing the customer segmentation, it is hoped that the company can provide appropriate promo offers to each customer segment and the steps that can be taken to increase the company's productivity and profit.


**Analytic Approach**

In the unsupervised learning, especially K-Means that will used for this dataset. The Silhouette score is used to evaluate the quality of clusters created using clustering algorithms such as K-Means in terms of how well samples are clustered with other samples that are similar to each other and the elbow method that used in determining the number of clusters in a dataset.

### Attibute Information

| Attribute | Description |
| --- | ---|
| VENDOR | a code indicating the provider associated with the trip record <br> - **1 = Yellow Taxi** <br> - **2 = Green Taxi** <br> - **3 = Blue Taxi** |
| passenger_count | the number of passengers in the vehicle (driver entered value)|
| trip_distance | The elapsed trip distance in miles reported by the taximeter. |
| rate_code| The final rate code in effect at the end of the trip|
| store_and_fwd_flag | This flag indicates whether the trip record was held in vehicle memory before sending to the vendor because the vehicle did not have a connection to the server <br><br> - Y=store and forward; <br> - N=not a store and forward trip |
| payment_type | A numeric code signifying how the passenger paid for the trip|
| fare_amount | The time and distance fare calculated by the meter|
| extra | Miscellaneous extras and surcharges |
| mta_tax| MTA tax that is automatically triggered based on the metered rate in use|
| tip_amount | Tip amount – This field is automatically populated for credit card tips Cash tips are not included|
| tolls_amount | Total amount of all tolls paid in trip|
| imp_surcharge | Total amount collected in trip for congestion surcharge|
| total_amount| The total amount charged to passengers. Does not include cash tips |
| pickup_location_id | Online Taxi Zone in which the taximeter was engaged|
| dropoff_location_id| Online Taxi Zone in which the taximeter was disengaged|

## Conclusion and Recommendation

**Conclusion :**

- Based on the results obtained and previously carried out several further searches on the data so that **several assumptions were used as limitations in selecting the data** used before making the clustering model. There are we only selected the data with have :
   1. Pickup and dropoff location id start from 1 to 263, 
   2. total amount > 0, 
   3. trip distance > 0, 
   4. Transaction's profit > $2.5 (Profit = fare_amount/trip_distance). According to [reference](https://www1.nyc.gov/site/tlc/passengers/taxi-fare.page),  we assume that impossible if the profit is less than $2.5, as we know that the minimum fee of Taxi is $2.5. 
<br><br>

- The PCA and the best feature combination technique by using the comparison of each silhouette scores. So, we found that the best combination features are **`tolls_amount`, `pickup_location_id`, and `dropoff_location_id`** with have the higest silhouette score = 0.82 based on K-Means clustering method with number of clusters = 2.

- After we compare the elbow method WCSS score for each number of clusters, the result shows that the plot looks like an elbow was founded in the number of clusters = 5. Where the elbow appears is usually the threshold for identifying the majority of the variation.

- We've done customer segmentation in order to categorize behavioral customer into 5 segments/class, there are 509 customers in class `Diamonds`,  10.998 customers in class `Platinum`, 82.082 customers in class `Gold`, 62.740 customers in class `Silver`, and 59.880 customers in class `Bronze`. To increase the profit and maintain the customers, we can offering them promo coupon for the next ride . The promo coupon will have different amount based on the customer's class so this can increase the statisfied rate about our services too. 


<br>

**Recommendation for business :**

- For class `Diamond` is have a big potential to be our customer's that will giving us the biggest profit based on the trip road, especially for those who ride to the airport and have to spend quite a lot of money for toll road access, we can offering them a **Diamond Promo Coupon to discount their trip which have highest amount of promo coupon** .

- For class `Platinum` is have potential to be our customers that will giving us the moderate profit based on the trip road, especially for those who ride to leave the airport and have to spend quite a lot of money for toll road access, we can offering them a **Platinum Promo Coupon to discount their trip which have the moderate amount of promo coupon**.

- For class `Gold` is have potential to be our loyal customers that can increase the taxi's profit based on the trip road, especially for those who ride from Lincoln Square East to Upper West Side South Area, we can offering them a **Gold Promo Coupon to discount their trip which have the regular amount of promo coupon**.

- For class `Silver` is have potential to be our loyal customers that can increase the taxi's profit day by day based on the trip road, especially for those who ride from Upper East Side South to Upper East Side North, we can offering them a **Silver Promo Coupon to discount their trip which have the small amount of promo coupon**.

- For class `Bronze` is have potential to be our loyal customers that can increase the taxi's profit day by day based on the trip road, especially for those who ride around in one location, we can offering them a **Bronze Promo Coupon to discount their trip which have the smallest amount of promo coupon**.

- The location that have a great demand for taxis are **Upper East Side South, Midtown Center, LaGuardia Airport, and Midtown East** based on the pickup location's demands for each class. So we could consider to invest more taxis in this area. 
