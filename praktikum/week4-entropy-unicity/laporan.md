# Laporan Praktikum Kriptografi
Minggu ke-: 4 
Topik:  Entropy & Unicity Distance (Evaluasi Kekuatan Kunci dan Brute Force)
Nama: Muhammad Fikri Ananta  
NIM: 230202817  
Kelas:5Ikra 

---

## 1. Tujuan
1.Menyelesaikan perhitungan sederhana terkait entropi kunci.
2.Menggunakan teorema Euler pada contoh perhitungan modular & invers.
3.Menghitung unicity distance untuk ciphertext tertentu.
4.Menganalisis kekuatan kunci berdasarkan entropi dan unicity distance.
5.Mengevaluasi potensi serangan brute force pada kriptosistem sederhana.

---

## 2. Dasar Teori
Entropy (Entropi)
Entropy dalam konteks kriptografi menggambarkan tingkat ketidakpastian atau keacakan dari sebuah kunci kriptografi. Semakin tinggi nilai entropi, semakin sulit bagi penyerang untuk menebak kunci dengan metode brute force karena ruang kunci (key space) menjadi lebih besar dan acak. Entropi biasanya diukur dalam satuan bit; misalnya, kunci 128-bit memiliki entropi maksimum 128 bit jika semua kombinasi kunci memiliki kemungkinan yang sama. Dalam evaluasi kekuatan kunci, entropi menjadi indikator utama seberapa kuat algoritma mampu melindungi data terhadap serangan tebak kunci. Kunci dengan entropi rendah mudah diprediksi, sedangkan kunci dengan entropi tinggi memerlukan waktu dan sumber daya komputasi yang sangat besar untuk dipecahkan.

Unicity Distance (Jarak Keunikan)
Unicity Distance adalah ukuran yang digunakan untuk menentukan berapa banyak ciphertext yang diperlukan agar penyerang dapat secara teoritis mengidentifikasi kunci unik yang digunakan dalam enkripsi. Konsep ini diperkenalkan oleh Claude Shannon dan berkaitan erat dengan redundansi pesan dan ukuran ruang kunci. Jika jumlah ciphertext yang dianalisis melebihi Unicity Distance, maka kunci dapat ditemukan secara unik melalui analisis kriptografi tanpa perlu brute force. Dalam evaluasi kekuatan kunci, semakin besar nilai Unicity Distance, semakin aman sistem karena dibutuhkan lebih banyak data terenkripsi untuk membedakan kunci yang benar dari kemungkinan lainnya. Dengan demikian, baik entropi maupun unicity distance merupakan faktor penting dalam menilai seberapa kuat suatu sistem kriptografi terhadap serangan brute force.
---

## 3. Alat dan Bahan
(- Python 3.x  
- Visual Studio Code / editor lain  
- Git dan akun GitHub  
- Library tambahan (misalnya pycryptodome, jika diperlukan)  )

---

## 4. Langkah Percobaan
(Tuliskan langkah yang dilakukan sesuai instruksi.  
Contoh format:
1. Membuat file `caesar_cipher.py` di folder `praktikum/week2-cryptosystem/src/`.
2. Menyalin kode program dari panduan praktikum.
3. Menjalankan program dengan perintah `python caesar_cipher.py`.)

---

## 5. Source Code
(Salin kode program utama yang dibuat atau dimodifikasi.  
Gunakan blok kode:

```python
# contoh potongan kode
def encrypt(text, key):
    return ...
```
)

---

## 6. Hasil dan Pembahasan
(- Lampirkan screenshot hasil eksekusi program (taruh di folder `screenshots/`).  
- Berikan tabel atau ringkasan hasil uji jika diperlukan.  
- Jelaskan apakah hasil sesuai ekspektasi.  
- Bahas error (jika ada) dan solusinya. 

Hasil eksekusi program Caesar Cipher:

![Hasil Eksekusi](screenshots/output.png)
![Hasil Input](screenshots/input.png)
![Hasil Output](screenshots/output.png)
)

---

## 7. Jawaban Pertanyaan
(Jawab pertanyaan diskusi yang diberikan pada modul.  
- Pertanyaan 1: Nilai entropy dalam konteks kekuatan kunci menunjukkan tingkat keacakan dan ketidakpastian dari kunci kriptografi. Semakin tinggi nilai entropi, semakin sulit bagi penyerang untuk menebak atau memprediksi kunci karena setiap kemungkinan kunci memiliki peluang yang sama untuk digunakan. Dengan kata lain, entropi yang tinggi berarti ruang kunci besar dan tidak teratur, sehingga memperkuat perlindungan terhadap serangan seperti brute force atau tebakan kunci.
- Pertanyaan 2: Unicity distance penting karena menunjukkan jumlah minimum ciphertext yang dibutuhkan agar penyerang dapat secara teoritis menentukan satu kunci unik yang digunakan untuk enkripsi. Jika unicity distance suatu cipher besar, maka dibutuhkan lebih banyak data terenkripsi untuk menemukan kunci yang benar, sehingga cipher tersebut lebih aman. Sebaliknya, jika unicity distance kecil, maka kunci dapat ditebak dengan lebih sedikit ciphertext, yang berarti cipher lebih mudah diserang melalui analisis kriptografi.
- Pertanyaan 3: Meskipun algoritma kriptografi modern dirancang sangat kuat dan memiliki ruang kunci besar, serangan brute force tetap menjadi ancaman karena perkembangan teknologi komputasi yang semakin cepat dan efisien. Dengan munculnya komputasi paralel, GPU, dan bahkan komputer kuantum, waktu yang dibutuhkan untuk mencoba semua kemungkinan kunci dapat berkurang drastis. Selain itu, kunci yang lemah, kesalahan implementasi, atau pemilihan sandi yang tidak acak juga dapat membuat sistem rentan terhadap brute force meskipun algoritmanya sendiri kuat. 
)
---

## 8. Kesimpulan
(Tuliskan kesimpulan singkat (2–3 kalimat) berdasarkan percobaan.  )

---

## 9. Daftar Pustaka
(Cantumkan referensi yang digunakan.  
Contoh:  
- Katz, J., & Lindell, Y. *Introduction to Modern Cryptography*.  
- Stallings, W. *Cryptography and Network Security*.  )

---

## 10. Commit Log
(Tuliskan bukti commit Git yang relevan.  
Contoh:
```
commit abc12345
Author: Nama Mahasiswa <email>
Date:   2025-09-20

    week2-cryptosystem: implementasi Caesar Cipher dan laporan )
```
