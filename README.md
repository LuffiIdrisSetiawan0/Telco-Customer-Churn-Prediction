# **Prediksi Churn dan Segmentasi Pelanggan**

## **Ringkasan Proyek**
Bayangkan sebuah perusahaan telekomunikasi yang selama bertahun-tahun telah melayani ribuan pelanggan dengan layanan telepon dan internet. Setiap hari, pelanggan-pelanggan baru datang, namun sebagian lainnya pergi tanpa memberikan alasan yang jelas. Bagi perusahaan ini, setiap pelanggan yang pergi adalah sebuah kehilangan besar—baik dari segi pendapatan maupun potensi untuk tumbuh di masa depan.

Melalui proyek ini, saya akan menyelidiki alasan di balik perilaku pelanggan yang memilih untuk berhenti berlangganan (churn). Tak hanya itu, saya juga akan mencoba memahami pola-pola yang tersembunyi dalam data, mengelompokkan pelanggan ke dalam segmen-segmen tertentu untuk membantu perusahaan lebih memahami kebutuhan mereka. Pada akhirnya, tujuan proyek ini adalah memberikan wawasan yang dapat mendorong perusahaan ini untuk meningkatkan kepuasan pelanggan dan menjaga loyalitas mereka.

---

## **Tujuan**
- Mengidentifikasi faktor-faktor utama yang memengaruhi churn pelanggan.
- Membangun model prediksi churn yang akurat.
- Memberikan rekomendasi berbasis data untuk mengurangi tingkat churn.

---

## **Dataset**
Dataset yang digunakan dalam proyek ini berasal dari IBM dan dapat diunduh melalui tautan berikut: 
[IBM Telco customer churn](https://www.kaggle.com/datasets/alfathterry/telco-customer-churn-11-1-3).

Dataset mencakup informasi pelanggan dari perusahaan telekomunikasi, dengan 7.043 baris dan beberapa fitur seperti:
- **Demografi**: Informasi seperti jenis kelamin, usia, status pernikahan, dan jumlah tanggungan.
- **Lokasi**: Negara, negara bagian, kota, dan kode pos tempat tinggal pelanggan.
- **Layanan**: Jenis layanan yang digunakan oleh pelanggan, termasuk layanan telepon, internet, dan fitur tambahan seperti keamanan online dan streaming TV.
- **Interaksi**: Informasi mengenai durasi berlangganan, metode pembayaran, dan apakah pelanggan pernah merujuk teman atau keluarga.
- **Status Pelanggan**: Status terkini pelanggan (berhenti, tetap, atau baru bergabung), skor kepuasan, skor churn, dan nilai seumur hidup pelanggan (Customer Lifetime Value/CLTV).

---

## **Temuan Utama**
### **Distribusi Churn**
- **Churn Rate**: 26,58% pelanggan berhenti berlangganan.

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

