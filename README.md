# ⚡ Electricity Consumption Forecasting Using Machine Learning

## 📋 Project Overview

Proyek prediksi konsumsi listrik harian menggunakan machine learning untuk mendukung grid management dan perencanaan kapasitas energi. Project ini dikerjakan sebagai bagian dari **seleksi Compfest 17 tahun 2025**, dengan fokus pada analisis time series dan ensemble learning untuk memprediksi pola konsumsi listrik berdasarkan data historis dan faktor lingkungan.

---

## 🎯 Context & Objective

Dalam konteks bisnis energi dan kebijakan publik, memprediksi konsumsi listrik harian merupakan hal yang mendesak karena:

### 1. Grid Management
Memastikan keseimbangan antara supply dan demand listrik secara real-time untuk mencegah blackout atau overload pada sistem distribusi

### 2. Perencanaan Kapasitas
Membantu perusahaan energi dalam merencanakan infrastruktur dan investasi jangka panjang berdasarkan proyeksi kebutuhan konsumsi

### 3. Efisiensi Operasional
Mengoptimalkan penggunaan sumber daya energi dan mengurangi biaya operasional dengan prediksi yang akurat

---

## 📊 Dataset

Dataset terdiri dari data konsumsi listrik harian dengan beberapa cluster berbeda, mencakup periode **2014-2021**. 

**Fitur utama:**
- Data temporal (tanggal)
- Variabel cuaca (suhu, radiasi matahari)
- Cluster ID (segmentasi geografis atau demografis)
- **Target:** konsumsi listrik harian

---

## 🔬 Methodology

### 1. Exploratory Data Analysis (EDA)
- Analisis dimensi data dan missing values
- Deteksi duplikasi data
- Statistik deskriptif dan distribusi konsumsi
- Analisis pola temporal dan seasonal trends

### 2. Feature Engineering

Fitur-fitur baru yang dibuat untuk meningkatkan pemahaman model terhadap pola konsumsi:

#### Temporal Features:
- `dayofweek`: hari dalam seminggu (0-6)
- `month`: bulan dalam tahun (1-12)
- `year`: tahun pengamatan (2014-2021)
- `dayofyear`: hari ke-n dalam setahun (1-365)
- `weekofyear`: minggu ke-n dalam setahun (1-53)

#### Cyclical Features:
- `sin_dayofyear`: representasi siklus tahunan menggunakan fungsi sinus
- `cos_dayofyear`: representasi siklus tahunan menggunakan fungsi cosinus

#### Interaction Features:
- `temp_radiation_interaction`: interaksi antara suhu dan radiasi matahari

**Impact:** Fitur-fitur ini meningkatkan pemahaman model dengan menangkap pola musiman dan siklikal dalam konsumsi listrik, serta mempertimbangkan efek interaksi antar variabel cuaca.

### 3. Model Development

Beberapa algoritma machine learning digunakan dan dibandingkan:

| Model | Description |
|-------|-------------|
| **Random Forest Regressor** | Ensemble method berbasis decision tree |
| **XGBoost** | Gradient boosting optimal untuk handling outliers |
| **LightGBM** | Gradient boosting framework yang efisien dan cepat |
| **Gradient Boosting Regressor** | Ensemble sequential learning |

Setiap model dilatih **per cluster** untuk menangkap karakteristik konsumsi yang berbeda-beda.

### 4. Model Evaluation & Validation

Evaluasi model menggunakan multiple metrics:
- **RMSE** (Root Mean Square Error): Mengukur magnitude error prediksi
- **MAPE** (Mean Absolute Percentage Error): Mengukur error dalam persentase
- **MAE** (Mean Absolute Error): Mengukur rata-rata absolute error

Analisis overfitting/underfitting dilakukan dengan membandingkan performa pada training dan validation set.

### 5. Model Optimization
- Hyperparameter tuning untuk setiap model
- Handling outliers dan data volatil pada cluster tertentu
- Cross-validation menggunakan **TimeSeriesSplit** untuk menghindari data leakage

---

## 🏆 Key Findings & Results

✅ Model secara umum **tidak mengalami overfitting atau underfitting** yang signifikan untuk cluster 1-3

⚠️ Cluster 4 menunjukkan tantangan khusus akibat karakteristik data yang lebih volatil, memerlukan pendekatan khusus dengan XGBoost yang lebih robust terhadap outliers

📈 Feature engineering temporal dan cyclical features terbukti **signifikan meningkatkan akurasi prediksi** dengan menangkap pola musiman

🎯 Ensemble methods (XGBoost, LightGBM) memberikan **performa terbaik** dibandingkan model individual

---

## 🛠️ Technical Stack

```
Programming Language: Python
Data Manipulation: Pandas, NumPy
Machine Learning: Scikit-learn, XGBoost, LightGBM
Visualization: Matplotlib, Seaborn
Model Selection: TimeSeriesSplit, GridSearchCV
Feature Engineering: Custom temporal and interaction features
```

---

## 💡 Challenges & Solutions

### Challenge 1: Data Volatility pada Cluster 4
**Solution:** Menggunakan XGBoost dengan tuning khusus karena lebih resistant terhadap outliers, serta menambahkan penalty regularization

### Challenge 2: Overfitting Risk pada Time Series Data
**Solution:** Implementasi TimeSeriesSplit untuk cross-validation yang proper, menghindari data leakage dari future information

### Challenge 3: Seasonal Pattern Recognition
**Solution:** Pembuatan cyclical features (sin/cos transformation) untuk menangkap pola musiman yang berulang

---

## 💼 Business Impact

Model ini dapat membantu perusahaan energi dalam:

1. **Real-time Grid Management**  
   Prediksi akurat memungkinkan penyesuaian supply listrik secara proaktif

2. **Cost Reduction**  
   Optimasi penggunaan generator dan pembelian energi dari external sources

3. **Infrastructure Planning**  
   Data-driven decision making untuk investasi infrastruktur jangka panjang

4. **Customer Service**  
   Meningkatkan reliability layanan dengan menghindari service interruption

---

## 🚀 Future Improvements

- [ ] Integrasi data eksternal (holiday calendar, economic indicators)
- [ ] Implementasi deep learning models (LSTM, GRU) untuk menangkap long-term dependencies
- [ ] Real-time prediction system dengan automated retraining
- [ ] Ensemble stacking untuk kombinasi multiple models
- [ ] Explainable AI untuk interpretasi prediksi kepada stakeholders

---

## 📌 Project Information

- **Year:** 2025
- **Context:** Compfest 17 Selection Competition
- **Type:** Machine Learning - Time Series Forecasting

---

## 📫 Connect

[Tambahkan kontak atau link portfolio Anda di sini jika diperlukan]
