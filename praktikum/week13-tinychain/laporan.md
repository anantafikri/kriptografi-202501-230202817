# Laporan Praktikum Kriptografi
Minggu ke-: 13 
Topik: TinyChain – Proof of Work (PoW) 
Nama: Muhammad Fikri Ananta  
NIM: 230202817  
Kelas: 5Ikra  

---

## 1. Tujuan
1. Menjelaskan peran hash function dalam blockchain.
2. Melakukan simulasi sederhana Proof of Work (PoW).
3. Menganalisis keamanan cryptocurrency berbasis kriptografi.

---

## 2. Dasar Teori
Blockchain merupakan teknologi penyimpanan data terdistribusi yang tersusun dari rangkaian blok yang saling terhubung menggunakan fungsi hash kriptografi. Setiap blok menyimpan data, waktu pembuatan, hash blok sebelumnya, serta hash miliknya sendiri. Penggunaan fungsi hash memastikan bahwa data yang telah tersimpan tidak dapat diubah tanpa terdeteksi, karena perubahan sekecil apa pun akan menghasilkan nilai hash yang berbeda dan merusak keterkaitan antarblok.

Proof of Work (PoW) adalah mekanisme konsensus yang digunakan untuk memvalidasi penambahan blok baru ke dalam blockchain. Pada mekanisme ini, node atau penambang harus menyelesaikan perhitungan matematis dengan mencari nilai nonce tertentu agar hash blok memenuhi kriteria tingkat kesulitan (difficulty) yang telah ditentukan. Proses ini membutuhkan waktu dan sumber daya komputasi, sehingga mencegah pihak yang tidak bertanggung jawab memanipulasi data blockchain dengan mudah.

Penerapan Proof of Work berperan penting dalam menjaga keamanan dan keandalan blockchain, terutama dalam mencegah terjadinya pemalsuan transaksi dan double spending. Namun, kelemahan utama PoW terletak pada efisiensi energi yang rendah karena proses komputasi dilakukan secara berulang. Oleh karena itu, meskipun PoW efektif dari sisi keamanan, penggunaannya perlu dipertimbangkan kembali untuk sistem yang menuntut efisiensi energi tinggi.

---

## 3. Alat dan Bahan
- Python 3.x  
- Visual Studio Code 
- Git dan akun GitHub  

---

## 4. Langkah Percobaan
1. Menyiapkan lingkungan kerja dengan membuat struktur folder sesuai ketentuan dan menggunakan Python versi 3.11 atau lebih baru.
2. Menyalin kode program dari panduan praktikum.
3. Menjalankan program untuk melakukan proses mining beberapa blok secara berurutan.
4. Mengamati hasil mining pada terminal dan melakukan screenshoot sebagai bukti percobaan.
5. Menganalisis hasil percobaan terkait waktu mining dan pengaruh difficulty terhadap proses Proof of Work.
   
---

## 5. Source Code
```python
import hashlib
import time


# KELAS BLOCK

class Block:
    def __init__(self, index, data, previous_hash):
        self.index = index
        self.timestamp = time.time()
        self.data = data
        self.previous_hash = previous_hash
        self.nonce = 0
        self.hash = self.calculate_hash()

    def calculate_hash(self):
        value = str(self.index) + str(self.timestamp) + str(self.data) + str(self.previous_hash) + str(self.nonce)
        return hashlib.sha256(value.encode()).hexdigest()

    def mine_block(self, difficulty):
        target = "0" * difficulty
        while self.hash[:difficulty] != target:
            self.nonce += 1
            self.hash = self.calculate_hash()
        print(f"Block {self.index} mined with nonce {self.nonce}")
        print(f"Hash: {self.hash}\n")


# KELAS BLOCKCHAIN

class Blockchain:
    def __init__(self):
        self.chain = [self.create_genesis_block()]
        self.difficulty = 4

    def create_genesis_block(self):
        return Block(0, "Genesis Block", "0")

    def get_latest_block(self):
        return self.chain[-1]

    def add_block(self, data):
        new_block = Block(
            len(self.chain),
            data,
            self.get_latest_block().hash
        )
        new_block.mine_block(self.difficulty)
        self.chain.append(new_block)


# UJI COBA BLOCKCHAIN

my_chain = Blockchain()

print("Mining Block 1...")
my_chain.add_block("Transaksi A ke B")

print("Mining Block 2...")
my_chain.add_block("Transaksi B ke C")

print("Mining Block 3...")
my_chain.add_block("Transaksi C ke D")

print("Blockchain selesai dibuat.")

```


---

## 6. Hasil dan Pembahasan
Berdasarkan percobaan yang dilakukan, program mini blockchain berhasil melakukan proses mining terhadap tiga blok menggunakan mekanisme Proof of Work. Setiap blok menghasilkan nilai hash yang diawali dengan empat angka nol sesuai tingkat difficulty yang ditetapkan, menandakan bahwa proses validasi berjalan dengan baik. Nilai nonce yang berbeda pada setiap blok menunjukkan bahwa pencarian hash dilakukan secara berulang dan bergantung pada data serta waktu pembuatan blok. Hasil ini membuktikan bahwa Proof of Work mampu meningkatkan keamanan blockchain dengan mempersulit manipulasi data, meskipun proses mining membutuhkan komputasi berulang yang berpotensi meningkatkan penggunaan sumber daya.

---

## 7. Jawaban Pertanyaan 
- Pertanyaan 1: Fungsi hash berperan untuk menjaga integritas data karena setiap perubahan kecil pada data akan menghasilkan nilai hash yang berbeda secara signifikan. Dengan adanya hash, setiap blok saling terhubung dan perubahan pada satu blok akan merusak seluruh rantai blockchain. 
- Pertanyaan 2: Proof of Work mencegah double spending dengan mewajibkan setiap transaksi untuk divalidasi melalui proses mining yang membutuhkan waktu dan sumber daya. Hal ini membuat penyerang sangat sulit untuk memalsukan transaksi atau menggandakan pengeluaran tanpa menguasai mayoritas kekuatan komputasi jaringan.
- Pertanyaan 3: Kelemahan utama Proof of Work adalah konsumsi energi yang tinggi karena proses mining membutuhkan perhitungan komputasi secara terus-menerus. Hal ini dapat menyebabkan pemborosan energi dan biaya operasional yang besar, terutama pada jaringan blockchain berskala besar. 

---

## 8. Kesimpulan
Berdasarkan percobaan yang telah dilakukan, dapat disimpulkan bahwa implementasi mini blockchain dengan mekanisme Proof of Work berhasil dijalankan dengan baik. Proses mining mampu menghasilkan hash yang valid sesuai tingkat difficulty yang ditentukan, sehingga setiap blok dapat divalidasi sebelum ditambahkan ke dalam blockchain. Percobaan ini menunjukkan bahwa Proof of Work efektif dalam menjaga integritas dan keamanan data, meskipun membutuhkan sumber daya komputasi yang relatif besar.

---

## 9. Daftar Pustaka  
- Stallings, W. (2017). Cryptography and Network Security: Principles and Practice (7th ed.). Pearson Education.  
- Stinson, D. R., & Paterson, M. B. (2019). Cryptography: Theory and Practice (4th ed.). CRC Press.

---

## 10. Commit Log
```
commit abc12345
Author: Muhammad Fikri Ananta <fikriadvan001@gmail.com>
Date:   2026-01-05

    week13-cryptosystem: TinyChain – Proof of Work (PoW) dan laporan )
```
