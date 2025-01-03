# **Prediksi Churn dan Segmentasi Pelanggan**

## **Ringkasan Proyek**
Proyek ini dirancang untuk membantu perusahaan telekomunikasi memahami perilaku pelanggan yang berhenti berlangganan (*churn*). Dengan analisis data mendalam dan pembelajaran mesin, proyek ini mengidentifikasi pola churn dan menghasilkan rekomendasi berbasis data untuk meningkatkan retensi pelanggan.

Dataset mencakup informasi dari 7.043 pelanggan, termasuk fitur demografis, layanan yang digunakan, dan status pelanggan.

---

## **Temuan Utama**
### **Distribusi Churn**
- **Churn Rate**: 26,58% pelanggan berhenti berlangganan.
- Pelanggan dengan kontrak **bulanan** memiliki churn rate tertinggi dibandingkan dengan pelanggan kontrak **tahunan**.

**Visualisasi**:
![Distribusi Churn](path/to/visualization1.png)

---

### **Analisis Fitur**
1. **Durasi Berlangganan (Tenure)**:
   - Pelanggan dengan **tenure kurang dari 12 bulan** lebih cenderung berhenti berlangganan.
   - Distribusi tenure menunjukkan pola churn yang kuat pada pelanggan baru.

2. **Kontrak Bulanan**:
   - Sebagian besar pelanggan churn memiliki kontrak bulanan.
   - Pelanggan dengan kontrak jangka panjang memiliki tingkat churn yang lebih rendah.

**Visualisasi**:
- Korelasi churn dengan fitur-fitur utama (heatmap):
![Heatmap Korelasi](path/to/visualization2.png)
- Distribusi Tenure berdasarkan status churn:
![Distribusi Tenure](path/to/visualization3.png)

---

## **Modeling**
### **Model yang Digunakan**:
1. **Logistic Regression**: Model baseline untuk memahami hubungan linier antara fitur.
2. **Random Forest**: Model untuk menangkap hubungan kompleks antar fitur.
3. **XGBoost**: Model terbaik untuk performa keseluruhan.

**Performa Model**:
| Model              | Akurasi | Presisi (Churn) | Recall (Churn) | F1-Score (Churn) |
|--------------------|---------|-----------------|----------------|------------------|
| Logistic Regression| 87.12%  | 78.34%          | 83.56%         | 80.87%           |
| Random Forest      | 92.41%  | 85.67%          | 89.31%         | 87.45%           |
| **XGBoost**        | **95.03%**| **92.00%**      | **90.00%**     | **91.00%**       |

---

## **Rekomendasi Strategis**
1. **Kontrak Jangka Panjang**:
   - Berikan insentif untuk pelanggan dengan kontrak bulanan agar beralih ke kontrak tahunan.

2. **Loyalty Program**:
   - Kembangkan program loyalitas untuk pelanggan baru dan pelanggan senior.

3. **Dukungan Pelanggan**:
   - Tingkatkan kecepatan dan kualitas dukungan teknis, terutama pada masalah internet.

---

## **Cara Menggunakan**
1. Clone repository ini:
   ```bash
   git clone https://github.com/username-anda/churn-prediction.git
