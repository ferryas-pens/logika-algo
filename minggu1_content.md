# MINGGU 1: PENGANTAR ALGORITMA DAN PEMROGRAMAN
## Mata Kuliah: Logika dan Algoritma Pemrograman

---

## **TUJUAN PEMBELAJARAN**

Setelah mengikuti pembelajaran pada minggu ini, mahasiswa diharapkan dapat:

1. **Memahami konsep dasar komputer dan cara kerjanya** dalam konteks pemrograman
2. **Menjelaskan definisi program dan bahasa pemrograman** serta peranannya dalam teknologi
3. **Mendefinisikan algoritma dan mengidentifikasi ciri-ciri algoritma yang baik**
4. **Memahami hubungan sistematis antara masalah, model, algoritma, dan program**
5. **Membuat algoritma sederhana** untuk menyelesaikan masalah komputasional dasar

---

## **BAGIAN 1: KONSEP DASAR KOMPUTER**

### **1.1 Definisi Komputer dan Komponennya**

Komputer adalah sebuah mesin elektronik yang dapat menerima data (input), memproses data tersebut sesuai dengan instruksi yang diberikan, dan menghasilkan informasi (output) yang berguna. Untuk memahami pemrograman, kita perlu memahami komponen dasar komputer dan cara kerjanya.

#### **Komponen Utama Komputer:**

**1. Hardware (Perangkat Keras)**
- **CPU (Central Processing Unit)**: "Otak" komputer yang menjalankan instruksi dan melakukan perhitungan
- **Memory/RAM**: Tempat penyimpanan sementara data dan instruksi saat program berjalan
- **Storage**: Penyimpanan permanen untuk data dan program (Hard Disk, SSD)
- **Input Devices**: Keyboard, mouse, microphone, kamera
- **Output Devices**: Monitor, printer, speaker

**2. Software (Perangkat Lunak)**
- **System Software**: Operating System (Windows, Linux, macOS)
- **Application Software**: Program aplikasi yang digunakan user
- **Programming Software**: Compiler, interpreter, IDE (Integrated Development Environment)

#### **1.2 Cara Kerja Komputer: Model Input-Process-Output**

Komputer bekerja mengikuti model sederhana yang disebut **IPO (Input-Process-Output)**:

```
INPUT → PROCESS → OUTPUT
```

**Contoh dalam kehidupan sehari-hari:**
- **Input**: User mengetik angka 5 dan 3 pada kalkulator
- **Process**: CPU melakukan operasi penjumlahan 5 + 3 = 8
- **Output**: Hasil "8" ditampilkan di layar

**Contoh dalam pemrograman:**
```
INPUT: Jari-jari lingkaran = 7
PROCESS: Menghitung luas = π × r² = 3.14 × 7² = 153.86
OUTPUT: Luas lingkaran = 153.86
```

#### **1.3 Sistem Bilangan dalam Komputer**

Komputer hanya memahami sistem bilangan biner (0 dan 1). Pemahaman ini penting untuk memahami bagaimana data disimpan dan diproses.

- **Decimal (Base 10)**: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9
- **Binary (Base 2)**: 0, 1
- **Hexadecimal (Base 16)**: 0-9, A-F

**Contoh Konversi:**
- Decimal 10 = Binary 1010
- Decimal 255 = Binary 11111111 = Hex FF

---

## **BAGIAN 2: PROGRAM DAN BAHASA PEMROGRAMAN**

### **2.1 Definisi Program Komputer**

Program komputer adalah sekumpulan instruksi yang ditulis dalam bahasa yang dapat dipahami komputer untuk menyelesaikan tugas atau masalah tertentu. Program memberitahu komputer "apa yang harus dilakukan" dan "bagaimana melakukannya".

**Karakteristik Program:**
1. **Sequence**: Instruksi dijalankan secara berurutan
2. **Selection**: Program dapat memilih jalur eksekusi berbeda
3. **Iteration**: Program dapat mengulang instruksi tertentu
4. **Modularity**: Program dapat dibagi menjadi bagian-bagian kecil

### **2.2 Jenis-Jenis Bahasa Pemrograman**

#### **Berdasarkan Tingkat Abstraksi:**

**1. Low-Level Languages (Bahasa Tingkat Rendah)**
- **Machine Language**: Kode binary (0,1) yang langsung dipahami CPU
- **Assembly Language**: Menggunakan mnemonic seperti MOV, ADD, SUB

**2. High-Level Languages (Bahasa Tingkat Tinggi)**
- Lebih mudah dipahami manusia
- Membutuhkan compiler/interpreter untuk diterjemahkan ke machine code
- Contoh: C, C++, Java, Python, JavaScript

#### **Berdasarkan Cara Eksekusi:**

**1. Compiled Languages**
- Source code diterjemahkan menjadi machine code sebelum dijalankan
- Contoh: C, C++, Rust, Go
- **Keuntungan**: Eksekusi cepat, tidak butuh runtime environment
- **Kerugian**: Proses kompilasi diperlukan setiap kali ada perubahan

**2. Interpreted Languages**
- Source code diterjemahkan dan dijalankan baris per baris saat runtime
- Contoh: Python, JavaScript, PHP
- **Keuntungan**: Development cepat, testing mudah
- **Kerugian**: Eksekusi lebih lambat, butuh interpreter

### **2.3 Proses Pengembangan Program**

```
Source Code → Compiler/Interpreter → Machine Code → Execution → Output
```

**Langkah-langkah pengembangan program:**
1. **Problem Analysis**: Memahami masalah yang akan diselesaikan
2. **Design**: Merancang solusi dan algoritma
3. **Coding**: Menulis kode program
4. **Testing**: Menguji program dengan berbagai input
5. **Debugging**: Memperbaiki error dan bug
6. **Documentation**: Mendokumentasikan program
7. **Maintenance**: Pemeliharaan dan update program

---

## **BAGIAN 3: DEFINISI DAN KARAKTERISTIK ALGORITMA**

### **3.1 Definisi Algoritma**

Algoritma adalah sekumpulan instruksi yang terdefinisi dengan baik dan berurutan untuk menyelesaikan suatu masalah. Algoritma menerima input dan menghasilkan output yang diinginkan.

**Asal kata "Algoritma":**
Berasal dari nama matematikawan Persia **Abu Ja'far Muhammad ibn Musa al-Khwarizmi** (780-850 M) yang menulis buku tentang sistem angka Hindu-Arab dan aljabar. Kata "algorithm" merupakan latinisasi dari nama "al-Khwarizmi".

#### **Definisi Algoritma Menurut Para Ahli:**
- **Donald Knuth**: "Algoritma adalah prosedur komputasional yang terdefinisi dengan baik yang mengambil beberapa nilai sebagai input dan menghasilkan beberapa nilai sebagai output"
- **Thomas Cormen**: "Algoritma adalah prosedur komputasional yang terdefinisi dengan baik untuk memecahkan masalah"
- **Rinaldi Munir**: "Algoritma adalah urutan langkah-langkah logis penyelesaian masalah yang disusun secara sistematis"

### **3.2 Ciri-Ciri Algoritma yang Baik**

Algoritma yang baik harus memiliki karakteristik berikut:

#### **1. Finite (Terbatas)**
- Algoritma harus berhenti setelah sejumlah langkah terbatas
- Tidak boleh infinite loop tanpa kondisi berhenti

**Contoh Salah:**
```
1. Mulai
2. Baca angka x
3. Cetak x
4. Kembali ke langkah 3  // Infinite loop!
```

**Contoh Benar:**
```
1. Mulai
2. Baca angka x
3. Cetak x
4. Selesai
```

#### **2. Definite (Pasti/Tidak Ambigu)**
- Setiap langkah harus jelas dan tidak bermakna ganda
- Tidak ada interpretasi yang berbeda-beda

**Contoh Ambigu:**
```
"Tambahkan sedikit garam ke dalam adonan"  // "Sedikit" tidak jelas
```

**Contoh Jelas:**
```
"Tambahkan 1 sendok teh garam ke dalam adonan"
```

#### **3. Input (Masukan)**
- Algoritma memiliki nol atau lebih input yang terdefinisi dengan baik
- Input harus jelas jenis dan formatnya

**Contoh:**
```
Input: Dua bilangan bulat positif (a dan b)
```

#### **4. Output (Keluaran)**
- Algoritma harus menghasilkan minimal satu output
- Output harus sesuai dengan tujuan algoritma

**Contoh:**
```
Output: Hasil penjumlahan a + b
```

#### **5. Effective (Efektif)**
- Setiap langkah harus dapat dilaksanakan dalam waktu yang wajar
- Operasi harus cukup dasar sehingga dapat dilakukan secara manual

#### **6. General (Umum)**
- Algoritma harus dapat menyelesaikan semua masalah dalam kategori yang sama
- Tidak hanya untuk kasus spesifik tertentu

### **3.3 Contoh Algoritma Sederhana**

#### **Algoritma 1: Menghitung Luas Lingkaran**
```
ALGORITMA Hitung_Luas_Lingkaran
INPUT: jari_jari (bilangan real positif)
OUTPUT: luas (bilangan real)

LANGKAH:
1. Mulai
2. Baca jari_jari
3. Hitung luas = 3.14159 × jari_jari × jari_jari
4. Tampilkan luas
5. Selesai
```

#### **Algoritma 2: Menentukan Bilangan Terbesar dari Tiga Bilangan**
```
ALGORITMA Bilangan_Terbesar
INPUT: a, b, c (tiga bilangan bulat)
OUTPUT: max (bilangan terbesar)

LANGKAH:
1. Mulai
2. Baca a, b, c
3. Jika a > b DAN a > c maka
     max = a
   Jika tidak, jika b > a DAN b > c maka
     max = b
   Jika tidak
     max = c
4. Tampilkan max
5. Selesai
```

---

## **BAGIAN 4: HUBUNGAN MASALAH → MODEL → ALGORITMA → PROGRAM**

### **4.1 Metodologi Penyelesaian Masalah**

Dalam pemrograman, kita mengikuti pendekatan sistematis untuk menyelesaikan masalah:

```
MASALAH REAL → MODEL ABSTRAK → ALGORITMA → PROGRAM → SOLUSI
```

#### **Langkah 1: Identifikasi Masalah**
- Memahami masalah yang akan diselesaikan
- Mengidentifikasi input dan output yang diharapkan
- Menentukan batasan dan constraints

**Contoh Masalah:**
"Seorang kasir di toko perlu menghitung total harga belanja customer dan kembalian yang harus diberikan."

#### **Langkah 2: Abstraksi ke Model**
- Menyederhanakan masalah dengan fokus pada aspek penting
- Mengabaikan detail yang tidak relevan
- Mendefinisikan variabel dan hubungannya

**Model untuk contoh di atas:**
- **Input**: Daftar harga barang, jumlah uang yang dibayar
- **Process**: Penjumlahan total harga, pengurangan dengan uang yang dibayar
- **Output**: Total harga, kembalian
- **Constraints**: Uang yang dibayar ≥ total harga

#### **Langkah 3: Desain Algoritma**
- Merancang langkah-langkah penyelesaian
- Menggunakan struktur kontrol (sequence, selection, iteration)
- Memastikan algoritma efisien dan benar

**Algoritma untuk contoh:**
```
ALGORITMA Kasir_Toko
1. Mulai
2. Inisialisasi total_harga = 0
3. Untuk setiap barang:
   3.1 Baca harga_barang
   3.2 total_harga = total_harga + harga_barang
4. Tampilkan total_harga
5. Baca uang_dibayar
6. Jika uang_dibayar < total_harga maka
     Tampilkan "Uang tidak cukup"
   Jika tidak
     kembalian = uang_dibayar - total_harga
     Tampilkan kembalian
7. Selesai
```

#### **Langkah 4: Implementasi Program**
- Menerjemahkan algoritma ke dalam bahasa pemrograman
- Memilih struktur data yang sesuai
- Mengoptimalkan kode

### **4.2 Contoh Lengkap: Dari Masalah ke Program**

#### **Masalah:**
"Sebuah sekolah ingin menghitung rata-rata nilai ujian siswa dan menentukan apakah siswa lulus atau tidak. Syarat lulus adalah rata-rata ≥ 70."

#### **Model:**
- **Input**: Nilai ujian matematika, fisika, kimia
- **Process**: Hitung rata-rata = (math + physics + chemistry) / 3
- **Decision**: Jika rata-rata ≥ 70 → Lulus, selainnya → Tidak Lulus
- **Output**: Rata-rata dan status kelulusan

#### **Algoritma:**
```
ALGORITMA Penentuan_Kelulusan
INPUT: nilai_math, nilai_physics, nilai_chemistry
OUTPUT: rata_rata, status_lulus

LANGKAH:
1. Mulai
2. Baca nilai_math, nilai_physics, nilai_chemistry
3. rata_rata = (nilai_math + nilai_physics + nilai_chemistry) / 3
4. Jika rata_rata >= 70 maka
     status_lulus = "LULUS"
   Jika tidak
     status_lulus = "TIDAK LULUS"
5. Tampilkan rata_rata dan status_lulus
6. Selesai
```

#### **Program (dalam pseudocode):**
```c
#include <stdio.h>

int main() {
    float math, physics, chemistry, rata_rata;
    
    printf("Masukkan nilai matematika: ");
    scanf("%f", &math);
    printf("Masukkan nilai fisika: ");
    scanf("%f", &physics);
    printf("Masukkan nilai kimia: ");
    scanf("%f", &chemistry);
    
    rata_rata = (math + physics + chemistry) / 3.0;
    
    printf("Rata-rata: %.2f\n", rata_rata);
    
    if (rata_rata >= 70) {
        printf("Status: LULUS\n");
    } else {
        printf("Status: TIDAK LULUS\n");
    }
    
    return 0;
}
```

---

## **BAGIAN 5: EFISIENSI ALGORITMA**

### **5.1 Konsep Efisiensi**

Efisiensi algoritma mengukur seberapa baik algoritma menggunakan sumber daya komputer. Terdapat dua jenis efisiensi utama:

#### **1. Time Complexity (Kompleksitas Waktu)**
- Mengukur waktu yang dibutuhkan algoritma untuk menyelesaikan masalah
- Biasanya dinyatakan sebagai fungsi dari ukuran input

**Contoh:**
- **Linear Search**: Untuk mencari 1 item dalam 1000 item, worst case perlu mengecek semua 1000 item
- **Binary Search**: Untuk mencari 1 item dalam 1000 item, maksimal perlu 10 langkah

#### **2. Space Complexity (Kompleksitas Ruang)**
- Mengukur memori yang dibutuhkan algoritma
- Termasuk memori untuk variabel, struktur data, dan recursive calls

### **5.2 Notasi Big O (Pengenalan)**

Big O notation digunakan untuk menggambarkan efisiensi algoritma:

- **O(1)**: Constant time - waktu eksekusi tetap
- **O(n)**: Linear time - waktu eksekusi sebanding dengan ukuran input
- **O(n²)**: Quadratic time - waktu eksekusi sebanding dengan kuadrat ukuran input

**Contoh Algoritma O(1):**
```
ALGORITMA Akses_Array_Element
1. Baca index i
2. Tampilkan array[i]
```

**Contoh Algoritma O(n):**
```
ALGORITMA Cari_Maximum
1. max = array[0]
2. Untuk i = 1 sampai n-1:
   2.1 Jika array[i] > max maka max = array[i]
3. Tampilkan max
```

---

## **BAGIAN 6: REPRESENTASI ALGORITMA**

### **6.1 Natural Language (Bahasa Alami)**

Algoritma dapat ditulis menggunakan bahasa sehari-hari yang mudah dipahami.

**Contoh: Algoritma Membuat Teh**
```
1. Siapkan gelas, teh celup, gula, dan air panas
2. Masukkan teh celup ke dalam gelas
3. Tuangkan air panas ke dalam gelas
4. Tunggu 3-5 menit agar teh meresap
5. Angkat teh celup dari gelas
6. Tambahkan gula sesuai selera
7. Aduk hingga gula larut
8. Teh siap diminum
```

### **6.2 Structured Language (Bahasa Terstruktur)**

Menggunakan kata kunci khusus untuk memperjelas struktur algoritma.

**Kata Kunci Umum:**
- **MULAI/START** dan **SELESAI/END**: Menandai awal dan akhir algoritma
- **BACA/READ** dan **TULIS/WRITE**: Input dan output
- **JIKA...MAKA.../IF...THEN...**: Percabangan
- **SELAMA/WHILE** dan **UNTUK/FOR**: Perulangan

**Contoh:**
```
ALGORITMA Faktorial
INPUT: n (bilangan bulat non-negatif)
OUTPUT: faktorial (hasil n!)

MULAI
  BACA n
  faktorial ← 1
  UNTUK i = 1 SAMPAI n LAKUKAN
    faktorial ← faktorial × i
  TULIS faktorial
SELESAI
```

---

## **BAGIAN 7: STUDI KASUS DAN CONTOH IMPLEMENTASI**

### **7.1 Studi Kasus 1: Konverter Suhu**

#### **Masalah:**
Membuat program untuk mengkonversi suhu dari Celsius ke Fahrenheit dan Kelvin.

#### **Analisis:**
- **Input**: Suhu dalam Celsius
- **Process**: 
  - Fahrenheit = (Celsius × 9/5) + 32
  - Kelvin = Celsius + 273.15
- **Output**: Suhu dalam Fahrenheit dan Kelvin

#### **Algoritma:**
```
ALGORITMA Konverter_Suhu
INPUT: celsius
OUTPUT: fahrenheit, kelvin

LANGKAH:
1. MULAI
2. BACA celsius
3. fahrenheit ← (celsius × 9/5) + 32
4. kelvin ← celsius + 273.15
5. TULIS "Celsius: ", celsius
6. TULIS "Fahrenheit: ", fahrenheit
7. TULIS "Kelvin: ", kelvin
8. SELESAI
```

### **7.2 Studi Kasus 2: Kalkulator BMI**

#### **Masalah:**
Menghitung Body Mass Index (BMI) dan menentukan kategori kesehatan.

#### **Analisis:**
- **Input**: Berat badan (kg), Tinggi badan (m)
- **Process**: BMI = berat / (tinggi²)
- **Classification**:
  - BMI < 18.5: Underweight
  - 18.5 ≤ BMI < 25: Normal
  - 25 ≤ BMI < 30: Overweight
  - BMI ≥ 30: Obese

#### **Algoritma:**
```
ALGORITMA Kalkulator_BMI
INPUT: berat, tinggi
OUTPUT: bmi, kategori

LANGKAH:
1. MULAI
2. BACA berat, tinggi
3. bmi ← berat / (tinggi × tinggi)
4. JIKA bmi < 18.5 MAKA
     kategori ← "Underweight"
   JIKA TIDAK JIKA bmi < 25 MAKA
     kategori ← "Normal"
   JIKA TIDAK JIKA bmi < 30 MAKA
     kategori ← "Overweight"
   JIKA TIDAK
     kategori ← "Obese"
5. TULIS "BMI: ", bmi
6. TULIS "Kategori: ", kategori
7. SELESAI
```

### **7.3 Studi Kasus 3: Pencarian Nilai Minimum**

#### **Masalah:**
Mencari nilai terkecil dari sekumpulan bilangan.

#### **Algoritma:**
```
ALGORITMA Cari_Minimum
INPUT: n (jumlah bilangan), array bilangan[1..n]
OUTPUT: minimum

LANGKAH:
1. MULAI
2. BACA n
3. UNTUK i = 1 SAMPAI n LAKUKAN
     BACA bilangan[i]
4. minimum ← bilangan[1]
5. UNTUK i = 2 SAMPAI n LAKUKAN
     JIKA bilangan[i] < minimum MAKA
       minimum ← bilangan[i]
6. TULIS "Nilai minimum: ", minimum
7. SELESAI
```

---

## **BAGIAN 8: LATIHAN DAN EVALUASI**

### **8.1 Latihan Mandiri**

#### **Latihan 1: Algoritma Sederhana**
Buat algoritma untuk menghitung:
1. Luas dan keliling persegi panjang
2. Volume kubus
3. Rata-rata dari 5 bilangan

#### **Latihan 2: Algoritma dengan Kondisi**
Buat algoritma untuk:
1. Menentukan bilangan genap atau ganjil
2. Mencari nilai terbesar dari 4 bilangan
3. Menentukan jenis segitiga (sama sisi, sama kaki, sembarang)

#### **Latihan 3: Algoritma dengan Perulangan**
Buat algoritma untuk:
1. Menghitung jumlah bilangan 1 sampai n
2. Menampilkan tabel perkalian
3. Mencari bilangan prima dalam rentang tertentu

### **8.2 Soal Evaluasi**

#### **Soal 1 (Teori):**
Jelaskan perbedaan antara algoritma dan program! Berikan contoh masing-masing.

#### **Soal 2 (Praktik):**
Buat algoritma untuk menghitung gaji karyawan dengan ketentuan:
- Gaji pokok berdasarkan golongan (A: 3,000,000, B: 2,500,000, C: 2,000,000)
- Tunjangan 10% dari gaji pokok
- Potongan pajak 5% dari total gaji (gaji pokok + tunjangan)

#### **Soal 3 (Analisis):**
Analisis efisiensi algoritma berikut dan berikan perbaikan jika perlu:
```
ALGORITMA Cari_Duplikat
UNTUK i = 1 SAMPAI n LAKUKAN
  UNTUK j = i+1 SAMPAI n LAKUKAN
    JIKA array[i] = array[j] MAKA
      TULIS "Ditemukan duplikat: ", array[i]
```

---

## **BAGIAN 9: TOOLS DAN RESOURCES**

### **9.1 Recommended Online Resources**

#### **Pembelajaran Interaktif:**
- **W3Schools Programming**: Platform komprehensif untuk mempelajari konsep dasar pemrograman
- **Programiz**: Tutorial mudah diikuti untuk Python, C/C++, Java dengan compiler online
- **Codecademy**: Interactive coding lessons
- **Khan Academy Computer Programming**: Visual programming basics

#### **Visualisasi Algoritma:**
- **Algorithm Visualizer**: Visualisasi algoritma sorting dan searching
- **VisuAlgo**: Comprehensive algorithm visualization
- **Python Tutor**: Step-by-step code execution visualization

#### **Online Compilers:**
- **OnlineGDB**: Multi-language online compiler
- **Repl.it**: Cloud-based development environment
- **CodePen**: For web-based programming
- **Programiz Online Compiler**: Simple and clean interface

### **9.2 Recommended Books**
- **"Introduction to Algorithms" by Cormen, Leiserson, Rivest, and Stein**: Comprehensive algorithm textbook
- **"The Art of Computer Programming" by Donald Knuth**: Classic computer science reference
- **"Algoritma dan Pemrograman" by Rinaldi Munir**: Bahasa Indonesia reference

---

## **BAGIAN 10: RANGKUMAN DAN NEXT STEPS**

### **10.1 Rangkuman Materi**

Pada minggu ini, kita telah mempelajari:

1. **Konsep Dasar Komputer**: Hardware, software, dan model IPO (Input-Process-Output)
2. **Program dan Bahasa Pemrograman**: Jenis bahasa pemrograman dan proses pengembangan
3. **Algoritma**: Definisi, karakteristik, dan contoh-contoh algoritma sederhana
4. **Problem-Solving Methodology**: Hubungan sistematis masalah → model → algoritma → program
5. **Efisiensi**: Konsep time dan space complexity
6. **Representasi**: Cara menulis algoritma yang jelas dan terstruktur

### **10.2 Key Takeaways**

- **Algoritma adalah fondasi pemrograman**: Sebelum menulis kode, kita harus merancang algoritma yang jelas
- **Problem-solving approach**: Pendekatan sistematis dari analisis masalah hingga implementasi
- **Karakteristik algoritma baik**: Finite, definite, memiliki input/output, effective, dan general
- **Pentingnya efisiensi**: Memilih algoritma yang tepat dapat menghemat waktu dan sumber daya

### **10.3 Persiapan Minggu Depan**

Minggu depan kita akan mempelajari **"Konsep Dasar Pemrograman"** yang akan mencakup:
- Sejarah algoritma lebih detail (Al-Khwarizmi)
- Struktur algoritma (sekuensial, percabangan, looping, fungsi, rekursi)
- Analisis kompleksitas algoritma
- Fungsi algoritma dalam problem solving dan automation

### **10.4 Assignment untuk Minggu Depan**

**Tugas 1: Algoritma Luas Lingkaran (Wajib)**
Buat algoritma lengkap untuk menghitung luas lingkaran dengan input jari-jari. Algoritma harus mencakup:
- Input validation (jari-jari harus positif)
- Perhitungan dengan konstanta π = 3.14159
- Output yang informatif

**Format pengumpulan:**
1. Natural language algorithm
2. Structured language algorithm
3. Analisis input, process, output
4. Test cases (minimal 3 contoh)

**Tugas 2: Eksplorasi (Opsional)**
Pilih satu masalah dari kehidupan sehari-hari dan buatlah:
1. Analisis masalah
2. Model abstrak
3. Algoritma penyelesaian
4. Contoh implementasi dalam pseudocode

---

## **PENUTUP**

Pemrograman adalah skill yang sangat berharga di era digital ini. Namun, sebelum kita bisa menjadi programmer yang baik, kita harus memahami fondasi dasarnya: **algoritma**. Algoritma mengajarkan kita cara berpikir logis, sistematis, dan terstruktur dalam menyelesaikan masalah.

Ingatlah bahwa **"Algoritma yang baik adalah setengah dari solusi yang baik"**. Investasi waktu untuk memahami konsep dasar ini akan memberikan manfaat jangka panjang dalam perjalanan pembelajaran pemrograman Anda.

Pada pertemuan selanjutnya, kita akan mendalami struktur-struktur algoritma yang akan menjadi building blocks untuk membuat program yang lebih kompleks dan powerful.

**Happy Learning!** 🚀

---

**Referensi:**
- W3Schools Programming Concepts: https://www.w3schools.com/programming/
- Programiz Algorithm Tutorial: https://www.programiz.com/dsa/algorithm
- Various computer science textbooks and online resources
