Task 1 – Fraud Detection (Machine Learning End-to-End Pipeline)

Nama: Jaka Kelana Wijaya
NIM: 1103223048
Kelas: TK-46-02

🎯 Objective

Membangun end-to-end pipeline Machine Learning untuk memprediksi probabilitas sebuah transaksi online bersifat fraudulent. Pipeline meliputi:

Data loading

Preprocessing

Handling missing values

Handling class imbalance

Model training

Evaluation

Prediction untuk test set

Pembuatan submission file

📂 Dataset

train_transaction.csv → 590.540 baris, 392 fitur + target isFraud

test_transaction.csv → 506.691 baris, 392 fitur

Dataset memiliki class imbalance ekstrem, di mana transaksi fraud hanya ±3%.

🧪 1. Data Sampling (30.000 rows)

Karena ukuran dataset sangat besar dan Google Colab memiliki keterbatasan RAM (12 GB), training model pada seluruh dataset menyebabkan crash.

Untuk mengatasi hal tersebut digunakan:

Random sampling = 30.000 rows


Sampling ini tetap menjaga distribusi kelas.

🧹 2. Preprocessing
🔹 Missing Values Handling

Numerik → Median imputation

Kategorikal → Most Frequent + Ordinal Encoding

🔹 Fitur

378 fitur numerik

14 fitur kategorikal

Preprocessing dilakukan menggunakan ColumnTransformer.

⚖️ 3. Handling Class Imbalance

Model menggunakan:

class_weight = "balanced_subsample"


Agar model memberikan bobot lebih besar pada kelas fraud.

🤖 4. Model

Model utama: Random Forest Classifier

Parameter utama:

n_estimators = 150
class_weight = "balanced_subsample"
n_jobs = -1


Dipilih karena:

Stabil untuk high-dimensional tabular data

Tidak mudah crash

Mampu menangani imbalance

📊 5. Evaluation

Hasil pada validation set:

Metric	Value
ROC-AUC	0.898
Precision (1)	0.30
Recall (1)	0.45
F1-score (1)	0.35

Confusion Matrix menunjukkan model baik untuk mendeteksi kelas 0 (non-fraud), dan cukup baik untuk kelas fraud mengingat imbalance yang tinggi.

ROC-AUC 0.898 menandakan model memiliki kemampuan klasifikasi yang sangat baik.

📦 6. Batch Prediction untuk Test Set

Melakukan prediksi seluruh test set sekaligus menyebabkan crash.
Solusi: gunakan batch prediction (50.000 baris per batch).

Tujuan:

menghindari RAM overload

tetap menghasilkan submission lengkap 506.691 baris

📄 7. Submission File

File akhir:

submission_task1.csv


Berisi:

TransactionID

Predicted fraud probability

Jumlah baris: 506.691

Format sesuai instruksi tugas.

🚀 8. Cara Menjalankan Notebook

Upload dataset ke Google Drive

Buka notebook di Google Colab

Jalankan dari awal

Submission otomatis dihasilkan

📘 Kesimpulan

Pipeline ML berhasil dibangun secara end-to-end dengan preprocessing lengkap, model Random Forest, evaluasi metrik, dan pembuatan submission final.

Dengan teknik sampling + batch prediction, notebook berhasil berjalan tanpa crash meskipun dataset besar.
