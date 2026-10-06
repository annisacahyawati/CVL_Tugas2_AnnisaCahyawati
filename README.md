# CVL_Tugas2_AnnisaCahyawati 🚀 Evaluasi Arsitektur YOLO Modern pada Deteksi Objek Kecil Berkelompok

Repositori ini berisi kode (Jupyter Notebook), berkas konfigurasi, laporan analisis, dan luaran evaluasi model untuk pemenuhan **Tugas Individu Mata Kuliah Computer Vision MKA** (Pengajar: Wahyono, S. Kom., Ph.D.). 

Penelitian dalam repositori ini berfokus pada **Opsi C (YOLO)** untuk menguji keterbatasan arsitektur *You Only Look Once*.

## 📖 Deskripsi Eksperimen

Pada paper aslinya, J. Redmon et al. (2016) mengakui secara eksplisit di Bagian 2.4 bahwa YOLO memiliki kelemahan spasial saat mendeteksi objek kecil yang muncul secara berkelompok. Eksperimen di repositori ini dirancang untuk menjawab pertanyaan riset:
> **Apakah keterbatasan YOLO pada objek kecil berkelompok masih berlaku pada arsitektur YOLO modern, dan apakah intervensi peningkatan resolusi masukan dapat mengatasinya?**

Kami menggunakan model **YOLO11n** dan mengevaluasinya pada dataset **VisDrone2019-DET**, sebuah dataset tangkapan *drone* yang sarat dengan kerumunan objek berskala kecil. Dua skenario diujikan:
1. **Baseline**: Inferensi dengan resolusi input standar (`imgsz=640`).
2. **Intervensi**: Inferensi dengan resolusi input tinggi (`imgsz=1280`).

Metrik evaluasi difokuskan pada `mAP@0.5` dan `mAP@0.5:0.95`, yang dipecah secara spesifik untuk ukuran objek *small*, *medium*, dan *large*.

## 📂 Struktur Repositori

```text
├── Laporan_Tugas_CV_MKA_Opsi_C.pdf   # Laporan akhir format IEEE (maksimal 6 halaman)
├── Sesi_3_YOLO_VisDrone_Tugas.ipynb  # Notebook Google Colab berisi kode eksperimen lengkap
├── dataset.yaml                      # Konfigurasi pemetaan kelas dan path dataset VisDrone
└── runs/                             # Direktori hasil (dihasilkan otomatis oleh Ultralytics)
    └── detect/
        ├── baseline_640/             # Berisi grafik metrik, kurva PR, dan gambar prediksi baseline
        └── intervensi_1280/          # Berisi grafik metrik, kurva PR, dan gambar prediksi intervensi
