# Perbandingan konfigurasi n-gram pada TF-IDF dan Logistic Regression untuk klasifikasi sentimen ulasan PeduliLindungi–SATUSEHAT

Kode dan data pendukung artikel.

## Catatan tentang objek penelitian

Data berasal dari subset "SATUSEHAT" pada Indonesian Government App Review Dataset (IGAR) versi 3, yaitu ulasan Google Play Store periode 31 Maret 2020 sampai 14 Oktober 2021. Pada periode itu aplikasinya masih bernama PeduliLindungi. SATUSEHAT Mobile baru menggantikannya pada Maret 2023 melalui listing toko aplikasi yang sama, dan IGAR mengelompokkan ulasan tersebut sebagai SATUSEHAT. Temuan karena itu mewakili ulasan era PeduliLindungi, bukan SATUSEHAT Mobile masa kini.

## Isi repositori

| Berkas | Keterangan |
|---|---|
| `sentiment_revisi_v3.ipynb` | Notebook eksperimen: Pipeline TF-IDF + Logistic Regression, GridSearchCV 5-fold, uji McNemar eksak, interval Wilson dan Wald, analisis sensitivitas `min_df`, analisis fitur, audit kesalahan, dan verifikasi 50 ulasan. |
| `SATUSEHAT_clean_balanced.csv` | 4.000 ulasan hasil pembersihan dan sampling (2.000 positif, 2.000 negatif). Pemisah kolom `;`. |
| `SATUSEHAT_preprocessed_split.csv` | Sampel yang dipakai beserta kolom `split` (3.200 latih, 800 uji; masing-masing seimbang). Pemisah kolom `;`. |
| `hasil_sensitivitas_min_df.csv` | Hasil analisis sensitivitas `min_df`. |
| `audit_kesalahan.csv` | 131 kesalahan prediksi model unigram+bigram pada data uji (keluaran notebook sebelum diklasifikasi). |
| `audit_kesalahan_terisi.csv` | Klasifikasi 131 kesalahan tersebut (sentimen menurut isi teks dan kategori penyebab). |
| `verifikasi_50_baris_terisi.csv` | Penilaian ulang penulis atas 50 ulasan yang dipilih acak dari audit (seed 42). |
| `fig2_confusion_matrix.png`, `fig3_roc.png` | Gambar 2 (confusion matrix) dan Gambar 3 (kurva ROC) pada artikel. |

## Catatan replikasi

- **Data sumber:** IGAR versi 3, lisensi CC BY 4.0, tersedia di https://doi.org/10.17632/7zryc6k76z.3. Berkas data mentah (`Rating_labeled.csv`) tidak disertakan di repositori ini karena ukurannya besar; unduh dari tautan itu bila ingin membangun ulang sampel.
- **Sampel:** 2.000 ulasan positif dan 2.000 negatif. Notebook memiliki sakelar `RUN_SAMPLING`: `True` membangun ulang sampel dari data mentah (butuh `Rating_labeled.csv`), `False` memakai `SATUSEHAT_clean_balanced.csv` yang sudah ada di repositori. Untuk mereproduksi angka artikel tanpa mengunduh data mentah, gunakan `False`.
- **Seed:** 42 dipakai untuk seluruh proses acak (sampling, pembagian data stratified 80:20, dan model).
- **Versi:** Python 3.13.0, scikit-learn 1.7.2, pandas 2.3.3, NumPy 2.3.4, SciPy 1.16.3.

## Catatan audit

Klasifikasi awal 131 kesalahan dibantu model bahasa (Claude, Anthropic) dan diverifikasi penulis pada 50 ulasan yang dipilih acak: kesepakatan sentimen menurut isi teks 48 dari 50 (96%; Cohen's kappa = 0,93) dan kesepakatan kategori penyebab 45 dari 50 (90%; Cohen's kappa = 0,86). Penilaian dilakukan oleh satu penilai, sehingga proporsi kategori kesalahan bersifat indikatif.
