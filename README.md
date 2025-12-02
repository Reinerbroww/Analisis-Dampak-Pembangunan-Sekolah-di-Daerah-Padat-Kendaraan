# 🗺️ UAS GIS — Analisis Sekolah & Kepadatan Kendaraan  
### Studi Kasus: Kota Surabaya

Proyek ini merupakan tugas UAS Sistem Informasi Geografis (SIG) yang bertujuan menganalisis:
1. Dampak lokasi sekolah yang berada di area padat kendaraan.
2. Menentukan lokasi rekomendasi sekolah baru di zona minim kendaraan dengan ketersediaan lahan kosong.

Seluruh analisis dilakukan menggunakan data OpenStreetMap dan pengolahan peta pada QGIS.

---

## 📌 1. Tujuan Proyek
- Mengidentifikasi sekolah yang berada di dekat jalan-jalan utama yang berpotensi padat kendaraan.
- Melakukan analisis buffer dan overlay untuk menentukan dampak lalu lintas terhadap sekolah.
- Menemukan lokasi terbaik untuk pembangunan sekolah baru berdasarkan:
  - Daerah minim kendaraan
  - Kedekatan dengan permukiman
  - Ketersediaan lahan kosong
- Menghasilkan peta akhir berupa:
  - Peta sebaran sekolah
  - Peta buffer jalan utama
  - Peta sekolah terdampak kepadatan kendaraan
  - Peta zona minim kendaraan
  - Peta rekomendasi lokasi sekolah

---

## 📌 2. Data yang Digunakan
Semua data diambil dari OpenStreetMap melalui plugin **QuickOSM** di QGIS:

- Batas Administrasi Kota Surabaya  
- Jalan (highway: motorway, trunk, primary, secondary, tertiary)  
- Titik sekolah (amenity: school)  
- Permukiman (landuse: residential)  
- Lahan kosong (landuse: grass, vacant, brownfield, meadow)

---

## 📌 3. Alur Analisis GIS
### **A. Analisis Dampak Sekolah di Daerah Padat Kendaraan**
1. Filter jalan utama → motorway, trunk, primary, secondary  
2. Buat buffer 0–50 m (sangat padat) dan 50–150 m (padat)  
3. Lakukan **intersection** dengan titik sekolah untuk melihat sekolah yang terkena dampak  
4. Simpulkan hasil sebaran dan jumlah sekolah terdampak

### **B. Rekomendasi Lokasi Sekolah Baru**
1. Buat buffer >150–200 m dari jalan utama → zona minim kendaraan  
2. Buat buffer permukiman 300 m → sekolah harus dekat warga  
3. Overlay (intersection) zona minim kendaraan + buffer permukiman + lahan kosong  
4. Tentukan lokasi rekomendasi final yang memenuhi semua kriteria

---

## 📌 4. Pembagian Tugas Kelompok (3 Orang)

### 👤 **1. Reiner Dominicus (Saya) — Bagian Analisis**
- Menyusun alur analisis GIS secara lengkap  
- Menjelaskan metodologi dalam laporan  
- Menulis hasil analisis dampak sekolah  
- Menulis bagian rekomendasi lokasi sekolah  
- Menyusun narasi untuk setiap peta yang dibuat  
- Mengkoordinasi proses pengerjaan agar hasil peta sesuai analisis

> *Catatan:* Tidak membuat peta di QGIS, fokus pada analisis & penulisan.

---

### 👤 **2. Andika — Bagian Peta & QGIS**
- Mengumpulkan data OpenStreetMap via QuickOSM  
- Melakukan proses:
  - Filter jalan
  - Buffer jalan utama
  - Overlay dampak sekolah
  - Buffer permukiman
  - Overlay penentuan lokasi rekomendasi  
- Mendesain map layout (titel, legenda, skala, north arrow)

---

### 👤 **3. Pashya — Bagian Peta & Visualisasi Final**
- Membuat styling layer (warna jalan, sekolah, zona buffer, dan permukiman)  
- Membuat peta final:
  - Peta sebaran sekolah
  - Peta buffer dan dampak sekolah
  - Peta zona minim kendaraan
  - Peta rekomendasi lokasi sekolah  
- Mengekspor peta final ke format PNG/PDF  
- Mengatur tata letak peta di laporan (jika diperlukan)

---

## 📌 5. Output Yang Dihasilkan
- Peta sebaran sekolah di Kota Surabaya  
- Peta jalan utama dan zona padat kendaraan  
- Peta sekolah terdampak kepadatan kendaraan  
- Peta zona minim kendaraan  
- Peta lahan kosong  
- Peta rekomendasi lokasi sekolah baru  
- Analisis tertulis dalam laporan akhir

---

## 📌 6. Tool yang Digunakan
- **QGIS 3.x**  
- **QuickOSM Plugin**  
- Data **OpenStreetMap (OSM)**  
- Google Satellite (untuk referensi lahan kosong opsional)

---

## 📌 7. Cara Menjalankan Proyek di QGIS
1. Clone repo ini atau download ZIP  
2. Buka QGIS → Load semua layer yang ada di folder project  
3. Pastikan struktur folder tidak berubah  
4. Jika layer kosong, lakukan QuickOSM kembali menggunakan tag di atas  
5. Ikuti alur analisis yang sudah dijelaskan (buffer → overlay → intersect → layout)

---

## 📌 8. Lisensi
Proyek ini hanya untuk kebutuhan tugas UAS GIS dan tidak digunakan untuk keperluan profesional.

---

## 🙌 Terima Kasih
Jika ada yang mau diskusi atau revisi peta/analisis, chat saja di grup.
