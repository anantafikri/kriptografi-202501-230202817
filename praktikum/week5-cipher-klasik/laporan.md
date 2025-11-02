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
```python
def caesar_encrypt(plaintext, key):
    result = ""
    for char in plaintext:
        if char.isalpha():
            shift = 65 if char.isupper() else 97
            result += chr((ord(char) - shift + key) % 26 + shift)
        else:
            result += char
    return result

def caesar_decrypt(ciphertext, key):
    return caesar_encrypt(ciphertext, -key)

# Contoh uji
msg = "CLASSIC CIPHER"
key = 3
enc = caesar_encrypt(msg, key)
dec = caesar_decrypt(enc, key)
print("Plaintext :", msg)
print("Ciphertext:", enc)
print("Decrypted :", dec)

def vigenere_encrypt(plaintext, key):
    result = []
    key = key.lower()
    key_index = 0
    for char in plaintext:
        if char.isalpha():
            shift = ord(key[key_index % len(key)]) - 97
            base = 65 if char.isupper() else 97
            result.append(chr((ord(char) - base + shift) % 26 + base))
            key_index += 1
        else:
            result.append(char)
    return "".join(result)

def vigenere_decrypt(ciphertext, key):
    result = []
    key = key.lower()
    key_index = 0
    for char in ciphertext:
        if char.isalpha():
            shift = ord(key[key_index % len(key)]) - 97
            base = 65 if char.isupper() else 97
            result.append(chr((ord(char) - base - shift) % 26 + base))
            key_index += 1
        else:
            result.append(char)
    return "".join(result)

# Contoh uji
msg = "KRIPTOGRAFI"
key = "KEY"
enc = vigenere_encrypt(msg, key)
dec = vigenere_decrypt(enc, key)
print("Plaintext :", msg)
print("Ciphertext:", enc)
print("Decrypted :", dec)

def vigenere_encrypt(plaintext, key):
    result = []
    key = key.lower()
    key_index = 0
    for char in plaintext:
        if char.isalpha():
            shift = ord(key[key_index % len(key)]) - 97
            base = 65 if char.isupper() else 97
            result.append(chr((ord(char) - base + shift) % 26 + base))
            key_index += 1
        else:
            result.append(char)
    return "".join(result)

def vigenere_decrypt(ciphertext, key):
    result = []
    key = key.lower()
    key_index = 0
    for char in ciphertext:
        if char.isalpha():
            shift = ord(key[key_index % len(key)]) - 97
            base = 65 if char.isupper() else 97
            result.append(chr((ord(char) - base - shift) % 26 + base))
            key_index += 1
        else:
            result.append(char)
    return "".join(result)

# Contoh uji
msg = "KRIPTOGRAFI"
key = "KEY"
enc = vigenere_encrypt(msg, key)
dec = vigenere_decrypt(enc, key)
print("Plaintext :", msg)
print("Ciphertext:", enc)
print("Decrypted :", dec)
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
Berdasarkan percobaan kode pemrograman chipher klasik yang terdapat pada materi yang kemudian di salin ke vs code berjalan sesuai dengan yang diharapkan 

---

## 9. Daftar Pustaka 
- N., P., & Mira. (2022). Analysis of Classical Cryptographic Algorithms Caesar Cipher Vigenere Cipher and Hill Cipher – Study Literature. Journal of Information Technology, 2(1), 23-30. https://doi.org/10.46229/jifotech.v2i1.387. 
- O.E. Omolara, A.I. Oludare, & S.E. Abdulahi. (n.d.). Developing a Modified Hybrid Caesar Cipher and Vigenere Cipher for Secure Data Communication. Computer Engineering and Intelligent Systems.

---

## 10. Commit Log
commit abc12345
Author: Muhammad Fikri Ananta <fikriadvan001@gmail.com>
Date:   2025-11-02

    
```
