1. Project Overview

Tugas ini bertujuan untuk membangun pipeline end-to-end regression menggunakan Machine Learning dan Deep Learning untuk memprediksi nilai kontinu, yaitu tahun rilis lagu berdasarkan fitur-fitur numerik audio.

Pipeline meliputi:

Data loading

Data cleaning dan preprocessing

Handling missing values

Feature preparation (scaling & imputation)

Model training (ML & DL)

Basic hyperparameter tuning

Evaluasi menggunakan metrik regresi

Perbandingan performa model

Dataset yang digunakan adalah midterm-regresi-dataset.csv, di mana:

Kolom pertama → target (tahun rilis lagu)

89 kolom berikutnya → fitur numerik hasil ekstraksi sinyal audio

2. Dataset Description

Dataset memiliki:

515.344 baris

90 kolom

Seluruh fitur merupakan nilai numerik

Tidak memiliki header asli sehingga kolom dinamai ulang sebagai:

target, feature_1, feature_2, ..., feature_89


Target berupa tahun rilis lagu, sehingga merupakan continuous value yang cocok untuk regresi.

3. Preprocessing Workflow

Langkah-langkah preprocessing:

1) Split fitur dan target
target  = year released
features = feature_1 ... feature_89

2) Train-test split

Data dibagi 80% train dan 20% test.

3) Handling missing values

Fitur numerik → median imputation

4) Feature scaling

Digunakan StandardScaler

Scaling diperlukan terutama untuk model DL

5) Outlier handling

Dataset mengandung nilai ekstrem pada fitur tertentu.
Outlier tidak dihapus karena:

Random Forest relatif robust

Scaling membantu stabilisasi model DL

Menghapus outlier menyebabkan hilangnya variasi penting pada data

4. Models Implemented

Project ini menggunakan kombinasi Machine Learning dan Deep Learning:

A. Linear Regression (Baseline)

Digunakan sebagai pembanding dasar untuk performa regresi linear.

B. Random Forest Regressor

Model utama yang dapat menangani relasi non-linear pada data tabular.

C. Random Forest (Tuned)

Hyperparameter tuning menggunakan RandomizedSearchCV dengan:

n_estimators: [50, 100]

max_depth: [10, None]

cv: 2

sample: 30.000 baris (untuk menghindari crash RAM Colab)

D. Deep Learning (MLP)

Arsitektur MLP dengan:

Dense layers

ReLU activation

Dropout

Optimizer: Adam

Loss: MSE

Early Stopping & ReduceLROnPlateau

Digunakan untuk perbandingan performa ML vs DL.

5. Evaluation Metrics

Model dievaluasi menggunakan metrik regresi:

MSE (Mean Squared Error)

RMSE (Root Mean Squared Error)

MAE (Mean Absolute Error)

R² Score

Semua metrik dihitung pada test set.

6. Results
Model	RMSE	MAE	R²
Linear Regression	9.52	6.78	0.238
Random Forest	9.09	6.46	0.304
Random Forest (tuned)	9.47	6.81	0.245
Deep Learning (MLP)	16.15	13.76	-1.19
Interpretasi Singkat:

Random Forest baseline memberikan performa terbaik.

Random Forest tuned tidak melampaui baseline karena tuning dilakukan pada data sample kecil.

MLP menunjukkan performa rendah (R² negatif), karena model deep learning kurang cocok untuk dataset tabular numerik tanpa arsitektur yang sangat dituning.

Data regresi tabular seperti ini umumnya lebih cocok untuk model tree-based.

7. Key Findings

Data tabular dengan ratusan ribu baris cenderung lebih efektif menggunakan model ensemble seperti Random Forest.

Deep Learning membutuhkan arsitektur lebih kompleks atau fitur yang lebih informatif untuk bekerja dengan baik.

Hyperparameter tuning sederhana sudah meningkatkan pemahaman pipeline meskipun tidak memberikan performa terbaik.

End-to-end pipeline sudah berjalan mulai dari preprocessing hingga evaluasi, sesuai instruksi tugas.
