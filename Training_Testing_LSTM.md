## LSTM
---
Proses pembuatan model LSTM (*Long-Short Term Memory*) dilakukan dalam 3 tahap, yaitu *training* dan *evaluation*. Berikut merupakan penjelasan masing-masing tahapannya.
#### 1. Training
Pada tahap *training*, beberapa proses yang dilakukan antara lain **persiapan data training**, **pembuatan arsitektur model**, **pelatihan model**.

##### 1.1 Persiapan Data Training
Pada tahap ini, seluruh *dataset* yang digunakan akan dipecah (*split*) menjadi beberapa *subset*, yaitu data *train* (latih) dan data *validation* (validasi). Data *train* dan data *validation* dibuat dengan fungsi `train_test_split` dari *library* sklearn. Seluruh *dataset* dipecah menjadi dua *subset*, yaitu *data train* dan *data validation* dengan proporsi 80% dan 20%. Data *train* kemudian digunakan pada tahap *training* dan data *validation* digunakan pada tahap *evaluation*.

##### 1.2 Pembuatan Arsitektur Model
Pada tahap ini, dilakukan pembuatan arsitektur model LSTM dengan metode *sequential* menggunakan *library* TensorFlow Keras. Berikut merupakan arsitektur dari model LSTM yang dibuat.

Versi 1

![model_plot_lstm16](https://user-images.githubusercontent.com/76557114/208538472-67ab6b1d-16ee-4da0-8f54-6c3f1e162cca.png)

Versi 2

![model_plot_lstm18](https://user-images.githubusercontent.com/76557114/208538594-0a5d6a4f-e8b3-4b0f-9a2f-cbde9a022deb.png)


Gambar di atas merupakan arsitektur dari model LSTM yang telah dibuat. Terdapat dua versi model LSTM yang dibuat. Versi pertama menggunakan data lama dengan 16 kelas dan versi kedua menggunakan data baru dengan 18 kelas.
Untuk versi pertama, arsitekturnya terdiri dari lapisan input yang berukuran 150 kolom. Input tersebut kemudian mengirimkan data pada lapisan ***Embedding*** dengan jumlah *vocabulary* maksimum sebesar 3000 dan dimensi *embedding* berukuran 150. Hasil *embedding* kemudian akan dikirimkan pada lapisan ***SpatialDropout1D***. Setelah itu, data akan dikirimkan kepada lapisan LSTM pertama dengan jumlah unit sebesar 64. Lapisan berikutnya adalah lapisan LSTM kedua (*stacked*) dengan jumlah unit yang sama yaitu 64. Setelah data melalui lapisan LSTM, kemudian akan dikirim pada lapisan ***Dense*** (neuron biasa) dengan jumlah unit sebesar 64 dan *activation function* ReLu. Hasil dari lapisan ini kemudian akan dikirimkan pada lapisan terakhir (*output layer*) dengan total *output* sebesar 16.
Untuk versi kedua, susunan arsitekturnya hampir sama dengan versi kedua, namun jumlah unit pada *stacked* LSTM-nya berbeda, yaitu sebesar 128, dengan total *output* sebesar 18.

##### 1.3 Pelatihan Model
Pada tahap ini, data akan dipelajari representasinya oleh model yang telah dibuat. Pada tahap ini, digunakan dua buah *subset* data yaitu data *train* dan data *validation*. Data *train* digunakan untuk pelatihan model sementara data *validation* digunakan untuk mengukur performa model pada data yang belum pernah dilihat. Berikut merupakan konfigurasi dari tahap pelatihan model LSTM.
Versi 1
| No. | Hyperparameter | Nilai                           |
|-----|----------------|---------------------------------|
| 1.  | Optimizer      | Adam                            |
| 2.  | Loss           | Categorical Crossentropy        |
| 3.  | Epochs         | 120                             |
| 4.  | Batch Size     | 128                             |

Versi 2
| No. | Hyperparameter | Nilai                           |
|-----|----------------|---------------------------------|
| 1.  | Optimizer      | Adam                            |
| 2.  | Loss           | Categorical Crossentropy        |
| 3.  | Epochs         | 150                             |
| 4.  | Batch Size     | 128                             |
