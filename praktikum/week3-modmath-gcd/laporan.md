# Laporan Praktikum Kriptografi
Minggu ke-: 3 
Topik: Modular Math 
Nama: Muhammad Fikri Ananta 
NIM: 230202817 
Kelas: 5Ikra  

---

## 1. Tujuan
1. Menyelesaikan operasi aritmetika modular.
2. Menentukan bilangan prima dan menghitung GCD (Greatest Common Divisor).
3. Menerapkan logaritma diskrit sederhana dalam simulasi kriptografi.

---

## 2. Dasar Teori
**Teori Relevan**

Cipher klasik merupakan metode kriptografi tradisional yang digunakan untuk menyamarkan pesan agar tidak mudah dibaca oleh pihak yang tidak berwenang. Pada dasarnya, cipher klasik bekerja dengan cara mengganti (substitusi) atau menukar (transposisi) huruf-huruf dalam pesan asli (plaintext) menjadi bentuk terenkripsi (ciphertext). Contoh cipher klasik yang paling terkenal adalah *Caesar Cipher*, yang menggeser setiap huruf dalam pesan sejauh beberapa posisi dalam alfabet. Meskipun sederhana, cipher klasik menjadi dasar perkembangan sistem kriptografi modern.
Salah satu konsep penting yang digunakan dalam kriptografi, termasuk cipher klasik, adalah aritmetika modular. Aritmetika ini beroperasi berdasarkan sistem bilangan yang "berulang" setelah mencapai nilai tertentu yang disebut modulus. Misalnya, dalam sistem modulus 26 (jumlah huruf alfabet), hasil dari operasi penjumlahan 25 + 3 akan kembali ke 2, karena melewati batas 26. Konsep ini banyak digunakan untuk proses enkripsi dan dekripsi agar hasil perhitungan tetap berada dalam rentang alfabet yang valid.
Dengan menggabungkan teknik substitusi dan prinsip aritmetika modular, cipher klasik dapat mengubah pesan menjadi bentuk yang sulit dipahami tanpa kunci tertentu. Meskipun keamanan cipher klasik mudah ditembus dengan teknik analisis frekuensi, teori dasarnya tetap relevan dan menjadi pondasi penting bagi kriptografi modern yang menggunakan algoritma matematis lebih kompleks seperti AES dan RSA.


---

## 3. Alat dan Bahan
- Python 3.x  
- Visual Studio Code
- Git dan akun GitHub  

---

## 4. Langkah Percobaan
(Tuliskan langkah yang dilakukan sesuai instruksi.  
Contoh format:
1. Membuat file `Aritmetika Modular` di folder `praktikum/week3-Aritmetika Modular/src/`.
2. Menyalin kode program dari panduan praktikum.
3. Menjalankan program dengan perintah `python Aritmetika Modular.py`.)

---

## 5. Source Code

```python
def mod_add(a, b, n): return (a + b) % n
def mod_sub(a, b, n): return (a - b) % n
def mod_mul(a, b, n): return (a * b) % n
def mod_exp(base, exp, n): return pow(base, exp, n)  # eksponensiasi modular

print("7 + 5 mod 12 =", mod_add(7, 5, 12))
print("7 * 5 mod 12 =", mod_mul(7, 5, 12))
print("7^128 mod 13 =", mod_exp(7, 128, 13))
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
- Pertanyaan 1: Aritmetika modular menjadi dasar dalam operasi matematika kriptografi modern karena memungkinkan perhitungan dilakukan dalam ruang bilangan terbatas (modulus tertentu). Prinsip ini menjaga hasil operasi seperti penjumlahan, perkalian, dan eksponensiasi tetap berada dalam rentang yang aman dan efisien untuk diproses komputer. Dalam algoritma seperti RSA, Diffie-Hellman, dan ECC, operasi utama seperti enkripsi dan dekripsi dilakukan menggunakan perpangkatan dan perkalian modular, yang memastikan keamanan dan efisiensi sistem.
- Pertanyaan 2: nvers modular berperan penting dalam menentukan kunci privat yang digunakan untuk proses dekripsi. Pada algoritma RSA, setelah menentukan kunci publik (e), kunci privat (d) dihitung sebagai invers modular dari e terhadap fungsi totien φ(n). Artinya, d memenuhi persamaan e×d≡1(modϕ(n)). Tanpa invers modular ini, tidak mungkin melakukan dekripsi pesan dengan benar karena tidak ada cara untuk “membalikkan” operasi enkripsi secara matematis. 
- Pertanyaan 3: Tantangan utamanya adalah kompleksitas komputasi yang sangat tinggi. Untuk modulus besar (misalnya bilangan prima ratusan atau ribuan bit), menemukan nilai eksponen x dari persamaan ≡y(modp) hampir mustahil dilakukan dalam waktu wajar menggunakan komputer konvensional. Tidak ada algoritma efisien yang mampu menyelesaikan masalah logaritma diskrit dengan cepat pada modulus besar, sehingga kesulitannya menjadi dasar keamanan berbagai algoritma kriptografi seperti Diffie-Hellman dan ElGamal.
---

## 8. Kesimpulan
Berdasarkan hasil percobaan yang telah saya lakukan, Menunjukan keberhasilan 
--- 

## 9. Daftar Pustaka
(Cantumkan referensi yang digunakan.  
Contoh:  
- https://rifqimulyawan.com/literasi/modular-arithmetic/  
- https://artofproblemsolving.com/wiki/index.php/Modular_arithmetic/Introduction

---

## 10. Commit Log
```
commit abc12345
Author: Muhammad Fikri Ananta <fikriadvan001@gmail.com>
Date:   2025-10-21

    week3-modmath-gcd dan laporan )
```
