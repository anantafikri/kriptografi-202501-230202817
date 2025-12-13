# Laporan Praktikum Kriptografi
Minggu ke-: 9  
Topik: Digital Signature  
Nama: Muhammad Fikri Ananta 
NIM: 230202817  
Kelas: 5Ikra  

---

## 1. Tujuan
1. Mengimplementasikan tanda tangan digital menggunakan algoritma RSA/DSA.
2. Memverifikasi keaslian tanda tangan digital.
3. Menjelaskan manfaat tanda tangan digital dalam otentikasi pesan dan integritas data.

---

## 2. Dasar Teori
Digital signature dalam kriptografi adalah mekanisme keamanan yang digunakan untuk menjamin keaslian (authentication), keutuhan data (integrity), dan non-repudiation pada informasi digital. Tanda tangan digital bekerja dengan memanfaatkan kriptografi kunci publik (asimetris), di mana pengirim memiliki sepasang kunci yaitu kunci privat dan kunci publik. Kunci privat digunakan untuk membuat tanda tangan digital terhadap suatu pesan atau dokumen, sedangkan kunci publik digunakan oleh penerima untuk memverifikasi keabsahan tanda tangan tersebut.

Proses digital signature umumnya diawali dengan pembuatan nilai hash dari pesan menggunakan fungsi hash kriptografi seperti SHA-256. Nilai hash ini kemudian dienkripsi menggunakan kunci privat pengirim, sehingga menghasilkan tanda tangan digital. Saat pesan diterima, penerima akan mendekripsi tanda tangan menggunakan kunci publik pengirim dan membandingkan hasilnya dengan hash pesan yang dihitung ulang. Jika kedua nilai hash sama, maka pesan dipastikan tidak mengalami perubahan dan benar-benar berasal dari pengirim yang sah.

Digital signature banyak digunakan dalam berbagai sistem keamanan modern, seperti transaksi perbankan elektronik, sertifikat digital, email aman, dan dokumen hukum digital. Dengan adanya digital signature, pihak pengirim tidak dapat menyangkal telah mengirim pesan tersebut, sehingga memberikan jaminan hukum dan kepercayaan dalam komunikasi digital. Hal ini menjadikan digital signature sebagai komponen penting dalam penerapan keamanan informasi di era teknologi saat ini.

---

## 3. Alat dan Bahan 
- Visual Studio Code   
- Git dan akun GitHub  

---

## 4. Langkah Percobaan
1. Membuat tiga file `digital signature.py` di folder `praktikum/week9-cryptosystem/src/`.
2. Menyalin kode program dari panduan praktikum.
3. Menjalankan program dengan perintah `digital signature.py`

---

## 5. Source Code

```python
from Crypto.PublicKey import RSA
from Crypto.Signature import pkcs1_15
from Crypto.Hash import SHA256

# Generate pasangan kunci RSA
key = RSA.generate(2048)
private_key = key
public_key = key.publickey()

# Pesan yang akan ditandatangani
message = b"Hello, ini pesan penting."
h = SHA256.new(message)

# Buat tanda tangan dengan private key
signature = pkcs1_15.new(private_key).sign(h)
print("Signature:", signature.hex())

try:
    pkcs1_15.new(public_key).verify(h, signature)
    print("Verifikasi berhasil: tanda tangan valid.")
except (ValueError, TypeError):
    print("Verifikasi gagal: tanda tangan tidak valid.")

# Modifikasi pesan
fake_message = b"Hello, ini pesan palsu."
h_fake = SHA256.new(fake_message)

try:
    pkcs1_15.new(public_key).verify(h_fake, signature)
    print("Verifikasi berhasil (seharusnya gagal).")
except (ValueError, TypeError):
    print("Verifikasi gagal: tanda tangan tidak cocok dengan pesan.")
```

---

## 6. Hasil dan Pembahasan
Berdasarkan hasil eksekusi dari ketiga kode pemrograman mengenai digital signature menunjukan keberhasilan dan tidak ada kegagalan sesuai dengan hasil yang tertera pada folder screenshoot.

---

## 7. Jawaban Pertanyaan
(Jawab pertanyaan diskusi yang diberikan pada modul.  
- Pertanyaan 1: Perbedaan utama antara enkripsi RSA dan tanda tangan digital RSA terletak pada tujuan dan penggunaan kuncinya. Enkripsi RSA digunakan untuk menjaga kerahasiaan (confidentiality) pesan, di mana pesan dienkripsi menggunakan kunci publik penerima dan hanya dapat didekripsi dengan kunci privat penerima. Sebaliknya, tanda tangan digital RSA bertujuan untuk menjamin keaslian dan integritas pesan, di mana pengirim membuat tanda tangan dengan kunci privatnya sendiri, lalu penerima memverifikasinya menggunakan kunci publik pengirim. 
- Pertanyaan 2: Tanda tangan digital menjamin integritas dan otentikasi pesan karena proses penandatanganan melibatkan fungsi hash dan kunci privat pengirim. Nilai hash dari pesan akan berubah jika isi pesan dimodifikasi, sehingga tanda tangan menjadi tidak valid dan integritas pesan dapat terdeteksi. Selain itu, karena hanya pemilik kunci privat yang dapat membuat tanda tangan digital, penerima dapat memastikan identitas pengirim, sehingga otentikasi pesan dapat terjamin.
- Pertanyaan 3: Peran Certificate Authority (CA) dalam sistem tanda tangan digital modern adalah sebagai pihak tepercaya yang bertugas memverifikasi identitas pemilik kunci publik dan menerbitkan sertifikat digital. Sertifikat ini menghubungkan identitas pemilik dengan kunci publiknya, sehingga penerima pesan dapat yakin bahwa kunci publik tersebut benar milik pihak yang bersangkutan. Dengan adanya CA, risiko pemalsuan identitas dan serangan man-in-the-middle dapat diminimalkan dalam komunikasi digital.
)
---

## 8. Kesimpulan
Berdasarkan hasil eksekusi dari ketiga kode pemrograman mengenai digital signature menunjukan keberhasilan dan tidak ada kegagalan.

---

## 9. Daftar Pustaka
- William Stallings, Cryptography and Network Security: Principles and Practice, Pearson Education. 
- NIST (National Institute of Standards and Technology), Digital Signature Standard (DSS) – FIPS PUB 186.
- Bruce Schneier, Applied Cryptography: Protocols, Algorithms, and Source Code in C, Wiley.
---

## 10. Commit Log
(Tuliskan bukti commit Git yang relevan.  
Contoh:
```
commit abc12345
Author: Muhammad Fikri Ananta <fikriadvan001@gmail.com>
Date:   2025-12-13

    week3-cryptosystem: digital signature dan laporan )
```
