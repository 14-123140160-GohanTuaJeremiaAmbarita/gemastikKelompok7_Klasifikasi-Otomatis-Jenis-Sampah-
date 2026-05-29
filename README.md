# gemastikKelompok7_Klasifikasi-Otomatis-Jenis-Sampah-
Klasifikasi Otomatis Jenis Sampah untuk Mendukung Sistem Daur Ulang Mandiri Berbasis Komunitas

# Klasifikasi Otomatis Jenis Sampah untuk Mendukung Sistem Daur Ulang Mandiri Berbasis Komunitas

![Python](https://img.shields.io/badge/Python-3.11%2B-blue?style=for-the-badge&logo=python)
![PyTorch](https://img.shields.io/badge/PyTorch-2.12-ee4c2c?style=for-the-badge&logo=pytorch)
![GEMASTIK XVIII](https://img.shields.io/badge/GEMASTIK%20XVIII-2025-red?style=for-the-badge)

Repositori ini berisi implementasi kecerdasan buatan berbasis *Deep Learning* untuk melakukan klasifikasi otomatis jenis sampah berdasarkan citra/gambar. Proyek ini dikembangkan sebagai karya inovasi tim dalam ajang **Pagelaran Mahasiswa Nasional Bidang Teknologi Informasi dan Komunikasi (GEMASTIK) XVIII Tahun 2025** pada cabang kompetisi **Penambangan Data (Data Mining)**.

## 📌 Latar Belakang & Inovasi
Sistem ini dirancang untuk mengatasi permasalahan pemilahan sampah di tingkat komunitas/warga yang sering kali tidak berjalan optimal karena dilakukan secara manual. Melalui pendekatan *Computer Vision*, warga cukup mengambil foto objek sampah melalui perangkat digital, dan sistem akan otomatis mengategorikannya ke dalam salah satu dari 6 kelas (Cardboard, Glass, Metal, Paper, Plastic, Trash) demi kelancaran rantai pasok daur ulang mandiri yang berkelanjutan.

## 📁 Struktur Direktori Proyek
Proyek ini disusun secara modular dengan struktur repositori sebagai berikut agar mempermudah proses replikasi eksperimen:

```text
GEMASTIK_PD07/
│
├── dataset/                     # Folder penampung data gambar lokal
│   └── Garbage classification/  # Dataset TrashNet (Kaggle) terbagi atas 6 kelas objek
│       ├── cardboard/
│       ├── glass/
│       ├── metal/
│       ├── paper/
│       ├── plastic/
│       └── trash/
│
├── src/                         # Source code utama proyek
│   ├── train.py                 # Skrip untuk augmentasi, arsitektur ResNet18, dan pelatihan model
│   ├── prediksi.py              # Skrip untuk utilitas inferensi/prediksi data foto baru
│   └── visualisasi.py           # Skrip generator grafik performa evaluasi per kelas
│
├── models/                      # Penyimpanan berkas bobot model terlatih
│   └── pytorch_garbage_model.pth
│
├── output/                      # Output grafik evaluasi untuk lampiran laporan
│   ├── accuracy_plot.png        # Grafik tren penurunan nilai error (Loss)
│   └── performa_kelas_plot.png  # Grafik batang komparasi performa antar-kategori
│
└── README.md                    # Dokumentasi proyek Git
