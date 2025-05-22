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
- Jawaban Masalah 1: Menganalisis tren prevalensi stunting dan hubungannya dengan faktor-faktor seperti status ekonomi dan indikator malnutrisi lainnya (wasting, overweight, underweight).

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

### Kondisi Data 
- Menghapus fitur yang tidak dibutuhkan : 'Unnamed: 0','ISO code','Survey Year','Survey Sample (N)','Notes','Report Author','Source','Short Source','LLDC or SID2'
- Terdapat missing value pada fitur yang akan digunakan pada kolom:
   - Severe Wasting	: 228
   - Wasting	: 47
   - Overweight	: 136
   - Stunting	: 37
   - Underweight	: 22
- Terdapat outlier pada kolom : 'severe_wasting','wasting','overweight','underweight','popilation'

## Data Preparation
Teknik data preparation yang digunakan adalah 

- Menghapus beberapa fitur yang tidak dibutuhkan
- Mengatasi missing value dengan mengisi dengan nilai mean
- Mengatasi outlier dengan cara menghapus data outlier

Data preparation Utama : 
* Melakukan encoding pada data kategorikal (Country)
* Mengubah kolom Country menjadi kolom numerik baru Country_encoded dengan mengganti nama negara menjadi nilai rata-rata Stunting dari negara tersebut
* Menambahkan kolom baru Country_freq yang berisi nilai frekuensi country sebagai representasi numerik dari negara.
* Melakukan Reduksi Dimensi PCA terhdapat fitur severe wasting dan wasting untuk mengurangi dimensi pada dataset
* Hasil transformasi PCA disimpan di kolom baru dim_Wasting.
* Menghapus kolom 'severe wasting' dan 'wasting'
* Membuat fitur baru Underweight_Overweight dengan mengalikan nilai pada kolom Underweight dan Overweight.
* Membuat fitur baru Pop_Income dengan mengalikan U5 Population ('000s) dan Income Classification.
* Membuat fitur baru Year_squared dengan mengkuadratkan nilai pada kolom Year.
* Membuat fitur input X dengan menghapus kolom target Stunting dan kolom kategori asli Country dari DataFrame.
* Menambahkan kembali kolom Country tapi menggunakan hasil encoding (kolom Country_encoded) supaya data kategori menjadi numerik.
* Membuat variabel target y yang berisi nilai dari kolom Stunting.
* Pembagian data  (Train-Test-Split) untuk emmbagi data menajdi data latih dan data uji dengan skala 80:20
* Menggunakan StandardScaler untuk menstandarisasi fitur numerik agar memiliki mean 0 dan standar deviasi 1.

## Modeling
Model yang digunakan yaitu untuk membuat model regresi, terdapat 5 model yang diguankan yaitu 
  * Linear Regression : biasa untuk baseline model
    - Linear Regression adalah algoritma supervised learning yang digunakan untuk memprediksi nilai target (variabel dependen) berdasarkan satu atau lebih variabel independen. Algoritma ini bekerja dengan mencari garis lurus (dalam 2D) atau hyperplane (dalam dimensi yang lebih tinggi) yang paling cocok dengan data training.
    - Parameter yang digunakan yaitu parameter default dari scikit-learn:
      |Parameter | Nilai Default | Penjelasan |
      |-------------|--------|-------------------------------------------------------|
      fit_intercept | True | Menentukan apakah intercept (β₀) dihitung atau tidak|
      copy_X | True | Apakah data input X akan di-copy atau dimodifikasi langsungn |
      n_jobs | None | Jumlah processor yang digunakan untuk komputasi paralel
      positive | False | Apakah koefisien harus positif atau tidak|
  * Ridge Regression : model yang mengatasi multicollinearity
    - Ridge Regression adalah pengembangan dari Linear Regression yang menambahkan L2 regularization untuk mengatasi masalah multicollinearity dan overfitting. Algoritma ini menambahkan penalty term pada cost function.
    - Parameter yang digunakan :
      |Parameter | Nilai | Penjelasan |
      |----------|-------|------------|
      alpha | 1.0 | Strength regularisasi L2. Nilai lebih besar = regularisasi lebih kuat|
      random_state|123|Seed untuk reproducibility|
      fit_intercept|True (default)|Apakah intercept dihitung|
      copy_X|True (default)|Apakah data input di-copy|
  * Lasso Regression : model yang diguankan untuk feature selection
    - Lasso (Least Absolute Shrinkage and Selection Operator) menggunakan L1 regularization yang dapat melakukan feature selection otomatis dengan membuat beberapa koefisien menjadi nol.
    - Parameter yang digunakan :
      | Parameter|Nilai|Penjelasan|
      |----------|-----|---------|
      alpha | 0.1 | Strength regularisasi L1. Nilai lebih kecil dari Ridge untuk mencegah terlalu banyak fitur yang di-nol-kan
      |random_state| 123 | Seed untuk reproducibility
      |fit_intercept | True (default)| Apakah intercept dihitung
      |copy_X | True |(default)Apakah data input di-copy|

  * Random Forest Regressor : model parameter yang digunkaan untuk mengurangi overfitting
    - Random Forest adalah ensemble method yang menggabungkan banyak decision trees dengan teknik bagging dan random feature selection. Setiap tree dilatih pada subset data yang berbeda.
    - Parameter yang digunakan :
      | Parameter|Nilai|Penjelasan|
      |----------|-------|------------|
      | max_depth            | 5 | Kedalaman maksimum setiap tree (mencegah overfitting) 
      | min_samples_split    | 5  | Minimum sampel untuk melakukan split pada node 
      | min_samples_leaf     | 2 | Minimum sampel yang harus ada di setiap leaf          
      | max_features         | sqrt   | Jumlah fitur yang dipertimbangkan per split (√total_features)
      | n_estimators         | 100       | Jumlah decision trees dalam forest  
      | random_state         | 123       | Seed untuk reproducibility (hasil yang konsisten setiap kali dijalankan) 
      | n_jobs               | -1        | Menggunakan semua CPU cores untuk training paralel  
  * XGBoost Regresso : model regularisasi yang digunakan untuk mengurangi overfitting
    - XGBoost (Extreme Gradient Boosting) adalah algoritma gradient boosting yang menggunakan sequential ensemble. Setiap tree baru dilatih untuk memperbaiki error dari tree sebelumnya.
    - Parameter yang digunakan :
      | Parameter| Nilai   | Penjelasan |
      |----------|---------|-------------|
      | n_estimators        | 100     | Jumlah boosting rounds (trees)
      | learning_rate       | 0.05    | Step size untuk setiap boosting step (learning rate rendah untuk mencegah overfitting)
      | max_depth           | 3       | Kedalaman maksimum setiap tree (shallow trees mencegah overfitting)
      | subsample           | 0.8     | Proporsi sampel yang digunakan per tree (80% dari data) 
      | colsample_bytree    | 0.8     | Proporsi fitur yang digunakan per tree (80% dari fitur)
      | reg_alpha           | 0.1     | L1 regularization term
      | reg_lambda          | 1.0     | L2 regularization term
      | random_state        | 123     | Seed untuk reproducibility

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

### Contoh Skenario untuk melihat prediksi model 
![image](https://github.com/user-attachments/assets/1f78413a-b484-4969-aa6e-04befb7ca0f8)

**Output**
![image](https://github.com/user-attachments/assets/a912d302-709a-43ed-ae6e-6fa78d4dab39)

### Hasil Akhir sesuai permasalahan 
* Berdasarkan hasil akhir, faktor-faktor ekonomi sangat mempengaruhi  tingkat stunting
* Model regresi prediktif yang dibangun mampu memberikan prediksi terhadap tingkat prevalensi stunting di masa mendatang berdasarkan faktor-faktor ekonomi, Country, Income Classification, Year, U5 Population, dan prevalensi indikator malnutrisi lainnya
