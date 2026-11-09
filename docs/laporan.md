# Health-Risk-Segmentation-and-Classification-Project

# Laporan Proyek Machine Learning - Samuel Sahat Mardyantoro

## Domain Proyek

Kesehatan kardiometabolik merupakan salah satu isu global yang berkontribusi besar terhadap angka kesakitan dan kematian, seperti penyakit jantung, stroke, dan diabetes. Faktor risiko utama meliputi **tingkat obesitas, tekanan darah, kadar kolesterol, trigliserida, kebiasaan merokok, dan tingkat aktivitas fisik**.

Tantangan yang dihadapi adalah bagaimana mengelompokkan individu berdasarkan profil kesehatan mereka sehingga bisa dilakukan tindakan pencegahan lebih dini. Menurut data WHO (2021), lebih dari **17,9 juta orang meninggal setiap tahun akibat penyakit kardiovaskular**, dan sebagian besar kasus dapat dicegah dengan mengurangi faktor risiko.

Dengan penerapan machine learning, kita dapat membangun sistem segmentasi risiko kesehatan yang membantu tenaga kesehatan atau organisasi dalam:

* Mengidentifikasi individu dengan risiko kesehatan tinggi
* Memberikan rekomendasi gaya hidup yang sesuai
* Membantu pengambilan keputusan dalam intervensi kesehatan preventif

## Business Understanding

### Problem Statements

1. Bagaimana cara mengelompokkan individu berdasarkan faktor risiko kesehatan yang mereka miliki?
2. Dapatkah hasil clustering digunakan untuk membangun model klasifikasi yang dapat memprediksi risiko kesehatan seseorang berdasarkan profil datanya?
3. Faktor apa saja yang paling berpengaruh terhadap pembentukan cluster kesehatan?

### Goals

1. Melakukan clustering untuk menemukan pola kelompok risiko kesehatan (rendah, sedang, tinggi).
2. Membangun model klasifikasi yang mampu memprediksi cluster kesehatan individu.
3. Memberikan insight yang dapat dijadikan dasar rekomendasi kesehatan preventif.

### Solution Statements

* Menggunakan metode clustering (K-Means) untuk segmentasi kesehatan.
* Menggunakan **Random Forest** dan **Logistic Regression** untuk membandingkan performa klasifikasi hasil cluster.
* Mengevaluasi performa model dengan metrik seperti akurasi, precision, recall, dan f1-score.

## Data Understanding

Dataset ini berisi fitur biometrik dan gaya hidup individu.

* **Jumlah data**: 25.000 rows x 11 features

* **Fitur utama**:

  * **Age** → usia responden
  * **BMI** → indeks massa tubuh
  * **Systolic\_BP, Diastolic\_BP** → tekanan darah
  * **Total\_Cholesterol, HDL, LDL, Triglycerides** → profil lipid darah
  * **Smoking\_Status** → status merokok
  * **Physical\_Activity\_Level** → tingkat aktivitas fisik

* **Kondisi Data**:

  * Tidak ada duplikat
  * Missing value sangat sedikit, dapat diimputasi
  * Distribusi cukup bervariasi antar fitur

Dataset ini digunakan untuk melakukan **clustering kesehatan** dan selanjutnya dipakai sebagai label untuk proses klasifikasi.

## Data Preparation

* Mengubah tipe data menjadi sesuai (contoh: integer/float untuk biometrik).
* Normalisasi fitur numerik agar tidak ada dominasi skala.
* Encoding fitur kategorikal (misal status merokok).
* Splitting data → X (fitur), y (hasil cluster).
* Train-test split dengan rasio 80:20.

## Modeling

Modeling dilakukan dalam dua tahap:

1. **Clustering (K-Means)**

   * Jumlah cluster optimal = 4 (berdasarkan silhouette score).
   * Cluster menunjukkan pola risiko kesehatan:

     * **Cluster 0**: Usia lanjut, BMI tinggi, kolesterol & trigliserida tinggi → risiko tinggi.
     * **Cluster 1**: Usia lebih muda, BMI normal, profil lipid normal → risiko rendah.
     * **Cluster 2 & 3**: Risiko menengah dengan variasi pada BMI dan lipid.

2. **Klasifikasi Cluster**

   * Model yang digunakan: Random Forest & Logistic Regression.
   * Tuning dilakukan dengan Random Search.

### Parameter Terbaik

* **Random Forest**

  * n\_estimators = 1000
  * max\_depth = 30
  * min\_samples\_split = 6
  * min\_samples\_leaf = 2
  * max\_features = "sqrt"

* **Logistic Regression**

  * C = 10000.0
  * penalty = "l1"
  * solver = "liblinear"
  * max\_iter = 500

## Evaluation

### Random Forest

* Accuracy: **96.1%**
* Precision: 0.961
* Recall: 0.961
* F1-score: 0.961

### Logistic Regression

* Accuracy: **98.02%**
* Precision: 0.980
* Recall: 0.980
* F1-score: 0.980

### Perbandingan

* Random Forest mampu menangani non-linearitas, tetapi akurasi sedikit lebih rendah.
* Logistic Regression (linear model) ternyata memberikan hasil lebih tinggi, yang menunjukkan bahwa pemisahan cluster dapat dijelaskan dengan hubungan linier.
* Kedua model stabil dan menunjukkan keseimbangan antar kelas.

## Kesimpulan

Proyek ini berhasil membangun sistem segmentasi risiko kesehatan dengan K-Means, menghasilkan **4 kelompok risiko kesehatan** yang berbeda. Model klasifikasi selanjutnya mampu memprediksi cluster dengan sangat baik, di mana Logistic Regression mencapai akurasi **98%**. Hal ini menunjukkan bahwa pola risiko kesehatan dapat dipetakan dengan jelas dari fitur biometrik dan gaya hidup.

Dengan hasil ini, sistem machine learning dapat membantu tenaga kesehatan dalam **identifikasi dini individu berisiko tinggi** dan mendukung kebijakan intervensi preventif, misalnya program berhenti merokok, penurunan berat badan, atau edukasi pola makan.

---
