# Laporan Praktikum Kriptografi
Minggu ke-: 11 
Topik: Secret Sharing (Shamir’s Secret Sharing)  
Nama: Muhammad Fikri Ananta 
NIM: 230202817  
Kelas: 5Ikra  

---

## 1. Tujuan
1. Menjelaskan konsep Shamir Secret Sharing (SSS).
2. Melakukan simulasi pembagian rahasia ke beberapa pihak menggunakan skema SSS.
3. Menganalisis keamanan skema distribusi rahasia.

---

## 2. Dasar Teori
Shamir’s Secret Sharing (SSS) merupakan skema kriptografi yang digunakan untuk membagi suatu rahasia menjadi beberapa bagian (share) sehingga rahasia tersebut hanya dapat direkonstruksi apabila sejumlah minimum bagian tertentu (threshold) dikumpulkan. Skema ini diperkenalkan oleh Adi Shamir pada tahun 1979 dan didasarkan pada konsep matematika polinomial dalam aritmetika modulo bilangan prima. Setiap share yang dihasilkan tidak memberikan informasi berarti tentang rahasia apabila berdiri sendiri atau jumlahnya kurang dari threshold yang ditentukan.

Prinsip kerja SSS menggunakan polinomial berderajat k−1, di mana nilai rahasia ditempatkan sebagai konstanta polinomial. Nilai-nilai share diperoleh dari evaluasi polinomial pada titik-titik berbeda dan didistribusikan kepada pihak-pihak terkait. Rekonstruksi rahasia dilakukan dengan interpolasi Lagrange menggunakan minimal 𝑘 share. Tanpa memenuhi jumlah threshold tersebut, rahasia tidak dapat ditentukan secara matematis, sehingga sistem tetap aman meskipun sebagian share bocor.

Keunggulan utama Shamir’s Secret Sharing terletak pada keseimbangan antara keamanan dan ketersediaan data. Skema ini banyak digunakan dalam pengelolaan kunci kriptografi, pemulihan kata sandi, serta sistem yang memerlukan kontrol akses multi-pihak. Dengan pengaturan threshold yang tepat, SSS mampu memberikan perlindungan yang kuat terhadap kehilangan data dan penyalahgunaan rahasia.

---

## 3. Alat dan Bahan
- Python 3.x  
- Visual Studio Code 
- Git dan akun GitHub  

---

## 4. Langkah Percobaan
1. Menentukan rahasia yang akan dibagikan dan menetapkan parameter skema (k,n), yaitu jumlah minimum share untuk rekonstruksi dan total share yang dibuat.
2. Memilih bilangan prima sebagai modulus dan membentuk polinomial berderajat k−1 dengan rahasia sebagai konstanta.
3. Menghitung nilai polinomial pada beberapa titik berbeda untuk menghasilkan share, lalu mendistribusikannya kepada pihak terkait.
4. Mengumpulkan minimal k share untuk melakukan rekonstruksi rahasia menggunakan interpolasi Lagrange.
5. Memverifikasi bahwa rahasia hanya dapat diperoleh jika jumlah share memenuhi threshold yang ditentukan.

---

## 5. Source Code
```python
# Shamir Secret Sharing Manual (Python 3)

import random

# Fungsi modulo
def mod_inverse(a, p):
    return pow(a, -1, p)

# Interpolasi Lagrange
def lagrange_interpolation(x, points, p):
    total = 0
    for i, (xi, yi) in enumerate(points):
        prod = yi
        for j, (xj, _) in enumerate(points):
            if i != j:
                prod *= (x - xj) * mod_inverse(xi - xj, p)
                prod %= p
        total += prod
    return total % p

# Parameter
p = 2089          # bilangan prima
secret = 1234     # rahasia
k = 3
n = 5

# Polinomial: f(x) = a0 + a1*x + a2*x^2
coeff = [secret] + [random.randint(1, p-1) for _ in range(k-1)]

def f(x):
    return sum(coeff[i] * x**i for i in range(k)) % p

# Generate shares
shares = [(i, f(i)) for i in range(1, n+1)]

print("Shares:")
for s in shares:
    print(s)

# Rekonstruksi dengan 3 share
recovered = lagrange_interpolation(0, shares[:3], p)
print("\nRecovered Secret:", recovered)

```

---

## 6. Hasil dan Pembahasan
Hasil praktikum menunjukkan bahwa Shamir’s Secret Sharing mampu membagi rahasia menjadi beberapa share yang berbeda, di mana rahasia hanya dapat direkonstruksi jika jumlah share memenuhi nilai threshold yang ditentukan. Pengujian membuktikan bahwa penggunaan share sesuai threshold berhasil mengembalikan rahasia secara tepat, sedangkan jumlah share yang kurang dari threshold tidak menghasilkan nilai yang valid. Hal ini menegaskan bahwa setiap share tidak memberikan informasi berarti secara mandiri dan skema threshold efektif dalam menjaga keamanan rahasia. Dengan demikian, Shamir’s Secret Sharing dapat digunakan sebagai metode distribusi rahasia yang aman dan terkontrol.

---

## 7. Jawaban Pertanyaan
- Pertanyaan 1: SSS mencegah satu pihak memiliki kendali penuh atas rahasia, sehingga mengurangi risiko kebocoran dan penyalahgunaan. 
- Pertanyaan 2: Threshold menentukan tingkat keamanan dan toleransi kegagalan sistem, menyeimbangkan antara keamanan dan ketersediaan.
- Pertanyaan 3: Pada dompet cryptocurrency perusahaan, private key dibagi ke beberapa direksi, dan hanya dapat digunakan jika sejumlah minimum direksi menyetujui transaksi.  

---

## 8. Kesimpulan
Shamir’s Secret Sharing merupakan skema kriptografi yang efektif untuk mendistribusikan rahasia secara aman menggunakan konsep threshold. Skema ini memastikan rahasia tetap terlindungi meskipun sebagian share bocor, serta banyak diterapkan pada sistem keamanan modern yang membutuhkan kontrol akses tingkat tinggi.

---

## 9. Daftar Pustaka  
- Stinson, D. R. (2019). Cryptography: Theory and Practice (4th ed.). CRC Press..  
- Shamir, A. (1979). How to Share a Secret. Communications of the ACM, 22(11), 612–613.

---

## 10. Commit Log
```
commit abc12345
Author: Muhammad Fikri Ananta <fikriadvan001@gmail.com>
Date:   2026-01-05

    week11-cryptosystem: Secret Sharing (Shamir’s Secret Sharing) dan laporan 
```
