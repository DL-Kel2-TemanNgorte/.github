## BERT
---
Proses pembuatan model BERT (*Bidirectional Encoder for Representation Transformers*) dilakukan dalam 3 tahap, yaitu *training*, *testing*, dan *evaluation*, Berikut merupakan penjelasan masing-masing tahap.
#### 1. Training
Pada tahap *training*, beberapa proses yang dilakukan antara lain **persiapan data latih**, **pembuatan arsitektur model**, **pelatihan model**.

##### 1.1 Persiapan Data Latih
Pada proses persiapan data latih, seluruh *dataset* yang digunakan akan dipecah (*split*) menjadi beberapa *subset*, diantaranya data *train* (latih) dan data *validation* (validasi). Data *train* dan data *validation* dibuat dengan melakukan *split* terhadap *dataset* dengan menggunakan fungsi `train_test_split` dari *library* sklearn. Seluruh *dataset* dipecah menjadi dua (2) buah *subset*, yaitu *data train* dan *data validation* dengan proporsi 80% dan 20%. Data *train* dan data *validation* kemudian digunakan pada tahap *training*.

##### 1.2 Pembuatan Arsitektur Model
Pada proses ini, dilakukan pembuatan arsitektur model BERT dengan menggunakan model *pre-trained* indoBERT yang berasal dari indoBenchmark. IndoBERT merupakan salah satu arsitektur *transformer pre-trained* yang dilatih pada data teks Bahasa Indonesia. Model indoBERT dapat diunduh pada *website* HuggingFace.

##### 1.3 Pelatihan Model
Pada proses ini, data akan digunakan dan dipelajari representasinya oleh model yang telah dibuat. Pada tahap ini, digunakan dua (2) buah *subset* data yaitu data *train* dan data *validation*. Data *train* digunakan untuk pelatihan model sementara data *validation* digunakan untuk mengukur performa model pada data baru/belum pernah dilihat. Data *train* dan data *validation* dilakukan tokenisasi terlebih dahulu menggunakan *tokenizer* bawaan indoBERT sehingga menghasilkan tiga (3) buah nilai baru, yaitu `attention_mask`, `input_ids`, `token_type_ids`. Ketiga nilai ini kemudian akan digunakan dalam proses pelatihan model. Berikut merupakan *hyperparameter* yang digunakan saat pelatihan model.
| No. | Hyperparameter | Nilai                           |
|-----|----------------|---------------------------------|
| 1.  | Optimizer      | Adam                            |
| 2.  | Loss           | Sparse Categorical Crossentropy |
| 3.  | Epochs         | 30                             |
| 4.  | Batch Size     | 16                             |

Hasil dari proses pelatihan model akan dibahas pada tahap evaluasi.