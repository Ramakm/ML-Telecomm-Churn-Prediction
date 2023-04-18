# ML-Telecomm-Churn-Prediction-
![image](https://user-images.githubusercontent.com/8182816/232266830-31d6aea2-9b57-4d11-acb3-5f69fca94deb.png)

To reduce customer churn, telecom companies need to predict which customers are at high risk of churn.

For downloading the dataset, Please go this link as the size is more and i can't upload it there.

[Dataset CSV Link](https://www.kaggle.com/datasets/ramakrushnamohapatra/telecomm-churn-data)

# **Business Problem:**
In the telecom industry, customers are able to choose from multiple service providers and actively switch from one operator to another. In this highly competitive market, the telecommunications industry experiences an average of 15-25% annual churn rate. Given the fact that it costs 5-10 times more to acquire a new customer than to retain an existing one, customer retention has now become even more important than customer acquisition.
For many incumbent operators, retaining high profitable customers is the number one business goal. To reduce customer churn, telecom companies need to predict which customers are at high risk of churn. 
In this project, you will analyse customer-level data of a leading telecom firm, build predictive models to identify customers at high risk of churn and identify the main indicators of churn.

## **Understanding the Business Objective and the Data**

The dataset contains customer-level information for a span of four consecutive months - June, July, August and September. The months are encoded as 6, 7, 8 and 9, respectively.

The business objective is to predict the churn in the last (i.e. the ninth) month using the data (features) from the first three months. To do this task well, understanding the typical customer behaviour during churn will be helpful.

# **Data Dictionary:**

The data dictionary contains meanings of abbreviations. Some frequent ones are loc (local), IC (incoming), OG (outgoing), T2T (telecom operator to telecom operator), T2O (telecom operator to another operator), RECH (recharge) etc.
The attributes containing 6, 7, 8, 9 as suffixes imply that those correspond to the months 6, 7, 8, 9 respectively.

<!-- |Acronyms |   	Descriptions|
----------------------------
|MOBILE_NUMBER|	Customer phone number|
-                 -                    -
|CIRCLE_ID	|Telecom circle area to which the customer belongs to|
|LOC	|Local calls - within same telecom circle|
|STD	|STD calls - outside the calling circle|
|IC	|Incoming calls|
|OG|Outgoing calls|
|T2T	|Operator T to T, i.e. within same operator (mobile to mobile)|
|T2M  |  	Operator T to other operator mobile|
|T2O |   	Operator T to other operator fixed line|
|T2F |   	Operator T to fixed lines of T|
|T2C   | 	Operator T to it’s own call center|
|ARPU   | 	Average revenue per user|
|MOU   | 	Minutes of usage - voice calls|
|AON  | 	Age on network - number of days the customer is using the operator T network|
|ONNET  | 	All kind of calls within the same operator network|
|OFFNET   | 	All kind of calls outside the operator T network|
|ROAM	|Indicates that customer is in roaming zone during the call|
|SPL  | 	Special calls|
|ISD    |ISD calls|
|RECH  |  	Recharge|
|NUM   | 	Number|
|AMT  |  	Amount in local currency|
|MAX    	|Maximum|
|DATA |   	Mobile internet|
|3G  |  	3G network|
|AV  |	Average|
|VOL |   	Mobile internet usage volume (in MB)|
|2G  |  	2G network|
|PCK   | 	Prepaid service schemes called - PACKS|
|NIGHT |   	Scheme to use during specific night hours only|
|MONTHLY |   	Service schemes with validity equivalent to a month|
|SACHET  | 	Service schemes with validity smaller than a month|
|*.6    	|KPI for the month of June|
|*.7    |	KPI for the month of July|
|*.8    |	KPI for the month of August|
|*.9   |	KPI for the month of September|
|FB_USER	|Service scheme to avail services of Facebook and similar social networking sites|
|VBC    |	Volume based cost - when no specific scheme is not purchased and paid as per usage| -->
![image](https://user-images.githubusercontent.com/8182816/232224112-f83f7593-8ff2-4487-8b36-e310ebe25313.png)

# **Data Preparation:**

1. **Derive new features-** This is one of the most important parts of data preparation since good features are often the differentiators between good and bad models. Use your business understanding to derive features you think could be important indicators of churn.

2. **Filter high-value customers-** As mentioned above, you need to predict churn only for the high-value customers. Define high-value customers as follows: Those who have recharged with an amount more than or equal to X, where X is the 70th percentile of the average recharge amount in the first two months (the good phase).

3. **Tag churners and remove attributes of the churn phase-** Now tag the churned customers (churn=1, else 0) based on the fourth month as follows: Those who have not made any calls (either incoming or outgoing) AND have not used mobile internet even once in the churn phase. The attributes you need to use to tag churners are:

    * total_ic_mou_9

    * total_og_mou_9

    * vol_2g_mb_9

    * vol_3g_mb_9<br>
 
 After tagging churners, remove all the attributes corresponding to the churn phase (all attributes having ‘ _9’, etc. in their names).
 
# **Steps:**
 
    * Data Reading & Understanding
    * Data Cleaning
    * EDA
    * Train and Split
    * PCA 
    * Data Modelling

# **EDA:**
![image](https://user-images.githubusercontent.com/8182816/232468435-b5405bdf-3686-4e98-a08c-6c10bdc15a61.png)
![image](https://user-images.githubusercontent.com/8182816/232467793-cde3234a-c053-41e1-86fa-c81e93a054dd.png)
![image](https://user-images.githubusercontent.com/8182816/232468146-b0657c41-4fbc-4a96-9b88-9f97df4dcbe1.png)

# **Models Used:**<br>
   * Logistic Regression
   * SVM
   * Random Forest
   * Decision Tree
   
# **Conclusion:**<br>

   * The telecom industry experiences an annual churn rate of 15-25%, making customer retention more important than customer acquisition due to the high cost of acquiring new customers.
   * To manage High Value Customer Churn, we predicted customers likely to churn and identified factors influencing high churn.

   * A considerable drop in recharge, call usage, and data usage in the 8th month (Action Phase) was observed during exploratory analysis.
Important predictors affecting churn include 'arpu_7', 'max_rech_amt_6', 'std_og_t2m_mou_8', 'loc_og_t2m_mou_8', 'max_rech_data_8', 'last_day_rch_amt_8', 'total_data_rech_8', 'total_amt_8', 'roam_og_mou_8', 'loc_ic_t2m_mou_8'.
   * The average revenue per user in the 7th month plays a vital role in predicting churn.
   * Local and STD minutes of usage (incoming and outgoing) are the most influential features on customer churn.
   * The last day of recharge amount in the action phase and the maximum recharge for calling data in the 6th and 8th months should be focused on to prevent churn.
   * The last day of recharge, total recharge for data done, and the total amount spent on calls and data in the 8th month also play a crucial role in indicating churn.
   * Outgoing roaming calls made by clients in the 8th month also play a key role in predicting churn.
   * Strategies to prevent churn include improving network and customer satisfaction, providing customized plans, routine feedback calls, introducing attractive offers, and promotional offers
 
# **Requirements:**

matplotlib==3.4.3<br>
numpy==1.20.3<br>
pandas==1.3.4<br>
seaborn==0.11.2<br>
session_info==1.0.0<br>
sklearn==0.24.2<br>
