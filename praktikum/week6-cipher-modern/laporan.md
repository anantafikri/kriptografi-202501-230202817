# Laporan Praktikum Kriptografi
Minggu ke-: 6  
Topik: Cipher modern 
Nama: Muhammad Fikri Ananta 
NIM: 230202817  
Kelas: 5Ikra  

---

## 1. Tujuan
1.Mengimplementasikan algoritma DES untuk blok data sederhana.
2.Menerapkan algoritma AES dengan panjang kunci 128 bit.
3.Menjelaskan proses pembangkitan kunci publik dan privat pada algoritma RSA.


---

## 2. Dasar Teori
Cipher modern merupakan algoritma kriptografi yang dirancang untuk mengamankan data digital dengan tingkat keamanan lebih tinggi dibanding cipher klasik. DES (Data Encryption Standard) adalah algoritma simetris yang memanfaatkan blok 64-bit dan kunci 56-bit. Meskipun pernah menjadi standar internasional, kini DES dianggap tidak lagi aman karena panjang kuncinya terlalu pendek sehingga rentan terhadap serangan brute force. Namun konsep dasar DES, seperti Feistel Network dan operasi substitusi-permutasi, tetap menjadi fondasi penting dalam banyak algoritma modern.

Sebagai pengganti DES, AES (Advanced Encryption Standard) dikembangkan dengan struktur Substitution-Permutation Network (SPN) yang memberikan keamanan kuat, efisiensi tinggi, dan resistansi terhadap berbagai serangan kriptanalisis modern. AES bekerja dalam ukuran blok 128 bit dengan opsi panjang kunci 128, 192, atau 256 bit. AES menjadi standar global karena cepat digunakan di perangkat kecil maupun sistem berskala besar, serta tahan terhadap brute force berkat ruang kuncinya yang sangat luas.

Berbeda dari DES dan AES, RSA adalah algoritma asimetris yang menggunakan pasangan kunci publik dan privat, berdasarkan kesulitan faktorisasi bilangan besar. RSA banyak digunakan untuk enkripsi kunci, digital signature, dan pertukaran data aman di internet. Kelebihan utamanya adalah tidak memerlukan pertukaran kunci rahasia secara langsung, namun RSA lebih lambat dibanding cipher simetris dan biasanya dipadukan dengan AES dalam sistem hybrid. Ketiga algoritma ini menjadi dasar penting dalam pengamanan data modern, masing-masing dengan peran dan keunggulan berbeda dalam menjaga kerahasiaan serta integritas informasi.

---

## 3. Alat dan Bahan
- Python 3.x  
- Visual Studio Code  
- Git dan akun GitHub  

---

## 4. Langkah Percobaan
(Tuliskan langkah yang dilakukan sesuai instruksi.  
Contoh format:
1. Membuat file `cipher-modern.py` di folder `praktikum/week6-cryptosystem/src/`.
2. Menyalin kode program dari panduan praktikum.
3. Menjalankan program dengan perintah `python cipher-modern.py`.)

---

## 5. Source Code
```python
from Crypto.Cipher import DES
from Crypto.Random import get_random_bytes

key = get_random_bytes(8)  # kunci 64 bit (8 byte)
cipher = DES.new(key, DES.MODE_ECB)

plaintext = b"ABCDEFGH"
ciphertext = cipher.encrypt(plaintext)
print("Ciphertext:", ciphertext)

decipher = DES.new(key, DES.MODE_ECB)
decrypted = decipher.decrypt(ciphertext)
print("Decrypted:", decrypted)

from Crypto.Cipher import AES
from Crypto.Random import get_random_bytes

key = get_random_bytes(16)  # 128 bit key
cipher = AES.new(key, AES.MODE_EAX)

plaintext = b"Modern Cipher AES Example"
ciphertext, tag = cipher.encrypt_and_digest(plaintext)

print("Ciphertext:", ciphertext)

# Dekripsi
cipher_dec = AES.new(key, AES.MODE_EAX, nonce=cipher.nonce)
decrypted = cipher_dec.decrypt(ciphertext)
print("Decrypted:", decrypted.decode())

from Crypto.PublicKey import RSA
from Crypto.Cipher import PKCS1_OAEP

# Generate key pair
key = RSA.generate(2048)
private_key = key
public_key = key.publickey()

# Enkripsi dengan public key
cipher_rsa = PKCS1_OAEP.new(public_key)
plaintext = b"RSA Example"
ciphertext = cipher_rsa.encrypt(plaintext)
print("Ciphertext:", ciphertext)

# Dekripsi dengan private key
decipher_rsa = PKCS1_OAEP.new(private_key)
decrypted = decipher_rsa.decrypt(ciphertext)
print("Decrypted:", decrypted.decode())
```
)

---

## 6. Hasil dan Pembahasan
Berdasarkan hasil eksekusi program cipher modern yang telah  saya lakukan menunjukan keberhasilan yang dapat dilihat hasilnya pada screenshoot.

---

## 7. Jawaban Pertanyaan  
- Pertanyaan 1: Perbedaan mendasar antara DES, AES, dan RSA berada pada jenis kunci serta tingkat keamanannya. DES dan AES adalah algoritma simetris, sehingga menggunakan satu kunci yang sama untuk proses enkripsi dan dekripsi. DES hanya memiliki panjang kunci 56 bit sehingga rentan terhadap brute force, sementara AES jauh lebih aman dengan panjang kunci 128, 192, atau 256 bit. Di sisi lain, RSA merupakan algoritma asimetris yang menggunakan dua kunci berbeda, yaitu kunci publik dan kunci privat, sehingga mekanisme keamanannya berbeda dan tidak bergantung pada satu kunci rahasia seperti sistem simetris. 
- Pertanyaan 2: AES lebih banyak digunakan dibanding DES karena DES sudah tidak aman untuk standar keamanan modern. Panjang kunci DES yang hanya 56 bit terlalu pendek sehingga dapat dipecahkan dalam waktu singkat menggunakan komputasi masa kini. AES dirancang untuk memberikan keamanan yang jauh lebih kuat, performa tinggi, serta efisiensi baik di perangkat kecil maupun sistem besar. Stabilitas desain AES dan ketahanannya terhadap brute force serta berbagai serangan kriptanalisis menjadikannya standar global dalam enkripsi modern.
- Pertanyaan 3: RSA dikategorikan sebagai algoritma asimetris karena menggunakan dua kunci yang berbeda dan saling berpasangan, di mana kunci publik digunakan untuk mengenkripsi data atau memverifikasi tanda tangan, sementara kunci privat digunakan untuk mendekripsi atau membuat tanda tangan digital. Proses pembangkitan kunci RSA bergantung pada sifat matematika bilangan prima besar dan kesulitan memfaktorkan angka yang sangat besar. RSA menghasilkan satu kunci yang dapat dibagikan secara publik dan satu kunci yang harus disimpan secara rahasia, dan keamanan algoritma ini bergantung pada kenyataan bahwa memecahkan pasangan kunci tersebut tanpa mengetahui bilangan prima asalnya sangatlah sulit.
---

## 8. Kesimpulan
Berdasarkan hasil eksekusi program cipher modern yang telah  saya lakukan menunjukan keberhasilan yang dapat dilihat hasilnya pada screenshoot.

---

## 9. Daftar Pustaka
- William Stallings – “Cryptography and Network Security” (7th Edition).  
- Behrouz A. Forouzan – “Cryptography and Network Security.

---

## 10. Commit Log
```
commit abc12345
Author: Muhammad Fikri Ananta <fikriadvan001@gmail.com>
Date:   2025-11-15

    week6-cryptosystem: Cipher-modern dan laporan )
```
