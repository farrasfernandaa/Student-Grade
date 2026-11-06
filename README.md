# Executive Dashboard: Sosio-Ekonomi & Performa Akademik Siswa

## Overview
Sebuah *dashboard* analitik interaktif yang dirancang untuk membedah disparitas capaian akademik siswa ($N = 12.025$) berdasarkan faktor latar belakang sosio-ekonomi (SES), kepemilikan perangkat digital, keterlibatan orang tua, hingga tipologi institusi pendidikan. Proyek ini memetakan variabel determinan performa belajar siswa menjadi wawasan visual strategis guna memahami karakteristik distribusi nilai, disparitas fasilitas, efektivitas bimbingan belajar, dan penyimpangan performa terhadap tolok ukur acuan menggunakan **Power BI Desktop**.
<img width="3075" height="1763" alt="GradePredict_page-0001" src="https://github.com/user-attachments/assets/f520233b-d404-4941-a384-e232b3af4f1d" />


---

## Business Questions Framework
Tabel berikut menguraikan pertanyaan bisnis dan analitik utama yang dijawab melalui visualisasi pada *dashboard*:

| Dimensi Analisis | Pertanyaan Bisnis Utama |
| :--- | :--- |
| **Distribusi Nilai & Pendapatan** | • Bagaimana profil sebaran densitas nilai akhir siswa terdistribusi di setiap rentang kelas pendapatan keluarga (*Income Brackets*) |
| **Proporsi Tingkat Kelulusan** | • Berapa rasio sebaran siswa pada tiap kategori kelas predikat nilai akhir (*Donut Chart*) dari total populasi sampel |
| **Intervensi Bimbingan & Gender** | • Apakah keikutsertaan bimbingan belajar (*bimbel*) dan gender menciptakan disparitas nilai akhir yang signifikan |
| **Pola Belajar & Kehadiran** | • Bagaimana interaksi simultan antara alokasi jam belajar mandiri mingguan dan tingkat kehadiran memengaruhi rata-rata nilai siswa |
| **Kesenjangan Perangkat Digital** | • Sejauh mana tingkat keterlibatan orang tua mampu mengompensasi ketiadaan perangkat laptop/komputer di rumah |
| **Deviasi Mutu Antar Lembaga** | • Kelompok tipe sekolah dan wilayah mana yang mengalami deviasi performa tertinggi dan terendah terhadap rata-rata global ($66.9\%$) |

---

## Data Preparation & Calculated Fields (Power BI DAX)
- **Pengelompokan Institusi Komposit (`School_Group`):** Menggabungkan tipe sekolah dan klasifikasi wilayah tempat tinggal (`school_type` dan `School_Residence_Label`) via Calculated Column untuk memetakan unit analisis institusi secara granular.
- **Kalkulasi Deviasi Nilai Global (`Deviasi_Nilai`):** Menghitung deviasi rata-rata nilai masing-masing kelompok sekolah terhadap garis dasar rata-rata populasi global menggunakan kombinasi fungsi `AVERAGE` dan `CALCULATE(ALL(...))`.
- **Logika Pewarnaan Bersyarat Dinamis (`Warna_Deviasi`):** Menentukan heksadesimal tema neon secara dinamis (Cyan `#00F5D4` untuk deviasi positif dan Magenta `#D90368` untuk deviasi negatif) berbasis *Field Value*.
- **Standardisasi Presisi Desimal:** Mengunci format desimal skalar numerik pada sumbu dan tabel matriks melalui tab *Measure / Column Tools* agar seragam pada ketelitian satu digit di belakang koma.

---

## Visualizations & Dashboard Layout (Power BI)
- **Density Curve: Distribusi Nilai Akhir across Income Brackets (Area Chart):** Kurva sebaran densitas multi-layer yang memetakan spektrum nilai akhir siswa pada lima tingkat pendapatan (*Low*, *Lower-Middle*, *Middle*, *Upper-Middle*, dan *High*).
- **Proporsi Kelas Nilai (Donut Chart):** Diagram donat dengan metrik pusat total sampel ($12.025\text{K}$) yang membedah proporsi siswa di masing-masing predikat nilai, didominasi oleh kelas utama ($51.23\%$, $22.82\%$, dan $22.36\%$).
- **Distribusi Nilai: Dampak Bimbel & Gender (Clustered Column Chart):** Diagram kolom komparatif berdampingan yang menguji disparitas nilai akhir antara siswa laki-laki dan perempuan berdasarkan kepesertaan bimbel (0 vs 1).
- **Jam Belajar vs Kehadiran (Scatter Plot):** Plot sebaran titik dengan gradasi warna (*Dark to Light Warm*) yang memetakan korelasi waktu belajar mingguan dan rasio kehadiran terhadap nilai akhir siswa.
- **Disparitas Nilai: Keterlibatan Ortu & Akses Perangkat (Line Chart):** Grafik garis komparatif (*Cyan solid* vs *Magenta dashed*) berserta area arsiran (*shade area*) yang memperlihatkan rentang disparitas nilai pada skala keterlibatan orang tua (1–5).
- **Deviasi Nilai Kelompok dari Rata-rata Global 66.9% (Diverging Bar Chart):** Diagram batang horizontal bipolar berpusat di titik 0 yang mengurutkan surplus dan defisit capaian nilai kelompok institusi sekolah dari yang tertinggi hingga terendah.

---

## Key Business Insights
- **Ketimpangan Fasilitas Digital yang Konsisten:** Siswa dengan kepemilikan laptop/PC secara konsisten mencatatkan nilai rata-rata lebih tinggi di seluruh tingkat keterlibatan orang tua dibanding siswa tanpa akses perangkat.
- **Pengaruh Protektif Keterlibatan Orang Tua:** Kenaikan skor keterlibatan orang tua berbanding lurus dengan peningkatan nilai akhir sekaligus meredam ketimpangan nilai akibat ketiadaan perangkat komputasi di rumah.
- **Keunggulan Lembaga Perkotaan:** Institusi perkotaan berbantuan pemerintah (*Gov-Aided Urban*) dan swasta perkotaan (*Private-Unaided Urban*) mencatatkan surplus deviasi nilai tertinggi di atas batas rata-rata global $66.9\%$.
- **Disparitas Ekstrem Sekolah Perdesaan:** Sekolah di kawasan perdesaan (*Rural*) mengalami defisit nilai paling tajam di bawah garis rata-rata global, mengonfirmasi perlunya perhatian khusus pada disparitas mutu fasilitas wilayah pinggiran.

---

## Strategic Recommendations
- **Program Subsidi Fasilitas Komputasi Terarah:** Mengalokasikan bantuan perangkat laptop/PC dan akses internet prioritas bagi siswa berpenghasilan rendah di sekolah wilayah *Rural* guna memangkas kesenjangan akademik.
- **Penguatan Kemitraan Orang Tua dan Sekolah:** Mengembangkan lokakarya berkala untuk membekali orang tua dengan modul pendampingan belajar aktif di rumah, terutama pada keluarga tanpa fasilitas digital penuh.
- **Standarisasi Pengajaran dan Pengayaan Sekolah Perdesaan:** Mengimplementasikan program mentoring guru dan intervensi tutor tambahan di institusi *Government-Aided* dan *Private-Unaided* wilayah perdesaan untuk mendongkrak capaian nilai mendekati rata-rata global.

---

## Tools Used
- **Google Colab (Python / Pandas):** Lingkungan komputasi berbasis *cloud* untuk eksplorasi awal dataset, pembersihan data (*data cleaning*), perumusan fitur sintetis, dan validasi korelasi multivariat.
- **Power BI Desktop:** Platform visualisasi utama untuk pemodelan data (*Data Modeling*), kalkulasi DAX, pembuatan tema gelap (*Cyberpunk Dark Theme: #111827*), dan penataan tata letak visual interaktif bersudut membulat (*Rounded corners 8px*).
- **Dataset:** `student_grade_ses_dataset` ($N = 12.025$ baris data profil siswa, latar belakang sosial ekonomi keluarga, fasilitas digital, dan nilai capaian akhir).
