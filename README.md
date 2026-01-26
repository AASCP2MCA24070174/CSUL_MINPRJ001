# Customer Segmentation Using Unsupervised Learning

## Minor Project (21CSA697A)

### Project Description
This project focuses on customer segmentation using unsupervised machine learning techniques.
The objective is to analyze customer demographics, transaction behavior, and engagement data
to identify meaningful customer segments for data-driven marketing decisions.

### Dataset
This project uses the *E-Commerce* dataset from Kaggle:

🔗 https://www.kaggle.com/datasets/e-commerce/data

After downloading the dataset, place the file `E-commerce_data.xlsx` inside the `data/` directory.

### Tools & Technologies
- Python
- Pandas, NumPy
- Matplotlib, Seaborn
- Scikit-learn
- Jupyter Notebook

### Techniques Used
- Exploratory Data Analysis (EDA)
- Feature Engineering
- One-Hot Encoding
- Standardization (StandardScaler)
- K-Means Clustering
- Silhouette Score
- Elbow Method

### Workflow
1. Data Loading and Merging
2. Data Cleaning and EDA
3. Feature Selection and Encoding
4. K-Means Model Training
5. Cluster Analysis and Interpretation

### Results
- Optimal number of clusters selected using Elbow Method and Silhouette Score
- Customers segmented into 4 distinct clusters
- Each cluster represents unique purchasing behavior patterns

### How to Run
```bash
pip install -r requirements.txt
jupyter notebook
