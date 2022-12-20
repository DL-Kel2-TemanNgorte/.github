# BERT
---
## **Tahapan Penelitian**

Implementasi model BERT dilakukan dengan menggunakan **Indobenchmark**. 

Indobechmark merupakan *base model* yang digunakan untuk membangun model BERT pada proses *natural language processing* berbasis bahasa Indonesia. Indobechmark dilatih dan dievaluasi oleh Bryan Wilie, Karissa Vincentio, Genta Indra Winata, Samuel Cahyawijaya, Xiaohong Li, Zhi Yuan Lim, Sidik Soleman, Rahmad Mahendra, Pascale Fung, Syafri Bahar, dan Ayu Purwarianti.

Model *pre-trained* pada **Indobechmark** dilatih menggunakan *masked language modelling* (MLM) dan *next sentence objective* (NSP).

## **Alur Kerja**

1. **Prepare Dataset**, yaitu proses load dataset yang akan digunakan
2. **Text Preprocessing**, yang dilakukan dengan menghapus data duplikat, mengubah seluruh teks ke huruf kecil dan melakukan operasi regex untuk menghilangkan karakter atau simbol yang tidak diinginkan.
2. **Split into train and test**, untuk memisahkan dataset menjadi data training dan uji untuk mengukur performa akurasi model terhadap data baru.
3. **Tokenisasi**, proses tokenizer dilakukan dengan menggunakan AutoTokenizer, untuk mengubah bentuk teks ke dalam bentuk representasi nilai angka agar dapat dimengerti model untuk proses training.
4. **Proses Pembuatan Model dan Training**, yaitu proses pembuatan model BERT dan proses pelatihan model dengan data yang sudah disiapkan sebelumnya.
5. **Evaluasi**, yaitu proses evaluasi untuk melihat hasil pelatihan berdasarkan nilai train loss dan validation loss dari proses training.

## **Arsitektur Model**

Model diimplementasikan menggunakan IndoBert dari [HuggingFace](https://huggingface.co/). Contoh penggunaan model dapat dilihat pada source code berikut.

```python
from transformers import BertTokenizer, AutoModel
tokenizer = BertTokenizer.from_pretrained("indobenchmark/indobert-base-p1")
model = AutoModel.from_pretrained("indobenchmark/indobert-base-p1")

])
```

### **Implementasi Model**

Model diimplementasikan menggunakan IndoBert dari HuggingFace dengan versi **indobechmark**. Untuk penggunaan lebih jelas dapat dilihat pada source code berikut.

```python
checkpoint = "indobenchmark/indobert-base-p2"
tokenizer = AutoTokenizer.from_pretrained(checkpoint)
model = TFAutoModelForSequenceClassification.from_pretrained(checkpoint, num_labels=num_labels)
])
```

### **Penjelasan Arsitektur**

Model diimplementasikan dengan total 6 lapisan secara berurutan, yang antara lain adalah sebagai berikut.

- checkpoint merupakan deklarasi checkpoint untuk model dengan menggunakan **indobenchmark** yaitu **indobenchmark/indobert-base-p2**
- tokenizer merupakan penerapan tokenizer dengan memanfaatkan AutoTokenizer yang ada pada library
- Pembuatan model dilakukan dengan TFAutoModelForSequenceClassification yang merupakan base model untuk *text classification* yang tersedia pada HuggingFace


## **Evaluasi Model**

Model dilatih dengan dataset yang dibagi menjadi data training dan uji, dengan data **training 80%** dan **data uji 20%**. Training model dilakukan dengan **ukuran batch 16**.

Jumlah epoch yang digunakan pada percobaan adalah **30 epoch**.

Fungsi loss yang digunakan adalah `SparseCategoricalCrossentropy` penggunaaan SparseCategoricalCrossentropy adalah karena target diwakili oleh indeks kategori (yang dapat dimulai dari 0). Misalnya output memiliki bentuk 5x2, berarti kategori yang digunakan adalah 2, dan target berupa vektor 5 dimensi dengan entri 0 atau 1.

Optimizer yang digunakan adalah `Adam` karena merupakan optimizer adaptif yang dapat digunakan pada data sparse dan dapat digunakan tanpa mendefinisikan learning rate.

Metrik keluaran model yang ingin diukur adalah `accuracy`, untuk melihat akurasi hasil dari pelatihan model.

![trainbert](https://user-images.githubusercontent.com/80409196/208689313-69798097-1937-4dd4-87f0-df097c270338.png)


### **Grafik Nilai Loss dan Akurasi BERT**

Evaluasi hasil training model dilakukan dengan melihat nilai loss dan akurasi pada proses training dan validasi dengan data uji. Grafik nilai loss dan akurasi dapat dilihat pada gambar berikut.

 ![download](https://user-images.githubusercontent.com/80409196/208687161-afc3c78f-379c-43fb-a8c9-901b76ac76c6.png)

 Grafik nilai akurasi menunjukkan bahwa nilai akurasi kurang, baik dari validasi maupun train. Akurasi hanya mengalami kenaikan dan penurunan dengan maksimal nilai akurasi 0.25 atau **25%**

 Sedangkan grafik loss menunjukkan bahwa proses training tidak berjalan baik dikarenakan grafik loss yang naik dan turun secara signifikan, dimana seharusnya grafik loss yang baik adalah grafik yang memperlihatkan penurunan nilai loss pada tiap epoch.

### **Hasil Evaluasi Model BERT**

Kesimpulan hasil percobaan BERT dapat dilihat pada tabel berikut.

| Metrik              | Hasil Percobaan 1 |
| :------------------ | ----------------: | 
| Training Loss       |            2,5638 | 
| Validation Loss     |            2,6662 |
| Training Accuracy   |            18,59% |
| Validation Accuracy |            15,20% |  

Hasil evaluasi model menunjukkan bahwa model BERT memiliki performa yang **buruk** dan tidak dapat digunakan sebagai model pada aplikasi.

---
