# Deteksi Sarkasme Menggunakan _Bidirectional Encoder Representations from Transformers_ (BERT) Pada Teks Bahasa Indonesia 

Proyek ini merupakan proyek *Natural Language Processing* (NLP) yang merupakan tugas akhir perkuliahan gelar sarjana Teknik Informatika dan saat ini sedang menunggu publikasi.

## Deskripsi Proyek
Proyek ini merupakan penelitian yang berfokus pada deteksi sarkasme berbahasa Indonesia. Terdapat celah yang signifikan dalam penelitian deteksi sarkasme berbahasa Indonesia, yaitu penelitian sebelumnya yang menggunakan algoritma klasifikasi tradisional yang cenderung menggunakan representasi kata sederhana tanpa memperhitungkan hubungan sekuensial dan hubungan kontekstual antar kata dalam kalimat panjang. Sehingga, fokus target perbaikan pada penelitian ini adalah mengembangkan metode deteksi sarkasme dengan memanfaatkan representasi kontekstual dari model BERT dengan harapan mampu mengatasi keterbatasan model dalam mengklasifikasikan kalimat bernada sarkasme. Model BERT yang akan digunakan pada penelitian ini adalah Model IndoBERT beserta optimalisasi menggunakan AdamW yang diharapkan mampu memberikan pemahaman yang lebih baik tentang konteks dan niat dibalik kalimat sarkastik berbahasa Indonesia. Selain itu, dataset yang dikumpulkan pada penelitian ini diharapkan mampu menjawab keterbatasan yang disebabkan tidak adanya dataset khusus untuk deteksi sarkasme berbahasa Indonesia.

## Tujuan
1. Melakukan deteksi kalimat sarkasme menggunakan model BERT untuk memahami informasi kontekstual pada teks bahasa Indonesia.
2. Mengukur performa model BERT untuk deteksi sarkasme pada teks bahasa Indonesia. 

## Arsitektur Sistem 
![image](https://github.com/user-attachments/assets/cca14dba-34db-4b93-b18a-c29d23fe47a8)

## Datasets
Datasets yang digunakan merupakan hasil gabungan dari data-data yang diambil dari Twitter, Letterboxd, benchmark IndoNLU serta jurnal-jurnal bahasa dan sastra. Datasets berjumlah 4400 data dengan proporsi seimbang, 2200 berlabel sarkas dan 2200 berlabel tidak sarkas. Labelisasi datasets dibuat seimbang agar pelatihan dan evaluasi model dapat dilakukan lebih baik dan lebih objektif. Detail dataset sebagai berikut:

|      Sumber Data      |  Topik   |  Rentang Waktu  |  Jumlah Data  | 
|-----------------------|----------|-----------------|---------------|
| Scraping Twitter          |     |
| Scraping Letterbox           | `False`      |
