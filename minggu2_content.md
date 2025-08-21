# MINGGU 2: KONSEP DASAR PEMROGRAMAN
## Mata Kuliah: Logika dan Algoritma Pemrograman

---

## **TUJUAN PEMBELAJARAN**

Setelah mengikuti pembelajaran pada minggu ini, mahasiswa diharapkan dapat:

1. **Memahami sejarah algoritma** dari masa Al-Khwarizmi hingga era modern
2. **Mengidentifikasi fungsi algoritma** dalam problem solving dan automation
3. **Menguasai struktur dasar algoritma** (sekuensial, percabangan, looping, fungsi, rekursi)
4. **Menganalisis efisiensi algoritma** menggunakan konsep time dan space complexity
5. **Merancang algoritma sederhana** dengan struktur yang tepat dan efisien

---

## **BAGIAN 1: SEJARAH ALGORITMA DAN AL-KHWARIZMI**

### **1.1 Biografi Muhammad ibn Musa al-Khwarizmi**

Al-Khwarizmi adalah seorang matematikawan Islam yang menulis tentang numerals Hindu-Arab. Kata "algorithm" berasal dari namanya. Muhammad ibn Musa al-Khwarizmi (sekitar 780-850 M) adalah salah satu matematikawan paling berpengaruh dalam sejarah, yang sering disebut sebagai **"Bapak Aljabar"** dan **"Bapak Algoritma"**.

#### **Latar Belakang Historis:**

**Kehidupan dan Karier:**
- **Tempat Lahir**: Khwarezm (sekarang Uzbekistan), bagian dari Kekaisaran Persia
- **Periode Hidup**: Masa Keemasan Islam (Abbasid Caliphate)
- **Jabatan**: Kepala perpustakaan dan observatorium di **Bayt al-Hikmah** (House of Wisdom) Baghdad
- **Patron**: Khalifah Al-Ma'mun (813-833 M)

**Konteks Sejarah:**
Pada masa al-Khwarizmi, Baghdad adalah pusat pembelajaran dan penelitian terbesar di dunia. Bayt al-Hikmah merupakan institusi yang mengumpulkan, menerjemahkan, dan mengembangkan ilmu pengetahuan dari berbagai peradaban: Yunani, India, Persia, dan Mesopotamia.

### **1.2 Kontribusi Al-Khwarizmi terhadap Matematika**

#### **1. Pengembangan Aljabar**

Al-Khwarizmi dianggap sebagai bapak aljabar bukan hanya karena esainya memberi nama pada bidang ini, tetapi juga secara substansial. Inti dari aljabar adalah abstraksi.

**Karya Utama: "Kitab al-Jabr wa'l-Muqābala" (Buku Restorasi dan Pelengkap)**
- **al-Jabr** (الجبر): Restorasi/pengembalian - menambahkan suku yang hilang
- **al-Muqābala** (المقابلة): Perbandingan/pelengkap - mengurangi suku yang sama

**Contoh Metodologi al-Jabr:**
```
Persamaan asal: x² - 5x = 24
Al-Jabr (restorasi): x² - 5x + 25/4 = 24 + 25/4
Al-Muqābala (pelengkap): (x - 5/2)² = 24 + 25/4 = 121/4
Solusi: x - 5/2 = ±11/2, maka x = 8 atau x = -3
```

#### **2. Sistem Numerik Hindu-Arab**

Pada abad ke-12, terjemahan Latin dari buku al-Khwarizmi tentang aritmatika India (Algorithmo de Numero Indorum), yang mengkodifikasi berbagai numerals India, memperkenalkan sistem bilangan posisional berbasis desimal ke dunia Barat.

**Revolusi Sistem Bilangan:**
- **Sebelum al-Khwarizmi**: Eropa menggunakan angka Romawi (I, V, X, L, C, D, M)
- **Setelah al-Khwarizmi**: Adopsi angka Hindu-Arab (0, 1, 2, 3, 4, 5, 6, 7, 8, 9)

**Keunggulan Sistem Hindu-Arab:**
1. **Sistem Posisional**: Nilai angka tergantung posisinya
2. **Konsep Zero**: Revolutioner untuk matematika
3. **Efisiensi Kalkulasi**: Operasi aritmatika lebih mudah
4. **Skalabilitas**: Dapat merepresentasikan bilangan sangat besar

**Perbandingan Sistem:**
```
Bilangan 1994:
- Romawi: MCMXCIV (7 karakter)
- Hindu-Arab: 1994 (4 karakter)

Operasi 25 × 13:
- Romawi: XXV × XIII = ??? (sangat kompleks)
- Hindu-Arab: 25 × 13 = 325 (relatif mudah)
```

### **1.3 Dari Al-Khwarizmi ke "Algorithm"**

#### **Etimologi Kata "Algorithm":**

Al-Khwarizmi menulis buku tentang numerals Hindu-Arab, memberikan nama "algorithm" untuk proses ini melalui Latinisasi nama belakangnya.

**Evolusi Linguistik:**
```
Al-Khwarizmi → Algoritmi (Latin) → Algorithm (Modern)
```

**Tahapan Transformasi:**
1. **Abad ke-12**: Terjemahan Latin "Algoritmi de Numero Indorum"
2. **Abad ke-13-15**: "Algorismus" - metode kalkulasi menggunakan numerals Arab
3. **Abad ke-17-18**: "Algorithm" - prosedur sistematis penyelesaian masalah
4. **Abad ke-20**: Definisi modern - sekuence instruksi untuk komputer

### **1.4 Warisan Al-Khwarizmi dalam Era Digital**

#### **Relevansi Modern:**
1. **Fundamental Programming**: Setiap program komputer adalah implementasi algoritma
2. **Artificial Intelligence**: Machine learning algorithms
3. **Big Data**: Algoritma sorting dan searching
4. **Cryptography**: Algoritma enkripsi untuk keamanan digital
5. **Internet**: Search algorithms (Google, Bing)

**Contoh Aplikasi Modern dari Konsep Al-Khwarizmi:**
```
Algoritma Pencarian Google:
1. Input: Query pengguna
2. Process: Analisis relevansi menggunakan PageRank algorithm
3. Output: Hasil pencarian yang terurut berdasarkan relevansi

Mirip dengan metodologi al-Jabr:
- Restorasi: Mengumpulkan semua halaman web yang relevan
- Pelengkap: Mengurutkan berdasarkan kriteria relevansi
```

---

## **BAGIAN 2: FUNGSI ALGORITMA DALAM PROBLEM SOLVING**

### **2.1 Algoritma sebagai Problem Solving Tool**

Algoritma adalah prosedur langkah demi langkah, yang mendefinisikan serangkaian instruksi yang harus dieksekusi dalam urutan tertentu untuk mendapatkan output yang diinginkan.

#### **Karakteristik Problem Solving dengan Algoritma:**

**1. Systematic Approach (Pendekatan Sistematis)**
- Memecah masalah kompleks menjadi sub-masalah kecil
- Menyelesaikan setiap sub-masalah secara berurutan
- Mengintegrasikan solusi sub-masalah menjadi solusi total

**2. Reproducibility (Dapat Direproduksi)**
- Algoritma yang sama akan menghasilkan output yang sama untuk input yang sama
- Memberikan konsistensi dalam penyelesaian masalah
- Memungkinkan verifikasi dan validasi solusi

**3. Generalizability (Dapat Digeneralisasi)**
- Satu algoritma dapat menyelesaikan kelas masalah yang sama
- Tidak terikat pada kasus spesifik tertentu
- Dapat diadaptasi untuk masalah serupa

#### **Contoh Problem Solving: Sistem Penilaian Mahasiswa**

**Masalah:**
"Universitas perlu sistem untuk menghitung IPK mahasiswa berdasarkan nilai dan SKS mata kuliah."

**Decomposition (Pemecahan Masalah):**
```
Main Problem: Hitung IPK Mahasiswa
├── Sub-problem 1: Input data mata kuliah (nama, SKS, nilai)
├── Sub-problem 2: Konversi nilai huruf ke angka (A=4, B=3, C=2, D=1, E=0)
├── Sub-problem 3: Hitung total poin (nilai × SKS)
├── Sub-problem 4: Hitung total SKS
└── Sub-problem 5: IPK = total poin / total SKS
```

**Algoritma Solusi:**
```
ALGORITMA Hitung_IPK
INPUT: n (jumlah mata kuliah), data_matkul[1..n] {nama, sks, nilai_huruf}
OUTPUT: ipk

LANGKAH:
1. MULAI
2. total_poin ← 0
3. total_sks ← 0
4. UNTUK i = 1 SAMPAI n LAKUKAN
   4.1 nilai_angka ← konversi_nilai(data_matkul[i].nilai_huruf)
   4.2 poin ← nilai_angka × data_matkul[i].sks
   4.3 total_poin ← total_poin + poin
   4.4 total_sks ← total_sks + data_matkul[i].sks
5. ipk ← total_poin / total_sks
6. TAMPILKAN ipk
7. SELESAI

FUNGSI konversi_nilai(huruf):
  JIKA huruf = 'A' MAKA RETURN 4
  JIKA huruf = 'B' MAKA RETURN 3
  JIKA huruf = 'C' MAKA RETURN 2
  JIKA huruf = 'D' MAKA RETURN 1
  JIKA huruf = 'E' MAKA RETURN 0
```

### **2.2 Automation dan Efisiensi**

#### **Manfaat Automation melalui Algoritma:**

**1. Speed (Kecepatan)**
- Komputer dapat mengeksekusi jutaan instruksi per detik
- Proses yang membutuhkan jam/hari secara manual dapat diselesaikan dalam detik

**2. Accuracy (Akurasi)**
- Menghilangkan human error dalam kalkulasi
- Konsistensi dalam penerapan rules dan procedures

**3. Scale (Skalabilitas)**
- Dapat menangani volume data yang sangat besar
- Performa tidak menurun secara signifikan dengan peningkatan input size

**4. Cost Efficiency (Efisiensi Biaya)**
- Mengurangi kebutuhan tenaga kerja manual
- Investasi sekali untuk digunakan berulang kali

#### **Contoh Automation: Sistem ATM**

**Manual Process (Sebelum ATM):**
```
1. Pergi ke bank pada jam kerja
2. Ambil nomor antrian
3. Tunggu dipanggil teller
4. Tunjukkan buku tabungan dan identitas
5. Teller cek saldo manual
6. Isi slip penarikan
7. Teller hitung uang manual
8. Update buku tabungan manual
Total waktu: 30-60 menit
```

**Automated Process (ATM):**
```
ALGORITMA ATM_Withdrawal
1. Insert card
2. Input PIN
3. Select "Withdrawal"
4. Input amount
5. System check balance
6. IF balance >= amount THEN
     Dispense cash
     Update balance
     Print receipt
   ELSE
     Display "Insufficient funds"
7. Return card
Total waktu: 2-3 menit
```

### **2.3 Pattern Recognition dan Algorithm Design**

#### **Jenis-Jenis Pola dalam Problem Solving:**

**1. Sequential Pattern (Pola Berurutan)**
- Masalah yang diselesaikan langkah demi langkah
- Setiap langkah bergantung pada langkah sebelumnya

**Contoh: Algoritma Brewing Coffee**
```
1. Siapkan air (1 cup = 240ml)
2. Panaskan air hingga 90-96°C
3. Grind coffee beans (2 tbsp untuk 1 cup)
4. Letakkan filter di dripper
5. Tuang coffee grounds ke filter
6. Tuang air panas perlahan dalam gerakan melingkar
7. Tunggu coffee menetes sempurna
8. Coffee ready to serve
```

**2. Decision Pattern (Pola Keputusan)**
- Masalah yang memerlukan pengambilan keputusan berdasarkan kondisi tertentu

**Contoh: Algoritma Diagnosis Sederhana**
```
ALGORITMA Simple_Medical_Diagnosis
IF temperature > 38°C THEN
  IF has_cough = true THEN
    IF has_sore_throat = true THEN
      diagnosis = "Possible flu"
    ELSE
      diagnosis = "Possible cold"
  ELSE
    diagnosis = "Fever - consult doctor"
ELSE
  diagnosis = "Normal temperature"
```

**3. Iterative Pattern (Pola Berulang)**
- Masalah yang memerlukan pengulangan proses

**Contoh: Algoritma Search in Contact List**
```
ALGORITMA Search_Contact
INPUT: contact_list[], search_name
OUTPUT: contact_info or "Not found"

found = false
i = 0
WHILE i < contact_list.length AND found = false DO
  IF contact_list[i].name = search_name THEN
    RETURN contact_list[i]
    found = true
  ELSE
    i = i + 1
IF found = false THEN
  RETURN "Contact not found"
```

---

## **BAGIAN 3: STRUKTUR ALGORITMA**

### **3.1 Struktur Sekuensial (Sequential)**

Struktur sekuensial adalah struktur algoritma yang paling dasar, dimana instruksi dieksekusi satu per satu secara berurutan dari atas ke bawah.

#### **Karakteristik Struktur Sekuensial:**
- **Linear Flow**: Eksekusi mengikuti urutan yang telah ditetapkan
- **No Branching**: Tidak ada pengambilan keputusan
- **Deterministic**: Output dapat diprediksi berdasarkan input

#### **Contoh Struktur Sekuensial: Algoritma Menghitung Keliling Lingkaran**
```
ALGORITMA Keliling_Lingkaran
INPUT: jari_jari (float)
OUTPUT: keliling (float)

LANGKAH:
1. MULAI
2. BACA jari_jari
3. pi ← 3.14159
4. keliling ← 2 × pi × jari_jari
5. TAMPILKAN "Keliling lingkaran: ", keliling
6. SELESAI
```

#### **Implementasi dalam Pseudocode:**
```c
BEGIN
  READ radius
  pi := 3.14159
  circumference := 2 * pi * radius
  WRITE "Circumference: ", circumference
END
```

#### **Kegunaan Struktur Sekuensial:**
- Kalkulasi matematis sederhana
- Konversi data dan format
- Inisialisasi variabel
- Input/Output operations

### **3.2 Struktur Percabangan (Branching/Selection)**

Struktur percabangan memungkinkan algoritma membuat keputusan berdasarkan kondisi tertentu, menghasilkan jalur eksekusi yang berbeda.

#### **Jenis-Jenis Struktur Percabangan:**

**1. Simple IF (If Tunggal)**
```
IF kondisi THEN
  aksi
```

**2. IF-ELSE (If-Selain)**
```
IF kondisi THEN
  aksi_1
ELSE
  aksi_2
```

**3. Nested IF (If Bersarang)**
```
IF kondisi_1 THEN
  IF kondisi_2 THEN
    aksi_1
  ELSE
    aksi_2
ELSE
  aksi_3
```

**4. Multi-way IF (If Bertingkat)**
```
IF kondisi_1 THEN
  aksi_1
ELSE IF kondisi_2 THEN
  aksi_2
ELSE IF kondisi_3 THEN
  aksi_3
ELSE
  aksi_default
```

#### **Contoh Implementasi: Sistem Grading**
```
ALGORITMA Sistem_Grading
INPUT: nilai (integer, 0-100)
OUTPUT: grade (character)

LANGKAH:
1. MULAI
2. BACA nilai
3. IF nilai >= 90 THEN
     grade ← 'A'
   ELSE IF nilai >= 80 THEN
     grade ← 'B'
   ELSE IF nilai >= 70 THEN
     grade ← 'C'
   ELSE IF nilai >= 60 THEN
     grade ← 'D'
   ELSE
     grade ← 'E'
4. TAMPILKAN "Grade: ", grade
5. SELESAI
```

#### **Contoh Kompleks: Kalkulator BMI dengan Kategori**
```
ALGORITMA BMI_Calculator
INPUT: berat (float), tinggi (float)
OUTPUT: bmi (float), kategori (string)

LANGKAH:
1. MULAI
2. BACA berat, tinggi
3. bmi ← berat / (tinggi × tinggi)
4. IF bmi < 18.5 THEN
     kategori ← "Underweight"
     rekomendasi ← "Perbanyak asupan nutrisi seimbang"
   ELSE IF bmi < 25.0 THEN
     kategori ← "Normal"
     rekomendasi ← "Pertahankan pola hidup sehat"
   ELSE IF bmi < 30.0 THEN
     kategori ← "Overweight"
     rekomendasi ← "Kurangi kalori dan tingkatkan olahraga"
   ELSE
     kategori ← "Obese"
     rekomendasi ← "Konsultasi dengan dokter dan ahli gizi"
5. TAMPILKAN "BMI: ", bmi
6. TAMPILKAN "Kategori: ", kategori
7. TAMPILKAN "Rekomendasi: ", rekomendasi
8. SELESAI
```

### **3.3 Struktur Perulangan (Looping/Iteration)**

Struktur perulangan memungkinkan algoritma mengeksekusi sekumpulan instruksi berulang kali berdasarkan kondisi tertentu.

#### **Jenis-Jenis Struktur Perulangan:**

**1. FOR Loop (Perulangan Terhitung)**
- Digunakan ketika jumlah iterasi sudah diketahui
- Memiliki variabel counter yang berubah secara teratur

```
FOR counter = start TO end STEP increment DO
  aksi
```

**Contoh: Tabel Perkalian**
```
ALGORITMA Tabel_Perkalian
INPUT: n (bilangan yang akan dikalikan)
OUTPUT: tabel perkalian 1 sampai 10

LANGKAH:
1. MULAI
2. BACA n
3. FOR i = 1 TO 10 DO
     hasil ← n × i
     TAMPILKAN n, " × ", i, " = ", hasil
4. SELESAI
```

**2. WHILE Loop (Perulangan Berkondisi)**
- Digunakan ketika jumlah iterasi tidak diketahui sebelumnya
- Loop berlanjut selama kondisi bernilai true

```
WHILE kondisi DO
  aksi
```

**Contoh: Validasi Input**
```
ALGORITMA Input_Validation
OUTPUT: valid_number

LANGKAH:
1. MULAI
2. valid ← false
3. WHILE valid = false DO
     TAMPILKAN "Masukkan angka positif (1-100): "
     BACA input
     IF input >= 1 AND input <= 100 THEN
       valid_number ← input
       valid ← true
     ELSE
       TAMPILKAN "Input tidak valid, coba lagi!"
4. TAMPILKAN "Angka valid: ", valid_number
5. SELESAI
```

**3. DO-WHILE Loop (Perulangan Pascatest)**
- Loop dieksekusi minimal satu kali
- Kondisi dicek setelah eksekusi

```
DO
  aksi
WHILE kondisi
```

**Contoh: Menu Program**
```
ALGORITMA Menu_Program
LANGKAH:
1. MULAI
2. DO
     TAMPILKAN "=== MENU UTAMA ==="
     TAMPILKAN "1. Hitung Luas Lingkaran"
     TAMPILKAN "2. Hitung Volume Kubus"
     TAMPILKAN "3. Keluar"
     TAMPILKAN "Pilih menu (1-3): "
     BACA pilihan
     
     IF pilihan = 1 THEN
       hitung_luas_lingkaran()
     ELSE IF pilihan = 2 THEN
       hitung_volume_kubus()
     ELSE IF pilihan = 3 THEN
       TAMPILKAN "Terima kasih!"
     ELSE
       TAMPILKAN "Pilihan tidak valid!"
   WHILE pilihan ≠ 3
3. SELESAI
```

#### **Nested Loops (Perulangan Bersarang)**

Perulangan di dalam perulangan, berguna untuk memproses data multi-dimensi.

**Contoh: Pattern Printing**
```
ALGORITMA Print_Triangle_Pattern
INPUT: n (tinggi segitiga)
OUTPUT: pola segitiga

LANGKAH:
1. MULAI
2. BACA n
3. FOR i = 1 TO n DO
     FOR j = 1 TO i DO
       CETAK "*"
     CETAK newline
4. SELESAI

Output untuk n=5:
*
**
***
****
*****
```

### **3.4 Struktur Fungsi (Function/Modularization)**

Fungsi memungkinkan pemecahan algoritma kompleks menjadi modul-modul kecil yang dapat digunakan berulang kali.

#### **Keuntungan Menggunakan Fungsi:**
1. **Code Reusability**: Dapat digunakan berulang kali
2. **Modularity**: Pemecahan masalah menjadi bagian kecil
3. **Maintainability**: Mudah dipelihara dan diperbaiki
4. **Abstraction**: Menyembunyikan detail implementasi

#### **Jenis Fungsi:**

**1. Void Function (Prosedur)**
- Tidak mengembalikan nilai
- Digunakan untuk aksi/tindakan

```
PROCEDURE nama_prosedur(parameter)
  aksi
END PROCEDURE
```

**2. Function (Fungsi)**
- Mengembalikan nilai
- Digunakan untuk kalkulasi

```
FUNCTION nama_fungsi(parameter) RETURN tipe_data
  aksi
  RETURN nilai
END FUNCTION
```

#### **Contoh Implementasi: Kalkulator Modular**
```
ALGORITMA Kalkulator_Modular

// Fungsi untuk penjumlahan
FUNCTION tambah(a, b) RETURN float
  RETURN a + b
END FUNCTION

// Fungsi untuk pengurangan  
FUNCTION kurang(a, b) RETURN float
  RETURN a - b
END FUNCTION

// Fungsi untuk perkalian
FUNCTION kali(a, b) RETURN float
  RETURN a * b
END FUNCTION

// Fungsi untuk pembagian
FUNCTION bagi(a, b) RETURN float
  IF b ≠ 0 THEN
    RETURN a / b
  ELSE
    TAMPILKAN "Error: Pembagian dengan nol!"
    RETURN 0
END FUNCTION

// Prosedur untuk menampilkan menu
PROCEDURE tampilkan_menu()
  TAMPILKAN "=== KALKULATOR ==="
  TAMPILKAN "1. Penjumlahan"
  TAMPILKAN "2. Pengurangan"
  TAMPILKAN "3. Perkalian"
  TAMPILKAN "4. Pembagian"
  TAMPILKAN "5. Keluar"
END PROCEDURE

// Program utama
LANGKAH UTAMA:
1. MULAI
2. DO
     tampilkan_menu()
     BACA pilihan
     
     IF pilihan >= 1 AND pilihan <= 4 THEN
       BACA angka1, angka2
       
       IF pilihan = 1 THEN
         hasil ← tambah(angka1, angka2)
       ELSE IF pilihan = 2 THEN
         hasil ← kurang(angka1, angka2)
       ELSE IF pilihan = 3 THEN
         hasil ← kali(angka1, angka2)
       ELSE IF pilihan = 4 THEN
         hasil ← bagi(angka1, angka2)
       
       TAMPILKAN "Hasil: ", hasil
     ELSE IF pilihan ≠ 5 THEN
       TAMPILKAN "Pilihan tidak valid!"
   WHILE pilihan ≠ 5
3. SELESAI
```

### **3.5 Struktur Rekursi (Recursion)**

Rekursi adalah teknik dimana fungsi memanggil dirinya sendiri untuk menyelesaikan masalah yang dapat dipecah menjadi sub-masalah yang serupa tetapi lebih kecil.

#### **Komponen Rekursi:**
1. **Base Case**: Kondisi berhenti
2. **Recursive Case**: Pemanggilan diri sendiri dengan parameter yang lebih kecil

#### **Contoh Klasik: Faktorial**
```
FUNCTION faktorial(n) RETURN integer
  // Base case
  IF n = 0 OR n = 1 THEN
    RETURN 1
  ELSE
    // Recursive case
    RETURN n * faktorial(n-1)
END FUNCTION

Trace untuk faktorial(5):
faktorial(5) = 5 * faktorial(4)
             = 5 * (4 * faktorial(3))
             = 5 * (4 * (3 * faktorial(2)))
             = 5 * (4 * (3 * (2 * faktorial(1))))
             = 5 * (4 * (3 * (2 * 1)))
             = 5 * (4 * (3 * 2))
             = 5 * (4 * 6)
             = 5 * 24
             = 120
```

#### **Contoh Lanjutan: Fibonacci Sequence**
```
FUNCTION fibonacci(n) RETURN integer
  // Base cases
  IF n = 0 THEN
    RETURN 0
  ELSE IF n = 1 THEN
    RETURN 1
  ELSE
    // Recursive case
    RETURN fibonacci(n-1) + fibonacci(n-2)
END FUNCTION

Trace untuk fibonacci(5):
fibonacci(5) = fibonacci(4) + fibonacci(3)
             = (fibonacci(3) + fibonacci(2)) + (fibonacci(2) + fibonacci(1))
             = ((fibonacci(2) + fibonacci(1)) + (fibonacci(1) + fibonacci(0))) + ((fibonacci(1) + fibonacci(0)) + fibonacci(1))
             = (((1 + 1) + (1 + 0)) + ((1 + 0) + 1))
             = ((2 + 1) + (1 + 1))
             = (3 + 2)
             = 5
```

#### **Kapan Menggunakan Rekursi:**
- **Tree Structures**: Traversal pohon biner
- **Mathematical Sequences**: Faktorial, Fibonacci, dll
- **Divide and Conquer**: Merge sort, quick sort
- **Backtracking**: Pencarian solusi optimal

---

## **BAGIAN 4: EFISIENSI ALGORITMA (TIME & SPACE COMPLEXITY)**

### **4.1 Pentingnya Analisis Efisiensi**

Efisiensi algoritma dapat dianalisis pada dua tahap berbeda, sebelum implementasi dan setelah implementasi.

#### **Mengapa Efisiensi Penting:**

**1. Resource Constraints**
- **Memory**: Terbatas pada setiap sistem
- **Processing Power**: CPU speed terbatas
- **Time**: User experience bergantung pada response time
- **Energy**: Penting untuk mobile devices

**2. Scalability**
- Algoritma yang efisien untuk data kecil belum tentu efisien untuk data besar
- Big Data memerlukan algoritma yang scalable

**3. Cost Implications**
- Server resources = biaya operational
- Better algorithms = lower operational costs

#### **Jenis Analisis Efisiensi:**

**1. A Priori Analysis (Analisis Teoritis)**
Ini adalah analisis teoritis dari suatu algoritma. Efisiensi algoritma diukur dengan asumsi bahwa semua faktor lain, misalnya kecepatan prosesor, adalah konstan dan tidak mempengaruhi implementasi.

**2. A Posteriori Analysis (Analisis Empiris)**
Ini adalah analisis empiris dari suatu algoritma. Algoritma yang dipilih diimplementasikan menggunakan bahasa pemrograman. Kemudian dieksekusi pada mesin komputer target. Dalam analisis ini, statistik aktual seperti running time dan space required, dikumpulkan.

### **4.2 Time Complexity (Kompleksitas Waktu)**

Time complexity dari suatu algoritma merepresentasikan jumlah waktu yang dibutuhkan algoritma untuk berjalan hingga selesai. Kebutuhan waktu dapat didefinisikan sebagai fungsi numerik T(n), dimana T(n) dapat diukur sebagai jumlah langkah, dengan asumsi setiap langkah membutuhkan waktu konstan.

#### **Faktor yang Mempengaruhi Time Complexity:**
1. **Input Size (n)**: Ukuran data input
2. **Nature of Input**: Kondisi data (sorted, random, reverse sorted)
3. **Algorithm Design**: Struktur algoritma yang digunakan

#### **Notasi Big O - Pengantar Praktis**

Big O notation menggambarkan upper bound atau worst-case scenario dari kompleksitas algoritma.

**Common Time Complexities:**

**1. O(1) - Constant Time**
- Waktu eksekusi tidak bergantung pada ukuran input
- Selalu membutuhkan waktu yang sama

```
ALGORITMA Access_Array_Element
INPUT: array[], index
OUTPUT: array[index]

LANGKAH:
1. RETURN array[index]  // Satu operasi, tidak peduli ukuran array

Time Complexity: O(1)
```

**2. O(log n) - Logarithmic Time**
- Waktu eksekusi bertambah secara logaritmik
- Setiap iterasi mengurangi search space setengahnya

```
ALGORITMA Binary_Search
INPUT: sorted_array[], target
OUTPUT: index atau -1

LANGKAH:
1. left ← 0, right ← length(array) - 1
2. WHILE left ≤ right DO
     mid ← (left + right) / 2
     IF array[mid] = target THEN
       RETURN mid
     ELSE IF array[mid] < target THEN
       left ← mid + 1
     ELSE
       right ← mid - 1
3. RETURN -1

Time Complexity: O(log n)
```

**3. O(n) - Linear Time**
- Waktu eksekusi sebanding dengan ukuran input
- Harus memeriksa setiap elemen

```
ALGORITMA Linear_Search
INPUT: array[], target
OUTPUT: index atau -1

LANGKAH:
1. FOR i = 0 TO length(array) - 1 DO
     IF array[i] = target THEN
       RETURN i
2. RETURN -1

Time Complexity: O(n)
```

**4. O(n log n) - Linearithmic Time**
- Kombinasi dari linear dan logarithmic
- Common pada efficient sorting algorithms

```
ALGORITMA Merge_Sort (Simplified)
INPUT: array[]
OUTPUT: sorted_array[]

LANGKAH:
1. IF length(array) ≤ 1 THEN RETURN array
2. mid ← length(array) / 2
3. left ← merge_sort(array[0...mid-1])
4. right ← merge_sort(array[mid...end])
5. RETURN merge(left, right)

Time Complexity: O(n log n)
```

**5. O(n²) - Quadratic Time**
- Waktu eksekusi sebanding dengan kuadrat ukuran input
- Common pada nested loops

```
ALGORITMA Bubble_Sort
INPUT: array[]
OUTPUT: sorted_array[]

LANGKAH:
1. FOR i = 0 TO length(array) - 1 DO
     FOR j = 0 TO length(array) - i - 2 DO
       IF array[j] > array[j+1] THEN
         swap(array[j], array[j+1])

Time Complexity: O(n²)
```

#### **Perbandingan Performa Time Complexity:**

```
Input Size (n) | O(1) | O(log n) | O(n) | O(n log n) | O(n²)
----------------|------|----------|------|------------|-------
1               | 1    | 1        | 1    | 1          | 1
10              | 1    | 3        | 10   | 33         | 100
100             | 1    | 7        | 100  | 664        | 10,000
1,000           | 1    | 10       | 1K   | 10K        | 1M
10,000          | 1    | 13       | 10K  | 130K       | 100M
100,000         | 1    | 17       | 100K | 1.7M       | 10B
```

### **4.3 Space Complexity (Kompleksitas Ruang)**

Space complexity merepresentasikan jumlah ruang memori yang dibutuhkan algoritma dalam lifecycle-nya. Ruang yang dibutuhkan algoritma sama dengan jumlah dari dua komponen berikut:

#### **Komponen Space Complexity:**

**1. Fixed Part (Bagian Tetap)**
- Ruang yang diperlukan untuk menyimpan data dan variabel tertentu
- Tidak bergantung pada ukuran masalah
- Contoh: variabel sederhana, konstanta, ukuran program

**2. Variable Part (Bagian Variabel)**
- Ruang yang diperlukan variabel yang ukurannya bergantung pada ukuran masalah
- Contoh: dynamic memory allocation, recursion stack space

#### **Formula Space Complexity:**
```
S(P) = C + SP(I)
dimana:
S(P) = Space complexity dari program P
C = Fixed part (constant space)
SP(I) = Variable part yang bergantung pada instance characteristic I
```

#### **Contoh Analisis Space Complexity:**

**Contoh 1: Simple Sum Algorithm**
```
ALGORITMA SUM(A, B)
LANGKAH:
1. MULAI
2. C ← A + B + 10
3. RETURN C
4. SELESAI

Space Analysis:
- Fixed Part: 3 variabel (A, B, C) + 1 konstanta (10) = 4 unit
- Variable Part: 0 (tidak ada struktur data dinamis)
- Space Complexity: S(P) = 4 + 0 = O(1)
```

**Contoh 2: Array Sum Algorithm**
```
ALGORITMA Array_Sum(array[], n)
LANGKAH:
1. sum ← 0
2. FOR i = 0 TO n-1 DO
     sum ← sum + array[i]
3. RETURN sum

Space Analysis:
- Fixed Part: 2 variabel (sum, i) = 2 unit
- Variable Part: array[n] = n unit
- Space Complexity: S(P) = 2 + n = O(n)
```

**Contoh 3: Recursive Factorial**
```
FUNCTION factorial(n)
  IF n ≤ 1 THEN
    RETURN 1
  ELSE
    RETURN n * factorial(n-1)

Space Analysis:
- Setiap recursive call menggunakan stack space
- Maximum depth = n
- Space per call = constant
- Space Complexity: O(n) due to recursion stack
```

### **4.4 Trade-off antara Time dan Space**

Sering kali ada trade-off antara time complexity dan space complexity. Optimization untuk satu aspek mungkin memperburuk aspek lainnya.

#### **Contoh Trade-off: Fibonacci Calculation**

**1. Recursive Approach (Time Optimized untuk Readability)**
```
FUNCTION fibonacci_recursive(n)
  IF n ≤ 1 THEN
    RETURN n
  ELSE
    RETURN fibonacci_recursive(n-1) + fibonacci_recursive(n-2)

Time Complexity: O(2^n) - Very slow!
Space Complexity: O(n) - Recursion stack
```

**2. Dynamic Programming Approach (Time-Space Balanced)**
```
FUNCTION fibonacci_dp(n)
  IF n ≤ 1 THEN RETURN n
  
  dp[0] ← 0
  dp[1] ← 1
  FOR i = 2 TO n DO
    dp[i] ← dp[i-1] + dp[i-2]
  RETURN dp[n]

Time Complexity: O(n) - Much faster!
Space Complexity: O(n) - Array storage
```

**3. Space Optimized Approach (Space Optimized)**
```
FUNCTION fibonacci_optimized(n)
  IF n ≤ 1 THEN RETURN n
  
  prev2 ← 0
  prev1 ← 1
  FOR i = 2 TO n DO
    current ← prev1 + prev2
    prev2 ← prev1
    prev1 ← current
  RETURN current

Time Complexity: O(n) - Still fast
Space Complexity: O(1) - Minimal space!
```

---

## **BAGIAN 5: STUDI KASUS LENGKAP**

### **5.1 Studi Kasus: Sistem Manajemen Perpustakaan Sederhana**

Mari kita aplikasikan semua konsep yang telah dipelajari dalam satu sistem yang komprehensif.

#### **Problem Statement:**
"Perpustakaan membutuhkan sistem untuk mengelola buku, anggota, dan transaksi peminjaman dengan fitur pencarian dan laporan."

#### **Analisis Requirement:**

**Functional Requirements:**
1. **Book Management**: Add, search, update, delete books
2. **Member Management**: Register, search, update members
3. **Transaction Management**: Borrow, return books
4. **Reporting**: Books availability, overdue books

**Non-Functional Requirements:**
1. **Performance**: Response time < 2 seconds
2. **Scalability**: Handle up to 10,000 books dan 1,000 members
3. **Usability**: User-friendly menu system

#### **Data Model:**
```
STRUKTUR Book:
  isbn: string
  title: string
  author: string
  year: integer
  available: boolean

STRUKTUR Member:
  member_id: string
  name: string
  email: string
  join_date: date

STRUKTUR Transaction:
  transaction_id: string
  member_id: string
  isbn: string
  borrow_date: date
  due_date: date
  return_date: date (null jika belum dikembalikan)
```

#### **Algoritma Sistem Lengkap:**

**1. Main Menu System (Sequential + Selection)**
```
ALGORITMA Library_Management_System
LANGKAH:
1. MULAI
2. inisialisasi_data()
3. DO
     tampilkan_menu_utama()
     BACA pilihan
     
     SWITCH pilihan:
       CASE 1: book_management_menu()
       CASE 2: member_management_menu()
       CASE 3: transaction_menu()
       CASE 4: reporting_menu()
       CASE 5: TAMPILKAN "Terima kasih!"
       DEFAULT: TAMPILKAN "Pilihan tidak valid!"
   WHILE pilihan ≠ 5
4. SELESAI
```

**2. Book Search Function (Linear Search)**
```
FUNCTION search_book_by_title(books[], n, search_title) RETURN integer
  FOR i = 0 TO n-1 DO
    IF books[i].title CONTAINS search_title THEN
      RETURN i
  RETURN -1

Time Complexity: O(n)
Space Complexity: O(1)
```

**3. Advanced Book Search (Multiple Criteria)**
```
FUNCTION advanced_book_search(books[], n, criteria, search_term) RETURN array
  result_indices ← empty array
  count ← 0
  
  FOR i = 0 TO n-1 DO
    match ← false
    
    SWITCH criteria:
      CASE "title":
        match ← (books[i].title CONTAINS search_term)
      CASE "author":
        match ← (books[i].author CONTAINS search_term)
      CASE "year":
        match ← (books[i].year = convert_to_integer(search_term))
      CASE "available":
        match ← (books[i].available = convert_to_boolean(search_term))
    
    IF match THEN
      result_indices[count] ← i
      count ← count + 1
  
  RETURN result_indices[0..count-1]

Time Complexity: O(n)
Space Complexity: O(k) where k = number of matching results
```

**4. Book Sorting (Selection Sort Implementation)**
```
PROCEDURE sort_books_by_title(books[], n)
  FOR i = 0 TO n-2 DO
    min_index ← i
    FOR j = i+1 TO n-1 DO
      IF books[j].title < books[min_index].title THEN
        min_index ← j
    
    IF min_index ≠ i THEN
      swap(books[i], books[min_index])

Time Complexity: O(n²)
Space Complexity: O(1)
```

**5. Overdue Books Report (Complex Logic)**
```
FUNCTION generate_overdue_report(transactions[], n, current_date) RETURN array
  overdue_list ← empty array
  overdue_count ← 0
  
  FOR i = 0 TO n-1 DO
    // Check if book is not returned and past due date
    IF transactions[i].return_date = NULL AND 
       current_date > transactions[i].due_date THEN
      
      // Calculate days overdue
      days_overdue ← calculate_date_difference(current_date, transactions[i].due_date)
      
      // Create overdue record
      overdue_record ← {
        transaction_id: transactions[i].transaction_id,
        member_id: transactions[i].member_id,
        isbn: transactions[i].isbn,
        days_overdue: days_overdue,
        fine: calculate_fine(days_overdue)
      }
      
      overdue_list[overdue_count] ← overdue_record
      overdue_count ← overdue_count + 1
  
  RETURN overdue_list[0..overdue_count-1]

FUNCTION calculate_fine(days_overdue) RETURN float
  fine_per_day ← 1000.0  // Rp 1000 per hari
  max_fine ← 50000.0     // Maksimal Rp 50,000
  
  total_fine ← days_overdue * fine_per_day
  IF total_fine > max_fine THEN
    total_fine ← max_fine
  
  RETURN total_fine

Time Complexity: O(n)
Space Complexity: O(k) where k = number of overdue books
```

### **5.2 Optimization dan Improvement**

#### **Performance Optimization:**

**1. Binary Search untuk Data Terurut**
```
// Assuming books are sorted by ISBN
FUNCTION binary_search_book_by_isbn(books[], n, target_isbn) RETURN integer
  left ← 0
  right ← n - 1
  
  WHILE left ≤ right DO
    mid ← (left + right) / 2
    
    IF books[mid].isbn = target_isbn THEN
      RETURN mid
    ELSE IF books[mid].isbn < target_isbn THEN
      left ← mid + 1
    ELSE
      right ← mid - 1
  
  RETURN -1

Time Complexity: O(log n) - Much faster than linear search!
```

**2. Hash Table untuk Member Lookup (Advanced)**
```
// Conceptual hash table implementation
STRUKTUR HashTable:
  table: array of linked lists
  size: integer

FUNCTION hash_function(member_id, table_size) RETURN integer
  hash_value ← 0
  FOR each character c in member_id DO
    hash_value ← (hash_value * 31 + ASCII_value(c)) MOD table_size
  RETURN hash_value

FUNCTION search_member_hash(hash_table, member_id) RETURN Member
  index ← hash_function(member_id, hash_table.size)
  current ← hash_table.table[index].head
  
  WHILE current ≠ NULL DO
    IF current.data.member_id = member_id THEN
      RETURN current.data
    current ← current.next
  
  RETURN NULL

Average Time Complexity: O(1)
Worst Case Time Complexity: O(n) if all elements hash to same bucket
```

---

## **BAGIAN 6: LATIHAN DAN EVALUASI MENDALAM**

### **6.1 Latihan Struktur Algoritma**

#### **Latihan 1: Sequential Structure**
**Problem:** Buat algoritma untuk menghitung total harga belanja termasuk pajak dan diskon.

**Spesifikasi:**
- Input: harga_barang, jumlah_barang, persentase_diskon, persentase_pajak
- Diskon dihitung dari subtotal
- Pajak dihitung dari subtotal setelah diskon
- Output: subtotal, diskon, pajak, total_akhir

**Solusi:**
```
ALGORITMA Hitung_Total_Belanja
INPUT: harga_barang, jumlah_barang, persentase_diskon, persentase_pajak
OUTPUT: subtotal, diskon, pajak, total_akhir

LANGKAH:
1. MULAI
2. BACA harga_barang, jumlah_barang, persentase_diskon, persentase_pajak
3. subtotal ← harga_barang × jumlah_barang
4. diskon ← subtotal × (persentase_diskon / 100)
5. subtotal_setelah_diskon ← subtotal - diskon
6. pajak ← subtotal_setelah_diskon × (persentase_pajak / 100)
7. total_akhir ← subtotal_setelah_diskon + pajak
8. TAMPILKAN "Subtotal: Rp", subtotal
9. TAMPILKAN "Diskon: Rp", diskon
10. TAMPILKAN "Pajak: Rp", pajak
11. TAMPILKAN "Total Akhir: Rp", total_akhir
12. SELESAI
```

#### **Latihan 2: Selection Structure**
**Problem:** Sistem penilaian dengan multiple criteria.

**Spesifikasi:**
- Input: nilai_tugas, nilai_uts, nilai_uas, kehadiran
- Bobot: tugas 30%, UTS 30%, UAS 35%, kehadiran 5%
- Syarat lulus: nilai akhir ≥ 60 DAN kehadiran ≥ 75%
- Grade: A(85-100), B(70-84), C(60-69), D(45-59), E(0-44)

```
ALGORITMA Sistem_Penilaian_Lengkap
INPUT: nilai_tugas, nilai_uts, nilai_uas, kehadiran
OUTPUT: nilai_akhir, grade, status_lulus

LANGKAH:
1. MULAI
2. BACA nilai_tugas, nilai_uts, nilai_uas, kehadiran
3. nilai_akhir ← (nilai_tugas × 0.3) + (nilai_uts × 0.3) + (nilai_uas × 0.35) + (kehadiran × 0.05)
4. 
5. // Tentukan grade
6. IF nilai_akhir >= 85 THEN
     grade ← 'A'
   ELSE IF nilai_akhir >= 70 THEN
     grade ← 'B'
   ELSE IF nilai_akhir >= 60 THEN
     grade ← 'C'
   ELSE IF nilai_akhir >= 45 THEN
     grade ← 'D'
   ELSE
     grade ← 'E'

7. // Tentukan status kelulusan
8. IF nilai_akhir >= 60 AND kehadiran >= 75 THEN
     status_lulus ← "LULUS"
   ELSE
     status_lulus ← "TIDAK LULUS"
     IF nilai_akhir < 60 THEN
       TAMPILKAN "Alasan: Nilai akhir kurang dari 60"
     IF kehadiran < 75 THEN
       TAMPILKAN "Alasan: Kehadiran kurang dari 75%"

9. TAMPILKAN "Nilai Akhir: ", nilai_akhir
10. TAMPILKAN "Grade: ", grade
11. TAMPILKAN "Status: ", status_lulus
12. SELESAI
```

#### **Latihan 3: Iteration Structure**
**Problem:** Analisis data penjualan bulanan.

```
ALGORITMA Analisis_Penjualan_Bulanan
INPUT: n (jumlah hari), penjualan_harian[]
OUTPUT: total_penjualan, rata_rata, penjualan_tertinggi, penjualan_terendah, hari_terbaik

LANGKAH:
1. MULAI
2. BACA n
3. total_penjualan ← 0
4. penjualan_tertinggi ← 0
5. penjualan_terendah ← INFINITY
6. hari_terbaik ← 0

7. // Input dan analisis data
8. FOR i = 1 TO n DO
     TAMPILKAN "Masukkan penjualan hari ke-", i, ": "
     BACA penjualan_harian[i]
     
     total_penjualan ← total_penjualan + penjualan_harian[i]
     
     IF penjualan_harian[i] > penjualan_tertinggi THEN
       penjualan_tertinggi ← penjualan_harian[i]
       hari_terbaik ← i
     
     IF penjualan_harian[i] < penjualan_terendah THEN
       penjualan_terendah ← penjualan_harian[i]

9. rata_rata ← total_penjualan / n

10. // Output hasil analisis
11. TAMPILKAN "=== LAPORAN PENJUALAN BULANAN ==="
12. TAMPILKAN "Total Penjualan: Rp", total_penjualan
13. TAMPILKAN "Rata-rata Harian: Rp", rata_rata  
14. TAMPILKAN "Penjualan Tertinggi: Rp", penjualan_tertinggi
15. TAMPILKAN "Penjualan Terendah: Rp", penjualan_terendah
16. TAMPILKAN "Hari Terbaik: Hari ke-", hari_terbaik
17. SELESAI
```

### **6.2 Problem Solving Challenge**

#### **Challenge 1: Number Pattern Generator**
Buat algoritma yang dapat menghasilkan berbagai pola angka berdasarkan input user.

```
ALGORITMA Pattern_Generator
INPUT: pattern_type, size
OUTPUT: pattern sesuai pilihan

LANGKAH:
1. MULAI
2. TAMPILKAN "Pilih jenis pattern:"
3. TAMPILKAN "1. Triangle Numbers"
4. TAMPILKAN "2. Pyramid Numbers" 
5. TAMPILKAN "3. Diamond Pattern"
6. TAMPILKAN "4. Pascal Triangle"
7. BACA pattern_type, size

8. SWITCH pattern_type:
   CASE 1: generate_triangle_numbers(size)
   CASE 2: generate_pyramid_numbers(size)
   CASE 3: generate_diamond_pattern(size)
   CASE 4: generate_pascal_triangle(size)
   DEFAULT: TAMPILKAN "Pattern tidak valid"

9. SELESAI

PROCEDURE generate_triangle_numbers(n)
  FOR i = 1 TO n DO
    FOR j = 1 TO i DO
      CETAK j, " "
    CETAK newline

PROCEDURE generate_pyramid_numbers(n)
  FOR i = 1 TO n DO
    // Print spaces
    FOR j = 1 TO (n-i) DO
      CETAK " "
    // Print numbers
    FOR j = 1 TO i DO
      CETAK j, " "
    CETAK newline

PROCEDURE generate_pascal_triangle(n)
  FOR i = 0 TO n-1 DO
    // Print spaces for formatting
    FOR j = 0 TO (n-i-1) DO
      CETAK " "
    
    // Calculate and print Pascal triangle values
    FOR j = 0 TO i DO
      value ← calculate_pascal_value(i, j)
      CETAK value, " "
    CETAK newline

FUNCTION calculate_pascal_value(row, col) RETURN integer
  IF col = 0 OR col = row THEN
    RETURN 1
  ELSE
    RETURN calculate_pascal_value(row-1, col-1) + calculate_pascal_value(row-1, col)
```

---

## **BAGIAN 7: RANGKUMAN DAN EVALUASI**

### **7.1 Rangkuman Materi Minggu 2**

Pada pertemuan ini, kita telah membahas konsep-konsep fundamental yang menjadi pondasi dalam pemrograman:

#### **Key Learning Points:**

**1. Sejarah dan Warisan Al-Khwarizmi**
- Kontribusi Al-Khwarizmi dalam pengembangan aljabar dan sistem numerik
- Evolusi dari metode al-Jabr wa'l-Muqābala menjadi algoritma modern
- Relevansi warisan intelektual Islam dalam teknologi kontemporer

**2. Fungsi Algoritma dalam Problem Solving**
- Systematic approach untuk menyelesaikan masalah kompleks
- Automation dan efisiensi dalam computational tasks
- Pattern recognition dan generalisasi solusi

**3. Struktur Dasar Algoritma**
- **Sequential**: Linear execution flow
- **Selection**: Decision-making dengan conditional logic
- **Iteration**: Repetitive processes dengan loop structures
- **Function**: Modularization untuk code reusability
- **Recursion**: Self-referential problem solving

**4. Analisis Efisiensi**
- Time complexity: O(1), O(log n), O(n), O(n log n), O(n²)
- Space complexity: fixed part vs variable part
- Trade-off considerations antara time dan space

### **7.2 Practical Applications**

**Real-World Examples:**
- **E-commerce**: Shopping cart calculation algorithms
- **Banking**: Transaction processing systems
- **Healthcare**: Patient record management
- **Education**: Grading dan assessment systems
- **Transportation**: Route optimization algorithms

### **7.3 Assignment untuk Minggu Depan**

**Tugas Utama: Implementasi Algoritma Rata-rata dari 3 Bilangan**

Buatlah algoritma lengkap dengan spesifikasi berikut:

1. **Input Validation**: Pastikan input adalah bilangan valid
2. **Calculation**: Hitung rata-rata dengan presisi 2 decimal places
3. **Output Formatting**: Tampilkan hasil dengan format yang rapi
4. **Error Handling**: Handle kasus input yang tidak valid

**Format Pengumpulan:**
- Algoritma dalam natural language
- Algoritma dalam structured language
- Analisis complexity (time dan space)
- Test cases (minimal 5 contoh)
- Trace algorithm untuk satu test case

**Tugas Tambahan (Opsional):**
Pilih satu aplikasi dari kehidupan sehari-hari dan buat:
1. Problem analysis
2. Algorithm design dengan semua struktur (sequential, selection, iteration)
3. Efficiency analysis
4. Alternative solutions dan comparison

### **7.4 Preparation untuk Minggu Depan**

Minggu depan kita akan masuk ke **"Flowchart & Pseudocode"** yang akan mencakup:

- **Flowchart Symbols**: Standar ISO dan penggunaan yang tepat
- **Flowchart Types**: Process, decision, data flow diagrams
- **Pseudocode Standards**: Best practices dalam penulisan
- **Tools Usage**: Hands-on dengan draw.io
- **Complex Algorithm Visualization**: Multi-level flowcharts

**Persiapan yang Disarankan:**
1. Install atau akses draw.io (online)
2. Review materi minggu 1 dan 2
3. Practice dengan algoritma sederhana
4. Siapkan ide untuk final project

---

## **PENUTUP**

Pemahaman mendalam tentang konsep dasar pemrograman adalah investasi jangka panjang untuk karir di bidang teknologi. Dari warisan intelektual Al-Khwarizmi hingga algoritma modern yang menggerakkan artificial intelligence, prinsip-prinsip fundamental tetap sama: **systematic thinking, logical reasoning, dan efficient problem solving**.

Struktur algoritma yang kita pelajari hari ini - sequential, selection, iteration, function, dan recursion - adalah building blocks yang akan Anda gunakan dalam setiap program yang akan Anda tulis. Penguasaan analisis efisiensi akan membantu Anda membuat keputusan desain yang tepat ketika menghadapi masalah computational yang kompleks.

Ingatlah bahwa **"The best algorithms are not just correct, but also elegant and efficient"**. Teruslah berlatih dan eksperimen dengan berbagai pendekatan problem solving.

Sampai jumpa di pertemuan berikutnya, dimana kita akan mulai memvisualisasikan algoritma melalui flowchart dan pseudocode!

**Happy Algorithmic Thinking!** 🧠💻

---

*Total kata: ~5000 kata*

**Referensi:**
- Tutorialspoint Algorithms Basics: https://www.tutorialspoint.com/data_structures_algorithms/algorithms_basics.htm
- Historical sources on Al-Khwarizmi and Islamic Golden Age mathematics
- Modern computer science textbooks on algorithm analysis and design