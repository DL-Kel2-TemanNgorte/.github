## Penjelasan Algoritma LSTM
Algoritma LSTM atau *Long Short Term Memory* merupakan bentuk pengembangan dari *Reccurent Neural Network* yang dapat melakukan prediksi berdasarkan data yang tersimpan dalam jangka waktu panjang sekaligus dapat menghapus data yang sudah tidak perlu digunakan.

![Alt text](https://miro.medium.com/max/828/1*7cMfenu76BZCzdKWCfBABA.webp)

Berdasarkan penelitian yang dilakukan oleh **Hochreiter dan Schmidhuber** di tahun 1997 yang kemudian menjadi cikal bakal arsitektur LSTM modern, LSTM terbukti dapat menyelesaikan permasalahan yang cukup kompleks dan belum atau kurang dapat diselesaikan oleh algoritma *reccurent* lainnya.

### Gates Pada LSTM 
Terdapat tiga bagian gates yang hanya digunakan pada algoritma *Long Short-Term Memory*, dimana masing-masing memiliki fungsinya tersendiri. Penjelasan mengenai gates tersebut adalah sebagai berikut. 

#### Forget Gate
Bagian pertama yang dinamakan forget gates merupakan bagian yang akan menentukan apakah suatu informasi akan digunakan kembali atau diingat atau dilupakan.

![Alt text](http://colah.github.io/posts/2015-08-Understanding-LSTMs/img/LSTM3-focus-f.png)

#### Input Gate
Bagian kedua yaitu input gate yang berfungsi untuk mempelajari informasi baru yang diinputkan pada bagian ini

![Alt text](http://colah.github.io/posts/2015-08-Understanding-LSTMs/img/LSTM3-focus-i.png)

#### Output Gate
Bagian ketiga yaitu output gate, yaitu bagian yang akan memberikan informasi yang telah diperbarui pada timestamp saat itu ke timestamp berikutnya

![Alt text](http://colah.github.io/posts/2015-08-Understanding-LSTMs/img/LSTM3-focus-o.png)

### LSTM untuk Text Classification
  Terdapat banyak algoritma lainnya yang dapat digunakan untuk klasifikasi text seperti SVM atau Neural Network pada umumnya. Akan tetapi sebagian besar algoritma tersebut tidak memberikan hasil yang baik jika dibandingkan dengan LSTM. Hal tersebut karena LSTM mampu untuk mengingat informasi penting dengan efektif.

  Dengan menggunakan LSTM kita dapat menggunakan beberapa string kata untuk mengetahui kelas yang menjadi tempatnya. Hal tersebut sangat membantu dalam proses pengerjaan *natural language processing*. Jika menggunakan lapisan penyematan dan penyandian yang sesuai di LSTM, model akan dapat mengetahui arti sebenarnya dari *string* input dan akan memberikan kelas *output* yang paling akurat. 


---

## Cara Menjalankan Aplikasi
### Projek ini telah dihosting dengan menggunakan **Vercel App**

> **Vercel** merupakan layanan platform cloud yang memungkinkan pengembang menghosting situs web dan layanan web yang diterapkan secara instan, diskalakan secara otomatis, dan bersifat *serverless* dimana pengembang tidak perlu untuk selalu mengawasi dan mengelola server. 

![Alt text](https://miro.medium.com/max/1400/1*pJdLvOAPgVTfESZlSiCTwQ.webp)
---

### Untuk menjalankan aplikasi ini, dapat langsung mengakses link berikut

**[Website Teman Ngorte](https://chatbot-app-three.vercel.app/)**

## Cara Menggunakan Aplikasi
Aplikasi ini dapat digunakan dengan **2 cara login** yaitu sebagai berikut

### 1. Login dapat dilakukan dengan menggunakan Username dan Password

#### Step 1 : Login
Masukkan Username dan Password berikut

> Username : `pencurhat`  
Password : `curhatdong`

![test login](https://user-images.githubusercontent.com/80409196/208438023-3bac8870-89dd-43e9-b416-ba4f9fbbc215.png)

Pastikan Username dan Password sesuai, apabila tidak maka akan muncul **alert** yang menandakan Username atau Password salah

- alert **username** salah
![alertusername](https://user-images.githubusercontent.com/80409196/208442008-1daad28e-f63c-4039-9140-661214856cb2.png)


- alert **password** salah
![alertpass](https://user-images.githubusercontent.com/80409196/208442026-dd7bf761-8459-4c2b-8c07-929bae71782e.png)


#### Step 2 : 
Apabila kombinasi Username dan Password sudah sesuai, klik Pada tombol Login
![test login2](https://user-images.githubusercontent.com/80409196/208438176-cc6e56e5-4dc1-400f-bbec-e4300ee3f8f3.png)

#### Step 3 : 
Klik Pada Tombol "Yuk Curhat!"
![yukcurhat](https://user-images.githubusercontent.com/80409196/208438298-63e6d08c-d5a2-4763-9754-1d2b9c910bd8.png)

#### Step 4 : 
Sampaikan keluh kesahmu pada TimpalBot! TimpalBot akan menjadi teman curhatmu!
![chat](https://user-images.githubusercontent.com/80409196/208438371-13137646-9b63-42ba-9a56-7a0d02452b60.png)

#### Step 5 : 
Untuk kembali atau menutup bubble chat, dapat dilakukan dengan klik pada tombol **back**
![back2](https://user-images.githubusercontent.com/80409196/208438451-e1dbc417-52b4-4acc-9915-766822c8f7d6.png)

#### Step 6 : 
Untuk keluar dari aplikasi, dapat dilakukan dengan klik pada tombol **logout**
![logoutweb3](https://user-images.githubusercontent.com/80409196/208438521-643ba0df-1f4e-48ed-bfcd-6d44eb20feac.png)

#### Step 7 : 
Untuk konfirmasi logout, dapat dilakukan dengan klik **OK** pada pop up konfirmasi logout
![notif logout2](https://user-images.githubusercontent.com/80409196/208438706-d46ab361-9dd4-46ab-8f20-b4a31f76607e.png)

### 2. Menggunakan **Login as Guest**
Untuk menggunakan Login as Guest, pengguna **tidak perlu** memasukkan **username dan password**

#### Step 1 : 
Klik Pada Tombol Login as Guest
![loginguest](https://user-images.githubusercontent.com/80409196/208438979-8fa47924-92ca-44f4-ade1-b944d3d57b34.png)

#### Step 2 : 
Klik Pada Tombol "Yuk Curhat!"
![welcomeguest](https://user-images.githubusercontent.com/80409196/208439334-12eb3602-5317-4451-a7ce-48913a0a8f30.png)

#### Step 3 : 
Sampaikan keluh kesahmu pada TimpalBot! TimpalBot akan menjadi teman curhatmu!
![chat](https://user-images.githubusercontent.com/80409196/208438371-13137646-9b63-42ba-9a56-7a0d02452b60.png)

#### Step 4 : 
Untuk kembali atau menutup bubble chat, dapat dilakukan dengan klik pada tombol **back**
![back2](https://user-images.githubusercontent.com/80409196/208438451-e1dbc417-52b4-4acc-9915-766822c8f7d6.png)

#### Step 5 : 
Untuk keluar dari aplikasi, dapat dilakukan dengan klik pada tombol **logout**
![backguest2](https://user-images.githubusercontent.com/80409196/208440411-70f801fb-4330-4e5c-9fc1-f1c15e409132.png)

#### Step 6 : 
Untuk konfirmasi logout, dapat dilakukan dengan klik **OK** pada pop up konfirmasi logout
![logoutguest2](https://user-images.githubusercontent.com/80409196/208440696-4991064c-3104-46cc-a536-f64f2a20471d.png)

---
