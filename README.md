# Rossman Store Sales Forecasting

## 📝 Deskripsi Proyek
Proyek ini bertujuan untuk memprediksi penjualan harian toko Rossmann dengan memanfaatkan data historis penjualan, informasi promosi, data kompetitor, serta variabel pendukung lainnya.  
Proses dilakukan mulai dari pra-pemrosesan data, eksplorasi, pembuatan fitur, pelatihan model regresi, evaluasi performa, hingga menghasilkan dataset prediksi final serta model yang siap digunakan kembali.

---

## 🗂️ Struktur Repository

- **UAS_ABD_Kelompok_6_rossman_store_forecasting/**
  - **Insight with kibana/**
    - Berisi dashboard dan visualisasi hasil analisis data serta prediksi menggunakan Kibana
  - **. gitattributes**
    Merupakan file bawaan github untuk menyimpan dataset skala besar yang teridiri dari:
      - **📦 data_ori.zip**
        Merupakan folder referensi yang berisi dataset asli / dataset pendukung
    
      - **📦 data_final.zip**
         merupakan berkas arsip yang berisi kumpulan dataset akhir proyek. File ini digunakan untuk mengatasi batasan ukuran file pada GitHub sehingga seluruh dataset dapat tetap dibagikan dalam satu pake yang terdiri dari:
          - **data_prediksi_rf.csv**  
            Berisi hasil prediksi akhir penjualan yang dihasilkan oleh model Random Forest.
    
          - **data_test_final.csv**  
            Dataset uji yang telah melalui proses preprocessing dan feature engineering.
    
          - **data_train_final.csv**  
            Dataset latih final yang digunakan dalam proses pelatihan model.

  - **forecast_rossman_rf.pkl**
    - File model Random Forest yang sudah dilatih dan dapat digunakan kembali tanpa training ulang
  - **Pelatihan Model dan Prediksi.ipynb**
    - Notebook untuk proses pelatihan model, validasi, prediksi, dan visualisasi hasil
  - **Pra-pemrosesan Data.ipynb**
    - Notebook untuk EDA, preprocessing, pembuatan fitur, dan penyimpanan dataset
  - **README.md**
    - Dokumentasi proyek


## 📌 STRUKTUR NOTEBOOK

---
**Pelatihan Model dan Prediksi.ipynb**

**→ Membaca Dataset**  
Memuat dataset mentah ke dalam notebook untuk diproses.

**→ Visualisasi sample awalan dataset**  
Menampilkan beberapa baris awal dataset untuk memahami struktur data.

**→ EDA**  
Melakukan eksplorasi awal untuk melihat pola data, distribusi, serta potensi masalah seperti nilai kosong atau anomali.

**→ Preprocessing**  
Bagian utama yang berisi tahapan penyiapan data:
- **Integrasi karakteristik detail setiap dari dataset metadata**  
  Menggabungkan informasi tambahan dari metadata seperti karakteristik toko maupun informasi pendukung lainnya.
- **Pemerolehan Fitur Promo Seasonal Aktif**  
  Menentukan fitur yang menunjukkan periode promo musiman pada setiap toko.
- **Pemerolehan Fitur Kompetitor Aktif**  
  Menentukan fitur yang menunjukkan keberadaan kompetitor aktif pada waktu tertentu.
- **Hasil Akhir Fitur-Fitur yang Digunakan**  
  Menyusun fitur akhir yang siap digunakan pada proses pemodelan.
- **Pengisian Nilai yang Hilang pada Dataset Uji dengan Nilai Modus**  
  Menangani missing value pada dataset uji dengan mengganti menggunakan nilai modus atas dasar data kategori.
- **Penyimpanan data ke Elasticsearch**  
  Menyimpan hasil preprocessing ke Elasticsearch untuk kebutuhan analisis dan integrasi sistem.

**→ Penyimpanan data ke Elasticsearch**  
Dataset yang telah diproses disimpan ke database Elasticsearch.

**→ Penyimpanan Dataset Final ke Penyimpanan Lokal**  
Menyimpan dataset final ke penyimpanan lokal agar dapat digunakan pada tahap berikutnya.

---

**Pra-pemrosesan Data.ipynb**

**→ Membaca Dataset**  
Memuat dataset hasil preprocessing yang telah siap digunakan.

**→ Enkripsi fitur kategorik Data Latih dan Validasi**  
Mengubah fitur kategorik menjadi numerik agar dapat diproses oleh model machine learning.

**→ Pembagian Data Latih dan Validasi**  
Membagi dataset menjadi:
- Data latih (training dataset)
- Data validasi (validation dataset)  
untuk memastikan evaluasi model dilakukan secara objektif.

**→ Pelatihan Model Regresi**  
Melatih model regresi menggunakan data latih dan validasi sebagai proses evaluasi, untuk mempelajari pola hubungan antar fitur.

**→ Proses Prediksi**  
Menggunakan model yang telah dilatih untuk menghasilkan nilai prediksi pada dataset Uji maupun dataset baru.

**→ Enkripsi fitur kategorik Data Uji**  
Melakukan encoding pada dataset uji agar konsisten dengan dataset pelatihan.

**→ Visualisasi**  
Menampilkan hasil prediksi dalam bentuk grafik sehingga performa model dan pola hasil prediksi dapat dianalisis dengan lebih mudah.

---
## Visualisasi

### 🔹 Hasil Evaluasi Model
![Forecast 1](Insight%20with%20kibana/Hasil%20Evaluasi%20Model.png)

### 🔹 Hasil Forecasting 2 Bulan Aktual dan 1 Bulan Prediksi
![Forecast 1](Insight%20with%20kibana/Hasil%20Forecasting%202%20Bulan%20Aktual%20dan%201%20Bulan%20Prediksi.png)

### 🔹 Hasil Forecasting Perbandingan 1 Bulan terakhir Juli 2015 (Aktual) VS 1 Bulan pertama Agusutus 2015 (Prediksi)
![Forecast Perbandingan](Insight%20with%20kibana/Hasil%20Forecasting%20Perbandingan%201%20Bulan%20terakhir%20Juli%202015%20%28Aktual%29%20VS%201%20Bulan%20pertama%20Agusutus%202015%20%28Prediksi%29.png)

### 🔹 Histori Penjualan Setiap Bulan (Aktual)
![Histori Penjualan](Insight%20with%20kibana/Histori%20Penjualan%20Setiap%20Bulan.png)

### 🔹 Histori Penjualan VS Jumlah Pelanggan Setiap Bulan 
![Total Penjualan vs Total Pelanggan](Insight%20with%20kibana/Total%20Penjualan%20Vs%20Total%20Pelanggan%20Setiap%20Bulan.png)

### 🔹 Jumlah Transaksi VS Jumlah Kompetitor Aktif VS Jumlah Transaksi Menggunakan Promo
![Total Transaksi VS Kompetitor Aktif VS Promo Aktif](Insight%20with%20kibana/Total%20Transaksi%20VS%20Kompetitor%20Aktif%20VS%20Promo%20Aktif.png)

### 🔹 Jenis jenis toko pada dataset terhadap penjualan
![Jenis Toko Terhadap Total Penjualan](Insight%20with%20kibana/Jenis%20Toko%20Terhadap%20Total%20Penjualan.png)

### 🔹 Top 5 Toko Unggulan pada dataset terhadap penjualan
![Top 5 Toko Menurut Jenisnya](Insight%20with%20kibana/Top%205%20Toko%20Menurut%20Jenisnya.png)

### 🔹 Strategi Top 5 Toko Unggulan 
![Strategi Top 5 Toko Unggulan](Insight%20with%20kibana/Strategi%20Top%205%20Toko%20Unggulan.png)

---

## Integrasi Elasticsearch dan Kibana

### 🔹 Data View
![Data View Kibana](Insight%20with%20kibana/Data%20View%20Kibana.png)

### 🔹 Dashboard
![Dashboard Kibana](Insight%20with%20kibana/Dashboard%20Kibana.png)






