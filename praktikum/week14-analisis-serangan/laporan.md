# Laporan Praktikum Kriptografi
Minggu ke-: 14
Topik: Analisis Serangan 
Nama: Muhammad Fikri Ananta  
NIM: 230202817  
Kelas: 5Ikra 

---

## 1. Tujuan
1. Mengidentifikasi jenis serangan pada sistem informasi nyata.
2. Mengevaluasi kelemahan algoritma kriptografi yang digunakan.
3. Memberikan rekomendasi algoritma kriptografi yang sesuai untuk perbaikan keamanan.

---

## 2. Dasar Teori
(Ringkas teori relevan (cukup 2–3 paragraf).  
Contoh: definisi cipher klasik, konsep modular aritmetika, dll.  )

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
- Pertanyaan 1: Banyak sistem lama dirancang pada masa ketika kemampuan komputasi masih terbatas, sehingga mekanisme keamanannya tidak disiapkan untuk menghadapi daya komputasi modern. Akibatnya, sistem tersebut sering menggunakan kata sandi pendek, algoritma hash lama (misalnya tanpa salt atau key stretching), serta tidak memiliki pembatasan percobaan login (rate limiting). Selain itu, faktor manusia juga berperan besar, seperti penggunaan kata sandi lemah dan kebiasaan tidak memperbarui sistem karena alasan kompatibilitas atau biaya. 
- Pertanyaan 2: Kelemahan algoritma adalah masalah yang berasal dari desain matematis atau konsep dasar algoritma kriptografi itu sendiri. Jika algoritmanya sudah terbukti lemah, maka siapa pun yang menggunakannya akan berisiko, meskipun diimplementasikan dengan benar. Sebaliknya, kelemahan implementasi terjadi ketika algoritma yang sebenarnya kuat diterapkan secara keliru, misalnya menggunakan parameter yang salah, manajemen kunci yang buruk, atau kesalahan pemrograman. Dalam kasus ini, algoritmanya aman secara teori, tetapi praktik penerapannya membuat sistem menjadi rentan.
- Pertanyaan 3: Organisasi perlu menerapkan pendekatan berkelanjutan, bukan solusi sekali jadi. Langkah penting meliputi penggunaan algoritma dan standar kriptografi yang direkomendasikan saat ini, pembaruan sistem secara berkala, serta audit dan pengujian keamanan rutin. Selain itu, organisasi sebaiknya menerapkan prinsip crypto agility, yaitu kemampuan untuk mengganti algoritma atau parameter kriptografi dengan cepat jika ditemukan kelemahan baru. Edukasi sumber daya manusia dan penerapan kebijakan keamanan yang ketat juga menjadi faktor kunci untuk menjaga keamanan jangka panjang.

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
