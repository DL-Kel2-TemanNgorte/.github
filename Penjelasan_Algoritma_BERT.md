## Penjelasan Algoritma BERT
Algoritma BERT atau *Bidirectional Encoder Representations from Transformers* adalah teknik berbasis jaringan saraf untuk *pre-training* Natural Language. BERT dirancang untuk membantu komputer memahami makna bahasa ambigu dalam teks dengan menggunakan teks di sekitarnya untuk membangun konteks. Kerangka kerja BERT telah dilatih sebelumnya menggunakan teks dari Wikipedia dan dapat disesuaikan dengan kumpulan data pertanyaan dan jawaban.

![GoogleBert_1920](https://user-images.githubusercontent.com/76557114/208561287-ad16340c-16e7-481a-a7fc-7ef75d94daab.jpg)

Model ini diusulkan dan diterbitkan oleh Jacob Devlin dan rekan-rekannya dari Google Research pada tahun 2018. Selanjutnya di tahun 2019, Google mengumumkan bahwa BERT mulai diimplementasikan di mesin pencarinya. Kemudian pada akhir tahun 2020, BERT digunakan di hampir semua kueri pencarian bahasa Inggris. BERT juga sudah bersifat open-source dari Google pada November 2018. Artinya, siapa pun dapat menggunakan BERT untuk melatih sistem pemrosesan bahasa mereka sendiri untuk menjawab pertanyaan atau tugas lain.


### Cara Kerja Algoritma BERT
BERT memanfaatkan Transformer, mekanisme *attention* yang mempelajari hubungan kontekstual antara kata (atau sub-kata) dalam sebuah teks. Berbeda dengan model terarah, yang membaca input teks secara berurutan (kiri ke kanan atau kanan ke kiri), *encoder* Transformer membaca seluruh urutan kata sekaligus. Oleh sebab itu, BERT dianggap dua arah, meskipun akan lebih akurat untuk mengatakan bahwa itu tidak terarah. Karakteristik ini memungkinkan model mempelajari konteks sebuah kata berdasarkan seluruh lingkungannya (kiri dan kanan kata).

BERT juga merupakan teknik NLP pertama yang hanya mengandalkan mekanisme *self-attention*, yang dimungkinkan oleh *bidirectional* Transformer di pusat desain BERT. Ini penting karena sering kali sebuah kata dapat berubah artinya saat kalimat berkembang. Setiap kata yang ditambahkan menambah arti keseluruhan dari kata yang difokuskan oleh algoritma NLP. Semakin banyak kata yang hadir secara total dalam setiap kalimat atau frase, semakin ambigu kata yang menjadi fokus. BERT memperhitungkan makna yang diperbesar dengan membaca dua arah, memperhitungkan efek dari semua kata lain dalam sebuah kalimat pada kata fokus dan menghilangkan momentum kiri-ke-kanan yang mencondongkan kata-kata menuju makna tertentu saat kalimat berkembang.

![whatis-bert-h](https://user-images.githubusercontent.com/76557114/208569645-a6062700-7d13-4e1f-94e7-fa88ae368c26.png)

Misalnya, pada gambar di atas, BERT menentukan kata sebelumnya dalam kalimat yang dirujuk oleh kata "*is*", dan kemudian menggunakan mekanisme perhatiannya untuk menimbang opsi. Kata dengan skor terhitung tertinggi dianggap asosiasi yang benar (yaitu, "*is*" mengacu pada "*animal*", bukan "*he*"). Jika frasa ini adalah permintaan pencarian, hasilnya akan mencerminkan pemahaman yang lebih halus dan lebih tepat yang dicapai BERT ini.


### Pemanfaatan BERT
BERT unggul dan dapat dimanfaatkan untuk beberapa tugas berikut.

#### Pembangkit bahasa berbasis *sequence-to-sequence*, seperti:
- *Question answering*
- *Abstract summarization*
- *Sentence prediction*
- *Conversational response generation*

#### Natural Language Understanding, seperti:
- *Polysemy and coreference resolution*
- *Word sense disambiguation*
- *Natural language inference*
- *Sentiment classification*
