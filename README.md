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
Datasets yang digunakan merupakan hasil gabungan dari data-data yang diambil dari Twitter, Letterboxd, benchmark IndoNLU serta jurnal-jurnal bahasa dan sastra Indonesia. Datasets yang berhasil dikumpulkan sebanyak 4.492 data. Setelah dilakukan proses preprocessing dan anotasi berjumlah 4400 data dengan proporsi seimbang, 2200 berlabel sarkas dan 2200 berlabel tidak sarkas. Labelisasi datasets dibuat seimbang agar pelatihan dan evaluasi model dapat dilakukan lebih baik dan lebih objektif. Detail dataset sebagai berikut:

|            Sumber Data            |                    Topik                      |      Rentang Waktu      |  Jumlah Data  | 
|-----------------------------------|-----------------------------------------------|-------------------------|---------------|
| Scraping Twitter                  | Tweet Politik                                 | 12/01/2020 – 13/06/2022 | 1365          |
| Scraping Letterbox                | Review film Ashiap Man, Satria Dewa: Gatotkaca| 03/02/2022 – 03/05/2023 | 902           |
| Benchmarks IndoNLU                | Data sentimen analisis                        | 2019 - 2023             | 1760          |
| Jurnal Bahasa dan Sastra Indonesia| Umum                                          | tidak diketahui         | 468           |

## Requirements

### Spesifikasi
| Name          | Specification |
|---|---|
| CPU  | Intel(R) Xeon(R) CPU @ 2.30GHz |
| GPU    | Tesla T4 |
| RAM   | 12 GB |
| Storage   | 141 GB Available |

### Library
- Pandas
- Numpy
- Pytorch
- Transformers
- Random, time, datetime

## Eksperimen Model
Skenarion Eksperimen
| Eksperimen | Epoch | Model & Hyperparameter |
|---|---|---|
| Pertama  | 3 |`output_attentions = False, output_hidden_states = False, optimizer = AdamW(model.parameters(),lr = 2e-5, eps = 1e-8), num_warmup_steps = 0`|
| Kedua    | 3 |`output_attentions = False, output_hidden_states = False, attention_probs_dropout_prob=0.5, hidden_dropout_prob=0.5, optimizer = AdamW(model.parameters(), lr = 2e-5, eps = 1e-8), num_warmup_steps = 0`|
| Ketiga   | 3 |`output_attentions = False, output_hidden_states = False, attention_probs_dropout_prob=0.4, hidden_dropout_prob=0.4, optimizer = AdamW(model.parameters(), lr = 2e-5, eps = 1e-8), num_warmup_steps = 0`|
| Keempat  | 3 |`output_attentions = False, output_hidden_states = False, attention_probs_dropout_prob=0.4, hidden_dropout_prob=0.4, optimizer = AdamW(model.parameters(), lr = 2e-5, eps = 1e-8), num_warmup_steps = 150`|

## Evaluasi Model

| Eksperimen | _Accuracy_ | _Precision_ | _Recall_ | _F1-Score_ |
|---|---|---|---|---|
| 1  | 86.14% | 85.30% | 87.24% | 86.26% |
| 2  | 82.84% | 81.30% | 85.19% | 83.20% |
| 3  | 84.77% | 84.58% | 84.97% | 84.77% |
| 4  | 84.77% | 84.12% | 85.65% | 84.88% |

![image](https://github.com/user-attachments/assets/550fa04b-7136-4368-b47f-29b537971a04)

## Kesimpulan dan Saran

### Kesimpulan
1. Deteksi sarkasme menggunakan model BERT untuk teks bahasa Indonesia secara umum memiliki cara kerja seperti kasus pada analisis sentimen yaitu terdapat proses pengumpulan data, data preprocessing, pengembangan model, eksperimen model dan evaluasi model. Perbedaan paling mendasar terdapat pada pemahaman tentang konsep dan teori sarkasme yang nantinya akan mempengaruhi kode dan pengambilan keputusan. Pada tahapan data preprocessing, anotasi data dilakukan dengan membagi data menjadi dua kelas yaitu sarkasme dan non-sarkasme, pembersihan data-pun dilakukan tanpa menghilangkan tanda seru, serta tidak dilakukannya proses slangwords, stopwords maupun stemming. Selain itu, penerapan model BERT yang membedakan dengan model lainnya yaitu terdapat penambahan token khusus [CLS] dan [SEP]. Tokenisasi menggunakan IndoBERT serta pengembangan model dibantu dengan pustaka PyTorch dan AdamW Optimizer. Model akhir yang diusulkan diberi nama IndoSarcasm.
2. Kebaharuan penelitian ini berfokus pada dataset yang secara khusus dirancang untuk kasus sarkasme berbahasa Indonesia. Dataset berjumlah total 4400 data yang bersumber dari Twitter, Letterboxd, benchmark IndoNLU bagian sentimen analisis yang dilabelisai ulang dan jurnal-jurnal linguistik serta sastra dengan topik pembahasannya yaitu analisa komentar sarkasme di media sosial. Model IndoSarcasm yang dirancang menggunakan BERT, utamanya IndoBERT membuktikan dengan baik bahwa IndoSarcasm dapat mendeteksi kalimat sarkasme bahasa Indonesia. Hasil eksperimen membuktikan performa model IndoSarcasm memiliki akurasi sebesar 84.77% dengan nilai parameter lain yang relatif seimbang yaitu precision sebesar 84.58%, recall sebesar 84.97% dan F1-Score sebesar 84.77%. Hal ini diperkuat dengan hasil eksperimen selama pelatihan, yaitu tidak ditemukannya indikasi overfitting. 

### Saran
1. Penelitian ini membutuhkan dataset yang lebih besar dan komprehensif berkaitan dengan keragaman bentuk kalimat sarkasme. Dataset dapat ditambahkan dengan melakukan scraping di platform media sosial lainnya seperti YouTube, Facebook dan TikTok agar data lebih variatif, mengingat sarkasme memiliki kompleksitas tinggi karena dipengaruhi lingkungan. Sehingga semakin beragam lingkungannya, maka semakin kaya pemahaman model tentang kalimat sarkasme. Cara lainnya, dataset dapat ditambahkan dengan melakukan generate data menggunakan GPT-3.5 dari dataset yang sudah ada.
2. Labelisasi pada proses anotasi data masih terbatas sehingga pada penelitian selanjutnya dapat menambahkan beragam fitur labelisasi, seperti pada fitur tanda baca kriteria dapat ditambahkan dengan mempertimbangakn jumlah tanda tanya, jumlah titik, jumlah kata yang menggunakan huruf kapital dan jumlah tanda kutip. Fitur lainnya yang dapat ditambahkan yaitu fitur yang mempertimbangkan sintaksis dan semantik dalam kaidah bahasa. Selain itu, cara anotasi data, selain dilakukan secara manual, dapat dilakukan dengan crowdsourcing atau meminta pendapat expert dalam bidang linguistik.
3. _Hyperparameter_ pada penelitian ini terbatas pada menambahkan dropout dan num_warmup¬steps, merubahnya serta mengujinya dengan dua opsi nilai. Sehingga pada penelitian di masa depan pelatihan dapat diuji dengan mengganti berbagai macam hyperparameter dan membandingkannya secara komprehensif. Matriks evaluasi yang digunakan-pun terbatas menggunakan confusion matrix sehingga pada penelitian di masa depan matriks evaluasi dapat dikembangkan lebih lanjut menggunakan evaluasi Matthews Correlation Coefficient (MCC) atau mariks evaluasi lainnya. Selain itu, model dan pendekatakan deteksi sarkasme dapat dikembangkan dengan menerapkan model lain, seperti RoBERTa, T5 (Text-to-Text Transfer Transformer), XLNet atau pendekatakan yang bukan hanya mempertimbangkan teks atau konten komentarnya saja tetapi pendekatakan berdasarkan akun.
