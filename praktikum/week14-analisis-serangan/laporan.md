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
Kriptografi merupakan teknik yang digunakan untuk menjaga kerahasiaan, integritas, dan keaslian data dalam sistem informasi. Salah satu penerapan utama kriptografi adalah pada mekanisme autentikasi, khususnya dalam penyimpanan password. Umumnya, password tidak disimpan dalam bentuk asli (plaintext), melainkan diubah menjadi nilai hash menggunakan algoritma tertentu. Tujuan dari proses hashing ini adalah agar password asli tidak dapat diketahui meskipun data penyimpanan mengalami kebocoran.

Namun, tidak semua algoritma hash memiliki tingkat keamanan yang sama. Algoritma lama seperti MD5 dan SHA-1 dirancang pada saat kemampuan komputasi masih terbatas, sehingga saat ini sudah rentan terhadap serangan brute force, dictionary attack, maupun collision. Kelemahan ini diperparah apabila sistem tidak menerapkan salt atau mekanisme pembatasan percobaan login, sehingga penyerang dapat dengan mudah mencoba berbagai kombinasi password secara otomatis.

Untuk mengatasi permasalahan tersebut, dikembangkan algoritma hash khusus password seperti bcrypt, scrypt, dan Argon2. Algoritma ini dirancang agar proses hashing membutuhkan waktu dan sumber daya yang lebih besar, sehingga tidak efisien untuk diserang menggunakan brute force. Selain pemilihan algoritma yang tepat, keamanan sistem kriptografi juga sangat dipengaruhi oleh implementasi dan konfigurasi yang benar serta pembaruan sistem secara berkala.

---

## 3. Alat dan Bahan
- Python 3.x  
- Visual Studio Code  
- Git dan akun GitHub  

---

## 4. Langkah Percobaan
1. Menentukan password uji dan menghasilkan hash MD5 menggunakan bahasa pemrograman Python.
2. Menyusun daftar password sederhana sebagai wordlist percobaan.
3. Melakukan proses hashing pada setiap password dalam wordlist dan membandingkannya dengan hash target.
4. Menghentikan proses ketika ditemukan hash yang cocok dan mencatat password yang berhasil ditebak.

---

## 5. Source Code

```python
import hashlib

target_hash = "482c811da5d5b4bc6d497ffa98491e38"

wordlist = [
    "admin",
    "123456",
    "password",
    "password123",
    "qwerty",
    "letmein"
]

for word in wordlist:
    hash_word = hashlib.md5(word.encode()).hexdigest()
    if hash_word == target_hash:
        print("Password ditemukan:", word)
        break
    else:
        print("Mencoba:", word)

```


---

## 6. Hasil dan Pembahasan
Pendahuluan
Perkembangan teknologi informasi mendorong penggunaan sistem keamanan berbasis kriptografi dalam berbagai aplikasi, terutama pada mekanisme autentikasi dan perlindungan data. Namun, masih banyak sistem yang menggunakan algoritma atau konfigurasi lama sehingga rentan terhadap serangan. Oleh karena itu, analisis terhadap studi kasus serangan kriptografi nyata perlu dilakukan untuk memahami kelemahan sistem serta menentukan solusi yang lebih aman. Laporan ini membahas sebuah studi kasus serangan brute force dan dictionary attack pada sistem autentikasi yang menggunakan hash MD5. Analisis difokuskan pada identifikasi jenis serangan, evaluasi kelemahan yang ada, serta rekomendasi solusi yang relevan untuk meningkatkan keamanan sistem.

Studi Kasus Serangan Nyata
Deskripsi Kasus
Salah satu kasus yang sering ditemukan adalah penggunaan algoritma hash MD5 untuk menyimpan password pengguna. MD5 dirancang sebagai fungsi hash kriptografi, namun saat ini sudah dianggap tidak aman karena kecepatan komputasinya yang tinggi dan adanya collision. Dalam kasus ini, penyerang memperoleh file database berisi hash password MD5 akibat kebocoran sistem. Dengan memanfaatkan tools brute force dan dictionary attack, penyerang dapat mencoba berbagai kombinasi password hingga menemukan pasangan hash yang sesuai.

Jenis Serangan:
1. Brute Force Attack, Penyerang mencoba semua kemungkinan karakter secara sistematis hingga password ditemukan.
2. Dictionary Attack, Penyerang menggunakan daftar kata sandi umum yang sering dipakai pengguna.

Evaluasi Kelemahan Sistem
Berdasarkan hasil evaluasi, kelemahan sistem ditemukan pada aspek algoritma, implementasi, dan konfigurasi. Dari sisi algoritma, MD5 memiliki panjang hash yang relatif pendek dan tidak dirancang untuk menghadapi serangan brute force modern. Proses hashing yang sangat cepat menyebabkan algoritma ini mudah diproses oleh komputer dengan spesifikasi tinggi maupun GPU, sehingga meningkatkan peluang keberhasilan serangan. Dari sisi implementasi, sistem tidak menerapkan penggunaan salt pada password, sehingga password yang sama akan menghasilkan hash yang identik. Kondisi ini mempermudah penyerang dalam memanfaatkan teknik serangan berbasis tabel seperti rainbow table. Selain itu, pada aspek konfigurasi, tidak diterapkannya pembatasan jumlah percobaan login maupun mekanisme penguncian akun menyebabkan serangan brute force dapat dilakukan secara berulang tanpa adanya hambatan berarti.

Rekomendasi Solusi
Untuk meningkatkan keamanan sistem, disarankan mengganti algoritma MD5 dengan algoritma yang lebih aman dan dirancang khusus untuk penyimpanan password, seperti bcrypt, scrypt, atau Argon2. Algoritma tersebut memiliki mekanisme adaptive cost yang membuat proses hashing lebih lambat dan membutuhkan sumber daya lebih besar, sehingga menyulitkan serangan brute force. Selain itu, sistem perlu menerapkan peningkatan mekanisme keamanan dengan menambahkan salt unik pada setiap password, menerapkan pembatasan percobaan login serta penguncian akun setelah beberapa kali kegagalan, dan menggunakan autentikasi multi-faktor sebagai lapisan keamanan tambahan. Dengan penerapan solusi tersebut, sistem akan menjadi lebih tahan terhadap serangan brute force dan dictionary attack, serta mampu mengurangi risiko kebocoran data pengguna secara signifikan.

---

## 7. Jawaban Pertanyaan
- Pertanyaan 1: Banyak sistem lama dirancang pada masa ketika kemampuan komputasi masih terbatas, sehingga mekanisme keamanannya tidak disiapkan untuk menghadapi daya komputasi modern. Akibatnya, sistem tersebut sering menggunakan kata sandi pendek, algoritma hash lama (misalnya tanpa salt atau key stretching), serta tidak memiliki pembatasan percobaan login (rate limiting). Selain itu, faktor manusia juga berperan besar, seperti penggunaan kata sandi lemah dan kebiasaan tidak memperbarui sistem karena alasan kompatibilitas atau biaya. 
- Pertanyaan 2: Kelemahan algoritma adalah masalah yang berasal dari desain matematis atau konsep dasar algoritma kriptografi itu sendiri. Jika algoritmanya sudah terbukti lemah, maka siapa pun yang menggunakannya akan berisiko, meskipun diimplementasikan dengan benar. Sebaliknya, kelemahan implementasi terjadi ketika algoritma yang sebenarnya kuat diterapkan secara keliru, misalnya menggunakan parameter yang salah, manajemen kunci yang buruk, atau kesalahan pemrograman. Dalam kasus ini, algoritmanya aman secara teori, tetapi praktik penerapannya membuat sistem menjadi rentan.
- Pertanyaan 3: Organisasi perlu menerapkan pendekatan berkelanjutan, bukan solusi sekali jadi. Langkah penting meliputi penggunaan algoritma dan standar kriptografi yang direkomendasikan saat ini, pembaruan sistem secara berkala, serta audit dan pengujian keamanan rutin. Selain itu, organisasi sebaiknya menerapkan prinsip crypto agility, yaitu kemampuan untuk mengganti algoritma atau parameter kriptografi dengan cepat jika ditemukan kelemahan baru. Edukasi sumber daya manusia dan penerapan kebijakan keamanan yang ketat juga menjadi faktor kunci untuk menjaga keamanan jangka panjang.

---

## 8. Kesimpulan
Berdasarkan analisis yang dilakukan, dapat disimpulkan bahwa penggunaan algoritma kriptografi yang sudah usang seperti MD5 berpotensi menimbulkan risiko keamanan serius. Kelemahan tidak hanya berasal dari algoritma, tetapi juga dari implementasi dan konfigurasi sistem. Oleh karena itu, penerapan algoritma modern serta mekanisme keamanan tambahan sangat diperlukan untuk menjaga kerahasiaan dan integritas data.

---

## 9. Daftar Pustaka 
- Stallings, W. (2017). Cryptography and Network Security: Principles and Practice (7th ed.). Pearson Education.  
- Kahn Academy. (n.d.). Cryptographic hash functions.

---

## 10. Commit Log
```
commit abc12345
Author: Muhammad Fikri Ananta <fikriadvan001@gmail.com>
Date:   2026-01-05

    week14-cryptosystem: analisis serangan dan laporan )
```
