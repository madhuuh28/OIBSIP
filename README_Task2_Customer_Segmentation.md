# Task 2 --- Customer Segmentation Analysis

## 📌 Project Overview

This project focuses on **Customer Segmentation Analysis** for an
e-commerce business. The goal is to group customers based on their
purchasing behavior and identify meaningful customer segments for
targeted marketing.

The analysis uses **RFM (Recency, Frequency, Monetary)** features and
the **K-Means clustering algorithm** to identify customers with similar
purchasing patterns.

## 🎯 Objectives

-   Analyze customer purchasing behavior.
-   Handle missing, duplicate, and invalid transaction records.
-   Calculate average purchase value, purchase frequency, and historical
    customer lifetime value.
-   Build RFM features.
-   Standardize behavioral features.
-   Use the Elbow Method to select a suitable number of clusters.
-   Apply K-Means clustering.
-   Visualize and profile customer segments.
-   Recommend marketing actions for each segment.

## 🛠️ Technologies Used

-   Python
-   Pandas
-   NumPy
-   Scikit-learn
-   Matplotlib
-   Seaborn
-   Jupyter Notebook

## 📂 Dataset

The project uses the **Online Retail** transaction dataset.

Important fields include:

-   Invoice Number
-   Product/Stock Code
-   Product Description
-   Quantity
-   Invoice Date
-   Unit Price
-   Customer ID
-   Country

These fields support RFM analysis because the dataset contains customer
IDs, transaction dates, quantities, and prices.

## 🧹 Data Preparation

The notebook:

1.  Removes duplicate records.
2.  Converts invoice dates to datetime format.
3.  Removes transactions with missing Customer IDs.
4.  Removes invalid dates.
5.  Excludes non-positive quantities.
6.  Excludes non-positive unit prices.
7.  Calculates `TotalAmount` using:

`TotalAmount = Quantity × UnitPrice`

## 📊 Customer-Level Metrics

### Average Purchase Value

Average amount spent per invoice/order by a customer.

### Purchase Frequency

Number of unique invoices/orders made by a customer.

### Customer Lifetime Value Proxy

Total historical spending observed for a customer.

> This is a historical CLV proxy, not a prediction of future customer
> value.

## 🔄 RFM Analysis

### Recency

Number of days since the customer's latest purchase.

-   Lower Recency = more recently active
-   Higher Recency = inactive for longer

### Frequency

Number of unique invoices/orders made by the customer.

-   Higher Frequency = more frequent purchaser

### Monetary

Total historical spending by the customer.

-   Higher Monetary = higher-value customer

The clustering features are:

`Recency`, `Frequency`, and `Monetary`.

A log transformation is used to reduce skew, followed by
`StandardScaler`.

## 🤖 K-Means Clustering

K-Means is used to group customers with similar RFM behavior.

The notebook evaluates K values from **2 to 10** using the **Elbow
Method**. A Silhouette Score check is also included as supporting
validation.

The notebook starts with:

``` python
optimal_k = 4
```

Review the Elbow plot and change this value if another K is clearly more
appropriate.

## 📈 Visualizations

The project includes:

1.  **Frequency vs Monetary scatter plot**
2.  **Recency vs Monetary scatter plot**
3.  **Standardized cluster profile heatmap**
4.  **Customers per cluster bar chart**

Each major visualization is followed by an observation explaining the
result.

## 👥 Customer Segment Interpretation

K-Means cluster numbers do not have an inherent business meaning. The
clusters should be interpreted using their RFM profile.

  -----------------------------------------------------------------------
  Customer Type           Typical RFM Pattern     Marketing Action
  ----------------------- ----------------------- -----------------------
  **Champions / High      Low Recency, high       VIP rewards, loyalty
  Value**                 Frequency, high         benefits, early access
                          Monetary                

  **Loyal Customers**     Recent activity and     Cross-selling, bundles,
                          strong Frequency        loyalty points

  **Potential Loyalists** Recent activity with    Repeat-purchase
                          moderate                incentives and
                          Frequency/Monetary      recommendations

  **At-Risk High Value**  High Recency with       Personalized win-back
                          historically high       campaigns
                          Frequency/Monetary      

  **Hibernating / Low     High Recency with low   Low-cost reactivation
  Value**                 Frequency/Monetary      campaigns
  -----------------------------------------------------------------------

The actual customer type assigned to each cluster should be based on the
generated cluster profile, not on the cluster number.

## 💡 Key Insights

-   RFM transforms transaction history into actionable customer
    information.
-   Recency identifies active and inactive customers.
-   Frequency measures repeat purchasing behavior.
-   Monetary value identifies high-value customers.
-   Standardization prevents differences in feature scales from
    dominating K-Means.
-   Customer segments support personalized marketing.
-   Segment size and customer value should both be considered when
    allocating marketing resources.

## 📢 Marketing Recommendations

-   Reward high-value customers with VIP benefits and loyalty programs.
-   Encourage promising customers to make repeat purchases.
-   Use personalized recommendations and bundles for loyal customers.
-   Run win-back campaigns for valuable but inactive customers.
-   Use cost-effective reactivation campaigns for low-value inactive
    customers.
-   Recalculate RFM segments periodically as new transactions arrive.

## 📁 Project Structure

``` text
Task-2 Customer Segmentation/
│
├── Customer Dataset/
│   └── online_retail.csv
│
├── Task2_Customer_Segmentation.ipynb
│
└── README.md
```

## ▶️ How to Run

1.  Download the Online Retail dataset.
2.  Place `online_retail.csv` in the `Customer Dataset` folder.
3.  Open `Task2_Customer_Segmentation.ipynb` in VS Code or Jupyter
    Notebook.
4.  Select the Python kernel.
5.  Run the notebook cells from top to bottom.
6.  Review the Elbow Method plot.
7.  Adjust `optimal_k` if necessary.
8.  Review the cluster profiles and marketing recommendations.

## 🏁 Conclusion

This project demonstrates how **RFM analysis and K-Means clustering**
can segment e-commerce customers according to purchasing behavior.

The resulting segments provide a practical foundation for targeted
marketing, customer retention, loyalty programs, cross-selling, and
customer reactivation.

------------------------------------------------------------------------

**Task:** Customer Segmentation Analysis\
**Level:** Data Analytics --- Task 2
