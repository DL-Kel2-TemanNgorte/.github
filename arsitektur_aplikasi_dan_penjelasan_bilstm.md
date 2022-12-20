## Penjelasan Algoritma BiLSTM
Bidirectional Long Short – Term Memory Neural Network (BiLSTM) merupakan salah satu varian dari Long Short Term Memory yang paling sering digunakan. Input forward dan input backward adalah 2 jenis masukan yang dimasukkan ke dalam arsitektur Bidirectional Long Short Term Memory. Output dari arsitektur ini biasnya digabungkan jadi satu. Dengan layer arsitektur ini, model bisa menekuni data masa lalu (past) dan data masa mendatang (future) untuk setiap sekuen input.

![Alt text](https://data03.123doks.com/thumbv2/123dok/003/825/3825207/28.892.325.612.235.427/gambar-arsitektur-bilstm-sumber-graves-amp-schmidhuber.webp)

Bidirectional LSTM memanfaatkan informasi sebelumnya dan informasi setelahnya dengan memproses data dari dua arah. Forward layer berfungsi untuk merepresentasikan informasi sebelumnya, dan backward layer berfungsi untuk merepresentasikan informasi setelahnya.

![Alt text](https://docplayer.info/docs-images/113/206254265/images/2-1.jpg)

Gambar diatas merupakan arsitektur hidden layer BiLSTM. Setiap hidden layer keluaran unit pada layer bawah dan atas disatukan hingga membentuk nilai fitur yang lebih panjang dari pada LSTM biasa. Karena nilai fitur pada BiLSTM lebih panjang , maka informasi yang akan diproses pada proses selanjutnya yaitu feed forward neural akan mengklasifikasikan dengan lebih detail.

![arsitektur model bilstm](https://user-images.githubusercontent.com/62200309/208637445-1611a5dc-8940-4165-a90a-9a99c171289e.png)

Gambar diatas adalah arsitektur dari BiLSTM yang merupakan gabungan dari dua LSTM arah maju dan arah mundur. Terdapat hidden layer juga yang terhubung dari LSTM maju dan LSTM mundur. 

Dengan adanya hidden layer dua arah ini yang saling berlawanan maka model dapat memahami data dari depan dan belakang, sehingga proses pelatihan akan lebih memahami data pada time series. BiLSTM akan sangat berguna dalam hal pelatihan sekuensial apabila bisa mengakses dari informasi sebelum dan
sesudahnya. Jika LSTM hanya bisa mengakses informasi dari masa lalu saja, tetapi informasi masa mendatang tidak diketahui. BiLSTM bisa menjadi solusi untuk memecahkan masalah tersebut.

## Arsitektur Aplikasi Teman Ngorte

![Arsitektur Aplikasi Teman Ngorte](https://user-images.githubusercontent.com/62200309/208637731-815af47e-0080-44d6-a7cc-32b6f845ff9a.png)

Arsitektur dari chatbot Teman Ngorte terdiri dari 2 bagian yaitu Front End dan Backend. Pada bagian Fron End menggunakan framework React.js dan juga tailwind CSS untuk membuat user interface dari aplikasi chatbot. Bagian Front End dari chatbot ini kemudian dideploy di platform Vercel agar bisa diakses melalui internet. Pada bagian Back End menggunakan framework Flask dan bahasa pemrograman python untuk memproses segala logic dibelakang layar aplikasi chatbot teman ngorte dan membuat API yang digunakan untuk komunikasi data antara Front End dan Back End. Database yang digunakan pada aplikasi chatbot teman ngorte yaitu MySQL Database yang dideploy di pltform Railway. Aplikasi chatbot teman ngorte ini menggunakan model deep learning BiLSTM yang di buat menggunakan library Tensorflow, dimana model ini digunakan untuk memproses respons yang diberikan oleh chatbot terhadap chat atau pertanyaan dari pengguna.  Bagian Back End ini dideploy menggunakan platform cloud dari Google yang Bernama Google Cloud Platform dengan layanan Cloud Run dan Docker untuk mendeploy aplikasi Back End dari chatbot Temen Ngorte. Komunikasi antara bagian Front End dengan Back End menggunakan JSON API, dimana Bagian Front End mengirim HTTP Request ke bagian Back End, lalu pada  bagian Back End akan memproses HTTP Request tersebut dan mengirim hasil prosesnya dalam bentuk JSON API ke bagian Front End.

## Alasan BiLSTM lebih unggul dari pada model lain
Model BiLSTM yang dibuat, memiliki akurasi yang lebih tinggi dari pada model lain yang telah dibuat seperti LSTM dan BERT. Pada tahap pelatihan (training) model BiLSTM menghasilkan akurasi sebesar 94% dan loss sebesar 0.09,  jika dibandingkan dengan model lain yang telah dibuat seperti LSTM dimana menghasilkan akurasi sebesar 92% dan loss sebesar 0.1509, dan juga model BERT dimana menghasilkan akurasi sebesar 88% dan loss sebesar 0.3181. Hal ini membuktikan bahwa model BiLSTM lebih unggul dari pada model LSTM dan BERT.
