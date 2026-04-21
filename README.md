# Analisis-Sentimen-Game-RPG-Wuthering-Waves
🌊 Wuthering Waves Sentiment Analysis Indonesian Play Store Reviews
Proyek ini merupakan sistem analisis sentimen otomatis yang dirancang untuk mengevaluasi opini pemain game Wuthering Waves pada platform Google Play Store (Region Indonesia). Dengan menggunakan lebih dari 10.000 sampel data, proyek ini mengomparasi berbagai algoritma Machine Learning dan Deep Learning untuk mendapatkan akurasi klasifikasi terbaik.

🎯 Fitur & Keunggulan
Large-Scale Scraping: Mengambil 10.000 komentar terbaru menggunakan google-play-scraper.

Advanced Preprocessing: Pembersihan teks otomatis, penanganan slang (bahasa gaul), normalisasi kata, dan penghapusan duplikasi.

Data Balancing: Menggunakan RandomOverSampler untuk menangani ketidakseimbangan kelas (imbalance dataset).

Multi-Scheme Experiment: Perbandingan performa antara SVM, Random Forest, dan MLP (Deep Learning).

High Accuracy: Mencapai akurasi pengujian di atas 92% melalui optimasi hyperparameter dan TF-IDF N-Gram.

📊 Hasil Optimasi Model
Berdasarkan eksperimen pada 10.000 sampel data, berikut adalah performa dari tiga skema yang diuji:
Skema,Algoritma,Split Data,Akurasi
Skema 1,SVM (RBF Kernel),80/20,96.35%
Skema 2,Random Forest,80/20,96.43%
Skema 3,MLP (Deep Learning),70/30,93.20%

🛠️ Alur Kerja Teknis
Scraping: Pengambilan 10.000 ulasan menggunakan google-play-scraper.

Preprocessing: - Normalisasi kata slang (contoh: "yg" -> "yang", "ampas" -> "buruk").

Streamlining karakter berulang (contoh: "bagusss" -> "bagus").

Pembersihan simbol dan angka melalui Regex.

Balancing: Menggunakan RandomOverSampler untuk memastikan model tidak bias terhadap kelas mayoritas.

Feature Extraction: TF-IDF Vectorizer dengan rentang n-gram (1, 3) untuk menangkap konteks frasa.
