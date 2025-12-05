1. Deskripsi Singkat

Proyek ini berisi implementasi end-to-end clustering pipeline menggunakan metode unsupervised learning untuk mengelompokkan pelanggan kartu kredit berdasarkan perilaku penggunaan, pembayaran, dan aktivitas cash advance.
Dataset yang digunakan: clusteringmidterm.csv.

2. Tujuan

Melakukan preprocessing data (missing value, scaling).

Menentukan jumlah cluster optimal menggunakan Elbow Method dan Silhouette Score.

Membangun model clustering menggunakan K-Means.

Melakukan interpretasi cluster untuk memahami karakteristik setiap kelompok pelanggan.

(Tambahan) Menerapkan Deep Learning melalui Autoencoder untuk memperbaiki representasi fitur sebelum clustering.

3. Dataset

Fitur utama pada dataset meliputi:

BALANCE, PURCHASES, ONEOFF_PURCHASES, INSTALLMENTS_PURCHASES

CASH_ADVANCE, PURCHASES_FREQUENCY, CASH_ADVANCE_FREQUENCY

CREDIT_LIMIT, PAYMENTS, MINIMUM_PAYMENTS

PRC_FULL_PAYMENT, TENURE

Variabel CUST_ID tidak digunakan sebagai fitur dalam model.

4. Alur Pengerjaan

Load data dan eksplorasi awal.

Imputasi missing values menggunakan median.

Scaling data menggunakan StandardScaler.

(Opsional) PCA 2D untuk visualisasi awal.

Penentuan jumlah cluster optimal:

Elbow menunjukkan tekukan di sekitar k = 3–4

Silhouette Score tertinggi pada k = 3

Clustering menggunakan K-Means dengan k = 3.

Analisis cluster melalui rata-rata fitur dan heatmap normalisasi.

(Tambahan) Penerapan Deep Learning melalui Autoencoder untuk representasi fitur non-linear sebelum K-Means.

5. Ringkasan Interpretasi Cluster
Cluster 0 – Active High Spenders

Nilai tinggi pada PURCHASES, ONEOFF, dan INSTALLMENTS

Cash advance sangat rendah

Credit limit tinggi, pembayaran cukup baik

Pengguna aktif dan stabil

Cluster 1 – Low Usage / Low Risk

Balance kecil dan jarang bertransaksi

Tidak menggunakan cash advance

Sering melakukan full payment

Penggunaan kartu rendah dan risiko kecil

Cluster 2 – High Balance & High Cash Advance

Balance tertinggi

Cash advance paling sering

Jarang melakukan full payment

Memiliki risiko lebih tinggi dibanding cluster lain

6. Tambahan: Deep Learning (Autoencoder + K-Means)

Sebagai pengembangan, digunakan model Autoencoder untuk mempelajari representasi laten (latent space) dari data sebelum dilakukan clustering.

Hasil perbandingan:

Silhouette Score K-Means (fit pada fitur asli): 0.25

Silhouette Score Autoencoder + K-Means: 0.49

Peningkatan skor menunjukkan bahwa Autoencoder mampu menghasilkan representasi fitur yang lebih baik, sehingga cluster menjadi lebih terpisah dan mudah diidentifikasi.
Visualisasi latent space juga memperlihatkan pemisahan cluster yang lebih jelas dibandingkan clustering langsung pada fitur asli.

7. Tools & Library

Python

Pandas, NumPy

Scikit-Learn

TensorFlow / Keras

Matplotlib, Seaborn

Google Colab
