# Customer-Churn-Analysis-Using-Power-BI

## Project Overview 
This project conducts a comprehensive analysis of bank churn data using Power BI, focusing on customer attrition and its contributing factors. Utilizing a sample dataset, it aims to practice report creation, visualize key metrics, and derive actionable insights to enhance customer retention strategies.

## Project Objective 
* Identify and analyze the factors driving customer churn.
* Develop actionable insights from the data to implement strategies for reducing churn

## Data Collection 
The dataset used for this analysis is structured in CSV format, comprising 10,000 rows and 12 columns.
The dataset could be downloaded from https://www.kaggle.com/datasets/gauravtopre/bank-customer-churn-dataset 

## Data Description 

| **Dataset Column Name** | **Dataset Column Description**  | **Dataset Column Type and Possible Values** |
| :-------------       |:---------------------------| :---------------------------------------|
|**customer_id**|Customer Identification Number Unique number each customer has enrolled with the bank	|*Numeric*|
|**credit_score**	|Credit Score : Numerical value : it is a score given to the customer based on his/ her repayment history, types of loans previously availed, duration or length of credit history  etc and has seen by the bankers as a key parameter to offer credit.|	*Numeric*|
|**country**|	Location : Country in which the customer has the bank account |	Character ( Spain,	France and Germany)|
|**gender**	|Gender of the Customer|	*Character (Male or 	Female)*|
|**age**|	Attained Age of the Customer|*	Numeric ( Starts from Number 18 and there is no limit the oldest customer in the dataset is 92)*|
|**tenure**|	Tennure of liability	|*Numeric*|
|**balance**|	Total Account Balance of the customer|	*Decimal*|
|**products_number**|	Total number of Financial products used by the customer	|*Numeric ( 1 or 2 or 3 or 4 )*|
|**credit_card**	|Does the customer has a credit card	|*Numeric ( 1 - yes 0-No )*|
|**active_member**|	Active status of the customer	|*Numeric ( 1 - yes 0-No )*|
|**estimated_salary**	|Salary findings if he/she has a salaried account	|*Decimal*|
|**churn**|	Exited or not	|*Character ( 1 - yes 0-No )*|

## DAX - Data Analysis 

* **Total Customer**
  Count_Customer = COUNT(BankCustomerData[customer_id])
* **Unique Customer**
  Count_Unique_Customer = DISTINCTCOUNT(BankCustomerData[customer_id])
* **Churned Customers**
  Count_Churned_Customer = Sum(BankCustomerData[churn])
* **Churned Rate**
  Churn_Rate = [Count_Churned_Customer] / [Count_Customer]
* **Active Customers**
  Count_Active_Customer = Sum(BankCustomerData[active_member])
  
#### Categorization

* **Credit Card Category**
  
  Credit Card = 
    SWITCH(
        TRUE,
        [credit_card] = 0, "No",
        [credit_card] = 1, "Yes"
         )

* **Active Member Category**
    
    Active Member Category = 
    SWITCH( 
        TRUE,
        [active_member] = 0, "No",
        [active_member] = 1, "Yes"       
    )
    
* **Credit Score Category**
    
     CreditScore_Category = SWITCH(TRUE,[credit_score] >= 300 && [credit_score] <= 579, "Poor Score",
                                   [credit_score] >= 580 && [credit_score] <= 669, "Fair Score", 
                                   [credit_score] >= 670 && [credit_score] <= 739, "Good Score",
                                   [credit_score] >= 740 && [credit_score] <= 799, "Very Good Score",
                                   [credit_score] >= 800 && [credit_score] <= 850, "Excellent Score"
                              )
    
* **Product Subscribed Category**
   
    Product Subscribed = SWITCH(TRUE, [products_number] = 1, "Product 1", [products_number] = 2, "Product 2", [products_number] = 3, "Product 3", [products_number] = 4, "Product 4")
   
* **Salary Category**
  
   Salary Category = 
    SWITCH(
        TRUE,
        [estimated_salary] < 50000, "Low Income",
        [estimated_salary] >= 50000 && [estimated_salary] <= 100000, "Middle Income",
        [estimated_salary] > 100000, "High Income",
        "Unknown"
    )
  
  * **Balance Category**
    
    Balance Category = 
    SWITCH(
        TRUE,
        [balance] = 0, "$0",
        [balance] > 0 && [balance] <= 50000, "$0.01 and $50,000",
        [balance] > 50000 && [balance] <= 100000, "$50,001 and $100,000",
        [balance] > 100000 && [balance] <= 200000, "$100,001 and $200,000",
        [balance] > 200000 && [balance] <= 250898.09, "$200,001 and $250,898.09",
        "Unknown"
    )


## DashBoard Preparation 

### Overview
<img width="920" alt="image" src="https://github.com/SteffiTensingh/Customer-Churn-Analysis-Using-Power-BI/assets/112261367/59570f03-18db-40f8-a628-08b0b5a48218">

### Churn Rate of Customers by Age Group
<img width="922" alt="image" src="https://github.com/SteffiTensingh/Customer-Churn-Analysis-Using-Power-BI/assets/112261367/fe4d94cd-f193-40c2-ad2d-ff4a4c20c76c">

### Churn Rate By Categorical Measures 
* Balance column was catgorised by segments of the balance amounts.
* Product Number column was categorised as Product 1, Product 2, Product 3 and Product 4.
* Estimated Salary Column was categorised as High, Middle and Low Income.
* Tennure was categorised as New , established, veteran, Recent and Long-Term Customers.

<img width="922" alt="image" src="https://github.com/SteffiTensingh/Customer-Churn-Analysis-Using-Power-BI/assets/112261367/89144f35-cb26-4dc2-a596-5d5f2a12b2d5">

 ## Churn Rate by High Income Salary Category and Age 
 <img width="839" alt="image" src="https://github.com/SteffiTensingh/Customer-Churn-Analysis-Using-Power-BI/assets/112261367/08d74403-1ef5-4887-99ad-3201a9b01f35">

  ## Churn Rate by Low Income Salary Category and Age 
  <img width="842" alt="image" src="https://github.com/SteffiTensingh/Customer-Churn-Analysis-Using-Power-BI/assets/112261367/54fe96c6-6916-4f2e-a5f8-a0fb8ed91a3f">
   
  ## Churn Rate by Middle Income Salary Category and Age 
  <img width="833" alt="image" src="https://github.com/SteffiTensingh/Customer-Churn-Analysis-Using-Power-BI/assets/112261367/50ddb5a7-a665-415e-9583-021fb38e1748">

  ## Churn Rate By Tennure and Gender 
 <img width="788" alt="image" src="https://github.com/SteffiTensingh/Customer-Churn-Analysis-Using-Power-BI/assets/112261367/25cf5b85-9bcd-46be-8a5f-9770989b9f6a">

  ## Churn Rate by Credit Card and Credit Score
  <img width="872" alt="image" src="https://github.com/SteffiTensingh/Customer-Churn-Analysis-Using-Power-BI/assets/112261367/ab0e861c-18ce-4a2c-814b-60318c3da9e5">

  <img width="908" alt="image" src="https://github.com/SteffiTensingh/Customer-Churn-Analysis-Using-Power-BI/assets/112261367/b0e1cd2d-bc92-470e-9aaa-03d6c00cad6a">

  ## Products Subscribed VS Customer count
<img width="557" alt="image" src="https://github.com/SteffiTensingh/Customer-Churn-Analysis-Using-Power-BI/assets/112261367/6d32e266-66d3-4027-a4dd-9ced92b37999">

  ## Credit Card VS customer Count

  <img width="776" alt="image" src="https://github.com/SteffiTensingh/Customer-Churn-Analysis-Using-Power-BI/assets/112261367/1d51f5d9-f1c3-4465-aa83-b3387be91867">

  ## Credit Score VS Customer Count
 <img width="703" alt="image" src="https://github.com/SteffiTensingh/Customer-Churn-Analysis-Using-Power-BI/assets/112261367/a75650d4-cd10-4740-ad5e-1662146eeaa2">
 

# Key observations 
* There are 10,000 bank customers, out of which 2,037 customers have churned or exited, yielding a churn rate of 20.37%.
* The distribution of customers across countries shows a significant presence in France, with Spain following closely behind in the bank's customer base.
* The Churn rate is very high at 45.38%  middle aged customers between 51–60 years of age.
* A notable portion of the bank's customer base is aligned with products Product 1 (50.84 %) and product 2(45.9 %), reflecting high engagement levels and suggesting possible correlations between product satisfaction and lower churn rates.
* The majority of bank customers, nearly 70.55 % possess credit cards, underscoring the significance of credit card services in enhancing customer engagement.
* When filtering for churned customers by gender, there is a slightly higher churn rate observed among female customers compared to males.
* The uniform churn rates hovering around 20% across salary categories (High, Middle, Low) suggest that salary alone may not be a decisive factor influencing churn. Other factors like customer service, product satisfaction, and competitive advantages likely play more critical roles in customer retention strategies.
* Customers with a credit score categorized as 'Poor' (between 300 and 579) exhibit the highest churn rate at 22.02%.
* The majority of customers fall into the 'Fair' credit score category, followed by 'Good' and 'Poor' scores, respectively.
* In the analysis of customer counts and churn rates by bank group, the balance range of 100K to 200K showed the highest customer count at 4,765, which was higher than the lowest count in the 1K to 10K range.
* A high churn rate of 56.15% among inactive customers, compared to 26.3% among active customers, underscores the critical role of customer engagement in retention. Targeted efforts to re-engage inactive customers could effectively reduce churn and enhance overall retention rates for the bank.

# Suggestions 
* Direct targeted marketing efforts towards female customers with personalized promotions and campaigns, aiming to mitigate their higher churn rates.
* Capitalize on the strong engagement levels observed for Product 1 and Product 2. Enhance these products further based on customer feedback and satisfaction to potentially reduce churn rates associated with them.
* Since a significant majority of customers own credit cards, optimize credit card services to further enhance customer engagement. Consider introducing tailored offers or benefits to increase usage and satisfaction.
* Develop focused retention strategies for middle-aged customers (51-60 years) experiencing high churn rates. Additionally, customize approaches for customers with 'Poor' credit scores to address their unique needs and improve retention efforts.
* Given the significantly higher churn rate among inactive customers, devise proactive strategies to re-engage them. This could include personalized communication, exclusive offers, or incentives to regain their interest and loyalty.

## Project Conclusion
In conclusion, this churn analysis of bank customers has yielded valuable insights into factors influencing customer retention and satisfaction. 
Utilizing Power BI Desktop's visualization capabilities, we identified key trends such as demographic distributions, product usage patterns, and the impact of financial profiles on churn rates. 
These findings underscore the importance of data-driven strategies in enhancing customer retention and optimizing service delivery.




















