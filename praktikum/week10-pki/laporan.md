# Laporan Praktikum Kriptografi
Minggu ke-: 10  
Topik: Public Key Infrastructure (PKI & Certificate Authority)
Nama: Muhammad Fikri Ananta  
NIM: 230202817  
Kelas: 5Ikra 

---

## 1. Tujuan
1. Membuat sertifikat digital sederhana.
2. Menjelaskan peran Certificate Authority (CA) dalam sistem PKI.
3. Mengevaluasi fungsi PKI dalam komunikasi aman (contoh: HTTPS, TLS).

---

## 2. Dasar Teori
Public Key Infrastructure (PKI) merupakan suatu kerangka kerja yang digunakan untuk mengelola kunci kriptografi dan sertifikat digital guna menjamin keamanan komunikasi elektronik. PKI memanfaatkan kriptografi kunci publik, di mana setiap entitas memiliki sepasang kunci, yaitu kunci publik dan kunci privat. Kunci publik digunakan untuk enkripsi atau verifikasi tanda tangan digital, sedangkan kunci privat digunakan untuk dekripsi atau pembuatan tanda tangan digital. Dengan PKI, identitas pihak yang berkomunikasi dapat diverifikasi sehingga aspek keamanan seperti kerahasiaan, integritas data, autentikasi, dan non-repudiation dapat terjamin.

Certificate Authority (CA) adalah komponen utama dalam PKI yang berfungsi sebagai pihak tepercaya (trusted third party). CA bertugas menerbitkan, memvalidasi, dan mencabut sertifikat digital yang mengaitkan identitas pemilik dengan kunci publiknya. Proses ini dilakukan melalui verifikasi identitas sebelum sertifikat diterbitkan, sehingga pengguna dapat mempercayai bahwa kunci publik dalam sertifikat benar-benar milik entitas yang sah. Sertifikat digital ini umumnya mengikuti standar X.509 dan banyak digunakan pada layanan seperti HTTPS, email aman, dan tanda tangan digital.

Selain CA, PKI juga melibatkan komponen lain seperti Registration Authority (RA), repository sertifikat, serta mekanisme pencabutan sertifikat melalui Certificate Revocation List (CRL) atau Online Certificate Status Protocol (OCSP). Kombinasi komponen tersebut memungkinkan sistem keamanan yang terstruktur dan skalabel untuk lingkungan jaringan modern. Dengan adanya PKI dan CA, pertukaran data melalui jaringan publik dapat dilakukan secara aman tanpa memerlukan pertukaran kunci rahasia secara langsung.

---

## 3. Alat dan Bahan
- Python 3.x  
- Visual Studio Code  
- Git dan akun GitHub  

---

## 4. Langkah Percobaan
1. Langkah 1 — Membuat Sertifikat Digital Sederhana
2. Menyalin kode program dari panduan praktikum.
3. Langkah 2 — Memverifikasi Sertifikat
4. Langkah 3 — Analisis PKI

---

## 5. Source Code

```python
from cryptography import x509
from cryptography.x509.oid import NameOID
from cryptography.hazmat.primitives import hashes, serialization
from cryptography.hazmat.primitives.asymmetric import rsa
from datetime import datetime, timedelta

# Generate key pair
key = rsa.generate_private_key(public_exponent=65537, key_size=2048)

# Buat subject & issuer (CA sederhana = self-signed)
subject = issuer = x509.Name([
    x509.NameAttribute(NameOID.COUNTRY_NAME, u"ID"),
    x509.NameAttribute(NameOID.ORGANIZATION_NAME, u"UPB Kriptografi"),
    x509.NameAttribute(NameOID.COMMON_NAME, u"example.com"),
])

# Buat sertifikat
cert = (
    x509.CertificateBuilder()
    .subject_name(subject)
    .issuer_name(issuer)
    .public_key(key.public_key())
    .serial_number(x509.random_serial_number())
    .not_valid_before(datetime.utcnow())
    .not_valid_after(datetime.utcnow() + timedelta(days=365))
    .sign(key, hashes.SHA256())
)

# Simpan sertifikat
with open("cert.pem", "wb") as f:
    f.write(cert.public_bytes(serialization.Encoding.PEM))

print("Sertifikat digital berhasil dibuat: cert.pem")
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
- Pertanyaan 1: Fungsi utama Certificate Authority (CA) adalah sebagai pihak tepercaya yang menerbitkan dan memverifikasi sertifikat digital. CA mengikat identitas suatu entitas (seperti individu, organisasi, atau server) dengan kunci publiknya melalui sertifikat digital, sehingga pihak lain dapat memastikan bahwa kunci publik tersebut benar-benar milik entitas yang sah. Selain itu, CA juga bertanggung jawab melakukan pencabutan sertifikat jika terjadi pelanggaran keamanan atau perubahan status kepercayaan, sehingga keandalan sistem PKI tetap terjaga.  
- Pertanyaan 2: Self-signed certificate tidak cukup untuk sistem produksi karena sertifikat tersebut tidak diverifikasi oleh pihak ketiga yang tepercaya. Akibatnya, klien atau browser tidak dapat memastikan keaslian identitas pemilik sertifikat dan biasanya akan menampilkan peringatan keamanan. Dalam lingkungan produksi, kondisi ini membuka peluang serangan seperti peniruan identitas server, karena siapa pun dapat membuat self-signed certificate tanpa proses validasi identitas yang ketat.
- Pertanyaan 3: PKI mencegah serangan Man-in-the-Middle (MITM) dalam komunikasi TLS/HTTPS dengan memanfaatkan sertifikat digital yang ditandatangani oleh CA tepercaya. Saat klien terhubung ke server, sertifikat server diverifikasi menggunakan rantai kepercayaan (chain of trust) hingga ke CA yang dikenal. Jika sertifikat valid dan sesuai dengan identitas server, klien dapat yakin bahwa kunci publik yang diterima adalah milik server yang sah. Dengan demikian, penyerang tidak dapat dengan mudah menyisipkan diri di tengah komunikasi tanpa terdeteksi, karena sertifikat palsu tidak akan lolos proses verifikasi. 

---

## 8. Kesimpulan
(Tuliskan kesimpulan singkat (2–3 kalimat) berdasarkan percobaan.  )

---

## 9. Daftar Pustaka
- Tanenbaum, Andrew S., & Wetherall, David J. Computer Networks. Pearson. 
- Kahn Academy / Cloudflare Learning – What is PKI? dan What is a Certificate Authority?.
- Kahn Academy / NIST – Public Key Infrastructure (PKI)

---

## 10. Commit Log
```
commit abc12345
Author: Muhammad Fikri Ananta <fikriadvan001@gmail.com>
Date:   2025-12-13

    week10-cryptosystem: Public Key Infrastructure (PKI & Certificate Authority) dan laporan )
```
