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
    * **Temuan Skewness, Distribusi, dan Outlier**:
        * Hanya kolom **IPM** yang memiliki distribusi mendekati normal, dengan *skewness* sebesar -0.08. Kolom lainnya memiliki *skewness* > 1.2, menandakan distribusi tidak normal (*positively skewed*), yang umum terjadi dalam data ekonomi antar provinsi karena ketimpangan.
        * Setiap kolom numerik menunjukkan keberadaan *outlier*, yang terlihat jelas pada boxplot. Ini merefleksikan provinsi dengan nilai TKDD, realisasi, atau populasi yang sangat tinggi/rendah.
    * **Keputusan: Tidak Menghapus atau Mentransformasi Data**: Kami memutuskan untuk tidak menghapus *outlier* maupun melakukan transformasi distribusi karena dataset berisi data aktual dari seluruh provinsi Indonesia tahun 2023 (sehingga setiap baris sangat berarti dan tidak bisa dianggap sebagai *noise*), dan jumlah observasi sangat terbatas (38 baris data) yang dapat menurunkan validitas informasi. Nilai ekstrem kemungkinan besar merefleksikan kondisi nyata di lapangan, bukan kesalahan input data.
* **1.5 Penanganan Missing Values**: Ditemukan 15 nilai yang hilang tersebar pada 5 baris data (provinsi di Papua dan Sulawesi Utara). Imputasi dilakukan menggunakan nilai median dari provinsi-provinsi di wilayah geografis yang sama atau berdekatan, bukan seluruh data nasional, untuk meningkatkan ketepatan dan menghindari distorsi dari *outlier* nasional. Metode ini meningkatkan validitas analisis.

---

## 2. Exploratory Data Analysis (EDA) Insights

Bagian ini membahas eksplorasi data secara sistematis untuk menjawab lima rumusan masalah yang telah ditentukan dalam studi kasus. Analisis dilakukan dengan pendekatan visual dan statistik untuk memperoleh *insight* yang mendalam.

### 2.1 Perbandingan Pagu dan Realisasi TKDD di Setiap Provinsi

* **Sebaran Realisasi TKDD Didominasi oleh Provinsi yang Melebihi Target**:
    * Berdasarkan klasifikasi:
        * Sebanyak **20 provinsi (≈53%)** termasuk dalam kategori **Sangat Tinggi (>100%)**, menandakan bahwa realisasi anggaran mereka **melampaui pagu yang ditetapkan**.
        * Sisanya **18 provinsi (≈47%)** berada pada kategori **Tinggi (90–100%)**, yaitu realisasi hampir menyentuh 100%.
    * Tidak ada provinsi dengan realisasi di bawah 90%, yang menunjukkan bahwa **pengelolaan dan penyerapan dana TKDD di tahun 2023 secara umum cukup baik**.

* **Scatter Plot Pagu vs Realisasi Menunjukkan Hubungan yang Sejalan**:
    * Plot antara `Pagu TKDD` dan `Realisasi TKDD` membentuk **garis miring mendekati y = x**, yang berarti semakin besar pagu yang diberikan, maka cenderung semakin besar pula realisasi anggarannya.
    * Titik-titik data sebagian besar **berada di sekitar atau di atas garis merah putus-putus (y = x)**, yang menandakan bahwa **target realisasi umumnya tercapai bahkan terlampaui**.
    * Ini menguatkan *insight* bahwa **alokasi dan serapan anggaran berjalan linier dan efisien secara nasional**, meskipun perlu ditelusuri lebih dalam untuk provinsi dengan deviasi terbesar dari garis tersebut.

### 2.2 Provinsi dengan Realisasi TKDD Terendah dan Tertinggi

Data diurutkan berdasarkan nilai nominal realisasi (`Realisasi TKDD`) dan persentase realisasi (`Persentase Realisasi TKDD`) untuk mengidentifikasi provinsi dengan serapan anggaran terbesar/terkecil dan efektivitas penyerapan anggaran.

* **Provinsi dengan Realisasi TKDD Tertinggi (Nominal)**: Provinsi **Jawa Barat** memiliki realisasi TKDD tertinggi secara nominal dengan sekitar **Rp81,92 triliun**.
* **Provinsi dengan Realisasi TKDD Terendah (Nominal)**: Provinsi **Papua Pegunungan** memiliki realisasi TKDD terendah secara nominal dengan sekitar **Rp12,82 triliun**.
* **Provinsi dengan Persentase Realisasi TKDD Tertinggi**: Provinsi **Kalimantan Timur** memiliki persentase realisasi TKDD tertinggi, mencapai **113,87%**. Ini menunjukkan penyerapan dana yang sangat efektif dan efisien, bahkan melebihi target.
* **Provinsi dengan Persentase Realisasi TKDD Terendah**: Provinsi **DI Yogyakarta** memiliki persentase realisasi TKDD terendah, yaitu **98.89%**. Meskipun terendah, nilai ini masih tergolong sangat tinggi (di atas 90%), mengindikasikan bahwa seluruh provinsi di Indonesia berhasil merealisasikan TKDD mereka dengan sangat baik pada tahun 2023.

### 2.3 Faktor-faktor yang Mempengaruhi Tinggi-Rendahnya Realisasi TKDD

Untuk mengetahui faktor-faktor yang memengaruhi realisasi TKDD, dilakukan analisis korelasi dan regresi.
### *Langkah Analisis*:
A. Analisis Bivariat – Korelasi Antar Variabel  
1. Membuat *heatmap* korelasi untuk melihat hubungan antar variabel numerik dengan `Realisasi TKDD`.  
2. Fokus pada korelasi antara variabel independen terhadap variabel target.  

B. Analisis Multivariat – Regresi Linear OLS  
Untuk melihat kontribusi simultan berbagai variabel terhadap `Realisasi TKDD`, dilakukan regresi linear berganda.  
1. Uji Multikolinearitas dengan VIF  
2. Model Regresi OLS  

### 2.4 Hubungan antara Realisasi TKDD dan IPM

Dilakukan analisis korelasi antara `Persentase Realisasi TKDD` dan `IPM` (Indeks Pembangunan Manusia) untuk memahami apakah efektivitas penyerapan anggaran berkorelasi dengan tingkat pembangunan manusia di suatu provinsi.


### 2.5 Faktor-faktor yang Mempengaruhi IPM Tiap Provinsi

Untuk mengidentifikasi faktor-faktor yang memengaruhi IPM, dilakukan analisis korelasi dan regresi multivariat terhadap variabel-variabel yang relevan.


---
