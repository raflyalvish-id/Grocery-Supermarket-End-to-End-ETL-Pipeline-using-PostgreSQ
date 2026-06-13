# 🛒 Grocery Supermarket End-to-End ETL Pipeline using PostgreSQL

## 📌 Project Overview
Project ini bertujuan untuk membangun data pipeline otomatis (ETL) yang mengolah data transaksi mentah supermarket (periode Januari - Mei) dari skema **Staging Area**, ditransformasikan ke dalam **Data Warehouse (DWH)** dengan pemodelan *Star Schema*, hingga membentuk ringkasan siap pakai di **Data Mart (DM)** untuk kebutuhan visualisasi manajemen melalui Power BI.

### 🎯 Objectives
- Membangun data pipeline yang otomatis, terstruktur, dan bebas dari risiko redundansi data.
- Menerapkan *Performance Isolation* dengan memisahkan database operasional (OLTP) toko dengan database analitik laporan.
- Menganalisis tren transaksi bisnis harian, performa produk, dan kontribusi wilayah penjualan.

---

## 📂 Project Resources (Quick Links)
Untuk mempermudah review, Anda dapat langsung mengakses file utama project ini melalui tautan di bawah:
* 📊 **[Download Power BI Interactive Dashboard (ETL Dashboard.pbix)](./ETL%20Dashboard.pbix)**
* 📄 **[View Full Presentation Deck (ETL Pipeline using PostgreSQL.pdf)](./ETL%20Pipeline%20using%20PostgreSQL.pdf)**

---

## 🏗️ Data Architecture & Pipeline
Pipeline ini dibagi menjadi 4 fase utama:
1. **OLTP ➡️ Staging (Data Ingestion):** Fokus pada kecepatan transfer raw data transaksi ke database tanpa transformasi berat.
2. **Staging ➡️ DWH (Cleansing & Modeling):** Raw data dibersihkan dari duplikasi (*data profiling*) dan dipecah menjadi *Star Schema* yang memisahkan *fact table* dan *dimension tables*.
3. **DWH ➡️ DM (Aggregation & Automation):** Data detail diringkas menjadi tabel agregasi bisnis yang siap pakai secara otomatis lewat bantuan **Stored Procedure**.
4. **Data Mart ➡️ Power BI (Data Consumption):** Proses konsumsi data oleh BI Tools untuk visualisasi interaktif bagi tim eksekutif.

---

## 🗄️ Database Schema (Star Schema)
Tabel-tabel yang terbentuk di dalam Data Warehouse meliputi:
- **`fact_sales`**: Menyimpan data metrik transaksi (Quantity, Total Sales, dll)
- **`dim_product`**: Data master kategori dan nama produk.
- **`dim_store`**: Data master wilayah, kota, dan cabang store.
- **`dim_customer`**: Data master profil pelanggan.

---

## 📈 Executive Insights & Key Findings
Berdasarkan visualisasi data warehouse yang telah dibangun, berikut adalah temuan utamanya:
* **Macro Business Metrics:** Total revenue perusahaan mencapai **Rp 38.00 Miliar**, diperoleh dari 59K total transaksi dan 45K total pelanggan.
* **Hourly Sales Trend:** *Peak Hour* kuantitas transaksi terpadat berada pada jam 09.00 pagi (~2.57K transaksi). Namun, puncak omset penjualan tertinggi terjadi pada jam 21.00 malam yang mencapai Rp 1.71 Juta.
* **Regional Contribution:** Kontribusi pendapatan antar wilayah sangat kompetitif dan berimbang merata di kisaran ~16% per kota.
* **Product Performance:** Berdasarkan analisis kuadran Scatter Plot, kategori *Confections* dan *Meat* bertindak sebagai *revenue driver* utama perusahaan.

---

## 💡 Strategic Recommendations
1. **Hourly Shift Optimization:** Mengoptimalkan alokasi staf kasir aktif menjelang jam 09.00 pagi untuk mengurai antrean padat, serta mengamankan stok barang (*restock*) sebelum jam 21.00 malam.
2. **Driving Retention:** Rasio transaksi per pelanggan masih rendah (~1.3x). Disarankan meluncurkan *Customer Loyalty Program* (sistem poin/member) untuk merangsang *repeat order*.
3. **Regional Expansion:** Karena performa pendapatan di seluruh cabang saat ini sudah sangat stabil dan merata (Rp 6.2M - Rp 6.4M per kota), perusahaan siap melakukan ekspansi pasar ke kota besar baru yang sejenis.

