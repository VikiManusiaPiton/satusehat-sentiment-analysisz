# Perbandingan konfigurasi n-gram pada TF-IDF dan Logistic Regression untuk klasifikasi sentimen ulasan SATUSEHAT (2020-2021)

Kode dan data pendukung artikel Jurnal TIMES.

## Isi repositori
- `sentiment_revisi.ipynb` - notebook eksperimen (Pipeline TF-IDF + Logistic Regression, GridSearchCV 5-fold, McNemar, Wilson, analisis fitur, audit kesalahan).
- `SATUSEHAT_clean_balanced.csv` - 3.994 ulasan hasil pembersihan (1.997 positif, 1.997 negatif).
- `SATUSEHAT_preprocessed_split.csv` - sampel yang dipakai beserta penanda `train`/`test` (3.195 latih, 799 uji).
- `hasil_sensitivitas_min_df.csv` - hasil analisis sensitivitas `min_df`.
- `audit_kesalahan_terisi.csv` - klasifikasi 128 kesalahan prediksi model unigram+bigram.
- `cek_20_baris.csv` - verifikasi penulis pada 20 baris audit yang dipilih acak (17 dari 20 sesuai).

## Catatan replikasi
- Data sumber: Indonesian Government App Review Dataset (IGAR) versi 3, lisensi CC BY 4.0.
- Sampel 2.000 positif + 2.000 negatif diambil di Altair AI Studio **tanpa mencatat seed**. Berkas `SATUSEHAT_preprocessed_split.csv` adalah sampel persis yang dipakai; jangan mengambil sampel ulang bila ingin mereproduksi angka artikel.
- Seed 42 dipakai untuk pembagian data (stratified 80:20) dan model.
- Versi: Python 3.13.0, scikit-learn 1.7.2, pandas 2.3.3, NumPy 2.3.4, SciPy 1.16.3.

## Catatan audit
Klasifikasi awal 128 kesalahan dibantu model bahasa dan diverifikasi sebagian oleh penulis (20 sampel acak). Proporsi kategori bersifat indikatif.
