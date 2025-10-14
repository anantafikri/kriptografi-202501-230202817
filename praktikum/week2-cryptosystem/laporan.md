# Laporan Praktikum Kriptografi
Minggu ke-: 2  
Topik: Cryptosystem  
Nama: Muhammad Fikri Ananta 
NIM: 230202817  
Kelas: 5IKRA  

---

## 1. Tujuan
(Tuliskan tujuan pembelajaran praktikum sesuai modul.)
1. Mengidentifikasi komponen dasar kriptosistem (plaintext, ciphertext, kunci, algoritma).
2. Menggambarkan proses enkripsi dan dekripsi sederhana.
3. Mengklasifikasikan jenis kriptosistem (simetris dan asimetris).
---

## 2. Dasar Teori
Kriptografi terbagi menjadi dua jenis utama, yaitu kriptografi simetris dan kriptografi asimetris. Kriptografi simetris menggunakan satu kunci yang sama untuk proses enkripsi dan dekripsi, sehingga baik pengirim maupun penerima harus memiliki kunci yang identik. Kelebihan sistem ini adalah prosesnya yang lebih cepat dan efisien, karena algoritma yang digunakan relatif sederhana. Namun, kelemahannya terletak pada keamanan distribusi kunci, sebab jika kunci jatuh ke tangan pihak yang tidak berwenang, maka seluruh pesan dapat terbaca. Contoh algoritma kriptografi simetris antara lain DES (Data Encryption Standard) dan AES (Advanced Encryption Standard). DES merupakan algoritma lama yang menggunakan kunci 56-bit dan kini dianggap kurang aman, sedangkan AES lebih modern dengan panjang kunci 128-bit, 192-bit, atau 256-bit, serta banyak digunakan pada sistem keamanan data saat ini.
Berbeda dengan itu, kriptografi asimetris menggunakan dua kunci berbeda, yaitu kunci publik untuk enkripsi dan kunci privat untuk dekripsi. Sistem ini lebih aman karena tidak memerlukan pengiriman kunci rahasia, sehingga mengatasi kelemahan distribusi kunci pada sistem simetris. Kriptografi asimetris juga memungkinkan penerapan tanda tangan digital dan otentikasi identitas, sehingga banyak digunakan dalam sistem komunikasi yang memerlukan keamanan tinggi. Contoh algoritma asimetris adalah RSA (Rivest-Shamir-Adleman) dan ECC (Elliptic Curve Cryptography). RSA menggunakan bilangan prima besar sebagai dasar keamanannya dan banyak diterapkan pada HTTPS atau email terenkripsi, sedangkan ECC lebih efisien karena memberikan tingkat keamanan tinggi dengan ukuran kunci yang lebih kecil, cocok untuk perangkat modern seperti ponsel dan IoT.
---

## 3. Alat dan Bahan
(- Python 3.x  
- Visual Studio Code / editor lain  
- Git dan akun GitHub  
- Excalidraw

---

## 4. Langkah Percobaan
(Tuliskan langkah yang dilakukan sesuai instruksi.  
Contoh format:
1. Membuat file `cesar_ciper.py` 
2. Menyalin kode program dari panduan praktikum dan menambahkan kode pemrograman.
3. Menjalankan program dengan perintah `python cesar_ciper.py`.)

---

## 5. Source Code
(Salin kode program utama yang dibuat atau dimodifikasi.  
Gunakan blok kode:

```python
def caesar_encryption():
    alpha_upper = "ABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZ"
    alpha_lower = "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"
    symbolic = "~!@#$%^&*()-=+_`}{[]|':;><,./?"
    integer = "1234567890"
    
    shift = int(input("Enter shift value 0-25: "))
    text = input("Enter plain text: ")
    encrypted_text = ""
    
    for s in text:
        if s.isupper():
            s_index = alpha_upper.find(s)
            new_index = (s_index + shift) % 26
            new_char = alpha_upper[new_index]
            encrypted_text += new_char
        elif s.islower():
            s_index = alpha_lower.find(s)
            new_index = (s_index + shift) % 26
            new_char = alpha_lower[new_index]
            encrypted_text += new_char
        elif s == " ":
            encrypted_text += " "
        elif s.isnumeric():
            encrypted_text += s
        else:
            s_index = symbolic.find(s)
            new_char = symbolic[s_index]
            encrypted_text += new_char

    print("Encryption result:", encrypted_text)

def caesar_decryption():
    alpha_upper = "ABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZ"
    alpha_lower = "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"
    symbolic = "~!@#$%^&*()-=+_`}{[]|':;><,./?"
    integer = "1234567890"
    
    text = input("Enter plain text: ")
    
    for shift in range(26):
        decrypted_text = ""
        for s in text:
            if s.isupper():
                s_index = alpha_upper.find(s)
                new_index = (s_index - shift) % 26
                new_char = alpha_upper[new_index]
                decrypted_text += new_char
            elif s.islower():
                s_index = alpha_lower.find(s)
                new_index = (s_index - shift) % 26
                new_char = alpha_lower[new_index]
                decrypted_text += new_char
            elif s == " ":
                decrypted_text += " "
            elif s.isnumeric():
                decrypted_text += s
            else:
                s_index = symbolic.find(s)
                new_char = symbolic[s_index]
                decrypted_text += new_char

        print("Decryption result with shift", shift, ":", decrypted_text)

def caesar_cipher():
    print("Menu")
    print("0. Exit")
    print("1. Encryption")
    print("2. Decryption")
    option = input("Enter your choice: ")

    if option == "1":
        caesar_encryption()
    elif option == "2":
        caesar_decryption()
    elif option == "0":
        return
    else:
        print("Invalid choice, please try again.")
        caesar_cipher()

    caesar_cipher()

caesar_cipher()
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
- Pertanyaan 1: Kriptosistem merupakan suatu sistem yang digunakan untuk mengamankan pesan agar tidak dapat dibaca oleh pihak yang tidak berhak. Dalam sebuah kriptosistem terdapat beberapa komponen utama yang saling berhubungan. Komponen pertama adalah plaintext, yaitu pesan asli yang masih dapat dibaca dan belum mengalami proses enkripsi. Kedua adalah ciphertext, yaitu hasil dari proses enkripsi yang berupa teks acak dan tidak dapat dimengerti tanpa proses dekripsi. Komponen ketiga adalah algoritma enkripsi, yaitu prosedur atau rumus matematika yang digunakan untuk mengubah plaintext menjadi ciphertext. Selanjutnya terdapat algoritma dekripsi, yaitu proses kebalikan dari enkripsi yang berfungsi untuk mengubah ciphertext kembali menjadi plaintext agar pesan dapat dipahami oleh penerima. Terakhir, terdapat kunci (key) yang berperan penting dalam proses enkripsi dan dekripsi. Kunci ini bisa berupa satu kunci yang sama (pada kriptografi simetris) atau sepasang kunci publik dan privat (pada kriptografi asimetris).
- Pertanyaan 2: Kriptografi simetris dan asimetris memiliki karakteristik, kelebihan, dan kelemahan masing-masing. Pada sistem simetris, proses enkripsi dan dekripsi menggunakan kunci yang sama. Kelebihan dari sistem ini adalah prosesnya lebih cepat dan efisien, karena algoritma yang digunakan relatif sederhana dan membutuhkan sumber daya komputasi yang lebih sedikit. Namun, sistem simetris memiliki kelemahan utama, yaitu pada keamanan distribusi kunci, sebab kunci harus dibagikan kepada penerima terlebih dahulu, dan jika kunci tersebut jatuh ke tangan orang yang tidak berwenang, maka pesan dapat dengan mudah dibaca.
Sementara itu, sistem asimetris menggunakan dua kunci yang berbeda, yaitu kunci publik untuk enkripsi dan kunci privat untuk dekripsi. Kelebihan sistem ini adalah keamanan distribusi kunci yang lebih baik, karena kunci publik dapat dibagikan secara bebas tanpa mengancam keamanan pesan. Namun, kelemahannya terletak pada kecepatan proses yang lebih lambat dan perhitungan matematis yang lebih kompleks dibandingkan sistem simetris.
- Pertanyaan 3: Distribusi kunci merupakan masalah utama dalam kriptografi simetris karena sistem ini hanya menggunakan satu kunci yang sama untuk proses enkripsi dan dekripsi. Agar komunikasi dapat berlangsung, kunci tersebut harus dibagikan terlebih dahulu kepada pihak penerima. Proses pengiriman atau pembagian kunci inilah yang menjadi titik lemah, karena jika kunci tersebut dicegat oleh pihak ketiga, maka seluruh pesan yang terenkripsi dapat dengan mudah dibuka dan dibaca. Selain itu, dalam sistem dengan banyak pengguna, jumlah kunci yang harus dikelola akan meningkat secara signifikan, sehingga menimbulkan masalah skalabilitas dan keamanan. Oleh karena itu, distribusi kunci menjadi salah satu tantangan terbesar dalam penerapan kriptografi simetris di dunia nyata.
)
---

## 8. Kesimpulan
Berdasarkan percobaan yang saya lakukan menunjukan keberhasilan kode program yang sudah dijalankan.

---

## 9. Daftar Pustaka
[(Cantumkan referensi yang digunakan.  
Contoh:  
- https://share.google/u8iXPUBRQRvvCJP9R)

---

## 10. Commit Log
(Tuliskan bukti commit Git yang relevan.  
Contoh:
```
commit abc12345
Author: Muhammad Fikri Ananta<fikriadvan001@gmail.com>
Date:   2025-10-14

    week2-cryptosystem: implementasi Caesar Cipher dan laporan )
```
