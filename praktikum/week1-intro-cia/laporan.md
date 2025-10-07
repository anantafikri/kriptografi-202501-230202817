# Laporan Praktikum Kriptografi
Minggu ke-: 1 
Topik: Sejarah Kriptografi dan Prinsip CIA
Nama: Muhammad Fikri Ananta 
NIM: 230202817  
Kelas: 5IKRA  

---

## 1. Tujuan
1. Menjelaskan sejarah dan evolusi kriptografi dari masa klasik hingga modern.
2. Menyebutkan prinsip Confidentiality, Integrity, Availability (CIA) dengan benar.
3. Menyimpulkan peran kriptografi dalam sistem keamanan informasi modern.
4. Menyiapkan repositori GitHub sebagai media kerja praktikum. 

---

## 2. Dasar Teori
Kriptografi berasal dari bahasa Yunani “kryptos” yang berarti tersembunyi dan “graphein” yang berarti menulis. Secara umum, kriptografi adalah ilmu dan seni untuk menjaga keamanan pesan agar hanya dapat dibaca oleh pihak yang berhak melalui proses pengkodean dan penyandian. Tujuan utamanya adalah menjaga kerahasiaan informasi dari akses tidak sah serta menjamin integritas dan keaslian pesan yang dikirimkan.
Era kriptografi klasik
Pada masa awal, kriptografi bersifat sederhana dan manual. Salah satu teknik tertua adalah Caesar Cipher, yang digunakan oleh Julius Caesar untuk mengirim pesan rahasia dengan cara menggeser huruf pada alfabet sejumlah tertentu. Misalnya, pesan “HELLO” dengan pergeseran tiga huruf menjadi “KHOOR”. Selain itu, bangsa Sparta menggunakan Skitala Spartan, yaitu alat berbentuk tongkat silinder yang membungkus pita kulit bertuliskan pesan. Pesan hanya dapat dibaca jika pita dibungkus kembali pada tongkat dengan diameter yang sama. Metode klasik ini cukup efektif di masa lalu, tetapi mudah dipecahkan dengan teknik analisis frekuensi seiring berkembangnya pengetahuan tentang pola bahasa.
Perkembangan kriptografi modern
Memasuki abad ke-20, kriptografi mulai menggunakan teknologi mekanik dan elektronik. Salah satu tonggak penting adalah Mesin Enigma yang digunakan oleh Jerman pada Perang Dunia II untuk mengenkripsi pesan militer. Mesin ini menghasilkan kombinasi enkripsi yang sangat kompleks, hingga akhirnya berhasil dipecahkan oleh tim sekutu yang dipimpin Alan Turing. Setelah perang, kriptografi berkembang pesat dengan hadirnya algoritma berbasis matematika dan komputer. Dua algoritma paling terkenal adalah RSA (Rivest–Shamir–Adleman) dan AES (Advanced Encryption Standard). RSA merupakan algoritma asimetris yang menggunakan pasangan kunci publik dan privat, sedangkan AES merupakan standar enkripsi simetris yang digunakan secara luas dalam berbagai sistem modern.
Evolusi menuju kriptografi kontemporer
Memasuki era digital, kriptografi menjadi tulang punggung keamanan informasi global. Muncul teknologi baru seperti Elliptic Curve Cryptography (ECC) yang menawarkan tingkat keamanan tinggi dengan panjang kunci lebih kecil, serta Diffie-Hellman Key Exchange yang memungkinkan pertukaran kunci aman melalui jaringan terbuka. Saat ini, konsep kriptografi juga diterapkan pada blockchain dan cryptocurrency seperti Bitcoin, di mana teknologi hashing dan tanda tangan digital memastikan setiap transaksi aman, transparan, dan tidak dapat diubah. Kriptografi kontemporer tidak hanya berfokus pada pengamanan data, tetapi juga integritas sistem terdistribusi dan privasi pengguna.

Prinsip CIA (Confidentialy, Integrity, Avalailability)
Prinsip CIA Triad merupakan tiga pilar utama dalam keamanan informasi. Ketiganya berfungsi menjaga agar sistem, data, dan layanan digital tetap aman, andal, dan dapat dipercaya.
1.	Confidentiality (Kerahasiaan)
Kerahasiaan bertujuan agar informasi hanya bisa diakses oleh pihak yang berwenang. Data harus terlindungi dari pengungkapan tidak sah baik selama penyimpanan maupun saat transmisi.
Contoh penerapan :
Sistem login dengan autentikasi dua faktor (A2F) untuk mencegah akses ilegal.

2.	Integrity (Integritas)
Integritas berarti menjaga agar data tidak berubah atau dimodifikasi tanpa izin selama proses penyimpanan maupun transmisi. Sistem harus bisa mendeteksi setiap perubahan yang tidak sah.
Contoh Penerapan :
Digital signature yang memastikan dokumen tidak diubah setelah ditandatangani.

3.	Avalailability (Ketersediaan)
Ketersediaan memastikan bahwa sistem dan data selalu dapat diakses oleh pengguna yang berhak kapan pun dibutuhkan. Hal ini mencakup perlindungan terhadap gangguan layanan seperti serangan DDoS, kerusakan perangkat keras, atau bencana alam.
Contoh Penerapan :
Backup data berkala untuk pemulihan sistem.

Kesimpulan
Kriptografi telah berevolusi dari teknik sederhana seperti Caesar Cipher menjadi teknologi kompleks seperti blockchain yang menopang ekosistem digital modern. Prinsip CIA Confidentiality, Integrity, dan Availability menjadi dasar dalam menjaga keamanan informasi di setiap lapisan sistem digital. Dengan penerapan yang tepat, kriptografi tidak hanya melindungi data, tetapi juga memastikan kepercayaan, keandalan, dan keberlangsungan sistem informasi di era siber.

---

## 3. Alat dan Bahan
Python 3.x  

---

## 4. Langkah Percobaan
(Tuliskan langkah yang dilakukan sesuai instruksi.  
Contoh format:
1. Membuat file `caesar_cipher.py` di folder `praktikum/week2-cryptosystem/src/`.
2. Menyalin kode program dari panduan praktikum.
3. Menjalankan program dengan perintah `python caesar_cipher.py`.)

---

## 5. Source Code
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
Jawaban quiz singkat
1.	Siapa tokoh yang dianggap sebagai bapak kriptografi modern?
Jawaban :
Tokoh yang dianggap sebagai bapak kriptografi modern adalah Whitfield Diffie
2.	Sebutkan algoritma kunci publik yang populer digunakan saat ini.
Jawaban :
Algoritma kunci publik yang paling populer digunakan saat ini antara lain :
- RSA (Rivest Shamir Adleman) yang digunakan secara luas untuk enkripsi data dan tanda tangan digital.
- ECC (Elliptic Curve Cryptography), Algoritma ini menawarkan keamanan tinggi dengan ukuran kunci yang lebih kecil.
- Diffie-Hellman Key Exchange  biasa digunakan untuk pertukaran kunci rahasia di jaringanpublik.
Ketiga algoritma ini menjadi tulang punggung keamanan data dalam berbagai aplikasi modern seperti HTTPS, VPN, email terenkripsi, dan cryptocurrency.
3.	Apa perbedaan utama antara kriptografi klasik dan kriptografi modern?
Jawaban : 
Perbedaan utama antara keduanya terletak pada metode dan tingkat keamanannya :
-Kriptografi klasik Menggunakan teknik sederhana berbasis alfabet seperti Caesar Cipher atau Vigenere Cipher. Proses enkripsinya dilakukan dengan substitusi dan transposisi huruf, yang mudah dipecahkan menggunakan analisis frekuensi.
-Kriptografi modern Menggunakan algoritma matematika kompleks dan berbasis komputer seperti RSA, AES, dan ECC. Kriptografi modern juga memanfaatkan konsep kunci publik dan privat serta teori bilangan besar untuk menjaga keamanan data.
Kesimpulannya kriptografi klasik bersifat manual dan mudah dibobol, sedangkan kriptografi modern sangat kuat karena didukung oleh komputasi digital dan algoritma matematis yang kompleks.

---

## 8. Kesimpulan
Berdasarkan percobaan yang sudah dilakukan  Teknik Caesar Cipher – Kriptografi Klasik: Dari percobaan menggunakan teknik Caesar Cipher, dapat disimpulkan bahwa metode ini merupakan bentuk kriptografi klasik yang sangat sederhana. Proses enkripsi dilakukan dengan menggeser huruf dalam teks asli sejumlah nilai tertentu, sedangkan dekripsi dilakukan dengan menggeser huruf ke arah sebaliknya.

---

## 9. Daftar Pustaka
Program Python untuk Enkripsi dan Dekripsi Menggunakan Caesar Cipher Apr4,2023

---

## 10. Commit Log
commit abc12345 Author: Muhammad Fikri Ananta fikriadvan001@gmail.com Date: 2025-10-07
    week2-cryptosystem: implementasi Caesar Cipher dan laporan )
```
