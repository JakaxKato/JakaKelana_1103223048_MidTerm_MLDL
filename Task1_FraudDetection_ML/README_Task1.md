Task 1 – Fraud Detection (Machine Learning & Deep Learning Pipeline)

Nama: Jaka Kelana Wijaya
NIM: 1103223048
Kelas: TK-46-02

Objective

Membangun pipeline end-to-end untuk memprediksi probabilitas terjadinya transaksi fraud. Proses mencakup loading data, preprocessing, penanganan missing values, encoding fitur kategorikal, training model Machine Learning dan Deep Learning, evaluasi, serta pembuatan file submission sesuai format tugas.

Dataset

train_transaction.csv: 590.540 baris, 392 fitur + target isFraud

test_transaction.csv: 506.691 baris, 392 fitur

Distribusi kelas sangat tidak seimbang dengan proporsi fraud sekitar 3%.

Karena keterbatasan RAM di Google Colab, digunakan sampling sebesar 30.000 baris dari data training. Sampling tetap menjaga distribusi kelas.

Preprocessing

Preprocessing dilakukan menggunakan ColumnTransformer dengan komponen berikut:

Fitur numerik: imputasi median

Fitur kategorikal: imputasi nilai paling sering dan OrdinalEncoder

Terdapat 378 fitur numerik dan 14 fitur kategorikal

Setelah transformasi, seluruh fitur menjadi bentuk numerik sehingga dapat digunakan baik untuk model Random Forest maupun model Deep Learning.

Handling Class Imbalance

Model Machine Learning menggunakan:

class_weight = "balanced_subsample"

Tujuannya agar model memberikan bobot lebih besar pada kelas fraud yang jumlahnya jauh lebih sedikit.

Modeling
1. Random Forest Classifier (Machine Learning)

Model ini dipilih karena stabil terhadap data tabular berdimensi besar dan cukup efektif menangani ketidakseimbangan kelas.

Parameter utama:

n_estimators = 150

class_weight = balanced_subsample

n_jobs = -1

Model dievaluasi pada validation set menggunakan AUC dan classification report.

2. Multilayer Perceptron (Deep Learning)

Model Deep Learning digunakan sebagai pembanding. Setelah preprocessing dan standard scaling, data digunakan untuk melatih arsitektur MLP dengan beberapa hidden layer.

Komponen utama:

Hidden layers dengan aktivasi ReLU

Dropout untuk mengurangi overfitting

Output beraktivasi sigmoid

Optimizer Adam

Callbacks EarlyStopping dan ReduceLROnPlateau

Model ini memberikan pendekatan alternatif berbasis Deep Learning sesuai cakupan kelas.

Evaluation
Random Forest

ROC–AUC: sekitar 0.898

Precision dan recall untuk kelas fraud cukup baik mengingat dataset sangat tidak seimbang.

Model lebih kuat mendeteksi kelas non-fraud, namun tetap mampu mengenali sebagian transaksi fraud.

Deep Learning

Model memberikan performa kompetitif dengan stabilitas yang baik pada validation set setelah proses scaling dan early stopping.
Perbandingan dilakukan menggunakan AUC dan akurasi sehingga terlihat perbedaan kemampuan model ML dan DL.

Batch Prediction untuk Test Set

Prediksi langsung dalam satu kali proses menyebabkan Colab kehabisan memori. Untuk mengatasi hal tersebut digunakan batch prediction (misalnya 50.000 baris tiap batch).
Pendekatan ini memungkinkan seluruh 506.691 baris test set diprediksi tanpa crash.

Submission File

Hasil akhir disimpan dalam file:

submission_task1.csv

Berisi dua kolom:

TransactionID

isFraud (probabilitas)

Jumlah baris sesuai dataset test: 506.691.

Cara Menjalankan Notebook

Unggah dataset ke Google Drive

Buka notebook di Google Colab

Jalankan seluruh sel dari awal

File submission akan dihasilkan secara otomatis

Kesimpulan

Pipeline end-to-end berhasil dibangun mencakup preprocessing, modeling menggunakan Machine Learning dan Deep Learning, evaluasi metrik, dan pembuatan submission. Dengan kombinasi teknik sampling serta batch prediction, proses dapat berjalan stabil tanpa kehabisan memori. Analisis AUC menunjukkan bahwa Random Forest dan MLP memiliki performa yang kompetitif, dengan Random Forest sedikit lebih kuat pada data tabular yang digunakan.
