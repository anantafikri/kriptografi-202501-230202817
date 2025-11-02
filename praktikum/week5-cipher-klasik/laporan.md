# Laporan Praktikum Kriptografi
Minggu ke-: 5  
Topik: Cipher Klasik (Caesar, Vigenère, Transposisi)  
Nama: Muhammad Fikri Ananta  
NIM: 230202817
Kelas: 5Ikra  

---

## 1. Tujuan
1. Menerapkan algoritma Caesar Cipher untuk enkripsi dan dekripsi teks.
2. Menerapkan algoritma Vigenère Cipher dengan variasi kunci.
3. Mengimplementasikan algoritma transposisi sederhana.
4. Menjelaskan kelemahan algoritma kriptografi klasik.

---

## 2. Dasar Teori
Cipher klasik merupakan dasar dari kriptografi modern yang berfokus pada teknik penyandian sederhana untuk mengubah pesan asli (plaintext) menjadi bentuk terenkripsi (ciphertext). Salah satu metode paling awal adalah Cipher Caesar, yang dikembangkan oleh Julius Caesar. Teknik ini menggunakan pergeseran huruf tetap pada alfabet, misalnya setiap huruf digeser tiga posisi ke kanan. Meskipun mudah diimplementasikan, cipher ini lemah terhadap serangan frekuensi karena pola kemunculan huruf masih mudah dikenali.

Selanjutnya, Cipher Vigenère memperkuat konsep substitusi dengan menggunakan kunci berulang untuk menentukan pergeseran setiap huruf. Setiap huruf pada teks disandikan berdasarkan posisi huruf dalam kunci, menghasilkan variasi pergeseran yang lebih kompleks dibandingkan Caesar. Dengan demikian, pola frekuensi menjadi lebih tersebar, membuat analisis kriptografi klasik seperti frequency analysis lebih sulit. Namun, cipher ini tetap dapat dipecahkan dengan metode seperti Kasiski examination atau Index of Coincidence jika panjang kunci diketahui.

Berbeda dengan dua cipher sebelumnya yang menggunakan teknik substitusi, Cipher Transposisi bekerja dengan cara menukar posisi huruf tanpa mengubah identitasnya. Pesan disusun ulang menurut aturan tertentu, seperti kolom atau baris pada matriks. Contohnya, Columnar Transposition Cipher menyusun huruf pesan dalam kolom berdasarkan urutan kunci numerik. Teknik ini mengaburkan struktur pesan tanpa mengganti karakter aslinya, dan sering digunakan dalam kombinasi dengan substitusi untuk meningkatkan keamanan. Meskipun cipher klasik sederhana, pemahaman terhadap prinsipnya sangat penting karena menjadi dasar bagi rancangan algoritma kriptografi modern.

---

## 3. Alat dan Bahan
- Python 3.x  
- Visual Studio Code 
- Git dan akun GitHub  

---

## 4. Langkah Percobaan
1. Membuat file `Cipher_Klasik_Caesar_Vigenère_Transposisi.py` di folder `praktikum/week5-Cipher Klasik (Caesar, Vigenère, Transposisi)`.
2. Menyalin kode program dari panduan praktikum.
3. Menjalankan program dengan perintah `Cipher_Klasik_Caesar_Vigenère_Transposisi.py`.)

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
- Pertanyaan 1: Kelemahan utama dari algoritma Caesar Cipher adalah penggunaan satu kunci pergeseran tetap yang sangat sederhana, sehingga jumlah kemungkinan kuncinya sangat terbatas. Dengan hanya 25 kemungkinan pergeseran pada alfabet Latin, cipher ini dapat dengan mudah dipecahkan menggunakan metode brute force atau frequency analysis. Sementara itu, Vigenère Cipher memang lebih kuat karena menggunakan kunci berulang untuk menentukan pergeseran tiap huruf, tetapi tetap memiliki kelemahan jika kunci yang digunakan terlalu pendek atau berulang. Pola pengulangan ini dapat dianalisis menggunakan metode seperti Kasiski examination atau Index of Coincidence untuk menebak panjang kunci dan mengembalikan pesan asli. 
- Pertanyaan 2: Cipher klasik seperti Caesar dan Vigenère mudah diserang menggunakan analisis frekuensi karena pola distribusi huruf dalam bahasa alami tetap tampak meskipun sudah disandikan. Dalam bahasa Inggris atau Indonesia, misalnya, huruf tertentu seperti “E” atau “A” muncul lebih sering. Teknik analisis frekuensi memanfaatkan pola kemunculan ini dengan membandingkan frekuensi huruf pada ciphertext dengan frekuensi umum dalam bahasa tersebut. Karena cipher klasik tidak mengubah karakteristik statistik bahasa, pola-pola ini tetap terlihat sehingga pesan dapat didekripsi tanpa mengetahui kunci secara langsung.
- Pertanyaan 3: Perbandingan antara cipher substitusi dan cipher transposisi terletak pada cara keduanya mengubah pesan. Cipher substitusi mengganti setiap huruf dengan simbol atau huruf lain, sedangkan cipher transposisi hanya menukar posisi huruf tanpa mengubah identitasnya. Cipher substitusi lebih mudah dipahami dan digunakan, tetapi masih meninggalkan jejak pola frekuensi yang dapat dianalisis. Sebaliknya, cipher transposisi menyamarkan urutan huruf sehingga teks tampak acak, tetapi struktur huruf aslinya masih sama, membuatnya lemah terhadap analisis pola posisi. Dalam praktiknya, kombinasi kedua metode ini sering digunakan untuk meningkatkan keamanan pesan dalam sistem kriptografi klasik.

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
