Air Pollution Clustering using K-Means

This project uses K-Means Clustering and PCA to analyze air pollution and weather data from Spain. The goal is to identify pollution patterns and environmental risk groups using machine learning.  ￼

⸻

Dataset

Dataset Source:
Hugging Face METRAQ Air Quality Dataset￼

The dataset contains:

* Air pollution measurements
* Temperature
* Humidity
* Wind speed
* Wind direction
* Atmospheric pressure

⸻

Tools Used

* Python
* PySpark
* Scikit-Learn
* Pandas
* Matplotlib
* Seaborn
* Google Colab

⸻

How to Run the Project

1. Install Dependencies

pip install pyspark pandas numpy matplotlib seaborn scikit-learn

⸻

2. Mount Google Drive (Google Colab)

from google.colab import drive
drive.mount('/content/drive')

⸻

3. Start PySpark

from pyspark.sql import SparkSession
spark = SparkSession.builder \
    .appName("AirPollutionKMeans") \
    .getOrCreate()

⸻

4. Load the Dataset

df = spark.read.csv(
    "/content/drive/MyDrive/BigDataProject/air_quality_data.csv",
    header=True,
    inferSchema=True
)
df.show(5)

⸻

Data Preprocessing

The project performs:

* Removing null values
* Cleaning data
* Feature scaling
* Feature engineering
* PCA dimensionality reduction

Example:

df_clean = df.dropna()

⸻

Run K-Means Clustering

from pyspark.ml.clustering import KMeans
kmeans = KMeans(k=4, seed=42)
model = kmeans.fit(data)
predictions = model.transform(data)

⸻

Visualizations

The project includes:

* Elbow Method
* Silhouette Analysis
* PCA Cluster Visualization
* Sensitivity Analysis

These help evaluate cluster quality and pollution patterns.

⸻

Key Findings

* The optimal number of clusters was K = 4
* K-Means successfully grouped pollution patterns
* PCA helped visualize pollution behavior
* K-Means was sensitive to random initialization seeds

￼

⸻

Researchers

* Raphael Zeth Acosta
* Darrie Andrei Dizon
* Milaine Antonelle Dumpit
* Zane Orilla

University of Santo Tomas
Department of Mathematics and Physics

￼
