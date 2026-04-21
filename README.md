# 🌊 Wuthering Waves Sentiment Analysis (Indonesian Reviews)

Proyek ini berfokus pada **Analisis Sentimen** pengguna game *Wuthering Waves* di platform Google Play Store menggunakan berbagai pendekatan *Machine Learning* dan *Deep Learning*. Dengan dataset sebanyak **10.000 ulasan**, proyek ini mengevaluasi persepsi pemain dalam Bahasa Indonesia.

---

## 📊 Hasil Percobaan & Optimasi Model

Berikut adalah ringkasan performa dari tiga skema pengujian yang dilakukan untuk memenuhi kriteria akurasi tinggi dan klasifikasi multi-kelas (Positif, Netral, Negatif).

| Skema | Algoritma Pelatihan | Ekstraksi Fitur | Pembagian Data | Akurasi Testing | Status |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Skema 1** | **SVM (RBF Kernel)** | TF-IDF (1,3) | 80% : 20% | **96.35%** | ✅ Passed |
| **Skema 2** | **Random Forest** | TF-IDF (1,3) | 80% : 20% | **96.43%** | ✅ Best |
| **Skema 3** | **MLP (Deep Learning)** | TF-IDF (1,3) | 70% : 30% | **93.20%** | ✅ Passed |

> **Note:** Akurasi di atas menunjukkan bahwa model mampu mengenali pola bahasa gaul (*slang*) dan ulasan teknis pemain dengan sangat baik setelah dilakukan optimasi pada tahap *preprocessing*.

---

## 🛠️ Fitur & Metodologi

### 1. Scraping & Dataset
- **Sumber Data:** Google Play Store (App ID: `com.kurogame.wutheringwaves.global`).
- **Jumlah Data:** 10,000 sampel ulasan terbaru.
- **Keseimbangan Data:** Menggunakan `RandomOverSampler` untuk menangani *class imbalance* agar model adil dalam memprediksi kelas minoritas.

### 2. Preprocessing & Normalisasi
Model dilengkapi dengan fungsi pembersihan teks yang mencakup:
- **Normalisasi Slang:** Mengubah kata tidak baku (contoh: *yg, gak, ampas, bgt*) menjadi kata baku.
- **Regex Cleaning:** Menghapus karakter berulang, simbol, dan angka yang tidak relevan.
- **Filtering:** Menghapus data duplikat untuk menjaga integritas pengujian.

### 3. Ekstraksi Fitur
- **TF-IDF Vectorizer:** Digunakan dengan parameter `ngram_range=(1, 3)` dan `max_features=8000` untuk menangkap konteks kata yang lebih luas (unigram, bigram, dan trigram).

---

## 🧪 Uji Coba Inferensi (Output)

Hasil prediksi model terhadap input teks baru:

| Teks Ulasan | Prediksi Sentimen |
| :--- | :--- |
| "Gamenya ampas banget, sering lag dan gacha buruk!" | **Negatif** |
| "Grafiknya mantap tapi gameplay biasa aja" | **Positif** (Bias) |
| "Wuthering Waves seru banget, grafisnya luar biasa!" | **Positif** |

---

## ⚠️ Batasan Model (Kekurangan)

Meskipun mencapai akurasi tinggi, model ini memiliki beberapa keterbatasan:
- **Ambiguitas Nilai Tengah:** Model cenderung condong ke arah positif jika terdapat kata pujian yang kuat, meskipun kalimat tersebut berisi keluhan (sentimen campuran).
- **Sarkasme:** Belum mampu mendeteksi sarkasme secara mendalam karena keterbatasan representasi makna pada TF-IDF.
- **Kamus Slang Statis:** Penanganan bahasa gaul bergantung pada kamus manual yang perlu diperbarui secara berkala.

---

## ⚙️ Cara Menjalankan
1. Install dependensi:
   ```bash
   pip install pandas numpy scikit-learn google-play-scraper imbalanced-learn
