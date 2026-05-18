# 📱 Blu Sentiment Analysis — Review App Blu by BCA Digital

Analisis sentimen terhadap ulasan pengguna aplikasi **blu by BCA Digital** dari Google Play Store.  
Data diambil pada **17 Mei 2026** | Scrapped Review: 29.542 Review | 

---

## 📁 Struktur Proyek

```
Blu-SentimentAnalysis/
│
├── Scraping/               # Pengambilan data review dari Google Play
│   └── 1-scraping.ipynb
│
├── Preprocessing/          # Pembersihan & normalisasi teks
│   └── 2-preprocessing.ipynb
│
├── Feature Engineering/    # Ekstraksi fitur teks (TF-IDF, dll)
│   └── feature_engineering.ipynb
│
├── Modeling/               # Training model klasifikasi sentimen
│   └── modeling.ipynb
│
├── Evaluation/             # Evaluasi model (confusion matrix, ROC, dll)
│   └── evaluation.ipynb
│
├── Visualization/          # Visualisasi insight & dashboard bisnis
│   └── visualization.ipynb
│
├── data/                   # File CSV & gambar output (tidak di-push ke GitHub)
│
├── data_export_helper.ipynb  # Helper: sambungkan output Feature Engineering ke Modeling
├── requirements.txt
└── README.md
```

---

## 🔄 Alur Kerja (Pipeline)

```
Google Play Store
      ↓
 [Scraping]          → Ambil review + rating dari app blu
      ↓
 [Preprocessing]     → Cleaning, normalisasi, stopwords, stemming Bahasa Indonesia
      ↓
 [Feature Eng.]      → Labeling sentimen dari rating, TF-IDF vectorization
      ↓
 [data_export_helper] → Export CSV ke folder data/
      ↓
 [Modeling]          → Training & perbandingan 4 model ML
      ↓
 [Evaluation]        → Confusion matrix, ROC-AUC, error analysis, feature importance
      ↓
 [Visualization]     → Word cloud, tren bulanan, topik keluhan, business insight
```

---

## 🤖 Model yang Digunakan

| Model | Kelebihan |
|---|---|
| Logistic Regression | Cepat, interpretable, baseline yang kuat |
| Naive Bayes (MultinomialNB) | Sangat cepat, cocok untuk teks pendek |
| SVM (LinearSVC) | Performan tinggi untuk klasifikasi teks |
| Random Forest | Robust, tahan overfitting |

Model terbaik dipilih berdasarkan **F1 Score weighted** pada test set.

---

## 📊 Label Sentimen

| Label | Kriteria Rating |
|---|---|
| ✅ Positif | Rating 4–5 ⭐ |
| ⚠️ Netral | Rating 3 ⭐ |
| ❌ Negatif | Rating 1–2 ⭐ |

---

## ⚙️ Cara Menjalankan

### 1. Install dependencies
```bash
pip install -r requirements.txt
```

### 2. Download NLTK data (jika perlu)
```python
import nltk
nltk.download('stopwords')
nltk.download('punkt')
```

### 3. Jalankan notebook secara berurutan
```
1. Scraping/scraping.ipynb
2. Preprocessing/preprocessing.ipynb
3. Feature Engineering/feature_engineering.ipynb
4. data_export_helper.ipynb          ← PENTING: sambungkan ke folder data/
5. Modeling/modeling.ipynb
6. Evaluation/evaluation.ipynb
7. Visualization/visualization.ipynb
```

---

## 📌 Sumber Data

- **Aplikasi:** blu by BCA Digital  
- **Platform:** Google Play Store  
- **Package ID:** `com.bcadigital.blu`  
- **Link:** [Play Store](https://play.google.com/store/apps/details?id=com.bcadigital.blu)  
- **Tanggal Scraping:** 2 Maret 2026  
- **Jumlah Review:** ~113.000 ulasan

---

## 🛠️ Tech Stack

- **Python 3.10+**
- `google-play-scraper` — scraping review
- `pandas`, `numpy` — manipulasi data
- `nltk`, `Sastrawi` — NLP Bahasa Indonesia
- `scikit-learn` — machine learning
- `matplotlib`, `seaborn`, `wordcloud` — visualisasi

---

## 📈 Output Visualisasi

| File | Deskripsi |
|---|---|
| `distribusi_label.png` | Pie & bar chart distribusi sentimen |
| `model_comparison.png` | Perbandingan akurasi semua model |
| `confusion_matrix.png` | Confusion matrix model terbaik |
| `roc_auc_curve.png` | ROC-AUC per kelas |
| `feature_importance.png` | Kata paling berpengaruh per kelas |
| `viz_distribusi_sentimen.png` | Dashboard distribusi sentimen |
| `viz_tren_sentimen.png` | Tren sentimen per bulan |
| `viz_wordcloud.png` | Word cloud per sentimen |
| `viz_top_words.png` | Top 15 kata per sentimen |
| `viz_rating_vs_sentimen.png` | Korelasi rating vs sentimen |
| `viz_topik_keluhan.png` | Topik keluhan utama negatif |

---

## 🚀 Pengembangan Selanjutnya

- [ ] Fine-tuning **IndoBERT** untuk akurasi lebih tinggi
- [ ] **Topic Modeling** (LDA) untuk mengelompokkan isu otomatis
- [ ] Deployment sebagai **REST API** (FastAPI/Flask)
- [ ] **Streamlit Dashboard** untuk visualisasi interaktif
- [ ] Jadwalkan scraping otomatis (weekly/monthly)

---

## 👤 Author

**adljna** · [GitHub](https://github.com/adljna)
