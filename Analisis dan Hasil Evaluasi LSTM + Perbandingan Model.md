# **Implementasi Chatbot dengan Long Short-Term Memory**

## **Daftar Isi**

- [**Implementasi Chatbot dengan Long Short-Term Memory**](#implementasi-chatbot-dengan-long-short-term-memory)
  - [**Daftar Isi**](#daftar-isi)
  - [**Dataset**](#dataset)
  - [**Tahapan Penelitian**](#tahapan-penelitian)
  - [**Alur Kerja**](#alur-kerja)
  - [**Arsitektur Model**](#arsitektur-model)
    - [**Implementasi Model**](#implementasi-model)
    - [**Penjelasan Arsitektur**](#penjelasan-arsitektur)
  - [**Evaluasi Model**](#evaluasi-model)
    - [**Grafik Nilai Loss dan Akurasi LSTM**](#grafik-nilai-loss-dan-akurasi-lstm)
    - [**Hasil Evaluasi Model LSTM**](#hasil-evaluasi-model-lstm)
  - [**Perbandingan**](#perbandingan)
    - [**Perbandingan Implementasi LSTM dengan BiLSTM**](#perbandingan-implementasi-lstm-dengan-bilstm)
    - [**Perbandingan Implementasi LSTM dengan BERT**](#perbandingan-implementasi-lstm-dengan-bert)
    - [**Perbandingan Implementasi LSTM, BiLSTM, dan BERT**](#perbandingan-implementasi-lstm-bilstm-dan-bert)

## **Dataset**
Dataset yang digunakan bersumber dari berbagai website antara lain sebagai berikut.

- Kaggle ([https://www.kaggle.com/datasets/narendrageek/mental-health-faq-for-chatbot](https://www.kaggle.com/datasets/narendrageek/mental-health-faq-for-chatbot))
- Alodokter ([https://www.alodokter.com/komunitas/topic-tag/kesehatan-mental](https://www.alodokter.com/komunitas/topic-tag/kesehatan-mental))
- Hellosehat ([https://hellosehat.com/community/kesehatan-mental/](https://hellosehat.com/community/kesehatan-mental/))
- SehatQ ([https://www.sehatq.com/forum/psikologi?](https://www.sehatq.com/forum/psikologi?))

Data yang terkumpul dari sumber-sumber tersebut berjumlah 1981 sampel dengan 18 kelas yaitu `salam`, `depresi`, `keluarga`, `hubungan`, `kecemasan`, `konseling_fundamental`, `harga_diri`, `trauma`, `cari_bantuan`, `perubahan_perilaku`, `definisi`, `penyalahgunaan_zat`, `manajemen_emosi`, `tips_pengobatan`, `diagnosis_dini`, `peningkatan_pola_tidur`, `profesional_yang_benar`, dan `bye_thanks`.

## **Tahapan Penelitian**

Pada implementasi model LSTM ini, **terdapat dua percobaan**. Perbedaan kedua percobaan ini terdapat pada **jumlah kelas**, dan **jumlah epoch** pada proses training.

Percobaan pertama hanya diambil 16 kelas dari total 18 kelas, dengan pengecualian terhadap kelas `salam` dan `bye_thanks`. Percobaan kedua menggunakan keseluruhan kelas.

Jumlah epoch pada proses training percobaan pertama adalah **120 epoch**, dan percobaan kedua adalah **150 epoch**.

## **Alur Kerja**

1. **Text Preprocessing**, yang dilakukan dengan mengubah seluruh teks ke huruf kecil dan melakukan operasi regex untuk menghilangkan karakter atau simbol yang tidak diinginkan.
2. **Split dan shuffle dataset**, untuk memisahkan dataset training dan uji untuk mengukur performa akurasi model terhadap data yang berbeda.
3. **Tokenisasi**, untuk mengubah teks ke dalam bentuk representasi nilai angka yang dapat dimengerti oleh model untuk proses training.
4. **Proses Training**, dimana model LSTM dilatih dengan dataset agar dapat melakukan klasifikasi teks chat dengan baik.
5. **Evaluasi**, untuk melihat ukuran hasil pelatihan berdasarkan nilai akurasi dan loss dari proses training menggunakan dataset training dan uji.

## **Arsitektur Model**

Model diimplementasikan menggunakan framework TensorFlow yang disimpan dalam format HDF5. Visualisasi arsitektur model yang digunakan dapat dilihat pada gambar berikut.

- Arsitektur Percobaan Pertama
    ![Alt text](https://i.ibb.co/xMwkL35/chatbot-model-lstm-withval-databaru-h5-2.jpg "Arsitektur LSTM pertama")  
- Arsitektur Percobaan Kedua
    ![Alt text](https://i.ibb.co/8BgDNMB/chatbot-model-lstm-withval-datafix72-h5.jpg, "Arsitektur LSTM kedua")

Perbedaan arsitektur dari kedua percobaan hanya terletak pada dense layer keluaran, dimana percobaan pertama berjumlah 16 unit neuron dan percobaan kedua berjumlah 18 unit neuron. Jumlah unit ini disesuaikan dengan jumlah kelas keluaran model.

### **Implementasi Model**

Implementasi model menggunakan TensorFlow dilakukan secara sekuensial, dengan menggabungkan beberapa layer secara berurutan. Parameter yang diatur dalam implementasi secara lebih jelas dapat dilihat pada source code dalam blok kode berikut.

```python
model = tf.keras.Sequential([
    tf.keras.layers.Embedding(MAX_NB_WORDS, EMBEDDING_DIM, input_length=X_train.shape[1]),
    tf.keras.layers.SpatialDropout1D(0.2),
    tf.keras.layers.LSTM(64, dropout=0.2, recurrent_dropout=0.2, return_sequences=True),
    tf.keras.layers.LSTM(64, dropout=0.2, recurrent_dropout=0.2),
    tf.keras.layers.Dense(64, activation='relu'),
    tf.keras.layers.Dense(16, activation='softmax') # Output percobaan pertama 16 kelas, percobaan kedua 18 kelas
])
```

### **Penjelasan Arsitektur**

Model diimplementasikan dengan total 6 lapisan secara berurutan, yang antara lain adalah sebagai berikut.

- Lapisan pertama digunakan lapisan **Embedding** dengan ukuran vocabulary 3000 kata dan panjang input 150 data representasi token untuk satu kalimat sesuai ukuran pada data (X_train.shape[1]). Ukuran keluaran embedding adalah 150 x 150 (150 pertama merupakan nilai yang didefinisikan sendiri, 150 berikutnya merupakan panjang input).
- **SpatialDropout1D** digunakan pada lapisan berikutnya untuk mencegah overvitting dengan **menghilangkan 20 persen fitur**. **SpatialDropout1D** sama seperti Dropout biasa, namun **SpatialDropout1D** menghilangkan seluruh feature map 1 dimensi ketimbang elemen individual.
- Diikuti dengan lapisan **LSTM** dengan jumlah unit 64, nilai droput 0.2 dan recurrent dropout 0.2 untuk mencegah overvitting. Diberikan parameter **return_sequences=True** agar model mengembalikan output terakhir dalam sequence output **LSTM**. Fungsi aktivasi recurrent yang digunakan adalah sigmoid dan fungsi aktivasi keluaran yang digunakan adalah TanH.
- Dilanjutkan dengan lapisan **LSTM** dengan parameter yang sama, namun tanpa **return_sequences=True**, sehingga layer mengembalikan seluruh output sequence.
- **Dense** layer digunakan sebagai lapisan fully connected neural network, dengan jumlah neuron sebanyak 64 dan fungsi aktivasi relu.
- Digunakan **Dense** layer pada lapisan keluaran untuk menghasilkan output 16 kelas yang diklasifikasi. Fungsi aktivasi yang digunakan adalah **softmax** agar dapat memberikan keluaran probabilitas masing-masing kelas.

## **Evaluasi Model**

Model dilatih dengan dataset yang dibagi menjadi data training dan uji, dengan data **training 80%** dan **data uji 20%**. Proses training dilakukan dengan **ukuran batch 128**.

Jumlah epoch pada percobaan pertama adalah **120 epoch**, dan percobaan kedua adalah **150 epoch**.

Fungsi loss yang digunakan adalah `categorical_crossentropy` karena label yang digunakan **one-hot encoded** dengan keluaran fungsi aktivasi softmax pada lapisan keluaran model yang menghasilkan probabilitas untuk masing-masing label.

Optimizer yang digunakan adalah `Adam` karena merupakan optimizer adaptif yang dapat digunakan pada data sparse dan dapat digunakan tanpa mendefinisikan learning rate.

Metrik keluaran model yang ingin diukur adalah `accuracy`, untuk melihat kesesuaian hasil klasifikasi model.

### **Grafik Nilai Loss dan Akurasi LSTM**

Evaluasi hasil training model dilakukan dengan melihat nilai loss dan akurasi pada proses training dan validasi dengan data uji. Grafik nilai loss dan akurasi dapat dilihat pada gambar berikut.

- Grafik Percobaan Pertama
    ![Alt text](https://i.ibb.co/YfWXHRT/output-120.jpg "Hasil Evaluasi Model 1")  

    Grafik nilai akurasi menunjukkan bahwa nilai akurasi baik pada proses training maupun validasi mengalami peningkaan secara signifikan. Namun, pada grafik akurasi validasi tidak terjadi peningkatan signifikan ketika mencapai epoch ke-40.

    Grafik nilai loss menunjukkan bahwa nilai loss pada proses training mengalami penurunan signifikan dari 1.0 menjadi 0.15, namun nilai loss validasi mengalami peningkatan signifikan dari 1.5 menjadi 2.73. Hal ini menunjukkan bahwa model belum berhasil melakukan generalisasi sehingga terjadi peningkatan nilai loss ketika berhadapan dengan data uji.

- Grafik Percobaan Kedua
    ![Alt text](https://i.ibb.co/6DydDcv/output2.jpg "Hasil Evaluasi Model 2")  

    Grafik nilai akurasi menunjukkan bahwa nilai akurasi baik pada proses training maupun validasi mengalami peningkaan, namun pada beberapa kurun waktu sempat mengalami stagnansi, dan beberapa lainnya mengalami peningkatan tajam.

    Grafik nilai loss menunjukkan bahwa nilai loss pada proses training mengalami penurunan signifikan dari 2.75 menjadi 0.8, dan nilai loss validasi dari 2.5 menjadi 1.73. Hal ini juga menunjukkan bahwa model berhasil melakukan pembelajaran dengan baik namun masih belum optimal.

### **Hasil Evaluasi Model LSTM**

- Hasil Percobaan Pertama
  
    Hasil training pada epoch terakhir (ke-120) didapatkan nilai akurasi training mencapai 92,03% dan akurasi validasi 69,75%. Nilai loss pada proses training adalah sebesar 0,1436 dan loss nilai validasi adalah sebesar 0,6975.

    ![Alt text](https://i.ibb.co/42ph3v3/Screenshot-2022-12-20-at-20-10-37.png "Nilai Akurasi dan Loss Epoch Terakhir Percobaan 1")

- Hasil Percobaan Kedua

    Hasil training pada epoch terakhir (ke-150) didapatkan nilai akurasi training mencapai 72,93% dan akurasi validasi 62,46%. Nilai loss pada proses training adalah sebesar 0,8099 dan loss nilai validasi adalah sebesar 1,7347.

    ![Alt text](https://i.ibb.co/gyjZzY5/Screenshot-2022-12-20-at-20-08-26.png "Nilai Akurasi dan Loss Epoch Terakhir Percobaan 2")

Perbandingan hasil kedua percobaan lebih jelas dapat dilihat pada tabel berikut.

| Metrik              | Hasil Percobaan 1 | Hasil Percobaan 2 |
| :------------------ | ----------------: | ----------------: |
| Training Loss       |            0,1509 |            0,8099 |
| Validation Loss     |            2,7392 |            1,7347 |
| Training Accuracy   |            92,03% |            72,93% |
| Validation Accuracy |            69,75% |            62,46% |

Hasil evaluasi model menunjukkan bahwa **performa model LSTM terbaik didapat dari percobaan pertama**. Akurasi model pada proses training yang dihasilkan cukup tinggi, yaitu mencapai 92 persen, namun akurasi pada proses pengujian menggunakan dataset validasi hanya mencapai 69 persen. Hal ini menunjukkan bahwa model masih belum berhasil melakukan klasifikasi teks dengan baik dan perlu penelitian lebih lanjut.

Hasil percobaan kedua mendapatkan performa akurasi dan loss yang lebih buruk, karena terdapat perbedaan jumlah kelas. Dimana percobaan pertama hanya terdapat 16 kelas, sedangkan percobaan kedua terdapat 18 kelas. Peningkatan jumlah epoch pada percobaan kedua juga memiliki kontribusi yang kurang signifikan terhadap upaya peningkatan performa dari percobaan pertama.

---

## **Perbandingan**

Selanjutnya, hasil percobaan terbaik dibandingkan dengan beberapa model yang juga diimplementasikan. Tim kami mengimplementasikan beberapa model deep learning yang berbeda untuk membuat sebuah AI Chatbot, yaitu model LSTM, Bidirectional LSTM, dan BERT. Seluruh proses yang berkaitan dengan persiapan data dibuat sama persis untuk menjaga konsistensi data yang menjadi masukan model sekaligus untuk mendapatkan ukuran perbandingan antar model.

---

### **Perbandingan Implementasi LSTM dengan BiLSTM**

Implementasi BiLSTM pada aplikasi kami menyerupai dengan implementasi LSTM. Letak perbedaan dari kedua implementasi ini terdapat pada lapisan LSTM pada arsitektur yang diganti dengan lapisan BiLSTM.

Implementasi arsitektur Bidirectional LSTM serupa dengan LSTM, namun lapisan LSTM yang ada di-wrap ke dalam lapisan Bidirectional RNN yang akan membuat dua lapisan LSTM dengan dua arah berbeda, satu ke arah forward dan satu ke arah backward. 

Lapisan Bidirectional ini memungkinkan setiap komponen urutan input memiliki informasi dari sekuens sebelum dan saat ini (past and present).Perbedaan lebih detail dapat dilihat pada gambar berikut.

![](https://www.researchgate.net/profile/Arvind-Mohan-3/publication/324769532/figure/fig2/AS:619510805561344@1524714294669/LSTM-and-BiLSTM-Architectures_W640.jpg)

Model BiLSTM dilatih dengan jumlah epoch sebanyak 100, dengan hyperparameter yang sama dengan model LSTM. Grafik nilai loss dan akurasi, serta nilai pada epoch terakhir dari model BiLSTM dapat dilihat pada kedua gambar berikut.

![](https://i.ibb.co/qnJTgBs/bilstm.jpg)

![](https://i.ibb.co/SmJKjm4/Screenshot-2022-12-19-at-17-30-56.png)

Untuk memudahkan perbandingan kedua model, dapat dengan melihat tabel perbandingan dari metrik loss dan akurasi berikut.

| Metrik              | Model LSTM | Model BiLSTM |
| :------------------ | ---------: | -----------: |
| Training Loss       |     0,1509 |   **0,0506** |
| Validation Loss     |     2,7392 |   **1,6496** |
| Training Accuracy   |     92,03% |   **97,59%** |
| Validation Accuracy |     69,75% |   **75,26%** |

Model BiLSTM yang kami kembangkan **menghasilkan performa yang lebih baik dibandingkan dengan model LSTM**. Akurasi maksimal yang didapatkan pada proses training mencapai 97,59% dan akurasi validasi mencapai 75,26%. Model LSTM hanya mampu mendapatkan akurasi 92,03% pada proses training, dan 69,75% pada validasi.

Nilai loss juga memiliki perbedaan signifikan, dimana model BiLSTM secara umum memiliki nilai loss yang lebih kecil dibanding model LSTM. Nilai loss minimal yang didapatkan pada proses training adalah 0,0506 dan nilai loss validasi adalah 1,6496. Model LSTM memiliki nilai loss 0,1509 pada proses training, dan 2,7392 pada proses validasi.

Model BiLSTM menghasilkan akurasi yang lebih tinggi karena menggunakan lapisan bidirectional yang memungkinkan terdapat dua LSTM pada satu lapisan, dengan dua arah yang berbeda. Hal ini memungkinkan data input untuk diproses dalam dua arah sekuens, sehingga menghasilkan representasi fitur kata dalam satu kalimat yang lebih baik, yang membantu meningkatkan performa model secara signifikan.

---

### **Perbandingan Implementasi LSTM dengan BERT**

Model BERT yang diimplementasikan dalam percobaan ini adalah model **IndoBERT** `indobert-base-p2` yang didapat dari [huggingface](https://huggingface.co/indobenchmark/indobert-base-p2). Model diimplementasikan dengan AutoModel `TFAutoModelForSequenceClassification`, yang dapat membangun model klasifikasi menggunakan basis model lain.

Perbedaan lain dari implementasi model LSTM dengan BERT adalah fungsi loss yang digunakan, dimana implementasi LSTM menggunakan `categorical_crossentropy` sedangkan implementasi BERT menggunakan `sparse_categorical_crossentropy`. Hal ini karena label klasifikasi model BERT menggunakan label integer, sedangkan model LSTM menggunakan one-hot encoding. Model BERT dilatih dengan jumlah epoch sebanyak 30 dengan optimizer `adam`.

Grafik nilai loss dan akurasi, serta nilai pada epoch terakhir dari model BERT dapat dilihat pada kedua gambar berikut.

![](https://i.ibb.co/2MpB8Nr/bert.jpg)

![](https://i.ibb.co/563RRkZ/Screenshot-2022-12-20-at-20-27-01.png)

Untuk memudahkan perbandingan kedua model, dapat dengan melihat tabel perbandingan dari metrik loss dan akurasi berikut.

| Metrik              | Model LSTM | Model BERT |
| :------------------ | ---------: | ---------: |
| Training Loss       | **0,1509** |     2,5638 |
| Validation Loss     |     2,7392 | **2,6662** |
| Training Accuracy   | **92,03%** |     18,59% |
| Validation Accuracy | **69,75%** |     15,20% |

Model BERT yang kami kembangkan **menghasilkan performa yang lebih buruk dibandingkan dengan model LSTM**. Model BERT hanya mampu mendapatkan akurasi 18,59% pada proses training dan 15,20% pada validasi, sedangkan model LSTM mendapatkan akurasi maksimal 92,03% pada proses training dan 69,75% pada proses validasi.

Nilai loss juga memiliki perbedaan signifikan, dimana model LSTM secara umum memiliki nilai loss yang lebih kecil dibanding model BERT. Nilai loss minimal yang didapatkan pada proses training adalah 0,1509 dan nilai loss validasi adalah 2,7392. Model BERT memiliki nilai loss 2,5638 pada proses training, dan 2,6662 pada proses validasi.

Hasl ini menunjukkan bahwa model BERT yang diimplementasikan belum berhasil melakukan pembelajaran dengan baik terhadap dataset yang digunakan. Kami belum menemukan alasan spesifik mengenai hal ini, sehingga perlu penelitian lebih lanjut.

---

### **Perbandingan Implementasi LSTM, BiLSTM, dan BERT**

Perbandingan terakhir digunakan untuk melihat model terbaik yang dapat digunakan pada aplikasi chatbot berdasarkan performa model yang telah diteliti, yang dapat dilihat pada tabel berikut.

| Metrik              | Model LSTM | Model BiLSTM | Model BERT |
| :------------------ | ---------: | -----------: | ---------: |
| Training Loss       |     0,1509 |   **0,0506** |     2,5638 |
| Validation Loss     |     2,7392 |   **1,6496** |     2,6662 |
| Training Accuracy   |     92,03% |   **97,59%** |     18,59% |
| Validation Accuracy |     69,75% |   **75,26%** |     15,20% |

Dari tabel perbandingan di atas, dapat dilihat bahwa model dengan performa terbaik secara keseluruhan adalah model BiLSTM. Model BiLSTM memiliki nilai akurasi tertinggi pada proses training sebesar 97,59% dan validasi sebesar 75,26%, serta nilai loss terendah pada proses training sebesar 0,0506 dan validasi sebesar 1,6495. Sehingga, model yang kami gunakan pada aplikasi chatbot adalah model BiLSTM.