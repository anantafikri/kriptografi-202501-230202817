# Laporan Praktikum Kriptografi
Minggu ke-: 12 
Topik: Aplikasi TLS & E-commerce  
Nama: Muhammad Fikri Ananta  
NIM: 230202817  
Kelas: 5Ikra  

---

## 1. Tujuan
1. Menganalisis penggunaan kriptografi pada email dan SSL/TLS.
2. Menjelaskan enkripsi dalam transaksi e-commerce.
3. Mengevaluasi isu etika & privasi dalam penggunaan kriptografi di kehidupan sehari-har

---

## 2. Dasar Teori
Transport Layer Security (TLS) merupakan protokol kriptografi yang digunakan untuk mengamankan komunikasi data melalui jaringan komputer, khususnya internet. TLS bekerja dengan mengenkripsi data yang dikirimkan antara klien dan server sehingga menjaga kerahasiaan, integritas, dan keaslian informasi. Dalam penerapannya, TLS memanfaatkan kombinasi kriptografi kunci publik dan kunci simetris, di mana kunci publik digunakan pada tahap awal komunikasi untuk pertukaran kunci, sedangkan kunci simetris digunakan untuk proses enkripsi data selanjutnya karena lebih efisien.

Sertifikat digital memiliki peran penting dalam mekanisme TLS karena berfungsi untuk memverifikasi identitas server yang diakses oleh pengguna. Sertifikat ini diterbitkan oleh Certificate Authority (CA) yang tepercaya dan berisi informasi mengenai identitas pemilik sertifikat serta kunci publik yang digunakan. Dengan adanya sertifikat digital, risiko serangan seperti penyamaran server atau Man-in-the-Middle dapat diminimalkan.

Dalam konteks email dan e-commerce, TLS menjadi fondasi utama dalam melindungi data sensitif seperti kredensial login, informasi pribadi, dan detail transaksi. Selain meningkatkan keamanan teknis, penggunaan TLS juga berkontribusi terhadap perlindungan privasi pengguna. Namun demikian, penerapan kriptografi perlu diimbangi dengan pertimbangan etika dan hukum agar keamanan data tidak bertentangan dengan hak privasi dan kebutuhan pengawasan yang sah.

---

## 3. Alat dan Bahan
- Python 3.x  
- Visual Studio Code   
- Git dan akun GitHub  

---

## 4. Langkah Percobaan
1. Menyiapkan lingkungan praktikum dengan memastikan koneksi internet aktif dan browser (Chrome atau Firefox) terpasang.
2. Mengakses website e-commerce yang menggunakan HTTPS, kemudian memeriksa informasi sertifikat SSL/TLS melalui ikon keamanan pada browser.
3. Membandingkan akses website yang menggunakan HTTPS dengan HTTP untuk melihat perbedaan tingkat keamanan.
4. Mengidentifikasi isu etika dan privasi terkait penggunaan kriptografi dalam komunikasi digital.
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
A. Analisis SSL/TLS pada Website E-commerce
Pengujian dilakukan menggunakan browser Google Chrome terhadap beberapa website e-commerce populer, seperti Tokopedia dan Shopee. Berdasarkan hasil observasi, website-website tersebut telah menerapkan protokol HTTPS yang menandakan penggunaan SSL/TLS sebagai mekanisme pengamanan komunikasi data. Informasi sertifikat digital menunjukkan bahwa sertifikat diterbitkan oleh Certificate Authority (CA) yang tepercaya, memiliki masa berlaku yang masih aktif, serta menggunakan algoritma enkripsi modern seperti RSA atau ECDSA yang dikombinasikan dengan algoritma simetris AES. Penerapan HTTPS ini memastikan bahwa data yang dikirimkan antara pengguna dan server telah terenkripsi, sehingga mampu mengurangi risiko penyadapan dan akses oleh pihak yang tidak berwenang.

B. Perbandingan HTTP dan HTTPS
Website dengan HTTP tidak memiliki lapisan enkripsi, sehingga data dapat dibaca atau dimodifikasi oleh pihak ketiga. Sebaliknya, HTTPS dengan TLS memberikan perlindungan terhadap penyadapan dan manipulasi data, serta meningkatkan kepercayaan pengguna.

C. Studi Kasus Penerapan TLS pada E-Commerce
Pada transaksi e-commerce, TLS berperan penting saat proses login, pengisian data pribadi, dan pembayaran. Enkripsi memastikan bahwa informasi sensitif seperti username, password, dan detail pembayaran tidak dapat diakses oleh pihak lain. Jika TLS tidak digunakan, transaksi online berisiko terhadap serangan Man-in-the-Middle, di mana penyerang dapat menyadap atau mengubah data yang sedang dikirim. Oleh karena itu, TLS menjadi komponen wajib dalam sistem e-commerce modern.

D. nalisis Etika dan Privasi
Penggunaan email terenkripsi seperti PGP atau S/MIME bertujuan melindungi isi pesan dari akses pihak yang tidak berwenang. Namun, dalam lingkungan organisasi muncul dilema antara perlindungan privasi karyawan dan kebutuhan audit keamanan, sehingga diperlukan kebijakan yang jelas dan transparan. Dari sisi etika, perusahaan dan pemerintah memiliki kepentingan dalam pengawasan komunikasi terenkripsi, tetapi tetap harus menghormati hak privasi pengguna. Oleh karena itu, penerapan kriptografi perlu dilakukan secara seimbang antara keamanan, privasi, dan kepentingan hukum.

---

## 7. Jawaban Pertanyaan 
- Pertanyaan 1: HTTP tidak menggunakan enkripsi sehingga data dapat disadap, sedangkan HTTPS menggunakan TLS untuk mengamankan komunikasi data.
- Pertanyaan 2: Sertifikat digital berfungsi untuk memverifikasi identitas server dan mencegah pengguna terhubung ke server palsu.
- Pertanyaan 3: Kriptografi melindungi privasi pengguna, namun dapat menimbulkan tantangan hukum dan etika terkait pengawasan serta penegakan hukum.  

---

## 8. Kesimpulan
Berdasarkan hasil praktikum, dapat disimpulkan bahwa SSL/TLS memiliki peran penting dalam menjaga keamanan komunikasi digital, khususnya pada email dan e-commerce. Selain meningkatkan keamanan data, penerapan TLS juga menimbulkan tantangan etika dan privasi yang perlu dikelola melalui kebijakan yang tepat.

---

## 9. Daftar Pustaka
- Rescorla, E. (2018). The Transport Layer Security (TLS) Protocol Version 1.3. RFC 8446. 
- Stalling, W. (2017). Cryptography and Network Security: Principles and Practice (7th ed.). Pearson Education.

---

## 10. Commit Log
```
commit abc12345
Author: Muhammad Fikri Ananta <fikriadvan001@gmail.com>
Date:   2026-01-05

    week12-cryptosystem: Aplikasi TLS & E-commerce dan laporan 
```
