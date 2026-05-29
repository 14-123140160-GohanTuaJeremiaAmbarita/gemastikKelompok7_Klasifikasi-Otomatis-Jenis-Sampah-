# gemastikKelompok7_Klasifikasi-Otomatis-Jenis-Sampah-
Klasifikasi Otomatis Jenis Sampah untuk Mendukung Sistem Daur Ulang Mandiri Berbasis Komunitas

# Klasifikasi Otomatis Jenis Sampah untuk Mendukung Sistem Daur Ulang Mandiri Berbasis Komunitas

![Python](https://img.shields.io/badge/Python-3.11%2B-blue?style=for-the-badge&logo=python)
![PyTorch](https://img.shields.io/badge/PyTorch-2.12-ee4c2c?style=for-the-badge&logo=pytorch)
![GEMASTIK XIX](https://img.shields.io/badge/GEMASTIK%20XVIII-2026-red?style=for-the-badge)

Repositori ini berisi implementasi kecerdasan buatan berbasis *Deep Learning* menggunakan arsitektur *Convolutional Neural Network* (CNN) untuk klasifikasi otomatis jenis sampah berdasarkan citra digital. Proyek inovasi ini dikembangkan dan disempurnakan pada tahun **2026** sebagai karya orisinal tim dalam ajang **Pagelaran Mahasiswa Nasional Bidang Teknologi Informasi dan Komunikasi (GEMASTIK) XVIII** pada cabang kompetisi **Penambangan Data (Data Mining)**.

---

## 📌 Urgensi & Masalah Nyata di Masyarakat
Krisis pengelolaan sampah di Indonesia, khususnya pada kawasan padat penduduk dan komunitasi lokal, berakar dari rendahnya tingkat pemilahan sampah langsung dari sumbernya (rumah tangga). Metode pemilahan manual terbukti tidak efisien karena:
1. **Kurangnya Literasi Visual:** Warga sering kali kesulitan membedakan kategori spesifik sampah (misal: plastik PET vs plastik PVC, atau kertas berlapis minyak vs karton bersih).
2. **Faktor Keengganan (*Inconvenience*):** Proses pemilahan manual membutuhkan waktu ekstra, sehingga sampah cenderung langsung dibuang dalam kondisi tercampur (*mixed waste*).
3. **Penurunan Nilai Ekonomis:** Sampah yang tercampur akan mengalami kontaminasi silang (terutama oleh sampah organik/residu), sehingga menurunkan nilai jual material pada rantai pasok industri daur ulang (*circular economy*).

---

## 💡 Inovasi yang Dibuat: *Community-Driven Smart Sorting*
Proyek ini memajukan proses penambangan data citra konvensional menjadi sebuah solusi integratif berskala komunitas. Inovasi fundamental yang kami tawarkan meliputi:

* **Sistem Inferensi Nirsentuh Berbasis Citra:** Menggantikan input teks manual menjadi pemrosesan visual. Warga cukup mengarahkan kamera *smartphone* atau menaruh sampah di bawah modul kamera Tempat Sampah Pintar (*Smart Bin*), dan kecerdasan buatan akan langsung mendeteksi jenis material secara *real-time*.
* **Penerapan Deep Transfer Learning (ResNet18):** Alih-alih membangun model CNN dari nol yang rentan terhadap *overfitting*, kami memanfaatkan model ResNet18 yang telah dilatih menggunakan jutaan gambar (ImageNet). Metode ini memberikan kemampuan ekstraksi fitur tepian (*edge*), bayangan (*shadow*), dan refleksi material (kaca/logam) yang sangat superior meski diambil dengan kamera *smartphone* kelas menengah.
* **Arsitektur Pemrosesan Lokal Mandiri:** Kode dirancang agar dapat berjalan secara lokal (*on-premise*) maupun diintegrasikan ke perangkat komputasi tepi (*edge computing* seperti Raspberry Pi). Hal ini memastikan implementasi di tingkat RT/RW tidak ketergantungan penuh pada bandwidth internet yang besar.
* **Peta Akurasi Adaptif Komunitas:** Model dilatih menggunakan teknik augmentasi gambar ekstrem (rotasi, pergeseran nilai, pengecilan/pembesaran objek) untuk menyimulasikan kondisi riil di lapangan—seperti kondisi botol yang sudah remuk, kertas yang terlipat, atau pencahayaan lingkungan pembuangan sampah yang minim.

---

## 🛠️ Apa yang Dilakukan dalam Eksperimen Ini?
Proyek penambangan data ini dilakukan melalui siklus *KDD (Knowledge Discovery in Databases)* yang ketat pada data tak terstruktur (gambar):

1. **Eksplorasi Data Citra (TrashNet):** Mengelola dan menganalisis 2.527 aset gambar sampah yang terbagi ke dalam 6 kelas utama (*cardboard, glass, metal, paper, plastic, trash*).
2. **Data Preprocessing & Augmentasi:** Mengubah ukuran seluruh matriks gambar menjadi resolusi seragam $128 \times 128$ piksel, menormalisasi nilai warna RGB menggunakan standar ImageNet, serta menerapkan fungsi manipulasi acak (*RandomHorizontalFlip*, *RandomRotation*) untuk melipatgandakan variasi sudut pandang model.
3. **Data Splitting yang Adil:** Membagi dataset secara acak terkontrol dengan proporsi 80% untuk fase pengisian pengetahuan model (*Training Dataset*) dan 20% murni untuk fase pengujian performa (*Validation Dataset*).
4. **Pelatihan Arsitektur ResNet18:** Mengoptimalkan bobot *Convolutional Layers* menggunakan fungsi optimasi *Adam* dengan tingkat pembelajaran (*learning rate*) 0.001 serta fungsi kerugian *Cross Entropy Loss* untuk menekan tingkat *error* di setiap babak (*epoch*).
5. **Evaluasi Multimetrik Lapangan:** Melakukan ekstraksi *Classification Report* menyeluruh untuk melihat performa detail model lewat parameter *Precision*, *Recall*, dan *F1-Score*, bukan sekadar melihat akurasi mentah.

---

## 📁 Struktur Direktori Proyek
```text
GEMASTIK_PD07/
│
├── dataset/                     # Penyimpanan aset data gambar lokal
│   └── Garbage classification/  # Dataset TrashNet terbagi atas 6 sub-folder kelas
│       ├── cardboard/           # Sampel visual kardus cokelat, kotak packing
│       ├── glass/               # Sampel botol kaca sirup, pecahan kaca
│       ├── metal/               # Sampel kaleng aluminium, tutup botol logam
│       ├── paper/               # Sampel kertas dokumen, koran, majalah
│       ├── plastic/             # Sampel botol plastik benang, gelas plastik, kresek
│       └── trash/               # Sampel residu, komponen tercampur, organik dapur
│
├── src/                         # Source code/skrip Python utama
│   ├── train.py                 # Skrip pelatihan model, pembuatan plot loss, dan validasi
│   ├── prediksi.py              # Skrip inferensi cepat untuk mendeteksi file gambar baru
│   └── visualisasi.py           # Skrip generator chart performa batang untuk laporan
│
├── models/                      # Folder penyimpanan berkas bobot kecerdasan buatan
│   └── pytorch_garbage_model.pth
│
└── output/                      # Folder dokumentasi grafik hasil running riil
    ├── accuracy_plot.png        # Grafik tren penurunan tingkat error (Loss)
    └── performa_kelas_plot.png  # Grafik batang komparasi keandalan antar-kategori
