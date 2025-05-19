# Laporan Proyek Machine Learning - Debi Welani Christin Saragih

## 🌍 Domain Proyek : Kesehatan
Malnutrisi anak merupakan salah satu permasalahan kesehatan global yang berdampak langsung pada kelangsungan hidup dan perkembangan anak. Laporan Joint Child Malnutrition Estimates 2021 menunjukkan bahwa pada tahun 2020:

- 149,2 juta anak di bawah usia 5 tahun mengalami stunting (tinggi badan rendah untuk usia),

- 45,4 juta anak mengalami wasting (berat badan rendah untuk tinggi badan),

- 38,9 juta anak mengalami overweight (kelebihan berat badan).

Stunting secara khusus menjadi perhatian karena merupakan bentuk malnutrisi kronis yang dapat menurunkan kemampuan belajar, produktivitas ekonomi, hingga meningkatkan risiko penyakit tidak menular di masa depan. Masalah ini juga berkontribusi pada terjadinya siklus kemiskinan antargenerasi, karena anak yang mengalami malnutrisi cenderung memiliki kualitas hidup yang lebih rendah saat dewasa.

Namun, meskipun telah dilakukan berbagai intervensi, data global menunjukkan bahwa hanya 25% negara yang saat ini berada di jalur yang benar (on track) untuk mencapai target pengurangan stunting pada tahun 2030. Sementara itu, tantangan yang lebih kompleks juga muncul karena tren overweight pada anak juga meningkat, terutama di negara berkembang.

Dataset yang digunakan dalam proyek ini, yaitu malnutrition-estimates.csv dari Kaggle, menyajikan data prevalensi malnutrisi berdasarkan negara, tahun, dan klasifikasi ekonomi, yang dikompilasi dari sumber kredibel seperti UNICEF, WHO, dan World Bank. Data ini memberikan gambaran penting untuk:

- Menganalisis hubungan antara status ekonomi suatu negara dan prevalensi stunting,

- Membangun model prediktif (regresi) untuk memperkirakan nilai prevalensi stunting di tahun-tahun mendatang.

Mengapa masalah ini perlu diselesaikan:
- Dampak jangka panjang terhadap perkembangan otak dan fisik anak, khususnya di masa awal kehidupan (periode 1000 hari pertama).

- Kontribusi terhadap siklus kemiskinan antar generasi yang dapat memperparah ketimpangan sosial.

- Ketidaktercapaian target global dalam pengurangan stunting dan overweight anak di bawah usia 5 tahun.

- Kebutuhan model prediktif untuk membantu pemangku kebijakan dalam mengarahkan intervensi lebih dini dan tepat sasaran.

Proyek ini bertujuan untuk membangun sistem prediksi berbasis data guna membantu para pengambil keputusan dalam mengalokasikan sumber daya, menetapkan prioritas, dan merancang kebijakan gizi anak yang lebih efektif.

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
  * Ridge
  * Lasso
  * XGBoost Regressor
  * Dengan evaluasi menggunakan metrik seperti:

    * MAE (Mean Absolute Error)

    * RMSE (Root Mean Squared Error)

    * R² Score

- Solusi 2: Melakukan Pra Pemrosesan

  * Encoding pada kolom Country.

  * Menangani missing values pada indikator malnutrisi.

  * Standarisasi variabel numerik jika diperlukan.

## Data Understanding
  Dataset yang digunakan berasal dari Kaggle dengan nama:
📁 malnutrition-estimates.csv
📎 Link: https://www.kaggle.com/datasets/ruchi798/malnutrition-across-the-globe
Dataset ini berisi data agregat tahunan prevalensi berbagai bentuk malnutrisi pada anak usia di bawah 5 tahun, yang dikelompokkan berdasarkan negara dan klasifikasi ekonomi. Tidak terdapat pemisahan berdasarkan jenis kelamin, indikator malnutrisi sudah dalam bentuk kolom terpisah.

Dataset terdiri dari 924 baris dan 20 kolom

### Variabel-Variabel 
- ISO code : Kode ISO
- Country	: Nama negara
- Survey Year : Tahun melakukan Survey
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
- Notes : Note yang ada pada dataset
- Report Author : Laporan penulis terhadap data
- Source : Sumber
- Short Source : Singkatan dari sumber
- U5 Population ('000s)	: Populasi anak di bawah usia 5 tahun (dalam ribuan)

  Tidak semua variabel akan digunakan

## Data Preparation
Teknik data preparation yang digunakan adalah 

- Menghapus beberapa fitur yang tidak dibutuhkan
- Mengatasi nilai null dengan mengisi dengan nilai mean
- Mengatasi outlier dengan cara menghapusnya

Data preparation Utama : 
* Melakukan encoding pada data kategorikal, teknik yang digunakan adalah Frequency Encoding. Supaya data yang bertipe kategori menjadi numerik sehingga model dapat mengerti pada data
* Melakukan Reduksi Dimensi PCA terhdapat fitur severe wasting dan wasting untuk mengurangi dimensi pada dataset
* Melakukan beberapa feature enginering seperti:
  - Fitur interaksi : menangkap beberapa fitur interaksi seperti (underweight dan overweight) dan (populasi dan income)
  - Membuat fitur polinomial : untuk menangkap hubungan non liniear antara year dan prevelensi Stunting
* Pembagian data  (Train-Test-Split) untuk emmbagi data menajdi data latih dan data uji dengan skala 80:20
* Melakukan standarisasi terhadap data numerik, supaya distribusi data mean dan std nya seragam

## Modeling
Model yang digunakan yaitu untuk membuat model regresi, terdapat 5 model yang diguankan yaitu 
  * Linear Regression : biasa untuk baseline model
  * Random Forest Regressor : model parameter yang digunkaan untuk mengurangi overfitting
  * Ridge Regression : model yang mengatasi multicollinearity)
  * Lasso Regression : model yang diguankan untuk feature selection
  * XGBoost Regresso : model regularisasi yang digunakan untuk mengurangi overfitting

Karena model yang digunakan ada 5, maka akan dilakukan evaluasi untuk memeilih model mana yang terbaik.
Model terbaik yang didapat adalah Ridge Regression, oleh karena itu kita menggunakan model Ridge Regression karena pada metrik, model yang paling baik adalah Ridge Regression

## Evaluation
Pada model ini, proses evaluasi yang digunakan adalah 
* MAE (Mean Absolute Error) : Mengukur rata-rata besarnya kesalahan prediksi
* RMSE (Root Mean Squared Error) : Mengukur akar dari rata-rata kuadrat kesalahan prediksi
* R² Score : Mengukur proporsi variasi dalam variabel target

  Hasil yang didapat : 
* Hasil Evaluasi semua model :
  ![image](https://github.com/user-attachments/assets/a86ba19d-9d4a-4469-9a5c-3d09f514ebbc)

* Hasil Evaluasi model Ridge Regression: 
  ![image](https://github.com/user-attachments/assets/720daac9-039c-4c5c-8251-f7c90d820de1)

# Contoh Skenario untuk melihat prediksi model 
![image](https://github.com/user-attachments/assets/588a5f28-3c39-4949-8378-84b639c675f5)

**Output**
![image](https://github.com/user-attachments/assets/d5c181a6-4149-4e88-9efa-d6b6ed5910cc)
