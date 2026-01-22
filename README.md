# Urban Heat Island (UHI) Analysis and Modeling Project

## 📌 Project Overview

This project focuses on analyzing and modeling **Urban Heat Island (UHI) intensity** using geospatial, environmental, and built‑environment variables derived from satellite data and field datasets. The workflow covers the full data science pipeline: data loading, visualization, feature engineering, outlier handling, exploratory analysis, and preparation for machine‑learning modeling.

The notebook (`Model.ipynb`) demonstrates how different spectral indices and urban indicators relate to UHI classes across multiple cities (Chile, Brazil, and Sierra Leone samples).

---

## 📂 Datasets Used

Three main CSV datasets were loaded:

* `sample_chile_uhi_data.csv` (Santiago, Chile)
* `sample_Brazil_uhi_data.csv` (Rio, Brazil)
* `sample_Sierra_V2.csv` (Sierra Leone)

Each dataset contains the following key variables:

* **Longitude / Latitude** – Geographic coordinates of each observation point.
* **UHI_Class** – Urban Heat Island category (target variable for classification).
* **median_NDVI** – Vegetation index (greenness). Higher values = more vegetation.
* **median_NDBI** – Built‑up index. Higher values = more urbanized surfaces.
* **median_NDWI** – Water/moisture index. Higher values = more surface water or moisture.
* **building_density_100m** – Building concentration within 100 m radius.

---

## 🛠 Libraries and Tools

The following libraries were imported and used:

* **NumPy, Pandas** – numerical computation and data manipulation
* **Matplotlib, Seaborn** – visualization
* **GeoPandas** – spatial data handling
* **pystac_client, planetary_computer, odc.stac** – accessing satellite imagery from Microsoft Planetary Computer
* **Rasterio** – reading GeoTIFF files
* **Scikit‑learn** – preprocessing, modeling, and evaluation

Warnings were suppressed for clean outputs, and Seaborn styling was enabled for better plots.

---

## 🛰 Satellite Data & Spectral Indices Visualization

GeoTIFF files were loaded for:

* Santiago (Chile)
* Rio (Brazil)
* Sierra Leone

A custom function `plot_spectral_indices()` was created to:

* Load GeoTIFF images
* Extract spectral bands
* Plot and visualize **NDVI, NDBI, and NDWI** indices

### Results

* NDVI highlighted vegetated vs. non‑vegetated areas.
* NDBI clearly showed built‑up urban zones.
* NDWI identified water and moisture‑rich surfaces.

These plots confirmed strong spatial variation in vegetation, built surfaces, and moisture across the cities.

---

## 📊 Exploratory Data Analysis (EDA)

### 1. Variable Interpretation

Detailed explanations were provided for all variables, describing how each contributes to understanding UHI behavior.

### 2. Scatter Plots & Pairwise Relationships

Scatter plots between:

* NDVI vs NDBI
* NDVI vs NDWI
* NDBI vs NDWI

#### Observations

* High NDBI (built‑up areas) is associated with stronger UHI intensity.
* High NDVI (vegetation) generally reduces UHI intensity.
* NDWI moderates temperature but is less dominant in dense urban cores.

### 3. Distribution Analysis

* **Violin plots and catplots** were used to analyze NDWI distribution across UHI classes.

#### Key Findings

* Low‑temperature classes showed higher NDWI occurrence.
* High‑temperature classes had the lowest moisture representation.
* Mid‑temperature classes dominated most samples.

---

## 🧪 Feature Engineering

A dedicated section performed feature engineering to improve model performance:

Steps included:

* Selecting relevant numerical features
* Transforming variables where necessary
* Encoding categorical variables (if present)
* Preparing clean feature matrices (`X`) and labels (`y`)

These steps ensured that the dataset was suitable for machine‑learning models.

---

## 🚨 Outlier Detection and Removal

Outlier handling was applied to both:

* **Training dataset**
* **Test dataset**

Using the **quantile (IQR) method**, extreme values were identified and removed for:

* NDVI
* NDBI
* NDWI
* Building density

### Results

* Reduced noise and extreme distortions in the dataset
* Improved data consistency and stability for modeling

---

## 🧩 Train–Test Preparation

The dataset was split into:

* **Training set** – for model learning
* **Test set** – for evaluation

Separate preprocessing and outlier handling were applied to both to avoid data leakage.

---

## 🤖 Modeling Preparation

The notebook prepares the data for machine‑learning classification of **UHI_Class** using:

* Clean numerical features
* Normalized / scaled inputs (where required)
* Balanced and filtered datasets after outlier removal

This sets the foundation for applying models such as:

* Random Forest
* Support Vector Machines
* K‑Nearest Neighbors
* Gradient Boosting

---

## 📈 Key Results & Insights

✔ Vegetation (NDVI) shows a strong cooling effect on UHI intensity.
✔ Built‑up density (NDBI and building density) strongly increases heat intensity.
✔ Moisture (NDWI) moderates temperature but is less influential in dense urban cores.
✔ Outlier removal significantly improved data quality and stability.

---

## 📁 Project Structure

```
Model.ipynb                # Main analysis notebook
sample_chile_uhi_data.csv # Chile dataset
sample_Brazil_uhi_data.csv# Brazil dataset
sample_Sierra_V2.csv      # Sierra Leone dataset
Data/
 ├── sample_chile.tiff
 ├── sample_Brazil.tiff
 └── sample_Sierra_V2.tiff
```

---

## 🚀 How to Run

1. Clone the repository:

```bash
git clone <repo-url>
```

2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Open the notebook:

```bash
jupyter notebook Model.ipynb
```

---

## 🧭 Conclusion

This project demonstrates a full geospatial machine‑learning workflow for **Urban Heat Island analysis**, combining satellite imagery, spatial indices, statistical exploration, feature engineering, and modeling preparation. It provides a strong foundation for predicting UHI intensity and supporting urban climate mitigation strategies.

---

