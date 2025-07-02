# Laporan Proyek Machine Learning - M. Aziz Chusaini

## Domain Proyek

Penggunaan media sosial telah menjadi bagian integral dari kehidupan sehari-hari, terutama di kalangan generasi muda, termasuk pelajar. Platform-platform seperti Instagram, TikTok, Twitter, dan lainnya menawarkan sarana untuk terhubung, berbagi informasi, dan mengekspresikan diri. Namun, di balik manfaatnya, muncul kekhawatiran mengenai potensi dampak negatif dari penggunaan media sosial yang berlebihan, yang seringkali disebut sebagai "kecanduan media sosial".
Kecanduan media sosial di kalangan pelajar menjadi perhatian khusus karena masa remaja dan awal dewasa adalah periode perkembangan penting yang melibatkan transisi akademik, sosial, dan emosional. Penggunaan media sosial yang berlebihan dapat berpotensi mengganggu fokus belajar, mengurangi waktu yang dialokasikan untuk kegiatan akademik, serta mempengaruhi kualitas tidur. Lebih lanjut, interaksi dan perbandingan sosial di platform media sosial juga dikhawatirkan dapat berkontribusi pada masalah kesehatan mental seperti kecemasan dan depresi.
Berbagai penelitian awal telah menyoroti adanya korelasi antara penggunaan media sosial yang tinggi dengan penurunan performa akademik dan kesejahteraan psikologis pada siswa. Namun, pemahaman yang lebih mendalam diperlukan mengenai faktor-faktor spesifik yang berkontribusi terhadap fenomena ini, platform mana yang paling problematik, dan bagaimana karakteristik demografi siswa berperan dalam tingkat ketergantungan mereka.
Proyek analisis dataset "Students Social Media Addiction" ini bertujuan untuk menggali lebih dalam hubungan antara pola penggunaan media sosial siswa dengan berbagai aspek kehidupan mereka, terutama tingkat adiksi terhadap media sosial, dan bagaimana hal itu dipengaruhi oleh variabel-variabel seperti jam penggunaan, kesehatan mental, kebiasaan tidur, dan demografi.

**Mengapa masalah tersebut harus diselesaikan?**
Masalah kecanduan media sosial di kalangan pelajar perlu diselesaikan karena berpotensi menghambat perkembangan akademik, sosial, dan psikologis mereka. Penggunaan media sosial yang berlebihan telah dikaitkan dengan penurunan konsentrasi belajar, manajemen waktu yang buruk, kurangnya interaksi sosial di dunia nyata, gangguan tidur, serta peningkatan risiko masalah kesehatan mental seperti kecemasan dan depresi [1]. Memahami akar permasalahan dan dampaknya secara kuantitatif melalui analisis data dapat membantu dalam merancang intervensi yang lebih efektif, seperti program literasi media sosial, dukungan psikologis, atau pengembangan fitur platform yang mendorong penggunaan yang lebih sehat. Selain itu, identifikasi kelompok pelajar yang paling rentan dapat memungkinkan upaya pencegahan yang lebih terarah.
Berbagai penelitian telah menyoroti dampak negatif penggunaan media sosial yang berlebihan pada pelajar. Misalnya, sebuah studi oleh Primack et al. (2017) menemukan bahwa penggunaan media sosial yang lebih tinggi secara signifikan dikaitkan dengan peningkatan risiko depresi yang dirasakan [2]. Penelitian lain oleh Rosen et al. (2016) menunjukkan adanya korelasi antara penggunaan media sosial yang sering dengan peningkatan gejala kecemasan [3]. Lebih lanjut, Alhassan et al. (2018) dalam meta-analisis mereka menemukan hubungan negatif antara penggunaan media sosial dan performa akademik [4]. Studi-studi ini menggarisbawahi pentingnya memahami dan mengatasi potensi dampak buruk kecanduan media sosial di kalangan pelajar.

referrence:

[1] Kuss, D. J., & Griffiths, M. D. (2011). Online social networking addiction: A systematic review of recent research. International Journal of Environmental Research and Public Health, 8(9), 3528-3552. [IEEE]

[2] Primack, B. A., Shensa, A., Sidani, J. E., Whaite, E. O., Lin, L. Y., Colditz, J. B., ... & Miller, E. (2017). Association between social media use and perceived social isolation in young adults. American Journal of Preventive Medicine, 53(1), 1-8. [APA]

[3] Rosen, L. D., Whaling, L. S., Rab, S., Carrier, L. M., & Cheever, N. A. (2013). The media and technology usage and attitudes scale: An empirical investigation. Computers in Human Behavior, 29(6), 2501-2511. [Umum]

[4] Alhassan, A. S., Lin, D., Hossain, S. F. A., Ahmed, T., & Cheema, S. (2018). The association between social media use and academic performance among university students: A meta-analytic review. Education and Information Technologies, 23(6), 2543-2559. [Umum]

## Business Understanding

### Problem Statements

1. Apa korelasi antara rata-rata jam penggunaan media sosial harian dengan performa akademik dan kesehatan mental?
2. Platform media sosial apa yang paling banyak digunakan berdasarkan demografi?
3. Bagaimana hubungan antara jam penggunaan media sosial dengan jumlah jam tidur per malam?
4. Model prediksi apa yang paling akurat dalam memodelkan skor adiksi media sosial?

### Goals

- Menganalisis korelasi antara `Avg_Daily_Usage_Hours` dengan `Mental_Health_Score`, `Sleep_Hours_Per_Night`, dan `Affects_Academic_Performance`.
- Mengidentifikasi platform media sosial yang paling sering digunakan berdasarkan `Gender` dan `Academic_Level`.
- Membangun model regresi untuk memprediksi `addict_score`.
- Membandingkan performa model: Linear Regression, KNN, Random Forest, dan Boosting.
- Menggunakan metrik MSE untuk evaluasi performa model.

## Data Understanding

### Dataset

Dataset: [Students' Social Media Addiction](https://www.kaggle.com/datasets/adilshamim8/social-media-addiction-vs-relationships)  
Jumlah data: **705 baris dan 13 kolom**

### Kondisi Awal Data

- **Missing Value**: Tidak ditemukan missing value pada seluruh kolom.
- **Data Duplikat**: Tidak ditemukan data duplikat secara eksplisit.
- **Outlier**: Outlier terdeteksi pada beberapa fitur numerik seperti `Avg_Daily_Usage_Hours` dan ditangani menggunakan metode IQR.

### Deskripsi Fitur

- **Student_ID**: ID unik siswa
- **Age**: Usia siswa
- **Gender**: Jenis kelamin
- **Academic_Level**: Tingkat pendidikan siswa
- **Country**: Negara tempat tinggal
- **Avg_Daily_Usage_Hours**: Rata-rata jam penggunaan media sosial setiap hari
- **Most_Used_Platform**: Platform media sosial yang paling sering digunakan
- **Sleep_Hours_Per_Night**: Rata-rata jam tidur setiap malam
- **Mental_Health_Score**: Skor kondisi kesehatan mental siswa
- **Affects_Academic_Performance**: Apakah media sosial memengaruhi performa akademik (Ya/Tidak)
- **Relationship_Status**: Status hubungan siswa (Single, In Relationship, dll)
- **Conflicts_Over_Social_Media**: Frekuensi konflik yang disebabkan oleh media sosial
- **addict_score**: Target variabel, skor adiksi media sosial (nilai numerik)

## Data Preparation

Langkah-langkah yang dilakukan:

1. **Penanganan Outlier**

   - Menggunakan metode IQR untuk menghapus outlier pada kolom numerik.

2. **Encoding**

   - Label encoding dan one-hot encoding dilakukan pada kolom kategorikal seperti `Gender`, `Academic_Level`, `Most_Used_Platform`, dll.

3. **Penghapusan Kolom Tidak Relevan**

   - Kolom `Country` asli dihapus setelah encoding karna tidak relevan.

4. **Split Data**

   - Data dibagi menjadi data latih dan data uji.

5. **Scaling**
   - Fitur numerik diskalakan menggunakan `StandardScaler` **terpisah** untuk data latih dan uji.

## Modeling

### 1. Linear Regression

Linear Regression adalah model baseline yang digunakan dalam proyek ini. Model ini bekerja dengan mencari hubungan linear antara variabel input dan output.

- **Cara kerja:** Model ini menghitung garis terbaik (best fit) yang meminimalkan total selisih kuadrat (Mean Squared Error) antara nilai prediksi dan nilai aktual.
- **Kelebihan:** Sederhana, cepat dilatih, dan hasilnya mudah diinterpretasikan.
- **Kekurangan:** Tidak mampu menangani hubungan non-linear dengan baik dan sensitif terhadap outlier.
- **Parameter:** Menggunakan parameter default dari pustaka `scikit-learn`.


### 2. K-Nearest Neighbors Regressor (KNN)

KNN adalah model berbasis instance-based learning yang memprediksi nilai target berdasarkan rata-rata dari k tetangga terdekat.

- **Cara kerja:** Model mencari sejumlah tetangga terdekat berdasarkan jarak (umumnya Euclidean), lalu menghitung rata-rata nilai target mereka sebagai prediksi.
- **Kelebihan:** Tidak memerlukan proses pelatihan yang berat dan dapat menangkap hubungan non-linear.
- **Kekurangan:** Sensitif terhadap skala fitur, performa buruk pada data berdimensi tinggi dan dataset besar.
- **Parameter:** `n_neighbors = 10`.


### 3. Random Forest Regressor

Random Forest adalah model ensemble yang terdiri dari banyak pohon keputusan (decision trees) dan menghasilkan prediksi dengan merata-ratakan hasil dari tiap pohon.

- **Cara kerja:** Setiap pohon dilatih menggunakan subset acak dari data dan fitur. Hasil akhir diambil dari rata-rata prediksi semua pohon.
- **Kelebihan:** Mampu menangani non-linearitas, robust terhadap overfitting jika dikonfigurasi dengan benar, dan menangani data besar dengan baik.
- **Kekurangan:** Dapat menjadi overfitting jika jumlah pohon terlalu banyak atau terlalu dalam, serta lebih sulit diinterpretasikan.
- **Tuning yang dilakukan:**  
  Dilakukan `GridSearchCV` untuk mendapatkan parameter terbaik:
  - `n_estimators`: 50  
  - `max_depth`: 16  
  - `min_samples_split`: 2  
  - `min_samples_leaf`: 1


### 4. Boosting Regressor (AdaBoost)

AdaBoost adalah teknik boosting yang menggabungkan beberapa weak learners (biasanya decision stumps) secara bertahap.

- **Cara kerja:** Model dilatih secara berurutan, di mana setiap model berikutnya fokus pada kesalahan dari model sebelumnya. Model akhir adalah gabungan bobot dari semua model sebelumnya.
- **Kelebihan:** Meningkatkan akurasi secara bertahap dan efektif pada dataset yang kompleks.
- **Kekurangan:** Lebih sensitif terhadap noise dan outlier.
- **Parameter:** `learning_rate = 0.05`.

Semua model dilatih pada data training dan dievaluasi pada data testing.

## Evaluation

### Metrik

- **Mean Squared Error (MSE)**: Digunakan untuk mengevaluasi performa model prediksi.

### Hasil Evaluasi

- Random Forest (RF) menunjukkan nilai MSE test yang paling rendah (0.000046), mengungguli model lainnya. Meskipun memiliki indikasi overfitting karena perbedaan besar dengan MSE train (0.000005).
- Boosting memiliki MSE test sebesar 0.00011, yang juga relatif rendah.
- Linear Regression (LR) memiliki MSE test sebesar 0.000094, sedikit lebih rendah dari Boosting.
- KNN memiliki MSE test yang paling tinggi (0.002476), menunjukkan performa yang kurang baik dibandingkan model lain.

**Kesimpulan Modeling**:  
Random Forest memberikan performa terbaik di data uji, meskipun memiliki indikasi overfitting. Boosting dan Linear Regression juga memberikan performa yang cukup baik. KNN memiliki performa terendah.

## Kesimpulan Umum

- **Korelasi**: Terdapat korelasi negatif yang signifikan antara rata-rata jam penggunaan media sosial dengan skor kesehatan mental dan jam tidur.
- **Platform Populer**: Platform paling sering digunakan adalah Instagram dan TikTok, terutama oleh perempuan dan siswa pada tingkat pendidikan lebih rendah.
- **Tidur dan Sosial Media**: Semakin tinggi jam penggunaan media sosial, semakin rendah jam tidur rata-rata siswa.
- **Model Terbaik**: Random Forest Regressor menunjukkan performa terbaik dalam memprediksi `addict_score` berdasarkan fitur yang tersedia.
