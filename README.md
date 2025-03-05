# 🛒 E-commerce Customer Segmentation Project  
**Identifying Customer Segments Using K-Means Clustering**  

---

## 📌 Overview  
This project analyzes transactional and demographic data from an e-commerce platform to segment customers into distinct groups. Two clustering models are developed:  
1. **Transaction-Level Model**: Analyzes individual transaction patterns.  
2. **Customer-Level Model**: Aggregates transactions to create customer-level behavioral metrics.  

---

## 📂 Dataset  
- **Source**: Multi-sheet Excel file (`E-commerce_data.xlsx`).  
- **Tables**:  
  - `customers`, `genders`, `cities`, `transactions`, `branches`, `merchants`.  
- **Key Features**:  
  - `transaction_date`, `burn_date`, `transaction_status`, `gender_id`, `city_id`, etc.  

---

## 🛠️ Workflow  

### **1. Data Preprocessing**  
- **Merged Data**: Combined 6 tables into a unified dataset using primary keys.  
- **Handled Missing Values**:  
  - Filled `burn_date` NaNs with `2099-12-31` (indicating unused coupons).  
- **Feature Engineering**:  
  - **Transaction-Level**: Split date columns into year/month/day.  
  - **Customer-Level**: Aggregated metrics like `recency_days`, `coupon_usage_rate`.  
- **Dimensionality Reduction**:  
  - Removed redundant columns (`gender_name`, `transaction_id`).  
  - Label-encoded `transaction_status`.  

### **2. Clustering Models**  
#### **Transaction-Level Model**  
- **Features**: 15 scaled numerical features (e.g., transaction dates, coupon lag).  
- **Clustering**: Manual K-Means implementation with `k=3`.  
- **Result**: Poor separation (Silhouette Score = **0.2**).  

#### **Customer-Level Model**  
- **Features**: Aggregated metrics (`total_transactions`, `success_rate`).  
- **Clustering**:  
  - Optimal `k=3` determined via Elbow Method.  
  - Silhouette Score = **0.23**.  
- **Visualization**: PCA-reduced 2D plot showing distinct clusters.  

---

## 📊 Results  
### **Customer-Level Clusters**  
| Cluster | Total Transactions | Recency (Days) | Coupon Usage Rate |  
|---------|--------------------|----------------|--------------------|  
| 0       | High               | Low            | Moderate           |  
| 1       | Moderate           | High           | Low                |  
| 2       | Low                | Moderate       | High               |  

## Interpretation
- **Cluster 0**:
    - High Engagement: Frequent purchases (high transactions) and recent activity (low recency).

    - Moderate Coupon Reliance: Use coupons occasionally but are not fully dependent on them.
  **`Strategy`**:

    - Reward loyalty with exclusive offers or early access to new products.

    - Upsell premium products (they’re likely to spend more).
- **Cluster 1**:
    - Declining Engagement: Haven’t purchased recently (high recency) and show moderate historical activity.

    - Coupon-Averse: Rarely use discounts.

  **`Strategy`**:

    - Re-engage with personalized reactivation campaigns (e.g., "We miss you!" discounts).

    - Investigate churn reasons (e.g., survey feedback).
- **Cluster 2**:
    - Low Spend: Infrequent purchases (low transactions) but somewhat recent activity (moderate recency).

    - Coupon Reliant: Highly dependent on discounts to make purchases.

   **`Strategy`**:
    - Target with time-sensitive coupon offers.

    - Bundle deals to increase basket size (e.g., "Buy 2, get 1 free").
      
### **Key Visualizations**  
- **Elbow Method Plot**: Optimal `k=3` identified.  
- **PCA Plot**: Clear separation of customer clusters.  

---

## 🔍 Key Takeaways
- Transaction-Level Model: Low silhouette score suggests overlapping clusters.

- Customer-Level Model: Actionable segments identified (e.g., "High-Recency Coupon Users").

- Recommendation: Use customer-level clusters for targeted marketing campaigns.
