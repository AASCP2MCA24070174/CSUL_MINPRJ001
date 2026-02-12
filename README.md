# E-Commerce Customer Segmentation Using Unsupervised Learning

## 📋 Project Overview

This project performs **customer segmentation** on e-commerce transaction data using unsupervised learning techniques (K-Means clustering). The goal is to identify distinct customer groups based on their transactional behavior, enabling data-driven marketing strategies, improved customer retention, and optimized product offerings.

By segmenting customers into meaningful groups, businesses can:
- Tailor marketing campaigns to specific customer needs
- Improve customer retention through targeted strategies
- Optimize inventory and product placement
- Enhance customer lifetime value
- Identify at-risk customers for proactive engagement

---

## 🎯 Project Objectives

1. **Data Integration**: Merge multiple sheets from an Excel file containing customer, transaction, and merchant information
2. **Feature Engineering**: Create RFM-like customer features (Recency, Frequency, Monetary) and additional behavioral metrics
3. **Clustering Analysis**: Apply K-Means clustering to identify optimal customer segments
4. **Visualization**: Create comprehensive visualizations using PCA, box plots, heatmaps, and pair plots
5. **Marketing Insights**: Derive actionable insights for each customer segment with tailored recommendations
6. **Results Export**: Output customer segments with cluster assignments for downstream analysis

---

## 📊 Dataset Description

The project uses a simulated e-commerce dataset (`E-commerce_data.xlsx`) containing the following sheets:

| Sheet | Description |
|-------|-------------|
| **customers** | Customer demographic information |
| **genders** | Gender mapping (ID → Gender Name) |
| **cities** | City mapping (ID → City Name) |
| **transactions** | Transactional records with dates, status, coupons, branch, and merchant info |
| **branches** | Branch information |
| **merchants** | Merchant details |

### Key Columns (After Merging)
- `customer_id`: Unique customer identifier
- `transaction_date`: Date of transaction
- `transaction_status`: Status of transaction (e.g., "burned" for coupon usage)
- `burn_date`: Date coupon was redeemed
- `join_date`: Date customer joined
- `city_name`: Customer's city
- `merchant_name`: Merchant name
- `gender_name`: Customer's gender

---

## 🔧 Feature Engineering

The following customer-level features were engineered for clustering:

### RFM-Based Features
- **Recency**: Days since the last purchase (from transaction_date)
- **Frequency**: Total number of transactions
- **Monetary**: Proxy for spending value calculated as `Frequency × (1 / (1 + Recency/30))`

### Behavioral Features
- **UniqueTransactions**: Count of unique transaction IDs
- **CouponUsage**: Number of burned/redeemed coupons
- **CityDiversity**: Number of unique cities visited
- **MerchantDiversity**: Number of unique merchants patronized
- **BranchDiversity**: Number of unique branches visited
- **PrimaryGender**: Most frequent gender associated with customer

All features were **standardized** using `StandardScaler` to ensure equal contribution to clustering.

---

## 🤖 Methodology

### 1. **Data Preprocessing**
   - Loaded data from multiple Excel sheets
   - Merged datasets using customer_id as key
   - Converted date columns to datetime format
   - Handled missing values during feature creation

### 2. **Feature Engineering & Scaling**
   - Created customer-level aggregation using groupby operations
   - Applied StandardScaler for feature normalization
   - Final feature set: 8 numerical features per customer

### 3. **Optimal K Determination**
   - **Elbow Method**: Evaluated inertia for k=2 to k=10
   - **Silhouette Score**: Analyzed cluster separation quality
   - **Business Context**: Considered interpretability (preferred 3-6 clusters)
   - **Result**: Selected k=4 clusters as optimal

### 4. **K-Means Clustering**
   - Applied K-Means++ initialization for better convergence
   - Used 10 initializations with random_state=42 for reproducibility
   - Fitted model on standardized features

### 5. **Visualization & Analysis**
   - **PCA Transformation**: Reduced dimensionality to 2D for visualization
   - **Distribution Analysis**: Histograms and box plots for feature distributions
   - **Correlation Analysis**: Heatmap showing feature relationships
   - **Cluster Profiling**: Feature statistics for each cluster
   - **Pair Plots**: Scatter matrix for feature relationships

### 6. **Marketing Insights**
   - Identified VIP customers (top 20% in Frequency & Monetary)
   - Segmented coupon enthusiasts (top 25% in CouponUsage)
   - Flagged at-risk customers (Recency > 90 days)
   - Generated cluster-specific marketing recommendations

---

## 📈 Clustering Results

### Cluster Summary
Four distinct customer segments were identified:

#### **Cluster 0: Engaged but Low Spend**
- High frequency, recent activity, low monetary value
- **Strategy**: Upselling, loyalty programs, cross-selling higher-value items
- **Action**: Implement rewards program to increase average transaction value

#### **Cluster 1: High Value, Low Engagement**
- Low frequency, recent purchase, high monetary value
- **Strategy**: Time-limited exclusive offers, VIP benefits, personalized emails
- **Action**: Create premium tier with exclusive perks and early product access

#### **Cluster 2: At-Risk/Dormant**
- Low frequency, inactive (high recency), low monetary value
- **Strategy**: Win-back campaigns, compelling discounts, re-engagement emails
- **Action**: Launch targeted re-engagement with special incentives

#### **Cluster 3: High Value, Formerly Active**
- High frequency historically, recent inactivity, high monetary value
- **Strategy**: Loyalty bonuses, personalized recommendations based on history
- **Action**: Proactive outreach with exclusive offers to reactivate

---

## 📁 Project Structure

```
Customer-Segmentation-Minor-Project/
├── data/
│   └── E-commerce_data.xlsx          # Input data with multiple sheets
├── notebooks/
│   └── Customer_segmentation_using_unsupervised_learning.ipynb
├── outputs/
│   ├── results/
│   │   └── customer_segments_complete.csv  # Main output with cluster assignments
│   └── plots/
│       ├── Distribution_of_Features.png
│       ├── Correlation_Heatmap.png
│       ├── Pair_Plot.png
│       ├── Box_Plots.png
│       ├── K-Means_Clustering.png
│       ├── KMeans_Clustering_PCA.png
│       └── KMeans_Cluster_Profiles.png
├── README.md                          # This file
├── requirements.txt                   # Python dependencies
└── METHODOLOGY.md                     # Detailed methodology and techniques

```

---

## 🚀 Getting Started

### Prerequisites
- Python 3.8+
- Jupyter Notebook or VS Code with Jupyter extension
- All dependencies listed in `requirements.txt`

### Installation

1. **Clone/Navigate to the project directory**
   ```bash
   cd Customer-Segmentation-Minor-Project
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Open the notebook**
   ```bash
   jupyter notebook notebooks/Customer_segmentation_using_unsupervised_learning.ipynb
   ```

### Running the Analysis

1. Execute cells sequentially from top to bottom
2. The notebook will:
   - Load and merge data from Excel
   - Generate 8 customer features
   - Determine optimal cluster count
   - Apply K-Means clustering
   - Generate visualizations
   - Export results to CSV

---

## 📊 Output Files

### Main Output
- **`customer_segments_complete.csv`**: Contains all customers with their assigned cluster (0-3) plus all calculated features

### Visualizations
- **Distribution plots**: Histogram of scaled features
- **Correlation heatmap**: Feature relationships
- **Pair plots**: Multi-dimensional relationships
- **Box plots**: Outlier identification per feature
- **PCA visualization**: 2D cluster visualization with centroids
- **Cluster profiles**: Feature distributions by cluster

---

## 🔍 Key Algorithms & Libraries

| Component | Library | Details |
|-----------|---------|---------|
| Data Loading | pandas | Multi-sheet Excel handling |
| Data Processing | pandas, numpy | Aggregation, transformation |
| Scaling | scikit-learn | StandardScaler normalization |
| Clustering | scikit-learn | KMeans algorithm |
| Dimensionality Reduction | scikit-learn | PCA for visualization |
| Evaluation | scikit-learn | Silhouette Score |
| Visualization | matplotlib, seaborn | Plots and heatmaps |

---

## 💡 Marketing Applications

### VIP Customer Strategy
- **Identification**: Top 20% by Frequency & Monetary value
- **Action**: Exclusive loyalty programs, VIP tiers, personal account managers
- **Expected ROI**: High due to existing spending patterns

### Coupon Enthusiast Targeting
- **Identification**: Top 25% by CouponUsage
- **Action**: Coupon-centric campaigns, flash sales, bundle offers
- **Expected ROI**: High engagement rates

### At-Risk Customer Recovery
- **Identification**: Recency > 90 days
- **Action**: Win-back campaigns, aggressive discounts, personalized outreach
- **Expected ROI**: Variable (depends on reason for inactivity)

### Cluster-Specific Campaigns
- Tailor messaging and offers based on cluster characteristics
- A/B test different strategies per cluster
- Monitor segment migration over time

---

## 📚 Data Cleaning & Preprocessing Notes

The notebook includes detailed discussion on:
- **Missing value imputation**: Beyond simple fillna(0) - mean/median/predictive methods
- **Outlier detection**: IQR method, Z-scores, Isolation Forest, LOF
- **Outlier treatment**: Capping/Winsorization, transformation, deletion
- **Feature scaling**: StandardScaler, Min-Max scaling, RobustScaler
- **Advanced techniques**: Polynomial features, interaction terms, time-based features

See `METHODOLOGY.md` for comprehensive coverage of alternative approaches.

---

## 🔐 Next Steps & Recommendations

### Short-term
1. ✅ Validate cluster stability with different initialization seeds
2. ✅ Test alternative clustering algorithms (DBSCAN, Hierarchical Clustering)
3. ✅ A/B test marketing strategies on identified segments
4. ✅ Monitor cluster migration patterns over time

### Medium-term
1. Incorporate temporal patterns (seasonal trends, purchase cycles)
2. Add customer feedback/NPS scores to cluster profiles
3. Implement real-time scoring for new customer classification
4. Develop predictive models for lifetime value (CLV) per cluster

### Long-term
1. Integration with CRM/marketing automation platform
2. Dynamic re-clustering on regular intervals (monthly/quarterly)
3. Multi-layer segmentation (combine with product affinity, geographic data)
4. Recommendation engine based on cluster behavior patterns

---

## 📝 Notes & Limitations

- **Data Quality**: Results depend on input data quality and completeness
- **Temporal Aspects**: Current features are snapshot-based; trend analysis could enhance insights
- **Recency Calculation**: Uses current date; should be recalculated as data updates
- **Coupon Bias**: High CouponUsage might indicate discounters vs. true high-value customers
- **External Factors**: Doesn't account for external market conditions or seasonality

---

## 👥 Contributors

Created as a Minor Project for Customer Analytics & Segmentation.

---

## 📄 License

This project is provided for educational and business intelligence purposes.

---

## 📧 Support & Questions

For questions or issues regarding this project, please review the detailed methodology in `METHODOLOGY.md` or consult the notebook's markdown sections for in-depth explanations.

---

**Last Updated**: February 12, 2026
**Python Version**: 3.8+
**Status**: Active & Maintained
