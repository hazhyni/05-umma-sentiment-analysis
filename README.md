Tentu, berikut adalah draf dokumentasi `README.md` yang mudah dimengerti, disesuaikan dengan isi *notebook* sentimen analisis aplikasi Umma:

# 📝 Dokumentasi: Umma Prayer App Sentiment Analysis

Proyek ini adalah analisis sentimen ulasan aplikasi doa Umma dari Google Play Store menggunakan pendekatan **Lexicon-Based** untuk pelabelan sentimen dan berbagai model **Machine Learning** (seperti Naive Bayes, Random Forest, Logistic Regression, dan Decision Tree) untuk klasifikasi otomatis.

## 🎯 Fitur Utama

Proyek ini mencakup alur kerja lengkap analisis teks, mulai dari pengumpulan data hingga implementasi model:

1.  **Pengumpulan Data (Web Scraping):** Mengambil hingga **1000** ulasan terbaru aplikasi Umma (`com.muslim.android`) langsung dari Google Play Store.
2.  **Pra-pemrosesan Teks Bahasa Indonesia:**
      * **Data Cleaning:** Menghapus duplikat, link, mention, hashtag, angka, dan tanda baca.
      * **Case Folding & Normalisasi Slang:** Mengubah teks menjadi huruf kecil dan menormalkan kata-kata slang bahasa Indonesia (seperti 'ga' menjadi 'tidak', 'aja' menjadi 'saja') menggunakan kamus slang eksternal.
      * **Stopword Removal:** Menghapus kata-kata umum (seperti 'dan', 'yang', 'di') dalam bahasa Indonesia dan Inggris.
      * **Stemming (Sastrawi):** Mengubah kata berimbuhan menjadi kata dasar (misalnya 'menggunakan' menjadi 'guna').
3.  **Pelabelan Sentimen (Lexicon-Based):** Menggunakan kamus leksikon sentimen berbahasa Indonesia untuk memberikan skor dan melabeli ulasan sebagai **Positif, Negatif,** atau **Netral**.
4.  **Visualisasi Data:**
      * Diagram batang dan lingkaran untuk menunjukkan **distribusi polaritas sentimen** ulasan.
      * **Word Cloud** (Awan Kata) untuk memvisualisasikan kata-kata yang paling sering muncul di ulasan Global, Positif, dan Negatif.
      * Visualisasi **Top 20 Kata** berdasarkan nilai TF-IDF.
5.  **Klasifikasi Sentimen (Machine Learning):**
      * Ekstraksi fitur menggunakan **TF-IDF Vectorization**.
      * Implementasi dan evaluasi model: **Naive Bayes (BernoulliNB), Random Forest, Logistic Regression,** dan **Decision Tree**.
6.  **Pengujian Model Terbaik:** Model dengan akurasi pengujian (test accuracy) tertinggi (**Logistic Regression** dengan akurasi $\approx 81\%$) dipilih untuk prediksi sentimen ulasan baru.

-----

## 🛠️ Persyaratan Sistem & Instalasi

Untuk menjalankan *notebook* ini, Anda membutuhkan lingkungan Python. Gunakan `pip` untuk menginstal pustaka yang diperlukan.

### 📦 Pustaka (Libraries)

Pustaka-pustaka berikut harus diinstal. Anda dapat menginstal semuanya sekaligus:

```bash
!pip install google-play-scraper
!pip install sastrawi
!pip install nltk
!pip install swifter
!pip install pandas numpy matplotlib seaborn scikit-learn wordcloud requests
```

Atau, jika Anda memiliki file `requirements.txt`:

```bash
pip install -r requirements.txt
```

### 🌍 Kebutuhan Eksternal

  * **Akses Internet:** Diperlukan untuk *web scraping* ulasan dari Google Play Store, mengunduh *resource* NLTK, dan memuat kamus slang serta leksikon sentimen dari GitHub.
  * **Kamus Slang dan Leksikon Sentimen:** Proyek secara otomatis memuat *resource* ini dari *URL* GitHub yang disediakan dalam kode (`slangdict.json`, `lexicon_positive.csv`, `lexicon_negative.csv`).
  * **Google Drive (Opsional):** Diperlukan jika Anda ingin menggunakan fitur *checkpoint* untuk menyimpan data pra-pemrosesan ke Google Drive.

-----

## 🚀 Cara Menjalankan

1.  **Unduh atau Clone** *repository* ini (jika ada, atau salin kode ke lingkungan Colab/Jupyter Anda).
2.  **Buka file `Umma_Prayer_App_Sentiment_Analysis.ipynb`** di Jupyter Notebook atau Google Colab.
3.  **Jalankan semua sel kode secara berurutan.** Pastikan untuk:
      * Menjalankan sel instalasi (`!pip install...`) terlebih dahulu.
      * Menjalankan sel impor pustaka dan inisialisasi NLTK (`nltk.download(...)`).
4.  **Scraping Dataset:** Sel kode untuk *scraping* akan mengambil ulasan baru (hingga 1000 ulasan) dari Play Store.
5.  **Preprocessing:** Proses ini, terutama **Stemming** dan **Slang Normalization** menggunakan `swifter`, akan memakan waktu.
6.  **Pelabelan & Analisis:** Visualisasi sentimen dan evaluasi model akan muncul di sel-sel berikutnya.
7.  **Pengujian Akhir:** Sel terakhir memungkinkan Anda memasukkan kalimat baru untuk diuji sentimennya menggunakan model **Logistic Regression** yang telah dilatih.
