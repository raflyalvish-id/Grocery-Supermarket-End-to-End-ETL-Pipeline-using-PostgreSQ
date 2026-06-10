# Grocery-Supermarket-End-to-End-ETL-Pipeline-using-PostgreSQ

## 📌 Project Overview
Project ini bertujuan untuk membangun data pipeline otomatis (ETL) yang mengolah data transaksi mentah supermarket (periode Januari - Mei) dari skema **Staging Area**, ditransformasikan ke dalam **Data Warehouse (DWH)** dengan pemodelan *Star Schema*, hingga membentuk ringkasan siap pakai di **Data Mart (DM)** untuk kebutuhan visualisasi manajemen melalui Power BI[cite: 2].

### 🎯 Objectives
- Membangun data pipeline yang otomatis, terstruktur, dan bebas dari risiko redundansi data[cite: 2].
- Menerapkan *Performance Isolation* dengan memisahkan database operasional (OLTP) toko dengan database analitik laporan[cite: 2].
- Menganalisis tren transaksi harian, performa produk, dan kontribusi wilayah penjualan[cite: 2].

---

## 🏗️ Data Architecture & Pipeline
Pipeline ini dibagi menjadi 4 fase utama[cite: 2]:
1. **OLTP ➡️ Staging (Data Ingestion):** Fokus pada kecepatan transfer raw data transaksi ke database tanpa transformasi berat[cite: 2].
2. **Staging ➡️ DWH (Cleansing & Modeling):** Raw data dibersihkan dari duplikasi (*data profiling*) dan dipecah menjadi *Star Schema* yang memisahkan *fact table* dan *dimension tables*[cite: 2].
3. **DWH ➡️ DM (Aggregation & Automation):** Data detail diringkas menjadi tabel agregasi bisnis yang siap pakai secara otomatis lewat bantuan **Stored Procedure**[cite: 2].
4. **Data Mart ➡️ Power BI (Data Consumption):** Proses konsumsi data oleh BI Tools untuk visualisasi interaktif bagi tim eksekutif[cite: 2].

---

## 🗄️ Database Schema (Star Schema)
Tabel-tabel yang terbentuk di dalam Data Warehouse meliputi[cite: 2]:
- **`fact_sales`**: Menyimpan data metrik transaksi (Quantity, Total Sales, dll)[cite: 2].
- **`dim_product`**: Data master kategori dan nama produk[cite: 2].
- **`dim_store`**: Data master wilayah, kota, dan cabang store[cite: 2].
- **`dim_customer`**: Data master profil pelanggan[cite: 2].

---

## 📈 Executive Insights & Key Findings
Berdasarkan visualisasi data warehouse yang telah dibangun, berikut adalah temuan utamanya[cite: 2]:
* **Macro Business Metrics:** Total revenue perusahaan mencapai **Rp 38.00 Miliar**, diperoleh dari 59K total transaksi dan 45K total pelanggan[cite: 2].
* **Hourly Sales Trend:** *Peak Hour* kuantitas transaksi terpadat berada pada jam 09.00 pagi (~2.57K transaksi)[cite: 2]. Namun, puncak omset penjualan tertinggi terjadi pada jam 21.00 malam yang mencapai Rp 1.71 Juta[cite: 2].
* **Regional Contribution:** Kontribusi pendapatan antar wilayah sangat kompetitif dan berimbang merata di kisaran ~16% per kota[cite: 2].
* **Product Performance:** Berdasarkan analisis kuadran Scatter Plot, kategori *Confections* dan *Meat* bertindak sebagai *revenue driver* utama perusahaan[cite: 2].

---

## 💡 Strategic Recommendations
1. **Hourly Shift Optimization:** Mengoptimalkan alokasi staf kasir aktif menjelang jam 09.00 pagi untuk mengurai antrean padat, serta mengamankan stok barang (*restock*) sebelum jam 21.00 malam[cite: 2].
2. **Driving Retention:** Rasio transaksi per pelanggan masih rendah (~1.3x)[cite: 2]. Disarankan meluncurkan *Customer Loyalty Program* (sistem poin/member) untuk merangsang *repeat order*[cite: 2].
3. **Regional Expansion:** Karena performa pendapatan di seluruh cabang saat ini sudah sangat stabil dan merata (Rp 6.2M - Rp 6.4M per kota), perusahaan siap melakukan ekspansi pasar ke kota besar baru yang sejenis[cite: 2].

---

## 🚀 How to Run This Project
1. Clone repositori ini:
```bash
   git clone [https://github.com/raflyalvish-id/](https://github.com/raflyalvish-id/)[nama-repo-kamu].git
