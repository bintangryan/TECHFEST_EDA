# 📊 DATA ANALYTICS TECHFEST 2025: Efektivitas Penyaluran Dana Transfer ke Daerah (TKDD)

## Studi Perbandingan Pagu dan Realisasi TKDD di Provinsi-Provinsi Indonesia Tahun 2023

---

## 👥 Tim Kami

* Bintang Ryan Wardana
* Nicholas Marco W.
* Stephanie Hebrina M. S.

## ❓ Rumusan Masalah

Dalam studi kasus ini, beberapa pertanyaan utama yang dijawab melalui analisis data adalah:

1.  **Bagaimana tingkat perbandingan antara pagu dan realisasi TKDD di setiap provinsi di Indonesia pada tahun 2023?**
2.  **Provinsi mana yang memiliki tingkat realisasi tertinggi dan terendah?**
3.  **Apa saja kemungkinan faktor-faktor yang memengaruhi tinggi-rendahnya realisasi TKDD?**
4.  **Apakah terdapat hubungan antara realisasi TKDD dan IPM suatu provinsi?**
5.  **Apa saja faktor-faktor yang memengaruhi IPM di tiap provinsi Indonesia pada tahun 2023?**

## 🎯 Tujuan Analisis

Berikut merupakan tujuan dari analisis data yang dilakukan:

* Melakukan analisis perbandingan antara pagu TKDD dan realisasi TKDD.
* Menghitung persentase realisasi dan mengklasifikasikannya ke dalam kategori tertentu.
* Mengidentifikasi provinsi dengan tingkat realisasi TKDD tertinggi dan terendah.
* Menggali faktor-faktor yang memengaruhi tinggi-rendahnya realisasi TKDD.
* Menganalisis hubungan antara realisasi TKDD dan IPM.
* Menggali faktor-faktor yang memengaruhi IPM setiap provinsi.
* Memberikan *insight* dan rekomendasi kebijakan untuk meningkatkan efektivitas alokasi dan pelaksanaan anggaran.

---

## 🧹 1. Data Preparation

Pada tahap ini, data disiapkan agar siap digunakan untuk proses analisis. Beberapa langkah yang dilakukan meliputi:

* **1.1 Memuat Dataset dan Library**: Mengimpor *library* utama (`pandas`, `matplotlib.pyplot`, `seaborn`, `numpy`, `statsmodels`, `scipy.stats`) dan membaca dataset dari file Excel.
* **1.2 Memahami Struktur Data & Statistik Deskriptif**: Inspeksi awal untuk memahami struktur dan isi data, termasuk jumlah baris, tipe data kolom, dan ringkasan statistik deskriptif.
* **1.3 Pengecekan Missing Values dan Duplikasi Data**: Memeriksa keberadaan nilai yang hilang dan data duplikasi. Ditemukan 15 data hilang tersebar pada 5 baris data (provinsi di Papua dan Sulawesi Utara), dan tidak ada duplikasi.
* **1.4 Visualisasi Distribusi Data (Skewness)**: Memvisualisasikan distribusi seluruh kolom numerik untuk mengidentifikasi *skewness* dan *outlier*.
* **1.5 Penanganan Missing Values**: Menggunakan nilai median dari provinsi dalam wilayah geografis yang sama atau berdekatan untuk imputasi, karena distribusi data tidak normal dan jumlah data terbatas. Keputusan untuk tidak menghapus *outlier* atau mentransformasi data didasarkan pada konteks data aktual dari seluruh provinsi di Indonesia.

---

## 2. Exploratory Data Analysis (EDA) Insights

Analisis data dilakukan untuk menjawab rumusan masalah.

### 2.1 Perbandingan Pagu dan Realisasi TKDD di Setiap Provinsi

* **Sebaran Realisasi TKDD Didominasi oleh Provinsi yang Melebihi Target**: Sebanyak **20 provinsi (sekitar 53%)** memiliki realisasi anggaran **melampaui pagu yang ditetapkan**, sementara **18 provinsi (sekitar 47%)** berada pada kategori **Tinggi (90–100%)**. Tidak ada provinsi dengan realisasi di bawah 90%, menunjukkan pengelolaan dan penyerapan dana TKDD pada tahun 2023 secara umum cukup baik.
* **Scatter Plot Pagu vs Realisasi Menunjukkan Hubungan yang Sejalan**: Plot antara `Pagu TKDD` dan `Realisasi TKDD` membentuk garis miring mendekati y = x. Ini berarti semakin besar pagu yang diberikan, cenderung semakin besar pula realisasi anggarannya. Titik data sebagian besar berada di sekitar atau di atas garis y=x, menandakan target realisasi umumnya tercapai atau terlampaui. Ini menguatkan *insight* bahwa alokasi dan serapan anggaran berjalan linier dan efisien secara nasional.

### 2.2 Provinsi dengan Realisasi TKDD Terendah dan Tertinggi

Data diurutkan berdasarkan nilai nominal (`Realisasi TKDD`) dan persentase realisasi (`Persentase Realisasi TKDD`) untuk mengidentifikasi provinsi dengan serapan anggaran terbesar/terkecil dan efektivitas penyerapan anggaran.

---

## Cara Menjalankan Notebook

1.  **Clone repositori ini:**
    ```bash
    git clone <URL_repositori_Anda>
    cd <nama_folder_repositori>
    ```

2.  **Instal dependensi:**
    Pastikan Anda memiliki Anaconda atau Miniconda terinstal. Buat *environment* baru dan instal *library* yang diperlukan:
    ```bash
    conda create -n techfest_env python=3.9
    conda activate techfest_env
    pip install pandas matplotlib seaborn numpy statsmodels scipy openpyxl
    ```

3.  **Tempatkan Dataset:**
    Pastikan file `dataset.xlsx` berada di lokasi yang sama dengan *notebook* atau sesuaikan *path* di kode Python Anda.

4.  **Jalankan Jupyter Notebook:**
    ```bash
    jupyter notebook EDA_kasih aba2 klo udh final_ITS.ipynb
    ```
    *Notebook* akan terbuka di *browser* Anda. Anda dapat menjalankan setiap sel secara berurutan.

---
