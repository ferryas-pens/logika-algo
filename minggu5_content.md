# Minggu 5: Operasi Seleksi (Decision/Branching)
## Logika dan Pemrograman

---

## 🎯 Tujuan Pembelajaran

Setelah mempelajari materi ini, mahasiswa diharapkan mampu:

1. **Memahami konsep dasar decision making** dalam pemrograman dan pentingnya struktur seleksi
2. **Menguasai statement if** dan implementasinya dalam berbagai kondisi
3. **Menggunakan if-else statement** untuk menangani kondisi true dan false
4. **Memahami nested if** dan penggunaannya dalam kondisi berlapis
5. **Menguasai switch-case statement** sebagai alternatif dari if-else ladder
6. **Merancang algoritma** yang menggunakan struktur seleksi untuk menyelesaikan masalah
7. **Membuat flowchart** untuk representasi visual algoritma dengan decision making
8. **Mengimplementasikan studi kasus** seperti penentuan lulus/tidak lulus dan sistem grading

---

## 🧠 Konsep Dasar Decision Making

### Apa itu Decision Making?

Decision making atau pengambilan keputusan adalah kemampuan program untuk memilih bagian kode mana yang akan dieksekusi berdasarkan kondisi tertentu. Dalam kehidupan sehari-hari, kita selalu membuat keputusan - seperti memilih makanan favorit atau warna mobil baru. Dalam pemrograman C, kita juga sering menghadapi situasi dimana program perlu membuat keputusan.

### Mengapa Decision Making Penting?

1. **Kontrol Alur Program**: Menentukan jalur eksekusi program berdasarkan kondisi
2. **Validasi Input**: Memastikan data yang dimasukkan user sesuai kriteria
3. **Logika Bisnis**: Mengimplementasikan aturan dan kebijakan dalam aplikasi
4. **Error Handling**: Menangani situasi error dan memberikan respons yang tepat

### Jenis-Jenis Conditional Statements

C menyediakan tiga jenis utama conditional statement:

1. **if statement** - Eksekusi kondisional sederhana
2. **if...else statement** - Pilihan antara dua alternatif
3. **switch statement** - Pilihan dari multiple alternatif

---

## 🔍 If Statement

### Sintaks dan Struktur

If statement adalah conditional statement paling dasar dalam C. Jika programmer ingin mengeksekusi beberapa statement hanya ketika kondisi tertentu terpenuhi, maka single if statement dapat digunakan.

```c
if (test expression) {
    // code
}
```

### Cara Kerja If Statement

If statement mengevaluasi test expression di dalam tanda kurung (). Jika test expression dievaluasi menjadi true, statements di dalam body if dieksekusi. Jika test expression dievaluasi menjadi false, statements di dalam body if tidak dieksekusi.

### Contoh Implementasi

#### Contoh 1: Program Menampilkan Bilangan Negatif
```c
// Program to display a number if it is negative
#include <stdio.h>
int main() {
    int number;
    
    printf("Enter an integer: ");
    scanf("%d", &number);
    
    // true if number is less than 0
    if (number < 0) {
        printf("You entered %d.\n", number);
    }
    
    printf("The if statement is easy.");
    return 0;
}
```

**Output 1:**
```
Enter an integer: -2
You entered -2.
The if statement is easy.
```

**Output 2:**
```
Enter an integer: 5
The if statement is easy.
```

Ketika user memasukkan -2, test expression number<0 dievaluasi menjadi true. Oleh karena itu, "You entered -2" ditampilkan di layar. Ketika user memasukkan 5, test expression number<0 dievaluasi menjadi false dan statement di dalam body if tidak dieksekusi.

#### Contoh 2: Validasi Nilai Ujian
```c
#include <stdio.h>
int main() {
    float nilai;
    
    printf("Masukkan nilai ujian: ");
    scanf("%f", &nilai);
    
    if (nilai >= 70) {
        printf("Selamat! Anda LULUS\n");
    }
    
    printf("Program selesai.\n");
    return 0;
}
```

#### Contoh 3: Cek Bilangan Positif
```c
#include <stdio.h>
int main() {
    int angka;
    
    printf("Masukkan sebuah angka: ");
    scanf("%d", &angka);
    
    if (angka > 0) {
        printf("%d adalah bilangan positif\n", angka);
    }
    
    if (angka == 0) {
        printf("Angka yang dimasukkan adalah nol\n");
    }
    
    return 0;
}
```

### Kondisi dalam If Statement

Test expression dapat menggunakan:
- **Relational operators**: `<`, `>`, `<=`, `>=`, `==`, `!=`
- **Logical operators**: `&&` (AND), `||` (OR), `!` (NOT)
- **Variabel boolean**: `1` (true), `0` (false)

---

## ⚖️ If-Else Statement

### Sintaks dan Struktur

If statement mungkin memiliki blok else yang opsional. Sintaks dari if..else statement adalah:

```c
if (test expression) {
    // run code if test expression is true
}
else {
    // run code if test expression is false
}
```

### Cara Kerja If-Else Statement

Jika test expression dievaluasi menjadi true, statements di dalam body if dieksekusi dan statements di dalam body else dilewati. Jika test expression dievaluasi menjadi false, statements di dalam body else dieksekusi dan statements di dalam body if dilewati.

### Contoh Implementasi

#### Contoh 1: Menentukan Bilangan Genap/Ganjil
```c
// Check whether an integer is odd or even
#include <stdio.h>
int main() {
    int number;
    
    printf("Enter an integer: ");
    scanf("%d", &number);
    
    // True if the remainder is 0
    if (number % 2 == 0) {
        printf("%d is an even integer.", number);
    }
    else {
        printf("%d is an odd integer.", number);
    }
    
    return 0;
}
```

**Output:**
```
Enter an integer: 7
7 is an odd integer.
```

Ketika user memasukkan 7, test expression number%2==0 dievaluasi menjadi false. Oleh karena itu, statement di dalam body else dieksekusi.

#### Contoh 2: Sistem Lulus/Tidak Lulus
```c
#include <stdio.h>
int main() {
    float nilai;
    
    printf("Masukkan nilai ujian: ");
    scanf("%f", &nilai);
    
    if (nilai >= 70) {
        printf("LULUS - Selamat!\n");
        printf("Nilai Anda: %.2f\n", nilai);
    }
    else {
        printf("TIDAK LULUS - Belajar lebih giat!\n");
        printf("Nilai Anda: %.2f\n", nilai);
        printf("Nilai minimum untuk lulus: 70\n");
    }
    
    return 0;
}
```

#### Contoh 3: Menentukan Bilangan Terbesar dari Dua Angka
```c
#include <stdio.h>
int main() {
    int num1, num2;
    
    printf("Masukkan dua bilangan: ");
    scanf("%d %d", &num1, &num2);
    
    if (num1 > num2) {
        printf("%d adalah bilangan yang lebih besar\n", num1);
    }
    else {
        printf("%d adalah bilangan yang lebih besar\n", num2);
    }
    
    return 0;
}
```

### Multiple Conditions

If-else dapat dikombinasikan dengan logical operators:

```c
#include <stdio.h>
int main() {
    int umur;
    char sim;
    
    printf("Masukkan umur: ");
    scanf("%d", &umur);
    printf("Punya SIM? (y/n): ");
    scanf(" %c", &sim);
    
    if (umur >= 17 && (sim == 'y' || sim == 'Y')) {
        printf("Boleh mengemudi mobil\n");
    }
    else {
        printf("Tidak boleh mengemudi mobil\n");
        if (umur < 17) {
            printf("Umur belum cukup (minimal 17 tahun)\n");
        }
        if (sim != 'y' && sim != 'Y') {
            printf("Harus memiliki SIM terlebih dahulu\n");
        }
    }
    
    return 0;
}
```

---

## 🎚️ If-Else Ladder

### Konsep If-Else Ladder

If...else statement mengeksekusi dua kode berbeda tergantung pada apakah test expression true atau false. Terkadang, pilihan harus dibuat dari lebih dari 2 kemungkinan. If...else ladder memungkinkan Anda untuk mengecek antara multiple test expressions dan mengeksekusi statements yang berbeda.

### Sintaks If-Else Ladder

```c
if (test expression1) {
    // statement(s)
}
else if(test expression2) {
    // statement(s)
}
else if (test expression3) {
    // statement(s)
}
.
.
else {
    // statement(s)
}
```

### Contoh Implementasi

#### Contoh 1: Membandingkan Dua Bilangan
```c
// Program to relate two integers using =, > or < symbol
#include <stdio.h>
int main() {
    int number1, number2;
    
    printf("Enter two integers: ");
    scanf("%d %d", &number1, &number2);
    
    //checks if the two integers are equal.
    if(number1 == number2) {
        printf("Result: %d = %d", number1, number2);
    }
    //checks if number1 is greater than number2.
    else if (number1 > number2) {
        printf("Result: %d > %d", number1, number2);
    }
    //checks if both test expressions are false
    else {
        printf("Result: %d < %d", number1, number2);
    }
    
    return 0;
}
```

**Output:**
```
Enter two integers: 12 23
Result: 12 < 23
```

#### Contoh 2: Sistem Grading
```c
#include <stdio.h>
int main() {
    float nilai;
    
    printf("Masukkan nilai (0-100): ");
    scanf("%f", &nilai);
    
    if (nilai >= 85) {
        printf("Grade: A (Excellent)\n");
    }
    else if (nilai >= 70) {
        printf("Grade: B (Good)\n");
    }
    else if (nilai >= 55) {
        printf("Grade: C (Fair)\n");
    }
    else if (nilai >= 40) {
        printf("Grade: D (Poor)\n");
    }
    else {
        printf("Grade: F (Fail)\n");
    }
    
    return 0;
}
```

#### Contoh 3: Kalkulator BMI
```c
#include <stdio.h>
int main() {
    float tinggi, berat, bmi;
    
    printf("Masukkan tinggi badan (m): ");
    scanf("%f", &tinggi);
    printf("Masukkan berat badan (kg): ");
    scanf("%f", &berat);
    
    bmi = berat / (tinggi * tinggi);
    
    printf("BMI Anda: %.2f\n", bmi);
    
    if (bmi < 18.5) {
        printf("Kategori: Underweight\n");
    }
    else if (bmi < 25.0) {
        printf("Kategori: Normal weight\n");
    }
    else if (bmi < 30.0) {
        printf("Kategori: Overweight\n");
    }
    else {
        printf("Kategori: Obesity\n");
    }
    
    return 0;
}
```

---

## 🪆 Nested If-Else

### Konsep Nested If-Else

Dimungkinkan untuk menyertakan if...else statement di dalam body dari if...else statement lainnya. Nested if-else berguna ketika kita perlu melakukan multiple checks yang saling bergantung.

### Contoh Implementasi

#### Contoh 1: Membandingkan Dua Bilangan (Nested Version)
```c
#include <stdio.h>
int main() {
    int number1, number2;
    
    printf("Enter two integers: ");
    scanf("%d %d", &number1, &number2);
    
    if (number1 >= number2) {
        if (number1 == number2) {
            printf("Result: %d = %d", number1, number2);
        }
        else {
            printf("Result: %d > %d", number1, number2);
        }
    }
    else {
        printf("Result: %d < %d", number1, number2);
    }
    
    return 0;
}
```

#### Contoh 2: Sistem Penerimaan Mahasiswa
```c
#include <stdio.h>
int main() {
    float nilai_matematika, nilai_fisika, rata_rata;
    
    printf("Masukkan nilai Matematika: ");
    scanf("%f", &nilai_matematika);
    printf("Masukkan nilai Fisika: ");
    scanf("%f", &nilai_fisika);
    
    rata_rata = (nilai_matematika + nilai_fisika) / 2;
    
    printf("Rata-rata nilai: %.2f\n", rata_rata);
    
    if (rata_rata >= 70) {
        if (nilai_matematika >= 60 && nilai_fisika >= 60) {
            printf("DITERIMA di jurusan Teknik\n");
            
            if (rata_rata >= 90) {
                printf("Mendapat beasiswa prestasi!\n");
            }
        }
        else {
            printf("TIDAK DITERIMA - Ada nilai mata pelajaran di bawah 60\n");
        }
    }
    else {
        printf("TIDAK DITERIMA - Rata-rata nilai kurang dari 70\n");
    }
    
    return 0;
}
```

#### Contoh 3: Sistem Diskon Berdasarkan Membership
```c
#include <stdio.h>
int main() {
    int is_member, purchase_amount;
    float discount = 0, final_amount;
    
    printf("Apakah Anda member? (1=Ya, 0=Tidak): ");
    scanf("%d", &is_member);
    printf("Masukkan jumlah pembelian: Rp ");
    scanf("%d", &purchase_amount);
    
    if (is_member == 1) {
        if (purchase_amount >= 500000) {
            discount = 0.15; // 15% discount
            printf("Diskon member premium: 15%%\n");
        }
        else if (purchase_amount >= 200000) {
            discount = 0.10; // 10% discount
            printf("Diskon member regular: 10%%\n");
        }
        else {
            discount = 0.05; // 5% discount
            printf("Diskon member basic: 5%%\n");
        }
    }
    else {
        if (purchase_amount >= 300000) {
            discount = 0.05; // 5% discount for non-members
            printf("Diskon pembelian besar: 5%%\n");
        }
        else {
            printf("Tidak ada diskon\n");
        }
    }
    
    final_amount = purchase_amount - (purchase_amount * discount);
    printf("Jumlah yang harus dibayar: Rp %.0f\n", final_amount);
    
    return 0;
}
```

---

## 🔀 Switch-Case Statement

### Konsep Switch Statement

Switch statement memungkinkan kita untuk mengeksekusi satu blok kode di antara banyak alternatif. Anda dapat melakukan hal yang sama dengan if...else..if ladder. Namun, sintaks dari switch statement jauh lebih mudah dibaca dan ditulis.

### Sintaks Switch-Case

```c
switch (expression) {
    case constant1:
        // statements
        break;
    case constant2:
        // statements
        break;
    .
    .
    .
    default:
        // default statements
}
```

### Cara Kerja Switch Statement

Expression dievaluasi sekali dan dibandingkan dengan nilai dari setiap case label. Jika ada yang cocok, statements yang sesuai setelah matching label dieksekusi. Sebagai contoh, jika nilai expression sama dengan constant2, statements setelah case constant2: dieksekusi sampai break ditemukan. Jika tidak ada yang cocok, default statements dieksekusi.

### Contoh Implementasi

#### Contoh 1: Kalkulator Sederhana
```c
// Program to create a simple calculator
#include <stdio.h>
int main() {
    char operation;
    double n1, n2;
    
    printf("Enter an operator (+, -, *, /): ");
    scanf("%c", &operation);
    printf("Enter two operands: ");
    scanf("%lf %lf", &n1, &n2);
    
    switch(operation) {
        case '+':
            printf("%.1lf + %.1lf = %.1lf", n1, n2, n1+n2);
            break;
        case '-':
            printf("%.1lf - %.1lf = %.1lf", n1, n2, n1-n2);
            break;
        case '*':
            printf("%.1lf * %.1lf = %.1lf", n1, n2, n1*n2);
            break;
        case '/':
            printf("%.1lf / %.1lf = %.1lf", n1, n2, n1/n2);
            break;
        // operator doesn't match any case constant +, -, *, /
        default:
            printf("Error! operator is not correct");
    }
    
    return 0;
}
```

**Output:**
```
Enter an operator (+, -, *, /): -
Enter two operands: 32.5 12.4
32.5 - 12.4 = 20.1
```

#### Contoh 2: Menu Sistem
```c
#include <stdio.h>
int main() {
    int pilihan;
    
    printf("=== MENU UTAMA ===\n");
    printf("1. Tambah Data\n");
    printf("2. Lihat Data\n");
    printf("3. Edit Data\n");
    printf("4. Hapus Data\n");
    printf("5. Keluar\n");
    printf("Pilih menu (1-5): ");
    scanf("%d", &pilihan);
    
    switch(pilihan) {
        case 1:
            printf("Anda memilih: Tambah Data\n");
            printf("Fitur ini akan menambahkan data baru\n");
            break;
        case 2:
            printf("Anda memilih: Lihat Data\n");
            printf("Menampilkan semua data...\n");
            break;
        case 3:
            printf("Anda memilih: Edit Data\n");
            printf("Fitur untuk mengubah data existing\n");
            break;
        case 4:
            printf("Anda memilih: Hapus Data\n");
            printf("Fitur untuk menghapus data\n");
            break;
        case 5:
            printf("Terima kasih! Program berakhir.\n");
            break;
        default:
            printf("Pilihan tidak valid! Silakan pilih 1-5\n");
    }
    
    return 0;
}
```

#### Contoh 3: Konversi Nilai Huruf
```c
#include <stdio.h>
int main() {
    char grade;
    
    printf("Masukkan grade (A, B, C, D, F): ");
    scanf(" %c", &grade);
    
    switch(grade) {
        case 'A':
        case 'a':
            printf("Excellent! Nilai: 85-100\n");
            printf("Keterangan: Sangat Baik\n");
            break;
        case 'B':
        case 'b':
            printf("Good! Nilai: 70-84\n");
            printf("Keterangan: Baik\n");
            break;
        case 'C':
        case 'c':
            printf("Fair! Nilai: 55-69\n");
            printf("Keterangan: Cukup\n");
            break;
        case 'D':
        case 'd':
            printf("Poor! Nilai: 40-54\n");
            printf("Keterangan: Kurang\n");
            break;
        case 'F':
        case 'f':
            printf("Fail! Nilai: 0-39\n");
            printf("Keterangan: Gagal\n");
            break;
        default:
            printf("Grade tidak valid! Gunakan A, B, C, D, atau F\n");
    }
    
    return 0;
}
```

### Penting tentang Break Statement

Jika kita tidak menggunakan break statement, semua statements setelah matching label juga akan dieksekusi. Contoh tanpa break:

```c
#include <stdio.h>
int main() {
    int day = 2;
    
    switch(day) {
        case 1:
            printf("Senin\n");
        case 2:
            printf("Selasa\n");
        case 3:
            printf("Rabu\n");
        default:
            printf("Hari lainnya\n");
    }
    
    return 0;
}
```

**Output:**
```
Selasa
Rabu
Hari lainnya
```

---

## 📊 Flowchart untuk Decision Making

### Flowchart If Statement

```
[START]
    ↓
[Input/Inisialisasi]
    ↓
[Kondisi True?] → [Tidak] → [Statement setelah if]
    ↓ [Ya]                      ↓
[Eksekusi statement if]         ↓
    ↓                          ↓
[Statement setelah if] ← ← ← ←
    ↓
[END]
```

### Flowchart If-Else Statement

```
[START]
    ↓
[Input/Inisialisasi]
    ↓
[Kondisi True?] → [Tidak] → [Eksekusi statement else]
    ↓ [Ya]                      ↓
[Eksekusi statement if]         ↓
    ↓                          ↓
[Statement setelah if-else] ← ←
    ↓
[END]
```

### Flowchart Switch-Case

```
[START]
    ↓
[Input/Inisialisasi]
    ↓
[Evaluasi expression]
    ↓
[Match case 1?] → [Ya] → [Eksekusi case 1] → [break?] → [Ya] → [END]
    ↓ [Tidak]                                    ↓ [Tidak]
[Match case 2?] → [Ya] → [Eksekusi case 2] → [break?] → [Ya] → [END]
    ↓ [Tidak]                                    ↓ [Tidak]
[Match case n?] → [Ya] → [Eksekusi case n] → [break?] → [Ya] → [END]
    ↓ [Tidak]                                    ↓ [Tidak]
[Eksekusi default] → [END]                [Lanjut ke case berikutnya]
```

---

## 🎯 Studi Kasus dan Implementasi

### Studi Kasus 1: Sistem Penentuan Lulus/Tidak Lulus

Sesuai dengan requirement dalam silabus, mari kita implementasikan sistem penentuan lulus/tidak lulus:

```c
#include <stdio.h>
int main() {
    float nilai;
    
    printf("=== SISTEM PENENTUAN KELULUSAN ===\n");
    printf("Masukkan nilai ujian (0-100): ");
    scanf("%f", &nilai);
    
    // Validasi input
    if (nilai < 0 || nilai > 100) {
        printf("Error: Nilai harus antara 0-100\n");
        return 1;
    }
    
    // Penentuan kelulusan sesuai requirement: ≥70 LULUS
    if (nilai >= 70) {
        printf("LULUS\n");
        printf("Selamat! Anda berhasil lulus ujian.\n");
        printf("Nilai Anda: %.2f\n", nilai);
        
        // Tambahan: kategori kelulusan
        if (nilai >= 90) {
            printf("Kategori: Cum Laude\n");
        }
        else if (nilai >= 80) {
            printf("Kategori: Sangat Memuaskan\n");
        }
        else {
            printf("Kategori: Memuaskan\n");
        }
    }
    else {
        printf("TIDAK LULUS\n");
        printf("Maaf, Anda belum berhasil lulus ujian.\n");
        printf("Nilai Anda: %.2f\n", nilai);
        printf("Nilai minimum untuk lulus: 70.00\n");
        printf("Selisih dari nilai lulus: %.2f\n", 70.0 - nilai);
    }
    
    return 0;
}
```

### Studi Kasus 2: Aplikasi ATM Sederhana

```c
#include <stdio.h>
int main() {
    int pilihan, pin, saldo = 1000000;
    int jumlah, pin_benar = 1234;
    
    printf("=== SELAMAT DATANG DI ATM ===\n");
    printf("Masukkan PIN: ");
    scanf("%d", &pin);
    
    if (pin != pin_benar) {
        printf("PIN salah! Akses ditolak.\n");
        return 1;
    }
    
    printf("PIN benar! Selamat datang.\n\n");
    
    printf("=== MENU ATM ===\n");
    printf("1. Cek Saldo\n");
    printf("2. Tarik Tunai\n");
    printf("3. Setor Tunai\n");
    printf("4. Keluar\n");
    printf("Pilih menu: ");
    scanf("%d", &pilihan);
    
    switch(pilihan) {
        case 1:
            printf("Saldo Anda: Rp %d\n", saldo);
            break;
            
        case 2:
            printf("Masukkan jumlah penarikan: Rp ");
            scanf("%d", &jumlah);
            
            if (jumlah <= 0) {
                printf("Jumlah tidak valid!\n");
            }
            else if (jumlah > saldo) {
                printf("Saldo tidak mencukupi!\n");
                printf("Saldo Anda: Rp %d\n", saldo);
            }
            else {
                saldo -= jumlah;
                printf("Penarikan berhasil!\n");
                printf("Jumlah ditarik: Rp %d\n", jumlah);
                printf("Saldo tersisa: Rp %d\n", saldo);
            }
            break;
            
        case 3:
            printf("Masukkan jumlah setoran: Rp ");
            scanf("%d", &jumlah);
            
            if (jumlah <= 0) {
                printf("Jumlah tidak valid!\n");
            }
            else {
                saldo += jumlah;
                printf("Setoran berhasil!\n");
                printf("Jumlah disetor: Rp %d\n", jumlah);
                printf("Saldo baru: Rp %d\n", saldo);
            }
            break;
            
        case 4:
            printf("Terima kasih telah menggunakan ATM!\n");
            break;
            
        default:
            printf("Pilihan tidak valid!\n");
    }
    
    return 0;
}
```

### Studi Kasus 3: Sistem Penilaian Mahasiswa

```c
#include <stdio.h>
int main() {
    float tugas, uts, uas, kehadiran, nilai_akhir;
    char grade;
    
    printf("=== SISTEM PENILAIAN MAHASISWA ===\n");
    
    // Input nilai
    printf("Masukkan nilai Tugas (0-100): ");
    scanf("%f", &tugas);
    printf("Masukkan nilai UTS (0-100): ");
    scanf("%f", &uts);
    printf("Masukkan nilai UAS (0-100): ");
    scanf("%f", &uas);
    printf("Masukkan persentase kehadiran (0-100): ");
    scanf("%f", &kehadiran);
    
    // Validasi input
    if (tugas < 0 || tugas > 100 || uts < 0 || uts > 100 || 
        uas < 0 || uas > 100 || kehadiran < 0 || kehadiran > 100) {
        printf("Error: Semua nilai harus antara 0-100\n");
        return 1;
    }
    
    // Hitung nilai akhir (bobot: Tugas 30%, UTS 30%, UAS 40%)
    nilai_akhir = (tugas * 0.3) + (uts * 0.3) + (uas * 0.4);
    
    printf("\n=== HASIL PENILAIAN ===\n");
    printf("Nilai Tugas: %.2f\n", tugas);
    printf("Nilai UTS: %.2f\n", uts);
    printf("Nilai UAS: %.2f\n", uas);
    printf("Kehadiran: %.1f%%\n", kehadiran);
    printf("Nilai Akhir: %.2f\n", nilai_akhir);
    
    // Tentukan grade berdasarkan nilai akhir
    if (nilai_akhir >= 85) {
        grade = 'A';
    }
    else if (nilai_akhir >= 70) {
        grade = 'B';
    }
    else if (nilai_akhir >= 55) {
        grade = 'C';
    }
    else if (nilai_akhir >= 40) {
        grade = 'D';
    }
    else {
        grade = 'F';
    }
    
    // Cek syarat kelulusan
    if (kehadiran < 75) {
        printf("Status: TIDAK LULUS\n");
        printf("Alasan: Kehadiran kurang dari 75%%\n");
        printf("Grade: F (karena tidak memenuhi syarat kehadiran)\n");
    }
    else {
        printf("Grade: %c\n", grade);
        
        if (grade == 'F') {
            printf("Status: TIDAK LULUS\n");
            printf("Alasan: Nilai akhir di bawah 40\n");
        }
        else {
            printf("Status: LULUS\n");
            
            // Tambahan keterangan berdasarkan grade
            switch(grade) {
                case 'A':
                    printf("Keterangan: Sangat Baik (Cum Laude)\n");
                    break;
                case 'B':
                    printf("Keterangan: Baik (Memuaskan)\n");
                    break;
                case 'C':
                    printf("Keterangan: Cukup\n");
                    break;
                case 'D':
                    printf("Keterangan: Kurang (Perlu Perbaikan)\n");
                    break;
            }
        }
    }
    
    return 0;
}
```

---

## 🔧 Perbandingan If-Else vs Switch-Case

### Kapan Menggunakan If-Else?

#### Keunggulan If-Else:
1. **Fleksibilitas tinggi**: Dapat menangani kondisi kompleks dengan logical operators
2. **Range conditions**: Dapat mengecek rentang nilai (contoh: `nilai >= 70 && nilai < 80`)
3. **Multiple variables**: Dapat mengecek beberapa variabel sekaligus
4. **Complex expressions**: Dapat menggunakan ekspresi matematika dan function calls

#### Contoh Penggunaan If-Else:
```c
// Cocok untuk range dan multiple conditions
if (umur >= 18 && umur <= 65 && memiliki_sim == 1) {
    printf("Boleh mengemudi\n");
}
else if (nilai >= 80.5 || (nilai >= 70 && kehadiran > 90)) {
    printf("Lulus dengan baik\n");
}
```

### Kapan Menggunakan Switch-Case?

#### Keunggulan Switch-Case:
1. **Readability**: Lebih mudah dibaca untuk multiple exact values
2. **Performance**: Lebih efisien untuk banyak kondisi dengan exact matching
3. **Maintainability**: Mudah ditambah atau dikurangi case
4. **Fall-through**: Dapat mengeksekusi multiple cases dengan satu kondisi

#### Contoh Penggunaan Switch-Case:
```c
// Cocok untuk exact values dan menu systems
switch(pilihan_menu) {
    case 1:
    case 2:
    case 3:
        printf("Menu valid\n");
        break;
    default:
        printf("Menu tidak valid\n");
}
```

### Tabel Perbandingan

| Aspek | If-Else | Switch-Case |
|-------|---------|-------------|
| **Tipe Kondisi** | Range, complex expressions | Exact values only |
| **Performance** | Slower untuk banyak kondisi | Faster untuk banyak exact values |
| **Readability** | Baik untuk logical conditions | Excellent untuk menu/categories |
| **Flexibility** | Sangat fleksibel | Terbatas pada equality check |
| **Data Types** | Semua tipe data | Integer, character, enum |
| **Maintenance** | Moderate | Easy untuk exact value cases |

---

## 📝 Latihan dan Soal

### Latihan Dasar

#### Latihan 1: Menentukan Bilangan Genap/Ganjil
Sesuai dengan requirement silabus, buat flowchart untuk menentukan bilangan genap/ganjil.

**Solusi Flowchart:**
```
[START]
    ↓
[Input: n]
    ↓
[Hitung: sisa = n % 2]
    ↓
[sisa == 0?] → [Ya] → [Output: "GENAP"]
    ↓ [Tidak]              ↓
[Output: "GANJIL"]         ↓
    ↓                     ↓
[END] ← ← ← ← ← ← ← ← ←
```

**Implementasi Program:**
```c
#include <stdio.h>
int main() {
    int n;
    
    printf("Masukkan sebuah bilangan: ");
    scanf("%d", &n);
    
    if (n % 2 == 0) {
        printf("%d adalah bilangan GENAP\n", n);
    }
    else {
        printf("%d adalah bilangan GANJIL\n", n);
    }
    
    return 0;
}
```

#### Latihan 2: Program Penentuan Lulus/Tidak Lulus
Implementasi sesuai requirement: jika nilai ≥70 maka LULUS, selain itu TIDAK.

**Solusi:**
```c
#include <stdio.h>
int main() {
    float nilai;
    
    printf("Masukkan nilai ujian: ");
    scanf("%f", &nilai);
    
    if (nilai >= 70) {
        printf("LULUS\n");
    }
    else {
        printf("TIDAK LULUS\n");
    }
    
    return 0;
}
```

### Latihan Menengah

#### Latihan 3: Sistem Login
Buat program login sederhana dengan username dan password.

**Solusi:**
```c
#include <stdio.h>
#include <string.h>
int main() {
    char username[50], password[50];
    
    printf("=== LOGIN SISTEM ===\n");
    printf("Username: ");
    scanf("%s", username);
    printf("Password: ");
    scanf("%s", password);
    
    if (strcmp(username, "admin") == 0 && strcmp(password, "12345") == 0) {
        printf("Login berhasil! Selamat datang, %s\n", username);
    }
    else {
        printf("Login gagal! Username atau password salah.\n");
    }
    
    return 0;
}
```

#### Latihan 4: Konverter Suhu
Buat program untuk konversi suhu dengan menu pilihan.

**Solusi:**
```c
#include <stdio.h>
int main() {
    int pilihan;
    float suhu, hasil;
    
    printf("=== KONVERTER SUHU ===\n");
    printf("1. Celsius ke Fahrenheit\n");
    printf("2. Fahrenheit ke Celsius\n");
    printf("3. Celsius ke Kelvin\n");
    printf("4. Kelvin ke Celsius\n");
    printf("Pilih konversi (1-4): ");
    scanf("%d", &pilihan);
    
    printf("Masukkan suhu: ");
    scanf("%f", &suhu);
    
    switch(pilihan) {
        case 1:
            hasil = (suhu * 9/5) + 32;
            printf("%.2f°C = %.2f°F\n", suhu, hasil);
            break;
        case 2:
            hasil = (suhu - 32) * 5/9;
            printf("%.2f°F = %.2f°C\n", suhu, hasil);
            break;
        case 3:
            hasil = suhu + 273.15;
            printf("%.2f°C = %.2f K\n", suhu, hasil);
            break;
        case 4:
            hasil = suhu - 273.15;
            printf("%.2f K = %.2f°C\n", suhu, hasil);
            break;
        default:
            printf("Pilihan tidak valid!\n");
    }
    
    return 0;
}
```

### Latihan Lanjutan

#### Latihan 5: Sistem Parkir
Buat program perhitungan biaya parkir berdasarkan jenis kendaraan dan lama parkir.

**Solusi:**
```c
#include <stdio.h>
int main() {
    int jenis_kendaraan, jam_parkir;
    int biaya = 0;
    
    printf("=== SISTEM PARKIR ===\n");
    printf("1. Motor\n");
    printf("2. Mobil\n");
    printf("3. Bus\n");
    printf("Pilih jenis kendaraan: ");
    scanf("%d", &jenis_kendaraan);
    
    printf("Masukkan lama parkir (jam): ");
    scanf("%d", &jam_parkir);
    
    if (jam_parkir <= 0) {
        printf("Lama parkir tidak valid!\n");
        return 1;
    }
    
    switch(jenis_kendaraan) {
        case 1: // Motor
            biaya = 2000; // Jam pertama
            if (jam_parkir > 1) {
                biaya += (jam_parkir - 1) * 1000;
            }
            printf("Jenis kendaraan: Motor\n");
            break;
            
        case 2: // Mobil
            biaya = 5000; // Jam pertama
            if (jam_parkir > 1) {
                biaya += (jam_parkir - 1) * 3000;
            }
            printf("Jenis kendaraan: Mobil\n");
            break;
            
        case 3: // Bus
            biaya = 10000; // Jam pertama
            if (jam_parkir > 1) {
                biaya += (jam_parkir - 1) * 5000;
            }
            printf("Jenis kendaraan: Bus\n");
            break;
            
        default:
            printf("Jenis kendaraan tidak valid!\n");
            return 1;
    }
    
    printf("Lama parkir: %d jam\n", jam_parkir);
    printf("Total biaya: Rp %d\n", biaya);
    
    return 0;
}
```

#### Latihan 6: Kalkulator Gaji Karyawan
Hitung gaji bersih berdasarkan jabatan, masa kerja, dan lembur.

**Solusi:**
```c
#include <stdio.h>
int main() {
    int jabatan, masa_kerja, jam_lembur;
    float gaji_pokok, tunjangan, bonus_masa_kerja, uang_lembur, gaji_kotor, pajak, gaji_bersih;
    
    printf("=== KALKULATOR GAJI ===\n");
    printf("1. Staff (Gaji Pokok: Rp 3,000,000)\n");
    printf("2. Supervisor (Gaji Pokok: Rp 5,000,000)\n");
    printf("3. Manager (Gaji Pokok: Rp 8,000,000)\n");
    printf("Pilih jabatan: ");
    scanf("%d", &jabatan);
    
    printf("Masukkan masa kerja (tahun): ");
    scanf("%d", &masa_kerja);
    
    printf("Masukkan jam lembur: ");
    scanf("%d", &jam_lembur);
    
    // Tentukan gaji pokok berdasarkan jabatan
    switch(jabatan) {
        case 1:
            gaji_pokok = 3000000;
            tunjangan = 500000;
            printf("Jabatan: Staff\n");
            break;
        case 2:
            gaji_pokok = 5000000;
            tunjangan = 1000000;
            printf("Jabatan: Supervisor\n");
            break;
        case 3:
            gaji_pokok = 8000000;
            tunjangan = 2000000;
            printf("Jabatan: Manager\n");
            break;
        default:
            printf("Jabatan tidak valid!\n");
            return 1;
    }
    
    // Hitung bonus masa kerja
    if (masa_kerja >= 10) {
        bonus_masa_kerja = gaji_pokok * 0.2; // 20%
    }
    else if (masa_kerja >= 5) {
        bonus_masa_kerja = gaji_pokok * 0.1; // 10%
    }
    else {
        bonus_masa_kerja = 0;
    }
    
    // Hitung uang lembur
    uang_lembur = jam_lembur * 50000;
    
    // Hitung gaji kotor
    gaji_kotor = gaji_pokok + tunjangan + bonus_masa_kerja + uang_lembur;
    
    // Hitung pajak (PPh 21)
    if (gaji_kotor > 7000000) {
        pajak = gaji_kotor * 0.15; // 15%
    }
    else if (gaji_kotor > 4000000) {
        pajak = gaji_kotor * 0.1; // 10%
    }
    else {
        pajak = gaji_kotor * 0.05; // 5%
    }
    
    // Hitung gaji bersih
    gaji_bersih = gaji_kotor - pajak;
    
    // Tampilkan rincian
    printf("\n=== RINCIAN GAJI ===\n");
    printf("Gaji Pokok: Rp %.0f\n", gaji_pokok);
    printf("Tunjangan: Rp %.0f\n", tunjangan);
    printf("Bonus Masa Kerja: Rp %.0f\n", bonus_masa_kerja);
    printf("Uang Lembur: Rp %.0f\n", uang_lembur);
    printf("Gaji Kotor: Rp %.0f\n", gaji_kotor);
    printf("Pajak: Rp %.0f\n", pajak);
    printf("Gaji Bersih: Rp %.0f\n", gaji_bersih);
    
    return 0;
}
```

---

## 💡 Tips dan Best Practices

### 1. Struktur Kondisi yang Jelas
```c
// BAIK - Kondisi yang jelas dan mudah dibaca
if (nilai >= 70 && kehadiran >= 75) {
    printf("LULUS\n");
}
else {
    printf("TIDAK LULUS\n");
}

// KURANG BAIK - Kondisi yang ambigu
if (!(nilai < 70 || kehadiran < 75)) {
    printf("LULUS\n");
}
```

### 2. Validasi Input
```c
// Selalu validasi input dari user
if (nilai < 0 || nilai > 100) {
    printf("Error: Nilai harus antara 0-100\n");
    return 1;
}
```

### 3. Gunakan else if untuk Multiple Conditions
```c
// BAIK - Menggunakan else if
if (nilai >= 85) {
    grade = 'A';
}
else if (nilai >= 70) {
    grade = 'B';
}
else if (nilai >= 55) {
    grade = 'C';
}
else {
    grade = 'F';
}

// KURANG EFISIEN - Multiple if
if (nilai >= 85) {
    grade = 'A';
}
if (nilai >= 70 && nilai < 85) {
    grade = 'B';
}
if (nilai >= 55 && nilai < 70) {
    grade = 'C';
}
if (nilai < 55) {
    grade = 'F';
}
```

### 4. Gunakan Curly Braces
```c
// BAIK - Selalu gunakan curly braces
if (kondisi) {
    statement1;
    statement2;
}

// RISIKO - Tanpa curly braces untuk multiple statements
if (kondisi)
    statement1;
    statement2; // Ini akan selalu dieksekusi!
```

### 5. Switch vs If-Else Guidelines
```c
// Gunakan switch untuk exact values
switch(hari) {
    case 1: printf("Senin"); break;
    case 2: printf("Selasa"); break;
    // ...
}

// Gunakan if-else untuk ranges
if (umur < 18) {
    printf("Anak-anak");
}
else if (umur < 60) {
    printf("Dewasa");
}
else {
    printf("Lansia");
}
```

### 6. Default Case dalam Switch
```c
// Selalu sediakan default case
switch(pilihan) {
    case 1:
        // ...
        break;
    case 2:
        // ...
        break;
    default:
        printf("Pilihan tidak valid!\n");
}
```

---

## 🔍 Debugging dan Error Handling

### Common Errors dan Solusinya

#### 1. Missing Break in Switch
```c
// SALAH - Missing break
switch(grade) {
    case 'A':
        printf("Excellent");
    case 'B':
        printf("Good");  // Ini akan tereksekusi juga jika grade = 'A'
        break;
}

// BENAR - Dengan break
switch(grade) {
    case 'A':
        printf("Excellent");
        break;
    case 'B':
        printf("Good");
        break;
}
```

#### 2. Wrong Equality Operator
```c
// SALAH - Assignment instead of comparison
if (nilai = 70) {  // Ini assignment, bukan comparison!
    printf("Lulus");
}

// BENAR - Comparison operator
if (nilai == 70) {
    printf("Lulus");
}
```

#### 3. Logical Operator Confusion
```c
// SALAH - Logical error
if (nilai >= 70 || nilai <= 100) {  // Selalu true!
    printf("Valid");
}

// BENAR - Correct logic
if (nilai >= 70 && nilai <= 100) {
    printf("Valid");
}
```

---

## 🎉 Kesimpulan

### Ringkasan Materi

Dalam minggu ke-5 ini, kita telah mempelajari konsep fundamental tentang operasi seleksi (decision/branching) dalam pemrograman. Berikut adalah poin-poin utama yang telah dibahas:

#### 1. **Pemahaman Decision Making**
- Decision making adalah kemampuan program untuk memilih jalur eksekusi berdasarkan kondisi
- Conditional statements menentukan alur program dan mengimplementasikan logika bisnis
- Validasi input dan error handling merupakan aplikasi penting dari decision making

#### 2. **If Statement**
- Statement kondisional paling dasar untuk eksekusi kondisional
- Menggunakan test expression yang dievaluasi menjadi true atau false
- Implementasi dalam berbagai skenario seperti validasi dan pengecekan kondisi

#### 3. **If-Else Statement**
- Menyediakan dua jalur eksekusi: satu untuk kondisi true, satu untuk false
- Dapat dikombinasikan dengan logical operators untuk kondisi kompleks
- If-else ladder untuk multiple conditions dengan prioritas berurutan

#### 4. **Nested If-Else**
- Struktur berlapis untuk decision making yang kompleks
- Berguna untuk kondisi yang saling bergantung
- Memungkinkan multiple level checking dalam satu flow

#### 5. **Switch-Case Statement**
- Alternatif yang lebih clean untuk multiple exact value checking
- Lebih efisien dan readable untuk menu systems dan categorization
- Pentingnya break statement untuk mencegah fall-through yang tidak diinginkan

### Key Takeaways

1. **If statement digunakan untuk conditional execution sederhana**
2. **If-else memberikan dua jalur alternatif berdasarkan kondisi**
3. **If-else ladder efektif untuk multiple conditions dengan prioritas**
4. **Nested if-else cocok untuk decision making berlapis yang kompleks**
5. **Switch-case optimal untuk exact value matching dan menu systems**
6. **Validasi input selalu penting dalam setiap conditional statement**
7. **Flowchart membantu visualisasi alur decision making**

### Persiapan untuk Minggu Selanjutnya

Materi operasi seleksi ini menjadi fondasi untuk:

- **Minggu 6**: Operasi Perulangan - akan mengkombinasikan loops dengan conditional statements
- **Minggu 7**: Studi Kasus Perbandingan & Konversi - implementasi decision making dalam kasus nyata  
- **Minggu 10**: Fungsi - decision making akan digunakan dalam modularisasi program

### Evaluasi Pembelajaran

Untuk mengukur pemahaman terhadap materi ini, pastikan Anda dapat:

✅ Membedakan kapan menggunakan if, if-else, nested if, dan switch-case
✅ Menulis program dengan conditional statements untuk berbagai skenario
✅ Membuat flowchart untuk algoritma d
    
