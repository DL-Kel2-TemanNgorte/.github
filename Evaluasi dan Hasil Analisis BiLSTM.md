### Evaluation
Pada tahap ini, dilakukan pengukuran/evaluasi performa model dalam memprediksi data validasi berdasarkan data latih yang telah digunakan pada tahap pelatihan. Pada tahap ini, metriks yang digunakan antara lain ***Loss***, ***accuracy***, ***balanced recall***, ***balanced precision***, dan ***balanced f1 score***. Berikut merupakan hasil evaluasi model.
| Metriks            | Training | Validation |
|--------------------|----------|------------|
| Loss               | 0.0506   | 1.6496     |
| Accuracy           | 0.9759   | 0.7526     |
| Balanced Recall    | 0.9746   | 0.5085     |
| Balanced Precision | 0.9771   | 0.5276     |
| Balanced F1 Score  | 0.9759   | 0.5174     |

| ![Grafik Evaluasi BiLSTM](https://raw.githubusercontent.com/DL-Kel2-TemanNgorte/Machine-Learning/main/assets/grafik%20evaluasi%20BiLSTM.png?token=GHSAT0AAAAAAB3GYHOL7YI7FZKWZYK323OSY5ALCGA) |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

Hasil dari tahap pelatihan (*training*) model mencapai rata-rata 95% untuk seluruh metriks. namun performa model secara keseluruhan menurun pada data validasi, dimana *loss* menurun sebesar 1.1 poin, *accuracy* menurun sebesar 22%, dan rata-rata *recall*, *precision*, dan *F1-score* menurutn sebesar 45%. Hal ini mengindikasikan bahwa model BiLSTM mengalami ***overfitting***.