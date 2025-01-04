# **Prediksi Churn dan Segmentasi Pelanggan**

## **Ringkasan Proyek**
Proyek ini dirancang untuk membantu perusahaan telekomunikasi memahami perilaku pelanggan yang berhenti berlangganan (*churn*). Dengan analisis data mendalam dan pembelajaran mesin, proyek ini mengidentifikasi pola churn dan menghasilkan rekomendasi berbasis data untuk meningkatkan retensi pelanggan.

Dataset mencakup informasi dari 7.043 pelanggan, termasuk fitur demografis, layanan yang digunakan, dan status pelanggan.

---

## **Temuan Utama**
### **Distribusi Churn**
- **Churn Rate**: 26,58% pelanggan berhenti berlangganan.
- Pelanggan dengan kontrak **bulanan** memiliki churn rate yang jauh lebih tinggi dibandingkan pelanggan dengan kontrak **tahunan**.

![Distribusi Churn](Image/Distribusi%20Churn%20Label.png)

---

### **Analisis Fitur Penting**
1. **Durasi Berlangganan (Tenure)**:
   - Pelanggan baru dengan **tenure kurang dari 12 bulan** memiliki risiko churn tertinggi.
   - Pelanggan dengan **tenure lebih dari 24 bulan** cenderung lebih loyal.

![Distribusi Tenure](Image/Distribution%20of%20Tenure%20in%20Months.png)

2. **Jenis Kontrak**:
   - Kontrak **bulanan** paling rentan terhadap churn.
   - Pelanggan dengan kontrak tahunan atau dua tahunan memiliki tingkat churn yang rendah.

![Churn Berdasarkan Kontrak](Image/Churn%20by%20Contract.png)

3. **Layanan Internet**:
   - Pelanggan yang menggunakan layanan internet **Fiber Optic** memiliki tingkat churn lebih tinggi dibandingkan pelanggan dengan **DSL** atau tanpa internet.

![Churn Berdasarkan Internet Service](Image/Churn%20by%20Internet%20Service.png)

![Churn Berdasarkan Internet Service](Image/Churn%20Berdasarkan%20Internet%20Type.png)

4. **Alasan Churn**:
   - Alasan utama pelanggan churn adalah **kompetitor menawarkan perangkat yang lebih baik**, **penawaran harga lebih menarik**, dan **ketidakpuasan terhadap layanan dukungan pelanggan**.

![Alasan Churn](Image/Churn%20Reasons.png)

---

### **Performa Model**

Berikut adalah hasil evaluasi tiga model yang digunakan dalam proyek ini berdasarkan metrik **Accuracy**, **Precision**, **Recall**, dan **F1-Score** untuk memprediksi pelanggan churn:

| Model               | Akurasi   | Precision (Churn) | Recall (Churn) | F1-Score (Churn) |
|---------------------|-----------|-------------------|----------------|------------------|
| Logistic Regression | 94.82%    | 89.71%            | **90.91%**     | 90.31%           |
| Random Forest       | **95.03%**| 90.86%            | 90.37%         | **90.62%**       |
| XGBoost             | **95.03%**| **91.53%**        | 89.57%         | 90.54%           |

---

## **Model Terbaik**

### **Random Forest atau XGBoost?**
- **Random Forest**:
  - Memiliki **F1-Score tertinggi (90.62%)**, sehingga memberikan keseimbangan terbaik antara Precision dan Recall.
  - Recall-nya sedikit lebih tinggi daripada XGBoost, membuatnya lebih cocok untuk mendeteksi pelanggan yang benar-benar churn (mengurangi False Negatives).

- **XGBoost**:
  - Memiliki **Precision tertinggi (91.53%)**, sehingga lebih andal dalam memprediksi pelanggan churn dengan akurasi tinggi (mengurangi False Positives).
  - Recall-nya sedikit lebih rendah dibandingkan Random Forest.

### **Rekomendasi Model**:
- Jika bisnis memprioritaskan **deteksi churn secara akurat tanpa banyak pelanggan salah teridentifikasi** sebagai churn (**Precision tinggi**), maka **XGBoost** adalah pilihan terbaik.
- Namun, jika **mendeteksi sebanyak mungkin pelanggan yang churn** lebih penting (**Recall tinggi**) untuk meminimalkan kehilangan pelanggan yang benar-benar churn, maka **Random Forest** lebih ideal.

**Kesimpulan Akhir**:
- Dalam proyek ini, **Random Forest** dipilih sebagai model utama karena memiliki **F1-Score tertinggi** dan performa keseluruhan yang sangat baik. XGBoost tetap menjadi alternatif kuat, terutama jika Precision menjadi prioritas bisnis.

![Confusion Matrix (XGBoost)](Image/Confusion%20Matrix.png)

---

## **Rekomendasi Strategis**
1. **Kontrak Jangka Panjang**:
   - Berikan insentif kepada pelanggan dengan kontrak bulanan agar beralih ke kontrak tahunan atau dua tahunan.

2. **Peningkatan Layanan**:
   - Tingkatkan kualitas layanan internet untuk pelanggan **Fiber Optic**.
   - Tingkatkan responsivitas dan efisiensi layanan dukungan pelanggan.

3. **Program Loyalitas**:
   - Kembangkan program loyalitas yang ditargetkan untuk pelanggan baru (tenure < 12 bulan) dan pelanggan senior.

