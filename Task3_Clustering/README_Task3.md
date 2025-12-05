1. Deskripsi Singkat

Proyek ini berisi implementasi end-to-end clustering pipeline menggunakan metode unsupervised learning untuk mengelompokkan pelanggan kartu kredit berdasarkan perilaku penggunaan, pembayaran, dan aktivitas cash advance.
Dataset yang digunakan: clusteringmidterm.csv.

2. Tujuan

Melakukan preprocessing data (missing value, scaling).

Menentukan jumlah cluster optimal menggunakan Elbow Method dan Silhouette Score.

Membangun model clustering (K-Means).

Melakukan interpretasi cluster untuk memahami karakteristik setiap kelompok pelanggan.

3. Dataset

Beberapa fitur utama:

BALANCE, PURCHASES, ONEOFF_PURCHASES, INSTALLMENTS_PURCHASES

CASH_ADVANCE, PURCHASES_FREQUENCY, CASH_ADVANCE_FREQUENCY

CREDIT_LIMIT, PAYMENTS, MINIMUM_PAYMENTS

PRC_FULL_PAYMENT, TENURE

Variabel CUST_ID tidak digunakan sebagai fitur.

4. Alur Pengerjaan

Load data dan eksplorasi awal.

Imputasi missing values menggunakan median.

Scaling seluruh fitur menggunakan StandardScaler.

(Opsional) PCA 2D untuk visualisasi.

Menentukan jumlah cluster optimal.

Elbow menunjukkan tekukan di sekitar k = 3–4

Silhouette Score tertinggi pada k = 3

Model akhir menggunakan K-Means (k = 3).

Analisis profil tiap cluster menggunakan rata-rata fitur dan heatmap normalisasi.

5. Ringkasan Interpretasi Cluster
Cluster 0 – Active High Spenders

Nilai tinggi pada PURCHASES, ONEOFF, INSTALLMENTS.

Cash advance sangat rendah.

Credit limit tinggi, pembayaran cukup baik.

Pelanggan aktif dan stabil.

Cluster 1 – Low Usage / Low Risk

Balance kecil, pembelian rendah.

Tidak menggunakan cash advance.

Cenderung sering membayar penuh.

Aktivitas penggunaan kartu rendah.

Cluster 2 – High Balance & High Cash Advance

Balance tertinggi dan paling sering cash advance.

Jarang membayar full payment.

Risiko lebih tinggi dibanding cluster lain.

6. Tools & Library

Python

Pandas, NumPy

Scikit-Learn

Matplotlib, Seaborn

Google Colab
