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
Public Key Infrastructure (PKI) merupakan sistem yang digunakan untuk mengelola kunci kriptografi dan sertifikat digital guna menjamin keamanan komunikasi. PKI memungkinkan proses autentikasi, kerahasiaan, integritas data, serta non-repudiation dengan memanfaatkan kriptografi kunci publik. Sertifikat digital berisi informasi identitas pemilik dan public key yang digunakan untuk verifikasi.

Certificate Authority (CA) berperan sebagai pihak tepercaya yang menerbitkan dan memvalidasi sertifikat digital. CA memastikan bahwa public key benar-benar milik entitas yang sah. Dalam komunikasi aman seperti HTTPS/TLS, browser memverifikasi sertifikat server melalui CA untuk mencegah serangan seperti Man-in-the-Middle (MITM).

---

## 3. Alat dan Bahan
- Python 3.x  
- Visual Studio Code  
- Git dan akun GitHub  

---

## 4. Langkah Percobaan
1. Membuat pasangan kunci (private key & public key).
2. Menentukan identitas sertifikat (subject).
3. Membuat sertifikat digital self-signed.
4. LMenandatangani sertifikat menggunakan private key.
5. Menyimpan sertifikat dalam format .pem.

---

## 5. Source Code

```python
from cryptography import x509
from cryptography.x509.oid import NameOID
from cryptography.hazmat.primitives import hashes, serialization
from cryptography.hazmat.primitives.asymmetric import rsa
from datetime import datetime, timedelta

# Generate private key
key = rsa.generate_private_key(
    public_exponent=65537,
    key_size=2048
)

# Subject & issuer
subject = issuer = x509.Name([
    x509.NameAttribute(NameOID.COUNTRY_NAME, "ID"),
    x509.NameAttribute(NameOID.ORGANIZATION_NAME, "UPB"),
    x509.NameAttribute(NameOID.COMMON_NAME, "localhost"),
])

# Create certificate
cert = x509.CertificateBuilder().subject_name(
    subject
).issuer_name(
    issuer
).public_key(
    key.public_key()
).serial_number(
    x509.random_serial_number()
).not_valid_before(
    datetime.utcnow()
).not_valid_after(
    datetime.utcnow() + timedelta(days=365)
).sign(key, hashes.SHA256())

# Save certificate
with open("cert.pem", "wb") as f:
    f.write(cert.public_bytes(serialization.Encoding.PEM))

print("Sertifikat digital berhasil dibuat")

```
)

---

## 6. Hasil dan Pembahasan
Hasil dari program di atas adalah sertifikat digital self-signed dalam format .pem. Sertifikat ini dapat digunakan untuk simulasi HTTPS atau pembelajaran PKI. Verifikasi sertifikat dilakukan dengan mencocokkan tanda tangan digital menggunakan public key. Dalam praktik nyata, sertifikat akan diverifikasi oleh CA tepercaya agar browser tidak menampilkan peringatan keamanan. Jika CA palsu digunakan, maka browser akan menolak sertifikat dan koneksi dianggap tidak aman. Oleh karena itu, PKI sangat penting dalam menjaga keamanan transaksi online seperti login, pembayaran, dan pertukaran data sensitif.

---

## 7. Jawaban Pertanyaan
- Pertanyaan 1: Fungsi utama Certificate Authority (CA) adalah sebagai pihak tepercaya yang menerbitkan dan memverifikasi sertifikat digital. CA mengikat identitas suatu entitas (seperti individu, organisasi, atau server) dengan kunci publiknya melalui sertifikat digital, sehingga pihak lain dapat memastikan bahwa kunci publik tersebut benar-benar milik entitas yang sah. Selain itu, CA juga bertanggung jawab melakukan pencabutan sertifikat jika terjadi pelanggaran keamanan atau perubahan status kepercayaan, sehingga keandalan sistem PKI tetap terjaga.  
- Pertanyaan 2: Self-signed certificate tidak cukup untuk sistem produksi karena sertifikat tersebut tidak diverifikasi oleh pihak ketiga yang tepercaya. Akibatnya, klien atau browser tidak dapat memastikan keaslian identitas pemilik sertifikat dan biasanya akan menampilkan peringatan keamanan. Dalam lingkungan produksi, kondisi ini membuka peluang serangan seperti peniruan identitas server, karena siapa pun dapat membuat self-signed certificate tanpa proses validasi identitas yang ketat.
- Pertanyaan 3: PKI mencegah serangan Man-in-the-Middle (MITM) dalam komunikasi TLS/HTTPS dengan memanfaatkan sertifikat digital yang ditandatangani oleh CA tepercaya. Saat klien terhubung ke server, sertifikat server diverifikasi menggunakan rantai kepercayaan (chain of trust) hingga ke CA yang dikenal. Jika sertifikat valid dan sesuai dengan identitas server, klien dapat yakin bahwa kunci publik yang diterima adalah milik server yang sah. Dengan demikian, penyerang tidak dapat dengan mudah menyisipkan diri di tengah komunikasi tanpa terdeteksi, karena sertifikat palsu tidak akan lolos proses verifikasi. 

---

## 8. Kesimpulan
PKI berperan penting dalam mengamankan komunikasi digital melalui penggunaan sertifikat dan kriptografi kunci publik. Praktikum ini menunjukkan bahwa pembuatan sertifikat digital dengan Python membantu memahami proses dasar PKI, meskipun sertifikat self-signed hanya cocok untuk keperluan pembelajaran.

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

    week10-cryptosystem: Public Key Infrastructure (PKI & Certificate Authority) dan laporan 
```
