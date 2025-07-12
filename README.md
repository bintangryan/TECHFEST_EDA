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

* **Provinsi dengan Realisasi TKDD Tertinggi (Nominal)**: Provinsi **Jawa Timur** memiliki realisasi tertinggi dengan total **Rp81,92 triliun**, mencerminkan skala pemerintahan daerah yang besar, kebutuhan fiskal tinggi, dan populasi yang padat.
* **Provinsi dengan Realisasi TKDD Terendah (Nominal)**: Provinsi **Gorontalo** mencatat realisasi TKDD sebesar **Rp6,16 triliun**, menjadi provinsi dengan jumlah anggaran TKDD yang paling kecil secara absolut di antara semua provinsi. Hal ini dapat disebabkan oleh kapasitas fiskal yang lebih kecil serta cakupan geografis dan jumlah penduduk yang relatif rendah.
* **Provinsi dengan Persentase Realisasi TKDD Tertinggi**: Provinsi **Kalimantan Timur** mencatat persentase realisasi sebesar **110,98%**, menandakan bahwa serapan anggaran melampaui target pagu yang ditetapkan. Hal ini bisa menunjukkan adanya kebutuhan tambahan dana, atau perubahan ketetapan pagu di tengah tahun anggaran.
* **Provinsi dengan Persentase Realisasi TKDD Terendah**: Provinsi **Papua** hanya merealisasikan **94,32%** dari total pagu anggaran TKDD. Meskipun tidak masuk kategori “rendah” (<90%), nilai ini menunjukkan bahwa masih terdapat gap serapan anggaran yang bisa diperbaiki. Faktor geografis dan infrastruktur dapat menjadi hambatan realisasi di wilayah ini.

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

**Urutan Faktor yang Paling Mempengaruhi Realisasi TKDD:**

Dari hasil gabungan **analisis bivariat dan multivariat**, berikut adalah urutan kekuatan pengaruh terhadap realisasi TKDD (dari paling besar hingga kecil):

1. **Pagu TKDD** *(dikeluarkan dari regresi, namun korelasinya sangat kuat → secara logis menjadi dasar realisasi)*
2. **PDRB ADHB (Harga Berlaku)** *(dikeluarkan dari model karena VIF tinggi, namun tetap signifikan secara korelasi)*
3. ✅ **Jumlah Penduduk**
4. ✅ **IPM (Indeks Pembangunan Manusia)**
5. ✅ **Anggaran APBN per Kapita**
6. ⚠️ **Persentase Penduduk Miskin**
7. ❌ **PDRB per Kapita**
8. ❌ **Laju Pertumbuhan PDRB**

Hasil dari analisis bivariat dan multivariat secara umum **saling mendukung**, memperkuat keyakinan bahwa faktor-faktor yang ditemukan memang berkontribusi nyata terhadap besarnya realisasi anggaran.
Temuan ini penting untuk menjadi dasar evaluasi dan perencanaan distribusi anggaran daerah yang **berbasis kebutuhan nyata dan kapasitas riil masing-masing provinsi**.

### 2.4 Hubungan antara Realisasi TKDD dan IPM

Dilakukan analisis korelasi antara `Persentase Realisasi TKDD` dan `IPM` (Indeks Pembangunan Manusia) untuk memahami apakah efektivitas penyerapan anggaran berkorelasi dengan tingkat pembangunan manusia di suatu provinsi.

Hasil analisis menunjukkan bahwa:
- **Hubungan antara IPM dan persentase realisasi TKDD** memiliki korelasi lebih kuat (**0.42**) dibandingkan dengan hubungan IPM dan nominal realisasi (**0.27**).
- Artinya, **efektivitas penyerapan anggaran (kualitas eksekusi)** lebih berdampak terhadap capaian IPM daripada sekadar besarnya dana yang dikucurkan.

Sebagai contoh:
- **DI Yogyakarta** berhasil mencapai IPM tinggi meskipun realisasi TKDD-nya tidak sebesar provinsi lain, menunjukkan efisiensi dan kualitas pengelolaan anggaran yang baik.
- Sebaliknya, provinsi dengan dana besar tetapi rendah dalam efektivitas penyerapan cenderung tidak optimal dalam meningkatkan IPM-nya.

👉 Dengan demikian, **kemampuan manajerial dan tata kelola fiskal daerah** dalam mengeksekusi anggaran menjadi faktor yang lebih krusial dibanding hanya besaran nominal anggaran itu sendiri.


### 2.5 Faktor-faktor yang Mempengaruhi IPM Tiap Provinsi

Berdasarkan analisis korelasi, berikut adalah poin-poin penting yang dapat disimpulkan:

1. PDRB (Produk Domestik Regional Bruto) — baik total maupun per kapita — menunjukkan hubungan positif sedang terhadap IPM. Ini menandakan bahwa provinsi dengan aktivitas ekonomi yang lebih besar cenderung memiliki indeks pembangunan manusia yang lebih tinggi.

2. Persentase Realisasi TKDD juga berkorelasi positif sedang terhadap IPM, yang menunjukkan bahwa efektivitas penyerapan anggaran daerah turut berperan dalam peningkatan kualitas hidup masyarakat.

3. Realisasi dan Pagu TKDD (nominal) hanya menunjukkan korelasi lemah terhadap IPM. Hal ini menegaskan bahwa jumlah dana saja tidak cukup, melainkan kemampuan dalam mengelola dan menyalurkan anggaran jauh lebih penting untuk mendorong pembangunan manusia.

4. Persentase Penduduk Miskin memiliki korelasi negatif sangat kuat (-0.81) terhadap IPM. Ini artinya, semakin tinggi angka kemiskinan di suatu provinsi, semakin rendah pula nilai IPM-nya. Kemiskinan terbukti menjadi faktor penghambat utama dalam pencapaian pembangunan manusia.

5. Variabel seperti Anggaran APBN per kapita, jumlah penduduk, dan laju pertumbuhan ekonomi memiliki korelasi rendah bahkan nyaris netral terhadap IPM, sehingga pengaruhnya terhadap peningkatan kualitas hidup masih belum terlalu signifikan jika berdiri sendiri.

Dengan demikian, untuk meningkatkan IPM secara menyeluruh, daerah perlu:

1. Mendorong pertumbuhan ekonomi yang inklusif,
2. Meningkatkan efisiensi penyerapan anggaran, dan
3. Mengarahkan kebijakan secara terukur untuk menurunkan tingkat kemiskinan, sebagai fondasi utama peningkatan IPM.

---
