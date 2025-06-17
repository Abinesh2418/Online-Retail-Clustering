# Customer Segmentation Using Online Retail Dataset

This project focuses on customer segmentation using the Online Retail  dataset. We apply RFM (Recency, Frequency, Monetary) analysis and KMeans clustering to identify distinct customer groups based on purchasing behavior.

## 📦 About the Dataset

**Abstract**:  
A real online retail transaction data set collected over two years (01/12/2009 to 09/12/2011) for a UK-based, non-store online retail company selling all-occasion gift-ware, often to wholesale clients.

**Dataset Source**: UCI Machine Learning Repository  
**Contains Missing Values?** Yes  

### 📌 Attribute Information:

- **InvoiceNo**: Unique invoice number. If it starts with 'C', it indicates cancellation.
- **StockCode**: Unique product/item code.
- **Description**: Name of the product.
- **Quantity**: Number of units sold per transaction.
- **InvoiceDate**: Date and time of invoice.
- **UnitPrice**: Price per unit in sterling (£).
- **CustomerID**: Unique ID for each customer.
- **Country**: Country of residence of the customer.

---

## 🚀 Project Workflow

This project follows a structured approach to segment customers based on their purchasing behavior using RFM analysis and KMeans clustering.

### 📥 1. Data Collection
- Loaded the dataset using `pandas`:
  ```python
  import pandas as pd
  df = pd.read_excel('online_retail_II.xlsx', sheet_name='Year 2010-2011')

  
### 🔍 2. Exploratory Data Analysis (EDA)
- Inspected the dataset structure and data types.
- Checked for null values and analyzed the distribution of key columns.
- Identified cancellation transactions by detecting InvoiceNo values starting with 'C'.
- Explored product codes and descriptions to ensure data consistency and relevance.

### 🧹 3. Data Cleaning
- Removed:
  - Canceled invoices (InvoiceNo starting with 'C')
  - Records with missing CustomerID
  - Transactions with Quantity ≤ 0 or UnitPrice ≤ 0
- Created a new column `SalesLineTotal` by multiplying Quantity and UnitPrice.
- Retained only valid transactions for further analysis.

### 🛠️ 4. Feature Engineering (RFM)
- Aggregated transactional data at the customer level to compute RFM values:
  - **Recency**: Number of days since the last purchase, based on the most recent date in the dataset.
  - **Frequency**: Number of unique invoices per customer.
  - **MonetaryValue**: Total amount spent by each customer.
 
### 🧪 5. Outlier Removal
- Detected and removed outliers from the RFM dataset using the **IQR (Interquartile Range)** method.
- Calculated the 25th percentile (Q1) and 75th percentile (Q3) for each RFM feature.
- Identified data points outside the range \[Q1 - 1.5 × IQR, Q3 + 1.5 × IQR\] as outliers.
- Removed these outliers to improve clustering accuracy and ensure better model performance.

### ⚙️ 6. Normalization
- Scaled the RFM features using `StandardScaler` to ensure better clustering performance.
- Standardization helps eliminate bias due to scale differences between features.

### 📉 7. Clustering - KMeans
- Used the **Elbow Method** and **Silhouette Score** to determine the optimal number of clusters.
- Based on the analysis, **k = 4** was chosen as the optimal number of clusters.
- Applied **KMeans Clustering** on the normalized RFM data.
- Assigned each customer to one of the 4 clusters based on their RFM scores.

### 📊 8. Cluster Profiling
- Calculated the average **Recency**, **Frequency**, and **Monetary** values for each cluster.
- Interpreted and labeled each cluster based on customer behavior:
  - **VIP**
  - **Loyal**
  - **Churned**
  - **Low Value**
- These labels help drive targeted marketing strategies.

### 📈 9. Visualization
- Created multiple visualizations to understand the customer segmentation:
  - **3D Scatter Plot** of RFM values color-coded by cluster
  - **Violin Plots** to visualize the distribution of R, F, M per cluster
  - **Bar Plots** to show the number of customers in each segment
  - **Boxplots** and **Pairplots** for comparative analysis of metrics across clusters
 
  ### 🧠 Cluster-Wise Conclusion

#### ✅ Cluster 0 (Skyblue)
**Observation:**
- Low MonetaryValue (low-spending customers)
- Low Frequency (rare purchases)
- Moderate Recency (recent but not very recent)

**Rationale:**
- These customers are not highly valuable. They visit occasionally and spend small amounts.

**Action:**
- Run retargeting campaigns with small discounts or product bundles.
- Send personalized recommendations to increase engagement and order value.

---

#### ✅ Cluster 1 (Orange)
**Observation:**
- Moderate-High MonetaryValue  
- Moderate-High Frequency  
- Low Recency (very recent customers)

**Rationale:**
- These are active and valuable customers. They buy often and recently.

**Action:**
- Consider them as potential loyalists.
- Launch loyalty programs or early access to offers.
- Ask for reviews or referrals.

---

#### ✅ Cluster 2 (Green)
**Observation:**
- Low MonetaryValue  
- Low Frequency  
- High Recency (long time since last interaction)

**Rationale:**
- These are likely churned or dormant customers who rarely engaged and haven’t returned in a long time.

**Action:**
- Initiate reactivation campaigns.
- Offer strong incentives (e.g., “We miss you” emails, major discounts).
- Use win-back strategies.

---

#### ✅ Cluster 3 (Purple)
**Observation:**
- High MonetaryValue  
- High Frequency  
- Low Recency (very recent)

**Rationale:**
- These are your best customers – high spenders, frequent buyers, and very recent.

**Action:**
- Tag as VIP customers.
- Prioritize with exclusive offers, priority support, or beta product access.
- Maintain high engagement to retain them.

## 📬 Contact

For any queries or suggestions, feel free to reach out:

- 📧 Email: [abineshbalasubramaniyam@example.com](mailto:abineshbalasubramaniyam@example.com)
- 💼 LinkedIn: [linkedin.com/in/abinesh-b-1b14a1290/](https://www.linkedin.com/in/abinesh-b-1b14a1290/)
