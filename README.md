README.md

Clustering Urban Air Pollution and Meteorological Conditions Using K-Means for Environmental Risk Analysis

This project applies K-Means Clustering and Principal Component Analysis (PCA) to a large-scale environmental dataset containing air pollution and meteorological measurements from Spain. The study focuses on identifying pollution regimes, atmospheric anomalies, and environmental risk patterns using unsupervised machine learning techniques.  ￼

⸻

Project Overview

This project analyzes approximately 6 GB of air-quality and meteorological data collected from monitoring stations across Spain. The dataset includes:

* Pollutant concentrations
* Temperature
* Relative humidity
* Wind speed
* Wind direction
* Barometric pressure

The project uses:

* PySpark for large-scale distributed data processing
* Scikit-Learn for machine learning
* K-Means Clustering for grouping pollution patterns
* PCA for dimensionality reduction and visualization
* Matplotlib/Seaborn for data visualization

The study identified an optimal cluster count of K = 4 using the Elbow Method and Silhouette Analysis.  ￼

⸻

Dataset

Dataset Source:
Hugging Face METRAQ Air Quality Dataset￼

The dataset contains:

* Air pollution measurements
* Meteorological variables
* Time-series environmental monitoring data

⸻

Project Structure

├── data/
│   └── air_quality_data.csv
│
├── notebooks/
│   └── BIG_DATA_KMeans_Code.ipynb
│
├── outputs/
│   ├── elbow_method.png
│   ├── silhouette_analysis.png
│   ├── pca_clusters.png
│   └── sensitivity_analysis.png
│
├── README.md
└── requirements.txt

⸻

Installation

1. Clone the Repository

git clone https://github.com/yourusername/air-pollution-kmeans.git
cd air-pollution-kmeans


2. Install Dependencies

pip install pyspark pandas numpy matplotlib seaborn scikit-learn


Running the Project

Option 1 — Google Colab (Recommended)

Step 1 — Upload Dataset to Google Drive

Upload the dataset CSV files into your Google Drive.

Example path:

/MyDrive/BigDataProject/

⸻

Step 2 — Mount Google Drive

from google.colab import drive
drive.mount('/content/drive')

⸻

Step 3 — Load Dataset Using PySpark

from pyspark.sql import SparkSession
spark = SparkSession.builder \
    .appName("AirPollutionKMeans") \
    .getOrCreate()
df = spark.read.csv(
    "/content/drive/MyDrive/BigDataProject/air_quality_data.csv",
    header=True,
    inferSchema=True
)
df.show(5)

⸻

Data Preprocessing

The preprocessing pipeline includes:

* Removing null values
* Feature engineering
* Pivoting pollutant variables
* Feature scaling
* Temporal alignment
* Outlier handling

Example preprocessing:

from pyspark.sql.functions import col
df_clean = df.dropna()
df_clean = df_clean.withColumn(
    "value",
    col("value").cast("double")
)

⸻

Running K-Means Clustering

from pyspark.ml.clustering import KMeans
kmeans = KMeans(
    k=4,
    seed=42,
    featuresCol="features"
)
model = kmeans.fit(final_df)
predictions = model.transform(final_df)

⸻

PCA Visualization

PCA is used to project the high-dimensional pollution data into a 2D space for visualization.

from pyspark.ml.feature import PCA
pca = PCA(
    k=2,
    inputCol="scaledFeatures",
    outputCol="pcaFeatures"
)
pca_model = pca.fit(data)

⸻

Visualizations Included

The project generates the following visualizations:

* Elbow Method Plot
* Silhouette Analysis
* PCA Cluster Visualization
* Cluster Sensitivity Analysis

These visualizations help evaluate:

* Optimal cluster count
* Cluster cohesion
* Cluster separation
* Model stability
* Environmental anomaly detection

⸻

Key Findings

* The optimal number of clusters was found to be K = 4
* K-Means successfully isolated high-risk pollution regimes
* PCA visualizations revealed elongated non-spherical pollution patterns
* The model showed sensitivity to random initialization seeds
* K-Means++ improved clustering stability significantly

￼
￼

⸻

Tools and Technologies

* Python
* PySpark
* Scikit-Learn
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Google Colab

⸻

Researchers

* Raphael Zeth Acosta
* Darrie Andrei Dizon
* Milaine Antonelle Dumpit
* Zane Orilla

Department of Mathematics and Physics
University of Santo Tomas
Manila, Philippines

￼

⸻

References

The complete references used in the study are included in the paper.  ￼
