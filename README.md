# Home Credit Default Risk: Credit Scoring

Proyek *project-based internship* Home Credit: membangun model *machine learning* untuk memprediksi **Probability of Default** nasabah pada tahap pengajuan pinjaman, sebagai dasar keputusan *auto-approval* atau *manual review*.

## 📌 Business Understanding

Home Credit ingin menurunkan rasio kredit macet (NPL) **tanpa** menurunkan *approval rate* atau menolak nasabah berkualitas. Tantangannya, data sangat *imbalanced*: hanya **8,07%** nasabah gagal bayar.

- `0` = Lancar (*Repaid*)
- `1` = Gagal bayar (*Default*)

## 🎯 Objectives

1. Memaksimalkan diskriminasi risiko.
2. Menyeimbangkan *Recall* dan *Precision* lewat *threshold tuning* untuk menjaga *approval rate*.
3. Mengkalibrasi probabilitas agar akurat secara aktual.

## 📏 Metrik Kesuksesan

| Metrik | Target | Hasil (Test) |
|--------|:------:|:------------:|
| ROC-AUC | > 0,75 | **0,786** ✅ |
| Gini | ≥ 0,50 | **0,572** ✅ |
| PR-AUC (metrik utama) | Baseline 0,081 | **0,287** ✅ |
| Brier Score | < 0,0742 (baseline) | **0,0657** ✅ |
| ECE | Rendah | **0,0033** ✅ |

**Dampak bisnis (threshold 0,16):** *approval rate* 86,5%, dan tingkat gagal bayar pada nasabah yang disetujui turun dari **8,07% menjadi 5,08%**. Nasabah di atas threshold diarahkan ke *manual review*.

## 🧭 Cara Membaca Project

Seluruh analisis ada di `main.ipynb` dengan alur CRISP-DM:

1. **Business Understanding**: masalah, tujuan, kriteria sukses
2. **Data Understanding**: EDA 7 tabel, missing value, outlier, distribusi target
3. **Data Preparation**: pembersihan, *feature engineering*, agregasi histori ke level nasabah
4. **Modeling**: Logistic Regression, Random Forest, LightGBM, *tuning*, kalibrasi
5. **Evaluation**: metrik final, *threshold tuning*, dampak bisnis
6. **Deployment**: rencana implementasi dan keterbatasan

## 📂 Dataset

Data berasal dari program *project-based internship* Home Credit dan terdiri dari 7 tabel relasional (aplikasi, biro kredit, kartu kredit, cicilan, POS cash, dan aplikasi sebelumnya). **Dataset tidak disertakan dalam repository ini** karena ukurannya besar dan merupakan materi program magang.

## ⚙️ Cara Menjalankan

1. Siapkan dataset sendiri di folder `datasets/` dengan nama file sesuai yang dipakai di `main.ipynb`.
2. Instal: `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`, `lightgbm`, `scipy`.
3. Jalankan `main.ipynb` secara berurutan (butuh RAM besar, karena `bureau_balance` ±27 juta baris).

## 🛠️ Tech Stack

Python · pandas · scikit-learn · LightGBM · Matplotlib · Seaborn