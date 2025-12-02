🗺️ **UAS GIS — Analisis Sekolah vs Kepadatan Kendaraan

(Studi Kasus: Kota Surabaya)**
Tema:
1️⃣ Analisis dampak sekolah di daerah padat kendaraan
2️⃣ Rekomendasi lokasi sekolah di zona minim kendaraan + tersedia lahan kosong

⭐ BAGIAN 1 — DATA YANG HARUS LO DOWNLOAD
✔ 1. Batas Administrasi Kota Surabaya

Sumber:

https://osm-boundaries.com

atau

Download langsung dari QGIS (QuickOSM)

Layer: Polygon boundary Surabaya

✔ 2. Layer Jalan (Roads) Surabaya

Sumber: OpenStreetMap → QuickOSM (di QGIS)
Tag:

Key: highway
Value: primary; secondary; tertiary; residential; trunk; motorway


Ini nanti penting buat:

Analisis zona padat kendaraan (jalan utama)

Buffer jalan

Menentukan aksesibilitas

✔ 3. Layer Titik Sekolah (SD–SMP–SMA)

Masih dari OSM → QuickOSM
Tag:

Key: amenity
Value: school

✔ 4. Layer Permukiman (Landuse Residential)

QuickOSM
Tag:

Key: landuse
Value: residential


Ini dipakai untuk rekomendasi lokasi (sekolah harus dekat pemukiman penduduk).

✔ 5. Layer Lahan Kosong (Empty Land)

Gunakan OSM juga:
Tag:

Key: landuse
Value: grass; meadow; vacant; brownfield


Kalau kurang lengkap →
Tambahin manual via digitizing (Polygon) berdasarkan citra satelit.

✔ 6. (Opsional tapi sangat berguna)

Layer Jalan arteri utama saja (motoway, trunk, primary).
Ini yang akan dianggap “daerah padat kendaraan”.

⭐ BAGIAN 2 — ALUR ANALISIS GIS (PENTING)

Gue bagi 2 bagian sesuai judul tugas lo:

🔶 A. Analisis Dampak Sekolah di Daerah Padat Kendaraan
STEP 1 — Tentukan Jalan Padat Kendaraan

Gunakan elemen jalan berikut:

motorway

trunk

primary

secondary

Caranya:
Filter di QGIS →
Layer → Filter → highway IN (‘primary’, ‘secondary’, ‘trunk’, ‘motorway’)

STEP 2 — Buat Buffer Jalan Utama

Tujuannya: menentukan zona padat kendaraan.

Rekomendasi:

Buffer 0–50 meter → sangat padat kendaraan

Buffer 50–150 meter → masih terdampak

QGIS:
Vector → Geoprocessing Tools → Buffer

Output: layer poligon zona padat kendaraan.

STEP 3 — Identifikasi sekolah di dalam zona padat kendaraan

Gunakan:
Vector → Geoprocessing → Intersection

Input:

Layer buffer jalan utama

Layer titik sekolah

Output:

Sekolah yang terkena dampak kemacetan/kepadatan kendaraan

Hasil analisis bisa lo tulis:

Jumlah sekolah yang berada di dalam buffer 50m

Jumlah sekolah dalam buffer 150m

Sebaran sekolah dekat jalan utama

🔶 B. Rekomendasi Lokasi Sekolah di Zona Minim Kendaraan
STEP 4 — Tentukan Zona Minim Kendaraan

Cara simple tapi sangat efektif:

1️⃣ Buat buffer negatif (dari jalan utama)

Buat buffer 150–200 meter dari jalan → artinya semakin jauh dari jalan besar, semakin minim kendaraan

2️⃣ Balikkan area (Difference)

Pakai Vector → Geoprocessing → Difference

Study area (Surabaya) dikurangi buffer 200m

Hasilnya = zona minim kendaraan

STEP 5 — Cari area sekolah harus dekat permukiman

Gunakan layer landuse = residential.

Buat buffer:

300 meter dari permukiman → artinya sekolah harus dekat warga, tidak terlalu jauh

STEP 6 — Overlay kriteria

Lakukan intersect 3 layer:

Zona minim kendaraan

Buffer permukiman (zona dekat warga)

Lahan kosong (empty land)

Vector → Geoprocessing → Intersect

Output:
👉 Kandidat lokasi baru sekolah yang ideal

STEP 7 — Pilih rekomendasi terbaik

Kriteria yang bisa lo tulis:

jauh dari jalan besar (aman, minim bising)

dekat permukiman (akses mudah)

berada di lahan kosong

luas area memadai

Lo bisa pilih 1–2 lokasi saja untuk laporan.

⭐ BAGIAN 3 — ALUR PENGERJAAN DI QGIS (STEP-BY-STEP)
1. Buka QGIS → Project baru
2. Download data via plugin QuickOSM
3. Load semua layer ke canvas
4. Styling layer biar rapi
Rekomendasi warna:

Jalan utama = merah

Jalan lain = abu

Sekolah = biru

Permukiman = kuning transparan

Zona padat kendaraan = merah transparan

Zona minim kendaraan = hijau muda

Lahan kosong = hijau tua

5. Lakukan analisis buffer
6. Lakukan overlay (intersection, difference)
7. Pilih lokasi rekomendasi
8. Buat Layout Peta

Masuk:
Project → New Print Layout

Isi:

Judul peta

Legenda

North Arrow

Skala

Nama kelompok

Sumber data: OpenStreetMap

⭐ BAGIAN 4 — NARASI ANALISIS (SIAP MASUK LAPORAN)

(bro tinggal copy)

1️⃣ Analisis Dampak Sekolah di Daerah Padat Kendaraan

Hasil buffer pada jalan-jalan utama Kota Surabaya menunjukkan bahwa sejumlah sekolah berada dalam radius 50–150 meter dari jalan arteri. Sekolah-sekolah ini berpotensi mengalami dampak kebisingan, kepadatan lalu lintas, hingga risiko kecelakaan yang lebih tinggi. Analisis intersection antara zona padat kendaraan dan titik sekolah memperlihatkan bahwa sebagian lembaga pendidikan terletak di area dengan mobilitas kendaraan yang tinggi, khususnya pada koridor Ahmad Yani, Margorejo, Wonokromo, dan Kenjeran.

2️⃣ Rekomendasi Lokasi Baru di Zona Minim Kendaraan

Area berjarak lebih dari 200 meter dari jalan utama diidentifikasi sebagai zona minim kendaraan. Zona ini kemudian di-overlay dengan permukiman sehingga hanya area yang dekat dengan warga (dalam radius 300 meter) yang dipertimbangkan. Dari hasil intersect antara zona minim kendaraan, permukiman, dan lahan kosong, ditemukan beberapa area yang layak dijadikan lokasi pembangunan sekolah baru. Lokasi ini berada di kawasan pinggiran seperti Gunung Anyar, Rungkut, dan Pakal yang memiliki kepadatan kendaraan rendah, aksesibilitas cukup, serta tersedia lahan kosong yang memadai.

⭐ BAGIAN 5 — OUTPUT YANG WAJIB ADA

Peta sebaran sekolah + jalan

Peta buffer jalan utama

Peta sekolah terdampak kepadatan kendaraan

Peta zona minim kendaraan

Peta overlay kandidat lokasi sekolah

Peta rekomendasi final
