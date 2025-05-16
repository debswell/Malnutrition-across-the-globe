# Laporan Proyek Machine Learning - Debi Welani Christin Saragih

## Domain Proyek
Malnutrisi anak merupakan salah satu tantangan kesehatan global yang serius dan berdampak jangka panjang terhadap perkembangan manusia. Berdasarkan laporan Joint Child Malnutrition Estimates 2021, pada tahun 2020 diperkirakan:

- 149,2 juta anak di bawah usia 5 tahun mengalami stunting (kerdil),

- 45,4 juta anak mengalami wasting (kurus akut),

- 38,9 juta anak mengalami overweight (kelebihan berat badan).

Stunting dan wasting bukan hanya menandakan kekurangan gizi, tetapi juga memiliki dampak jangka panjang terhadap kualitas hidup anak seperti penurunan kemampuan belajar, potensi penghasilan yang lebih rendah saat dewasa, dan meningkatnya risiko penyakit kronis. Overweight juga menjadi perhatian karena dapat menyebabkan obesitas dini dan penyakit tidak menular seperti diabetes atau penyakit jantung sejak usia muda.

Masalah malnutrisi anak harus segera ditangani karena:

- Dampak jangka panjang terhadap perkembangan otak dan fisik anak, terutama pada periode emas 1000 hari pertama kehidupan.

- Kontribusi terhadap siklus kemiskinan antar generasi – anak yang mengalami stunting cenderung memiliki performa pendidikan yang buruk dan produktivitas ekonomi yang rendah.

- Target global belum tercapai – Hanya sekitar 25% negara yang saat ini "on track" untuk mencapai target pengurangan stunting pada tahun 2030. Bahkan lebih sedikit negara yang diperkirakan akan mencapai target pengurangan overweight.

**Referensi :** 
UNICEF, WHO, & World Bank Group. (2021). Levels and trends in child malnutrition: Key findings of the 2021 edition of the Joint Child Malnutrition Estimates. https://data.unicef.org/topic/nutrition/malnutrition/

**File Download :** https://data.unicef.org/wp-content/uploads/2021/07/JME-2021-United-Nations-regions-v2.pdf

## Business Understanding
### Problem Statements
- Pernyataan Masalah 1: Prevalensi stunting masih tinggi di banyak negara, khususnya di negara berpenghasilan rendah, dan belum menunjukkan penurunan yang cukup signifikan dari waktu ke waktu.

- Pernyataan Masalah 2: Belum ada model prediktif berbasis data yang dapat memperkirakan nilai stunting di masa depan dengan mempertimbangkan faktor seperti klasifikasi pendapatan negara, populasi balita, dan indikator malnutrisi lainnya.
### Goals
- Jawaban Masalah 1: Menganalisis tren prevalensi stunting antar negara dan hubungannya dengan faktor-faktor seperti status ekonomi dan indikator malnutrisi lainnya (wasting, overweight, underweight).

- Jawaban Masalah 2: Membangun model regresi prediktif untuk memperkirakan nilai prevalensi stunting berdasarkan data Country, Income Classification, Year, U5 Population, dan prevalensi indikator malnutrisi lainnya.
### Solution Statements
- Solusi 1: Menggunakan algoritma machine learning regresi seperti:

  * Linear Regression (baseline model)

  * Random Forest Regressor

  * XGBoost Regressor

  * Dengan evaluasi menggunakan metrik seperti:

    * MAE (Mean Absolute Error)

    * RMSE (Root Mean Squared Error)

    * R² Score

- Solusi 2: Melakukan feature engineering:

  * One-hot encoding pada kolom Income Classification dan Country.

  * Menangani missing values pada indikator malnutrisi.

  * Normalisasi variabel numerik jika diperlukan.

## Data Understanding
  Dataset yang digunakan berasal dari Kaggle dengan nama:
📁 malnutrition-estimates.csv
📎 Link: https://www.kaggle.com/datasets/ruchi798/malnutrition-across-the-globe
Dataset ini berisi data agregat tahunan prevalensi berbagai bentuk malnutrisi pada anak usia di bawah 5 tahun, yang dikelompokkan berdasarkan negara dan klasifikasi ekonomi. Tidak terdapat pemisahan berdasarkan jenis kelamin, indikator malnutrisi sudah dalam bentuk kolom terpisah.

### Variabel-Variabel 
- Country	: Nama negara
- Year : Tahun data dikumpulkan
- Income Classification	: Kategori pendapatan negara menurut World Bank (Low, Lower-Middle, Upper-Middle, High)
- LDC	: Least Developed Country: 1 jika ya, 0 jika tidak
- LIFD : Low Income Food Deficit Country: 1 jika ya, 0 jika tidak
- LLDC or SID2 : Negara Landlocked Developing Country atau Small Island Developing States
- Survey Sample (N)	: Ukuran sampel survei (jumlah anak)
- Severe Wasting : Persentase anak dengan severe wasting (berat badan sangat rendah terhadap tinggi badan)
- Wasting	: Persentase anak dengan wasting (berat badan rendah terhadap tinggi badan)
- Overweight : Persentase anak overweight (kelebihan berat badan terhadap tinggi badan)
- Stunting : Persentase anak dengan stunting (tinggi badan rendah terhadap usia)
- Underweight	: Persentase anak underweight (berat badan rendah terhadap usia)
- U5 Population ('000s)	: Populasi anak di bawah usia 5 tahun (dalam ribuan)

## Data Preparation
