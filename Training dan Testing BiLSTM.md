## BiLSTM

Proses pembuatan model BiLSTM (*Bidirectional Long-Short Term Memory*) dilakukan dalam 3 tahap, yaitu *training* dan *testing*. Berikut merupakan penjelasan masing-masing tahap.
#### 1. Training
Pada tahap *training*, beberapa proses yang dilakukan antara lain **persiapan data latih**, **pembuatan arsitektur model**, **pelatihan model**.

##### 1.1 Persiapan Data Latih
Pada proses persiapan data latih, seluruh *dataset* yang digunakan akan dipecah (*split*) menjadi beberapa *subset*, diantaranya data *train* (latih) dan data *testing* (uji). Data *train* dan data *testing* dibuat dengan melakukan *split* terhadap *dataset* dengan menggunakan fungsi `train_test_split` dari *library* sklearn. Seluruh *dataset* dipecah menjadi dua (2) buah *subset*, yaitu *data train* dan *data testing* dengan proporsi 80% dan 20%. Data *train* kemudian digunakan pada tahap *training* dan data *testing* digunakan pada tahap *testing*.

##### 1.2 Pembuatan Arsitektur Model
Pada proses ini, dilakukan pembuatan arsitektur model BiLSTM dengan metode *sequential* menggunakan *library* Keras. Berikut merupakan arsitektur model BiLSTM yang dibuat.

| ![Arsitektur BiLSTM](https://i.ibb.co/m04Sxdr/arsitektur-Bi-LSTM.png) |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

Gambar di atas merupakan arsitektur dari model BiLSTM yang telah dibuat. Arsitektur pertama yaitu lapisan input yang berukuran 50 kolom. Input tersebut kemudian mengirimkan data pada lapisan ***Embedding*** dengan *vocabulary* maksimum berjumlah 2500 dan dimensi *embedding* berukuran 50. Hasil *embedding* kemudian akan dikirimkan pada lapisan ***SpatialDropout1D***. Setelah itu, data akan dikirimkan kepada lapisan BiLSTM pertama dengan jumlah unit sebesar 128 dan *activation function* ReLu. Lapisan berikutnya adalah lapisan BiLSTM kedua (*stacked*) dengan jumlah unit yang sama yaitu 128. Setelah data melalui lapisan BiLSTM, kemudian akan dikirim pada lapisan ***Dense*** (neuron biasa) dengan jumlah unit sebesar 64. Hasil dari lapisan ini kemudian akan dikirimkan pada lapisan terakhir (*output layer*) dengan total *output* sebesar 18.

##### 1.3 Pelatihan Model
Pada proses ini, data akan digunakan dan dipelajari representasinya oleh model yang telah dibuat. Pada tahap ini, digunakan dua (2) buah *subset* data yaitu data *train* dan data *validation*. Data *train* digunakan untuk pelatihan model sementara data *validation* digunakan untuk mengukur performa model pada data baru/belum pernah dilihat. Data *validation* didapatkan dengan memecah (*split*) data *train* dengan proporsi sebesar 20%. Berikut merupakan konfigurasi dari tahap pelatihan model.
| No. | Hyperparameter | Nilai                           |
|-----|----------------|---------------------------------|
| 1.  | Optimizer      | Adam                            |
| 2.  | Loss           | Sparse Categorical Crossentropy |
| 3.  | Epochs         | 100                             |
| 4.  | Batch Size     | 128                             |

Hasil dari proses pelatihan model akan dibahas pada tahap evaluasi.

#### 2. Testing
Pada tahap ini, model akan melakukan prediksi terhadap data uji (*testing*) yang belum pernah dilihat sebelumnya. Hal ini bertujuan untuk mengukur performa model untuk melakukan generalisasi. Data uji yang digunakan merupakan hasil *split* *dataset* dengan rasio 20% sehingga menghasilkan *subset* data dengan jumlah 397 observasi. Hasil *testing* akan dibahas pada tahap evaluasi.
