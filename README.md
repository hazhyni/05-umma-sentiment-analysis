# Analisis Sentimen Ulasan Aplikasi UMMA di Google Play Store (Fixing Bugs)

Proyek ini bertujuan untuk melakukan analisis sentimen terhadap ulasan pengguna mengenai aplikasi "UMMA" yang tersedia di Google Play Store. Analisis sentimen dilakukan untuk memahami persepsi pengguna terhadap aplikasi, mengidentifikasi sentimen positif dan negatif yang paling sering diungkapkan, dan mendapatkan wawasan berharga bagi pengembang aplikasi.

## Dataset

Dataset yang digunakan dalam proyek ini adalah ulasan pengguna yang diambil langsung dari Google Play Store menggunakan pustaka `google-play-scraper`. Ulasan diambil dari aplikasi dengan ID `com.muslim.android` (aplikasi UMMA).

## Metodologi

Proyek ini mengikuti alur kerja analisis sentimen umum yang meliputi tahapan berikut:

1.  **Pengumpulan Data (Scraping):**
    *   Menggunakan `google-play-scraper` untuk mengambil semua ulasan dari aplikasi UMMA.
    *   Menyimpan ulasan yang diambil ke dalam file CSV.

2.  **Pemrosesan Awal Data (Preprocessing):**
    *   Memuat data ulasan dari file CSV ke dalam Pandas DataFrame.
    *   Melakukan pembersihan data, termasuk menghapus baris dengan nilai yang hilang dan menghapus duplikat.
    *   Menerapkan serangkaian fungsi pembersihan teks:
        *   `cleaningText`: Menghapus mention, hashtag, RT, tautan, angka, dan tanda baca.
        *   `casefoldingText`: Mengubah teks menjadi huruf kecil.
        *   `fix_slangwords`: Mengganti kata-kata slang bahasa Indonesia dengan bentuk bakunya menggunakan kamus slang yang disediakan.
        *   `tokenizingText`: Memecah teks menjadi kata-kata (token).
        *   `filteringText`: Menghapus kata-kata umum (stopwords) dalam bahasa Indonesia dan Inggris.
        *   `stemmingText` (Opsional): Mengembalikan kata-kata ke bentuk dasarnya menggunakan Sastrawi. *(Catatan: Pada kode yang disediakan, fungsi `stemmingText` didefinisikan tetapi tidak digunakan dalam pipeline preprocessing pada kolom `text_akhir`. Namun, Anda bisa menggunakannya jika diperlukan.)*
        *   `toSentence`: Menggabungkan kembali token yang sudah difilter menjadi kalimat.

3.  **Pelabelan Sentimen:**
    *   Menggunakan pendekatan berbasis leksikon (dictionary-based) untuk menentukan polaritas sentimen setiap ulasan.
    *   Memuat kamus kata-kata positif (`lexicon_positive.csv`) dan negatif (`lexicon_negative.csv`) dari sumber eksternal.
    *   Fungsi `sentiment_analysis_lexicon_indonesia` menghitung skor sentimen berdasarkan kemunculan kata-kata dari kamus positif dan negatif dalam teks ulasan yang sudah diproses.
    *   Polaritas sentimen (`positive`, `negative`, `neutral`) ditentukan berdasarkan skor sentimen. Skor >= 0 dilabeli 'positive', dan skor < 0 dilabeli 'negative'.

4.  **Analisis dan Visualisasi:**
    *   Menampilkan distribusi polaritas sentimen (positif, negatif) dalam bentuk diagram lingkaran (pie chart).
    *   Menampilkan ulasan-ulasan teratas dengan skor sentimen positif dan negatif tertinggi/terendah.
    *   Membuat visualisasi *word cloud* dari kata-kata yang paling sering muncul dalam keseluruhan ulasan setelah preprocessing.

## Persyaratan

Untuk menjalankan kode ini, Anda memerlukan pustaka Python berikut:

*   `google-play-scraper`
*   `pandas`
*   `numpy`
*   `matplotlib`
*   `seaborn`
*   `datetime`
*   `re`
*   `string`
*   `nltk` (dengan resource `punkt` dan `stopwords` diunduh)
*   `Sastrawi`
*   `wordcloud`
*   `csv`
*   `requests`
*   `io`

Anda dapat menginstal pustaka-pustaka ini menggunakan pip:
```pip install google-play-scraper pandas numpy matplotlib seaborn nltk Sastrawi wordcloud requests)```

Pastikan juga untuk mengunduh resource NLTK yang diperlukan:
```python import nltk nltk.download('punkt') nltk.download('stopwords')```

## Cara Menjalankan

1.  Pastikan Anda memiliki Python terinstal.
2.  Instal pustaka yang diperlukan seperti yang disebutkan di bagian "Persyaratan".
3.  Unduh resource NLTK jika belum.
4.  Jalankan skrip Python atau *notebook* Jupyter/Colab yang berisi kode proyek ini.
5.  Data ulasan akan diambil dari Google Play Store, diproses, dan analisis sentimen akan dilakukan.
6.  Hasil analisis sentimen, termasuk distribusi polaritas dan word cloud, akan ditampilkan.

## File Proyek

*   Skrip Python atau *notebook* (`.py` atau `.ipynb`) yang berisi kode program.
*   `ulasan_aplikasi.csv`: File CSV yang berisi ulasan yang diambil dari Google Play Store.
*   *Lexicon files* (`lexicon_positive.csv` dan `lexicon_negative.csv`): Kamus kata-kata positif dan negatif yang digunakan untuk analisis sentimen. File-file ini diakses langsung dari URL GitHub dalam kode.

## Hasil

Hasil dari analisis sentimen ini akan menunjukkan:

*   Jumlah total ulasan yang diambil.
*   Jumlah ulasan setelah pembersihan (menghapus nilai kosong dan duplikat).
*   Distribusi persentase ulasan positif dan negatif.
*   Contoh ulasan dengan sentimen positif dan negatif yang kuat.
*   Visualisasi kata-kata yang paling sering muncul dalam ulasan.

Informasi ini dapat digunakan untuk memahami kekuatan dan kelemahan aplikasi UMMA berdasarkan masukan pengguna, serta memberikan panduan untuk perbaikan di masa mendatang.

