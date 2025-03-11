# Machine Learning Project: Mental Health Prediction

## Nama
- **Alyssa Khairunisa Maharani**
## NIM
- **09011282227119**
## UAS Machine Learning

## Deskripsi
Proyek ini bertujuan untuk memprediksi apakah seseorang membutuhkan perawatan kesehatan mental berdasarkan berbagai faktor seperti usia, jenis kelamin, riwayat keluarga, opsi perawatan, dan faktor lainnya. Model yang digunakan adalah **Random Forest Classifier**, dengan optimasi menggunakan **Hyperparameter Tuning** untuk mengurangi overfitting.

## Dataset
Dataset yang digunakan mengandung informasi tentang individu dan faktor-faktor yang mungkin mempengaruhi keputusan mereka untuk mencari perawatan kesehatan mental.

Fitur yang digunakan:
- **Age** (Usia)
- **Gender** (Jenis Kelamin)
- **Family History** (Riwayat Kesehatan Mental Keluarga)
- **Benefits** (Manfaat dari perusahaan)
- **Care Options** (Pilihan perawatan tersedia)
- **Anonymity** (Anonimitas dalam perusahaan)
- **Leave** (Kebijakan cuti terkait kesehatan mental)
- **Work Interfere** (Gangguan pekerjaan akibat kesehatan mental)
- **Obs Consequence** (Konsekuensi pengungkapan masalah mental)
- **Mental Health Interview** (Wawancara terkait kesehatan mental)
- **Wellness Program** (Program kesejahteraan di tempat kerja)
- **Seek Help** (Kemudahan mendapatkan bantuan)

## Instalasi dan Persiapan
1. Clone repositori ini:
   ```bash
   git clone https://github.com/username/repository.git
   ```
2. Masuk ke direktori proyek:
   ```bash
   cd repository
   ```
3. Install dependensi yang dibutuhkan:
   ```bash
   pip install -r requirements.txt
   ```

## Model dan Evaluasi
- **Preprocessing:** Data telah dinormalisasi menggunakan **StandardScaler**.
- **Model:** Random Forest Classifier digunakan sebagai model utama.
- **Evaluasi:**
  - Confusion Matrix
  - Akurasi Data Latih dan Uji
  - Cross-Validation
  - Learning Curve

## Hyperparameter Tuning
Untuk mengatasi overfitting dan meningkatkan akurasi data uji, dilakukan **Hyperparameter Tuning** menggunakan **GridSearchCV**:
```python
from sklearn.model_selection import GridSearchCV
from sklearn.ensemble import RandomForestClassifier

param_grid = {
    'n_estimators': [50, 100, 200],
    'max_depth': [10, 20, 30],
    'min_samples_split': [2, 5, 10],
    'min_samples_leaf': [1, 2, 4]
}

rf = RandomForestClassifier()
grid_search = GridSearchCV(rf, param_grid, cv=5, scoring='accuracy', n_jobs=-1)
grid_search.fit(X_train, y_train)
print("Best Parameters:", grid_search.best_params_)
```

## Hasil dan Analisis
- Akurasi rata-rata cross-validation: **82.89%**
- Akurasi pada data latih: **99.62%** (Overfitting terdeteksi)
- Akurasi pada data uji: **68.65%** (Masih bisa ditingkatkan dengan tuning lebih lanjut)
- Dengan tuning, akurasi dapat lebih seimbang antara train dan test.

## Cara Menjalankan Model
1. Jalankan skrip utama untuk training dan evaluasi:
   ```bash
   python main.py
   ```
2. Untuk melakukan tuning hyperparameter, jalankan:
   ```bash
   python tuning.py
   ```

