## BiLSTM
---
Proses pembuatan model BiLSTM (*Bidirectional Long-Short Term Memory*) dilakukan dalam 3 tahap, yaitu *training*, *testing*, dan *evaluation*, Berikut merupakan penjelasan masing-masing tahap.
#### 1. Training
Pada tahap *training*, beberapa proses yang dilakukan antara lain **persiapan data latih**, **pembuatan arsitektur model**, **pelatihan model**.

##### 1.1 Persiapan Data Latih
Pada tahap persiapan data latih, seluruh *dataset* yang digunakan akan dipecah (*split*) menjadi beberapa *subset*, diantaranya data *train* (latih) dan data *validation* (validasi). Data *train* dan data *validation* dibuat dengan melakukan *split* terhadap *dataset* dengan menggunakan fungsi `train_test_split` dari *library* sklearn. Seluruh *dataset* dipecah menjadi dua (2) buah *subset*, yaitu *data train* dan *data validation* dengan proporsi 80% dan 20%. Data *train* kemudian digunakan pada tahap *training* dan data *validation* digunakan pada tahap *evaluation*.

##### 1.2 Pembuatan Arsitektur Model
Pada tahap ini, dilakukan pembuatan arsitektur model BiLSTM dengan metode *sequential* menggunakan *library* Keras. Berikut merupakan arsitektur model BiLSTM yang dibuat.

| ![Arsitektur BiLSTM](../Machine-Learning/assets/arsitektur%20BiLSTM.png) |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
Gambar di atas merupakan arsitektur dari model BiLSTM yang telah dibuat. Arsitektur pertama yaitu lapisan input yang berukuran 50 kolom. Input tersebut kemudian mengirimkan data pada lapisan ***Embedding*** dengan *vocabulary* maksimum berjumlah 2500 dan dimensi *embedding* berukuran 50. Hasil *embedding* kemudian akan dikirimkan pada lapisan ***SpatialDropout1D***. Setelah itu, data akan dikirimkan kepada lapisan BiLSTM pertama dengan jumlah unit sebesar 128 dan *activation function* ReLu. Lapisan berikutnya adalah lapisan BiLSTM kedua (*stacked*) dengan jumlah unit yang sama yaitu 128. Setelah data melalui lapisan BiLSTM, kemudian akan dikirim pada lapisan ***Dense*** (neuron biasa) dengan jumlah unit sebesar 64. Hasil dari lapisan ini kemudian akan dikirimkan pada lapisan terakhir (*output layer*) dengan total *output* sebesar 18.

##### 1.3 Pelatihan Model
Pada tahap ini, data akan digunakan dan dipelajari representasinya oleh model yang telah dibuat. Pada tahap ini, digunakan dua (2) buah *subset* data yaitu data *train* dan data *validation*. Data *train* digunakan untuk pelatihan model sementara data *validation* digunakan untuk mengukur performa model pada data baru/belum pernah dilihat. Berikut merupakan konfigurasi dari tahap pelatihan model.
| No. | Hyperparameter | Nilai                           |
|-----|----------------|---------------------------------|
| 1.  | Optimizer      | Adam                            |
| 2.  | Loss           | Sparse Categorical Crossentropy |
| 3.  | Epochs         | 100                             |
| 4.  | Batch Size     | 128                             |

#### 2. Evaluation
Pada tahap ini, dilakukan pengukuran/evaluasi performa model dalam memprediksi data validasi berdasarkan data latih yang telah digunakan pada tahap pelatihan. Pada tahap ini, metriks yang digunakan antara lain ***Loss***, ***accuracy***, ***balanced recall***, ***balanced precision***, dan ***balanced f1 score***. Berikut merupakan hasil evaluasi model.
| Metriks            | Training | Validation |
|--------------------|----------|------------|
| Loss               | 0.0506   | 1.6496     |
| Accuracy           | 0.9759   | 0.7526     |
| Balanced Recall    | 0.9746   | 0.5085     |
| Balanced Precision | 0.9771   | 0.5276     |
| Balanced F1 Score  | 0.9759   | 0.5174     |

| ![Grafik Evaluasi BiLSTM](../Machine-Learning/assets/grafik%20evaluasi%20BiLSTM.png) |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
Hasil dari tahap pelatihan (*training*) model mencapai rata-rata 95% untuk seluruh metriks. namun performa model secara keseluruhan menurun pada data validasi, dimana *loss* menurun sebesar 1.1 poin, *accuracy* menurun sebesar 22%, dan rata-rata *recall*, *precision*, dan *F1-score* menurutn sebesar 45%. Hal ini mengindikasikan bahwa model BiLSTM mengalami ***overfitting***.