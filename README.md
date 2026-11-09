# Health Risk Segmentation and Classification

Segmentasi risiko kesehatan kardiometabolik dengan K-Means, dilanjutkan dengan model klasifikasi untuk memprediksi segmen individu baru.

## Ringkasan

Proyek ini terdiri dari dua tahap:

1. **Clustering**: K-Means mengelompokkan 25.000 individu ke dalam 4 segmen risiko. Fitur yang dipakai antara lain BMI, tekanan darah, kolesterol, trigliserida, kebiasaan merokok, dan aktivitas fisik.
2. **Klasifikasi**: label cluster digunakan untuk melatih Random Forest dan Logistic Regression.

## Hasil

| Model | Accuracy | Precision | Recall | F1 |
|---|---|---|---|---|
| Logistic Regression | 0.980 | 0.980 | 0.980 | 0.980 |
| Random Forest | 0.961 | 0.961 | 0.961 | 0.961 |

Label klasifikasi berasal dari hasil clustering, sehingga akurasi tinggi menunjukkan segmen yang terbentuk terpisah dengan jelas. Angka ini bukan akurasi diagnosis medis.

## Dataset

[Healthcare Dataset](https://www.kaggle.com/datasets/rajagrawal7089/healthcare) (Kaggle): 25.000 baris, 11 fitur.

## Struktur

```
.
├── 01_clustering.ipynb
├── 02_classification.ipynb
├── Dataset_Inisiasi.csv      # data awal
├── Dataset_Clustering.csv    # data dengan label cluster
└── docs/
    └── laporan.md
```

## Menjalankan

```bash
pip install pandas numpy scikit-learn matplotlib seaborn plotly jupyter
jupyter notebook
```

Jalankan `01_clustering.ipynb`, lalu `02_classification.ipynb`. Notebook ini dibuat di Google Colab, jadi path `/content/drive/...` perlu diganti dengan path lokal.

## Dokumentasi

Laporan lengkap ada di [docs/laporan.md](docs/laporan.md).
