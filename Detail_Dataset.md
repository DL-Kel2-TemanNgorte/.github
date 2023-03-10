## **Dataset**
Dataset yang digunakan bersumber dari berbagai *website* antara lain sebagai berikut.
- Kaggle ([https://www.kaggle.com/datasets/narendrageek/mental-health-faq-for-chatbot](https://www.kaggle.com/datasets/narendrageek/mental-health-faq-for-chatbot))
- Alodokter ([https://www.alodokter.com/komunitas/topic-tag/kesehatan-mental](https://www.alodokter.com/komunitas/topic-tag/kesehatan-mental))
- Hellosehat ([https://hellosehat.com/community/kesehatan-mental/](https://hellosehat.com/community/kesehatan-mental/))
- SehatQ ([https://www.sehatq.com/forum/psikologi?](https://www.sehatq.com/forum/psikologi?))
- GitHub ([https://raw.githubusercontent.com/bhumikabhatia/mental-health-chatbot-Miklal/main/model/20200325_counsel_chat.csv](https://raw.githubusercontent.com/bhumikabhatia/mental-health-chatbot-Miklal/main/model/20200325_counsel_chat.csv))

Data dari sumber-sumber tersebut dikumpulkan menjadi satu *file* berformat .csv dengan 3 kolom yakni pertanyaan, jawaban, dan label. Data yang didapatkan dari Kaggle dan GitHub telah memiliki label, sehingga data yang berasal dari *website* lainnya dilabeli secara manual. Data yang berbahasa Inggris juga diterjemahkan secara manual. Total data yang diperoleh berjumlah 1981 sampel dengan 18 kelas yaitu salam, depresi, keluarga, hubungan, kecemasan, konseling_fundamental, harga_diri, trauma, cari_bantuan, perubahan_perilaku, definisi, penyalahgunaan_zat, manajemen_emosi, tips_pengobatan, diagnosis_dini, peningkatan_pola_tidur, profesional_yang_benar, dan bye_thanks. Adapun persebaran data pada masing-masing labelnya sebagai berikut.

| No.  | Label                    | Jumlah      |
|------|--------------------------|-------------|
| 1.   | salam                    | 11          |
| 2.   | depresi                  | 359         |
| 3.   | keluarga                 | 334         |
| 4.   | hubungan                 | 328         |
| 5.   | kecemasan                | 249         |
| 6.   | konseling_fundamental    | 240         |
| 7.   | harga_diri               | 83          |
| 8.   | trauma                   | 66          |
| 9.   | cari_bantuan             | 58          |
| 10.  | perubahan_perilaku       | 51          |
| 11.  | definisi                 | 50          |
| 12.  | penyalahgunaan_zat       | 40          |
| 13.  | manajemen_emosi          | 38          |
| 14.  | tips_pengobatan          | 23          |
| 15.  | diagnosis_dini           | 22          |
| 16.  | peningkatan_pola_tidur   | 10          |
| 17.  | profesional_yang_benar   | 9           |
| 18.  | bye_thanks               | 10          |
