## Evaluation

Pada tahap ini, dilakukan pengukuran/evaluasi performa model dalam memprediksi data *testing* berdasarkan data latih yang telah digunakan pada tahap pelatihan. Pada tahap ini, metriks yang digunakan antara lain ***Loss*** dan ***accuracy***. Berikut merupakan hasil evaluasi model.
| Metriks  | Training | Validation | Testing |
|----------|----------|------------|---------|
| Loss     | 0.0984   | 2.0704     | 2.33    |
| Accuracy | 0.9424   | 0.7224     | 0.72    |

| ![Grafik Evaluasi BiLSTM](https://i.ibb.co/1z8jnqw/grafik-evaluasi-Bi-LSTM.png) |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

Hasil dari tahap pelatihan (*training*) model mencapai akurasi sebesar 94% dan *loss* sebesar 0.09. namun performa model secara keseluruhan menurun pada data validasi, dimana *loss* menurun sebesar 2 poin dan *accuracy* menurun sebesar 22%. Pada tahap *testing*, performa yang dihasilkan mirip dengan performa pada validasi. Hal ini mengindikasikan bahwa model BiLSTM mengalami ***overfitting***.