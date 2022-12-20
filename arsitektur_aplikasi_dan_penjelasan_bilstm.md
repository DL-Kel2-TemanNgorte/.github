## Penjelasan Algoritma BiLSTM
Bidirectional Long Short – Term Memory Neural Network (BiLSTM) merupakan salah satu varian dari Long Short Term Memory yang paling sering digunakan. Input forward dan input backward adalah 2 jenis masukan yang dimasukkan ke dalam arsitektur Bidirectional Long Short Term Memory. Output dari arsitektur ini biasnya digabungkan jadi satu. Dengan layer arsitektur ini, model bisa menekuni data masa lalu (past) dan data masa mendatang (future) untuk setiap sekuen input.

![Alt text](https://data03.123doks.com/thumbv2/123dok/003/825/3825207/28.892.325.612.235.427/gambar-arsitektur-bilstm-sumber-graves-amp-schmidhuber.webp)

Bidirectional LSTM memanfaatkan informasi sebelumnya dan informasi setelahnya dengan memproses data dari dua arah. Forward layer berfungsi untuk merepresentasikan informasi sebelumnya, dan backward layer berfungsi untuk merepresentasikan informasi setelahnya.

![Alt text](https://docplayer.info/docs-images/113/206254265/images/2-1.jpg)

Gambar diatas merupakan arsitektur hidden layer BiLSTM. Setiap hidden layer keluaran unit pada layer bawah dan atas disatukan hingga membentuk nilai fitur yang lebih panjang dari pada LSTM biasa. Karena nilai fitur pada BiLSTM lebih panjang , maka informasi yang akan diproses pada proses selanjutnya yaitu feed forward neural akan mengklasifikasikan dengan lebih detail.

![Alt text](https://previews.dropbox.com/p/thumb/ABywJH-PwlZHtIG9o9X-jVOD-zNbu8GC1Xfz5el265I3cpGJUhXkvMofoTN1oOBY8pTKwqvpMW5EuV0X9SCyo36cQRCBURYlelVGCn7WF1CPUYiFfq48JClJIelhA0fkCuE1hIEdKNS68F2gIHvK93lflloYf_v3fwSietP_FL3BC9SDnMZ80mB95-UwWBfTZ4ywCuzkXa6zlp1dzeXL7PPfcEd_S22_0vVd5W7fwLhcbpOi312TYI2hp_ciE3s_ZNzygJ3aK8Wqyzl9pkv2OaBkmay_FbVYBYmbvEzO8ptfZLQCV-pion43J-OU0KWZMIaR9uKiY9at62eh6fPebdF4HqYzEt4WQiJRRLJnLWtFha91F32tvWbc3S8uU-KWOkk/p.png)

Gambar diatas adalah arsitektur dari BiLSTM yang merupakan gabungan dari dua LSTM arah maju dan arah mundur. Terdapat hidden layer juga yang terhubung dari LSTM maju dan LSTM mundur. 

Dengan adanya hidden layer dua arah ini yang saling berlawanan maka model dapat memahami data dari depan dan belakang, sehingga proses pelatihan akan lebih memahami data pada time series. BiLSTM akan sangat berguna dalam hal pelatihan sekuensial apabila bisa mengakses dari informasi sebelum dan
sesudahnya. Jika LSTM hanya bisa mengakses informasi dari masa lalu saja, tetapi informasi masa mendatang tidak diketahui. BiLSTM bisa menjadi solusi untuk memecahkan masalah tersebut.


