# Laporan Praktikum Kriptografi
Minggu ke-: 7  
Topik: diffie-hellman  
Nama: Muhammad Fikri Ananta  
NIM: 230202817  
Kelas: 5Ikra  

---

## 1. Tujuan
1.Melakukan simulasi protokol Diffie-Hellman untuk pertukaran kunci publik.
2.Menjelaskan mekanisme pertukaran kunci rahasia menggunakan bilangan prima dan logaritma diskrit.
3.Menganalisis potensi serangan pada protokol Diffie-Hellman (termasuk serangan Man-in-the-Middle / MITM).

---

## 2. Dasar Teori
Diffie–Hellman adalah protokol pertukaran kunci yang memungkinkan dua pihak menghasilkan kunci rahasia bersama melalui jaringan yang tidak aman tanpa perlu berbagi kunci sebelumnya. Dasarnya adalah aritmetika modular dan kesulitan menyelesaikan Discrete Logarithm Problem (DLP), sehingga meskipun nilai publik yang dipertukarkan dapat dilihat oleh siapa saja, kunci rahasia tetap sulit ditebak.

Protokol ini bekerja dengan cara kedua pihak menyepakati bilangan prima besar dan generator sebagai parameter publik. Masing-masing memilih kunci privat acak kemudian menghitung kunci publiknya. Setelah saling bertukar nilai publik, keduanya dapat menghitung kunci rahasia yang sama melalui operasi perpangkatan modular. Penyerang yang mengintip hanya melihat nilai publik, tetapi tidak dapat memperoleh kunci rahasia tanpa memecahkan DLP.

Diffie–Hellman sendiri tidak menyediakan autentikasi, sehingga rentan terhadap serangan Man-in-the-Middle bila digunakan tanpa mekanisme tambahan. Dalam praktik modern, protokol ini sering dikombinasikan dengan tanda tangan digital atau digunakan dalam bentuk yang lebih efisien seperti Elliptic Curve Diffie–Hellman (ECDH) yang menawarkan keamanan tinggi dengan ukuran kunci lebih kecil.

---

## 3. Alat dan Bahan
- Python  
- Visual Studio Code   
- Git dan akun GitHub  

---

## 4. Langkah Percobaan

1. Membuat file `diffe_hellan.py` di folder `praktikum/week7-cryptosystem/src/`.
2. Menyalin kode program dari panduan praktikum.
3. Menjalankan program dengan perintah `python diffe_hellman.py`.)

---

## 5. Source Code
```python
import random

# parameter umum (disepakati publik)
p = 23  # bilangan prima
g = 5   # generator

# private key masing-masing pihak
a = random.randint(1, p-1)  # secret Alice
b = random.randint(1, p-1)  # secret Bob

# public key
A = pow(g, a, p)
B = pow(g, b, p)

# exchange public key
shared_secret_A = pow(B, a, p)
shared_secret_B = pow(A, b, p)

print("Kunci bersama Alice :", shared_secret_A)
print("Kunci bersama Bob   :", shared_secret_B)

```

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
- Pertanyaan 1: Diffie–Hellman memungkinkan pertukaran kunci melalui saluran publik karena keamanan protokol ini bergantung pada Discrete Logarithm Problem (DLP) yang sangat sulit dipecahkan secara komputasional. Meski dua pihak saling bertukar nilai publik yang dapat dilihat siapa saja, kunci rahasia tetap aman karena untuk menghitungnya penyerang harus menemukan eksponen privat dari operasi perpangkatan modular, sesuatu yang hampir mustahil dilakukan pada bilangan berukuran besar. Dengan begitu, dua pihak dapat menghasilkan kunci bersama tanpa perlu mengirimkan kunci itu secara langsung. 
- Pertanyaan 2: Kelemahan utama Diffie–Hellman murni adalah tidak adanya autentikasi. Protokol ini hanya menghasilkan kunci bersama tetapi tidak memverifikasi identitas pihak yang terlibat. Akibatnya, penyerang dapat melakukan Man-in-the-Middle (MITM) dengan berpura-pura menjadi masing-masing pihak, lalu membangun dua kunci berbeda dengan kedua korban tanpa terdeteksi. Selain itu, versi implementasi tertentu juga dapat rentan jika parameter seperti bilangan prima tidak cukup besar atau dipilih secara lemah.
- pertanyaan 3: Untuk mencegah serangan MITM, Diffie–Hellman harus digabungkan dengan mekanisme autentikasi. Cara yang umum digunakan adalah menandatangani nilai publik dengan tanda tangan digital (misalnya RSA, ECDSA), menggunakan sertifikat digital dari CA seperti pada TLS/HTTPS, atau menerapkan authenticated Diffie–Hellman seperti Station-to-Station (STS) protocol. Dengan cara ini, pihak yang bertukar kunci dapat memastikan bahwa nilai publik benar-benar berasal dari lawan komunikasi yang sah, sehingga penyerang tidak bisa menyusup di tengah proses pertukaran.

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
