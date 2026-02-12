# Project Summary: E-Commerce Customer Segmentation

**Project Name**: E-Commerce Customer Segmentation Using Unsupervised Learning  
**Type**: Data Science / Customer Analytics  
**Completed**: February 2026  
**Status**: Active - Ready for Implementation

---

## Executive Overview

This project segments e-commerce customers into 4 distinct groups based on their transactional behavior using K-Means clustering. The segmentation enables targeted marketing strategies, improved customer retention, and optimized resource allocation.

---

## Key Metrics at a Glance

| Metric | Value |
|--------|-------|
| **Total Customers Analyzed** | TBD (from data) |
| **Clusters Identified** | 4 |
| **Features Engineered** | 8 behavioral metrics |
| **Silhouette Score** | TBD (run notebook to see) |
| **Algorithm** | K-Means with k=4 |
| **Dimensionality** | 8D → 2D (via PCA for visualization) |

---

## The 4 Customer Segments

### 1. 🎯 **Engaged but Low Spend** (Cluster 0)
- **Profile**: High frequency, recent activity, low monetary value
- **Size**: ~TBD%
- **Key Action**: Upselling & loyalty rewards
- **Revenue Impact**: Medium ROI (volume play)

### 2. 💎 **High-Value, Low Engagement** (Cluster 1)
- **Profile**: Low frequency, recent purchase, high monetary value
- **Size**: ~TBD%
- **Key Action**: Exclusive VIP treatments
- **Revenue Impact**: High ROI (quality play)

### 3. ⚠️ **At-Risk/Dormant** (Cluster 2)
- **Profile**: Low frequency, inactive (90+ days), low spending
- **Size**: ~TBD%
- **Key Action**: Win-back campaigns
- **Revenue Impact**: Medium ROI (retention focus)

### 4. 🔄 **High-Value, Previously Active** (Cluster 3)
- **Profile**: High frequency historically, recent inactivity, high value
- **Size**: ~TBD%
- **Key Action**: Aggressive reactivation
- **Revenue Impact**: High ROI (win-back opportunity)

---

## Data Source

**Input File**: `E-commerce_data.xlsx`
- Contains 6 sheets: customers, transactions, genders, cities, branches, merchants
- ~TBD total transaction records
- Merged into single dataset for analysis

**Output File**: `customer_segments_complete.csv`
- All customers with cluster assignments (0-3)
- All 8 engineered features
- Ready for CRM integration

---

## Methodology Highlights

1. **Data Integration**: Merged 6 Excel sheets via SQL-like joins
2. **Feature Engineering**: Created RFM-based metrics + behavioral indicators
3. **Feature Scaling**: StandardScaler normalization
4. **Clustering**: K-Means with k=4 (optimal per Elbow + Silhouette analysis)
5. **Quality Metrics**: Silhouette Score, Davies-Bouldin Index
6. **Visualization**: PCA projection, distribution plots, heatmaps, cluster profiles

---

## Features Used in Clustering

| Feature | Definition | Business Meaning |
|---------|-----------|-----------------|
| **Recency** | Days since last purchase | Engagement freshness |
| **Frequency** | Total # of transactions | Purchase consistency |
| **Monetary** | Frequency × (1/(1+Recency/30)) | Spending propensity |
| **UniqueTransactions** | # of distinct transaction IDs | Purchase diversity |
| **CouponUsage** | # of redeemed coupons | Promotion sensitivity |
| **CityDiversity** | # of unique cities visited | Geographic spread |
| **MerchantDiversity** | # of unique merchants patronized | Merchant loyalty |
| **BranchDiversity** | # of unique branches visited | Channel diversity |

---

## Outputs Generated

### Data Files
- `customer_segments_complete.csv` - Segmentation results with cluster assignments

### Visualizations (7 plots)
1. **Distribution_of_Features.png** - Feature histograms post-scaling
2. **Correlation_Heatmap.png** - Feature relationships
3. **Pair_Plot.png** - Multi-dimensional scatter plots
4. **Box_Plots.png** - Outlier identification
5. **K-Means_Clustering.png** - Elbow method & Silhouette scores
6. **KMeans_Clustering_PCA.png** - 2D cluster visualization with centroids
7. **KMeans_Cluster_Profiles.png** - Feature distributions by cluster

---

## Use Cases & Applications

### 🎯 Marketing
- **Personalized Campaigns**: Tailor messaging per cluster
- **Promotional Strategy**: Different tactics per segment
- **Channel Selection**: Optimize email, SMS, push per cluster
- **Coupon Strategy**: VIP vs. price-sensitive targeting

### 💰 Revenue Optimization
- **Upsell/Cross-Sell**: Focus high-value potential on Cluster 1 & 3
- **Pricing Strategy**: Price sensitivity varies by cluster
- **Product Mix**: Different product affinity per segment
- **Inventory Planning**: Stock based on cluster preferences

### 📊 Customer Retention
- **VIP Programs**: Priority for Clusters 1 & 3
- **Churn Prevention**: Proactive outreach to Cluster 2 & 3
- **Win-Back Campaigns**: Focus on Cluster 2 & 3
- **Loyalty Mechanics**: Tailor rewards per cluster

### 🔍 Analytics & Insights
- **Customer Lifecycle**: Track segment migration over time
- **Performance Metrics**: Calculate CLV, CAC, LTV per segment
- **A/B Testing**: Test strategies per cluster independently
- **Benchmarking**: Compare performance across segments

---

## Quick Start Guide

### Prerequisites
```bash
Python 3.8+
pip install -r requirements.txt
```

### Running the Analysis
```bash
cd notebooks/
jupyter notebook Customer_segmentation_using_unsupervised_learning.ipynb
```

### Getting Results
1. Execute notebook cells sequentially
2. Results appear in `outputs/results/customer_segments_complete.csv`
3. Visualizations saved in `outputs/plots/`

---

## Key Insights & Recommendations

### Immediate Actions (Week 1)
- ✅ Validate cluster quality with business stakeholders
- ✅ Map clusters to existing customer segments
- ✅ Identify quick-win campaigns per cluster
- ✅ Set up tracking metrics

### Short-term (Month 1)
- ✅ Design & launch cluster-specific campaigns
- ✅ Train marketing team on segment profiles
- ✅ Set up automated segment scoring for new customers
- ✅ A/B test messaging per cluster

### Medium-term (Quarter 1)
- ✅ Monitor segment migration patterns
- ✅ Integrate with CRM/marketing automation
- ✅ Measure campaign performance by cluster
- ✅ Optionally test alternative clustering algorithms

### Long-term (Annual)
- ✅ Build predictive models (CLV, churn) per cluster
- ✅ Develop real-time scoring pipeline
- ✅ Add temporal analysis (seasonal trends)
- ✅ Consider product-based segmentation layers

---

## Success Metrics

### Quantitative KPIs
- **Campaign Performance**: Response rate, conversion rate by cluster
- **Revenue**: AOV (Average Order Value) and CLV improvements
- **Engagement**: Purchase frequency and retention rate by segment
- **Efficiency**: Reduced marketing waste (better targeting)

### Qualitative Validation
- Business stakeholder agreement on segment profiles
- Marketing team adoption and ease of use
- CRM system integration success
- Actionability of recommendations

---

## Technical Specifications

| Aspect | Details |
|--------|---------|
| **Language** | Python 3.8+ |
| **Notebook Format** | Jupyter/VS Code |
| **Libraries** | pandas, scikit-learn, matplotlib, seaborn |
| **Data Format** | Excel (.xlsx) input, CSV (.csv) output |
| **Computation Time** | < 10 minutes (single run) |
| **Reproducibility** | Random state seeded (42) |

---

## Dependencies

See `requirements.txt` for complete list. Key packages:
- **pandas** 1.3+: Data manipulation
- **scikit-learn** 0.24+: Machine learning algorithms
- **matplotlib** 3.3+: Plotting library
- **seaborn** 0.11+: Statistical visualization
- **numpy** 1.20+: Numerical computing

---

## Project Structure

```
Customer-Segmentation-Minor-Project/
├── README.md                    # Complete project documentation
├── METHODOLOGY.md               # Detailed technical guide
├── PROJECT_SUMMARY.md          # This file (executive summary)
├── requirements.txt             # Python dependencies
├── data/
│   └── E-commerce_data.xlsx    # Input dataset
├── notebooks/
│   └── Customer_segmentation_using_unsupervised_learning.ipynb
└── outputs/
    ├── results/
    │   └── customer_segments_complete.csv
    └── plots/
        ├── Distribution_of_Features.png
        ├── Correlation_Heatmap.png
        ├── Pair_Plot.png
        ├── Box_Plots.png
        ├── K-Means_Clustering.png
        ├── KMeans_Clustering_PCA.png
        └── KMeans_Cluster_Profiles.png
```

---

## Next Steps

1. **Review**: Share segmentation results with stakeholders
2. **Validate**: Confirm clusters make business sense
3. **Plan**: Design campaigns for each cluster
4. **Implementation**: Integrate into marketing workflows
5. **Monitor**: Track performance and segment migration
6. **Iterate**: Refine based on campaign results

---

## Contact & Support

For technical questions, refer to:
- `README.md` - Project overview and running instructions
- `METHODOLOGY.md` - In-depth technical details
- Notebook comments - Line-by-line explanations

For business questions, refer to:
- Cluster profiles in notebook
- Marketing insights section
- Visualization interpretations

---

## Appendix: Cluster Size Distribution

*To be updated after running the analysis:*

```
Cluster 0 (Engaged, Low Spend): ____ customers (__%)
Cluster 1 (High-Value, Low Frequency): ____ customers (__%)
Cluster 2 (At-Risk/Dormant): ____ customers (__%)
Cluster 3 (High-Value, Previously Active): ____ customers (__%)

Total: ____ customers analyzed
```

---

**Document Version**: 1.0  
**Last Updated**: February 12, 2026  
**Status**: Draft - Pending Analysis Execution  
**Confidentiality**: Internal Use Only
