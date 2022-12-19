## Penjelasan Algoritma LSTM
Algoritma LSTM atau *Long Short Term Memory* merupakan bentuk pengembangan dari *Reccurent Neural Network* yang dapat melakukan prediksi berdasarkan data yang tersimpan dalam jangka waktu panjang sekaligus dapat menghapus data yang sudah tidak perlu digunakan.

![Alt text](https://miro.medium.com/max/828/1*7cMfenu76BZCzdKWCfBABA.webp)

Berdasarkan penelitian yang dilakukan oleh Hochreiter dan Schmidhuber, LSTM terbukti dapat menyelesaikan permasalahan yang cukup kompleks dan belum atau kurang dapat diselesaikan oleh algoritma *reccurent neural network* sebelumnya.

### Gates Pada LSTM 
Terdapat tiga bagian gates yang hanya digunakan pada algoritma Long Short-Term Memory, dimana masing-masing memiliki fungsinya tersendiri. Penjelasan mengenai gates tersebut adalah sebagai berikut. 


#### Forget Gate
Bagian pertama yang dinamakan forget gates merupakan bagian yang akan menentukan apakah suatu informasi akan digunakan kembali atau diingat atau dilupakan

![Alt text](https://i.stack.imgur.com/PB51i.png)

#### Input Gate
Bagian kedua yaitu input gate yang berfungsi untuk mempelajari informasi baru yang diinputkan pada bagian ini

![Alt text](https://i.stack.imgur.com/AuQlH.png)

#### Output Gate
Bagian ketiga yaitu output gate, yaitu bagian yang akan memberikan informasi yang telah diperbarui pada timestamp saat itu ke timestamp berikutnya

![Alt text](https://i0.wp.com/neptune.ai/wp-content/uploads/2022/10/LSTM-network-4.png?resize=605%2C411&ssl=1)

### LSTM untuk Text Classification
  Terdapat banyak algoritma lainnya yang dapat digunakan untuk klasifikasi text seperti SVM atau Neural Network pada umumnya. Akan tetapi sebagian besar algoritma tersebut tidak memberikan hasil yang baik jika dibandingkan dengan LSTM. Hal tersebut karena LSTM mampu untuk mengingat informasi penting dengan efektif.

  Dengan menggunakan LSTM kita dapat menggunakan beberapa string kata untuk mengetahui kelas yang menjadi tempatnya. Hal tersebut sangat membantu saat bekerja dengan natural language processing. Jika kita menggunakan lapisan penyematan dan penyandian yang sesuai di LSTM, model akan dapat mengetahui arti sebenarnya dari string input dan akan memberikan kelas output yang paling akurat. 


---

## Cara Menjalankan Aplikasi

### Projek ini telah dihosting dengan menggunakan **Vercel App**

> **Vercel** merupakan layanan platform cloud yang memungkinkan pengembang menghosting situs web dan layanan web yang diterapkan secara instan, diskalakan secara otomatis, dan bersifat *serverless* dimana pengembang tidak perlu untuk selalu mengawasi dan mengelola server. 

![Alt text](https://miro.medium.com/max/1400/1*pJdLvOAPgVTfESZlSiCTwQ.webp)
---

### Untuk menjalankan aplikasi ini, dapat langsung mengakses link berikut

**[Website Teman Ngorte](https://chatbot-app-three.vercel.app/)**

## Cara Menggunakan Aplikasi
### Login dapat dilakukan dengan menggunakan Username dan Password berikut 
> Username : `yunho`  
Password : `aquagalon`

### Atau langsung dengan menggunakan fitur **Login as Guest**
---
