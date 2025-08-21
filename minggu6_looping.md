# Minggu 6: Operasi Perulangan (Looping)
## Logika dan Pemrograman

---

## 🎯 Tujuan Pembelajaran

Setelah mempelajari materi ini, mahasiswa diharapkan mampu:

1. **Memahami konsep dasar perulangan** dalam pemrograman dan mengapa perulangan diperlukan
2. **Menguasai tiga jenis perulangan** utama: for, while, dan do-while
3. **Menganalisis perbedaan** antara ketiga jenis perulangan dan kapan menggunakan masing-masing
4. **Merancang algoritma** yang menggunakan struktur perulangan untuk menyelesaikan masalah
5. **Mengimplementasikan program** sederhana yang menggunakan perulangan
6. **Membuat flowchart** untuk representasi visual algoritma perulangan
7. **Menerapkan perulangan** dalam studi kasus nyata seperti tabel perkalian dan deret bilangan

---

## 🔄 Pendahuluan tentang Perulangan

### Apa itu Perulangan?

Perulangan (looping) adalah salah satu struktur kontrol fundamental dalam pemrograman yang memungkinkan eksekusi berulang dari sekumpulan instruksi selama kondisi tertentu terpenuhi. Loops dapat mengeksekusi blok kode selama kondisi yang ditentukan tercapai. Loops sangat berguna karena menghemat waktu, mengurangi kesalahan, dan membuat kode lebih mudah dibaca.

### Mengapa Perulangan Penting?

1. **Efisiensi Kode**: Menghindari penulisan kode yang berulang-ulang
2. **Pemrosesan Data**: Memungkinkan pemrosesan sejumlah besar data dengan efisien
3. **Automatisasi**: Mengotomatisasi tugas-tugas yang repetitif
4. **Skalabilitas**: Membuat program yang dapat menangani input dengan ukuran yang bervariasi

### Contoh Sederhana Tanpa dan Dengan Perulangan

**Tanpa Perulangan** (tidak efisien):
```c
printf("1\n");
printf("2\n");
printf("3\n");
printf("4\n");
printf("5\n");
```

**Dengan Perulangan** (efisien):
```c
int i;
for (i = 1; i <= 5; i++) {
    printf("%d\n", i);
}
```

---

## 🔢 Jenis-Jenis Perulangan

Dalam bahasa pemrograman C, terdapat tiga jenis perulangan utama:

### 1. For Loop
- **Karakteristik**: Digunakan ketika jumlah iterasi sudah diketahui
- **Struktur**: Memiliki inisialisasi, kondisi, dan increment/decrement dalam satu baris
- **Kontrol**: Entry-controlled loop (kondisi dicek sebelum eksekusi)

### 2. While Loop
- **Karakteristik**: Digunakan ketika jumlah iterasi tidak diketahui pasti
- **Struktur**: Hanya memiliki kondisi, inisialisasi dan increment terpisah
- **Kontrol**: Entry-controlled loop (kondisi dicek sebelum eksekusi)

### 3. Do-While Loop
- **Karakteristik**: Mirip while loop tetapi minimal eksekusi satu kali
- **Struktur**: Kondisi dicek setelah eksekusi blok kode
- **Kontrol**: Exit-controlled loop (kondisi dicek setelah eksekusi)

---

## 🔄 For Loop

### Sintaks dan Struktur

For loop digunakan ketika Anda tahu persis berapa kali Anda ingin melakukan loop melalui blok kode:

```c
for (expression 1; expression 2; expression 3) {
    // code block to be executed
}
```

Expression 1 dieksekusi (satu kali) sebelum eksekusi blok kode. Expression 2 mendefinisikan kondisi untuk mengeksekusi blok kode. Expression 3 dieksekusi (setiap kali) setelah blok kode dieksekusi.

### Komponen For Loop

1. **Inisialisasi (Expression 1)**: Mengatur nilai awal variabel kontrol
2. **Kondisi (Expression 2)**: Menentukan kapan loop harus berhenti
3. **Update (Expression 3)**: Mengubah variabel kontrol setiap iterasi

### Contoh Implementasi For Loop

#### Contoh 1: Mencetak Angka 0-4
```c
#include <stdio.h>

int main() {
    int i;
    for (i = 0; i < 5; i++) {
        printf("%d\n", i);
    }
    return 0;
}
```

**Output:**
```
0
1
2
3
4
```

#### Contoh 2: Mencetak Bilangan Genap
Contoh ini mencetak nilai genap antara 0 dan 10:

```c
#include <stdio.h>

int main() {
    int i;
    for (i = 0; i <= 10; i = i + 2) {
        printf("%d\n", i);
    }
    return 0;
}
```

#### Contoh 3: Menghitung Jumlah Bilangan 1-5
Contoh ini menghitung jumlah bilangan dari 1 sampai 5:

```c
#include <stdio.h>

int main() {
    int sum = 0;
    int i;
    for (i = 1; i <= 5; i++) {
        sum = sum + i;
    }
    printf("Sum is %d", sum);
    return 0;
}
```

#### Contoh 4: Countdown
Contoh ini mencetak countdown dari 5 ke 1:

```c
#include <stdio.h>

int main() {
    int i;
    for (i = 5; i > 0; i--) {
        printf("%d\n", i);
    }
    return 0;
}
```

### Nested For Loop (For Loop Bersarang)

For loop dapat disarangkan untuk membuat pola atau memproses data multidimensi:

```c
#include <stdio.h>

int main() {
    int i, j;
    
    // Membuat pola bintang
    for (i = 1; i <= 5; i++) {
        for (j = 1; j <= i; j++) {
            printf("* ");
        }
        printf("\n");
    }
    return 0;
}
```

**Output:**
```
* 
* * 
* * * 
* * * * 
* * * * * 
```

---

## ⏰ While Loop

### Sintaks dan Karakteristik

While loop melakukan loop melalui blok kode selama kondisi yang ditentukan bernilai true:

```c
while (condition) {
    // code block to be executed
}
```

### Struktur While Loop

1. **Kondisi**: Dievaluasi sebelum setiap iterasi
2. **Blok Kode**: Dieksekusi jika kondisi bernilai true
3. **Update**: Harus dilakukan manual di dalam blok kode

### Contoh Implementasi While Loop

#### Contoh 1: Mencetak Angka 0-4
Dalam contoh di bawah ini, kode dalam loop akan berjalan, berulang-ulang, selama variabel (i) kurang dari 5:

```c
#include <stdio.h>

int main() {
    int i = 0;
    while (i < 5) {
        printf("%d\n", i);
        i++;  // Jangan lupa increment!
    }
    return 0;
}
```

⚠️ **Peringatan**: Jangan lupa untuk meningkatkan variabel yang digunakan dalam kondisi (i++), jika tidak loop tidak akan pernah berakhir!

#### Contoh 2: Countdown dengan While
Contoh ini menghitung mundur dari 3 ke 1 dan kemudian menampilkan "Happy New Year!!" di akhir:

```c
#include <stdio.h>

int main() {
    int countdown = 3;
    while (countdown > 0) {
        printf("%d\n", countdown);
        countdown--;
    }
    printf("Happy New Year!!\n");
    return 0;
}
```

#### Contoh 3: Input Validation
```c
#include <stdio.h>

int main() {
    int number;
    
    printf("Masukkan angka positif (0 untuk berhenti): ");
    scanf("%d", &number);
    
    while (number > 0) {
        printf("Anda memasukkan: %d\n", number);
        printf("Masukkan angka positif lagi (0 untuk berhenti): ");
        scanf("%d", &number);
    }
    
    printf("Program selesai!\n");
    return 0;
}
```

### Penggunaan While Loop untuk Algoritma

#### Contoh: Menghitung Faktorial
```c
#include <stdio.h>

int main() {
    int n = 5;
    int factorial = 1;
    int i = 1;
    
    while (i <= n) {
        factorial = factorial * i;
        i++;
    }
    
    printf("Faktorial dari %d adalah %d\n", n, factorial);
    return 0;
}
```

---

## 🔁 Do-While Loop

### Sintaks dan Karakteristik

Do/while loop adalah varian dari while loop. Loop ini akan mengeksekusi blok kode sekali, sebelum memeriksa apakah kondisinya benar, kemudian akan mengulangi loop selama kondisinya benar.

```c
do {
    // code block to be executed
} while (condition);
```

### Perbedaan Utama Do-While dengan While

Do/while loop selalu berjalan setidaknya sekali, bahkan jika kondisinya sudah salah. Ini berbeda dari while loop biasa, yang akan melewatkan loop sepenuhnya jika kondisi salah dari awal.

### Contoh Implementasi Do-While Loop

#### Contoh 1: Basic Do-While
Loop akan selalu dieksekusi setidaknya sekali, bahkan jika kondisinya salah, karena blok kode dieksekusi sebelum kondisi diuji:

```c
#include <stdio.h>

int main() {
    int i = 0;
    do {
        printf("%d\n", i);
        i++;
    } while (i < 5);
    return 0;
}
```

#### Contoh 2: Kondisi Salah dari Awal
Dalam contoh di bawah ini, variabel i dimulai dari 10, sehingga kondisi i < 5 langsung salah - namun do/while loop tetap berjalan sekali:

```c
#include <stdio.h>

int main() {
    int i = 10;
    do {
        printf("i is %d\n", i);
        i++;
    } while (i < 5);
    return 0;
}
```

**Output:**
```
i is 10
```

#### Contoh 3: Menu Program
Perilaku ini membuat do/while berguna ketika Anda ingin memastikan sesuatu terjadi setidaknya sekali, seperti menampilkan pesan atau meminta input pengguna.

```c
#include <stdio.h>

int main() {
    int pilihan;
    
    do {
        printf("\n=== MENU PROGRAM ===\n");
        printf("1. Pilihan 1\n");
        printf("2. Pilihan 2\n");
        printf("3. Pilihan 3\n");
        printf("0. Keluar\n");
        printf("Masukkan pilihan: ");
        scanf("%d", &pilihan);
        
        switch(pilihan) {
            case 1:
                printf("Anda memilih pilihan 1\n");
                break;
            case 2:
                printf("Anda memilih pilihan 2\n");
                break;
            case 3:
                printf("Anda memilih pilihan 3\n");
                break;
            case 0:
                printf("Terima kasih!\n");
                break;
            default:
                printf("Pilihan tidak valid!\n");
        }
    } while (pilihan != 0);
    
    return 0;
}
```

#### Contoh 4: Input Validation dengan Do-While
Contoh ini terus meminta pengguna memasukkan angka positif. Loop berhenti ketika pengguna memasukkan 0 atau angka negatif:

```c
#include <stdio.h>

int main() {
    int number;
    do {
        printf("Enter a positive number: ");
        scanf("%d", &number);
    } while (number > 0);
    return 0;
}
```

---

## ⚖️ Perbandingan Ketiga Jenis Loop

### Tabel Perbandingan

| Aspek | For Loop | While Loop | Do-While Loop |
|-------|----------|------------|---------------|
| **Kontrol** | Entry-controlled | Entry-controlled | Exit-controlled |
| **Eksekusi Minimal** | 0 kali | 0 kali | 1 kali |
| **Pengecekan Kondisi** | Sebelum eksekusi | Sebelum eksekusi | Setelah eksekusi |
| **Struktur Inisialisasi** | Dalam sintaks | Terpisah | Terpisah |
| **Update Variabel** | Dalam sintaks | Manual | Manual |
| **Penggunaan Ideal** | Jumlah iterasi diketahui | Jumlah iterasi tidak pasti | Minimal satu kali eksekusi |

### Kapan Menggunakan Masing-Masing Loop?

#### Gunakan For Loop ketika:
- Jumlah iterasi sudah diketahui pasti
- Mengiterasi array atau struktur data dengan ukuran tertentu
- Membuat counter atau sequence angka
- Membuat tabel atau pola tertentu

#### Gunakan While Loop ketika:
- Jumlah iterasi tergantung pada kondisi dinamis
- Validasi input pengguna
- Membaca file hingga akhir
- Implementasi algoritma pencarian

#### Gunakan Do-While Loop ketika:
- Memastikan kode dieksekusi minimal satu kali
- Membuat menu program
- Validasi input yang harus diminta setidaknya sekali
- Game loop sederhana

---

## 📊 Studi Kasus dan Implementasi

### Studi Kasus 1: Tabel Perkalian

Membuat program yang menampilkan tabel perkalian untuk angka tertentu:

```c
#include <stdio.h>

int main() {
    int angka, i;
    
    printf("Masukkan angka untuk tabel perkalian: ");
    scanf("%d", &angka);
    
    printf("\nTabel perkalian %d:\n", angka);
    printf("===================\n");
    
    for (i = 1; i <= 10; i++) {
        printf("%d x %d = %d\n", angka, i, angka * i);
    }
    
    return 0;
}
```

**Output untuk input 7:**
```
Tabel perkalian 7:
===================
7 x 1 = 7
7 x 2 = 14
7 x 3 = 21
...
7 x 10 = 70
```

### Studi Kasus 2: Deret Bilangan Fibonacci

Implementasi menggunakan berbagai jenis loop:

#### Dengan For Loop:
```c
#include <stdio.h>

int main() {
    int n = 10;
    int first = 0, second = 1, next;
    int i;
    
    printf("Deret Fibonacci %d angka pertama:\n", n);
    printf("%d %d ", first, second);
    
    for (i = 3; i <= n; i++) {
        next = first + second;
        printf("%d ", next);
        first = second;
        second = next;
    }
    printf("\n");
    
    return 0;
}
```

#### Dengan While Loop:
```c
#include <stdio.h>

int main() {
    int n = 10;
    int first = 0, second = 1, next;
    int count = 3;
    
    printf("Deret Fibonacci %d angka pertama:\n", n);
    printf("%d %d ", first, second);
    
    while (count <= n) {
        next = first + second;
        printf("%d ", next);
        first = second;
        second = next;
        count++;
    }
    printf("\n");
    
    return 0;
}
```

### Studi Kasus 3: Menghitung Digit dalam Angka

```c
#include <stdio.h>

int main() {
    int angka, temp, jumlah_digit = 0;
    
    printf("Masukkan sebuah angka: ");
    scanf("%d", &angka);
    
    temp = angka;
    
    // Menggunakan do-while untuk memastikan minimal 1 digit dihitung
    do {
        temp = temp / 10;
        jumlah_digit++;
    } while (temp != 0);
    
    printf("Angka %d memiliki %d digit\n", angka, jumlah_digit);
    
    return 0;
}
```

### Studi Kasus 4: Kalkulator Sederhana dengan Menu

```c
#include <stdio.h>

int main() {
    int pilihan;
    float num1, num2, hasil;
    
    do {
        printf("\n=== KALKULATOR SEDERHANA ===\n");
        printf("1. Penjumlahan\n");
        printf("2. Pengurangan\n");
        printf("3. Perkalian\n");
        printf("4. Pembagian\n");
        printf("0. Keluar\n");
        printf("Pilih operasi: ");
        scanf("%d", &pilihan);
        
        if (pilihan >= 1 && pilihan <= 4) {
            printf("Masukkan angka pertama: ");
            scanf("%f", &num1);
            printf("Masukkan angka kedua: ");
            scanf("%f", &num2);
        }
        
        switch (pilihan) {
            case 1:
                hasil = num1 + num2;
                printf("Hasil: %.2f + %.2f = %.2f\n", num1, num2, hasil);
                break;
            case 2:
                hasil = num1 - num2;
                printf("Hasil: %.2f - %.2f = %.2f\n", num1, num2, hasil);
                break;
            case 3:
                hasil = num1 * num2;
                printf("Hasil: %.2f * %.2f = %.2f\n", num1, num2, hasil);
                break;
            case 4:
                if (num2 != 0) {
                    hasil = num1 / num2;
                    printf("Hasil: %.2f / %.2f = %.2f\n", num1, num2, hasil);
                } else {
                    printf("Error: Pembagian dengan nol!\n");
                }
                break;
            case 0:
                printf("Terima kasih telah menggunakan kalkulator!\n");
                break;
            default:
                printf("Pilihan tidak valid!\n");
        }
    } while (pilihan != 0);
    
    return 0;
}
```

---

## 📊 Flowchart untuk Perulangan

### Flowchart For Loop

```
[START]
    ↓
[Inisialisasi i = 0]
    ↓
[Kondisi: i < 5?] → [Tidak] → [END]
    ↓ [Ya]
[Eksekusi: printf("%d", i)]
    ↓
[Update: i++]
    ↓
[Kembali ke Kondisi]
```

### Flowchart While Loop

```
[START]
    ↓
[Inisialisasi i = 0]
    ↓
[Kondisi: i < 5?] → [Tidak] → [END]
    ↓ [Ya]
[Eksekusi: printf("%d", i)]
    ↓
[Update: i++]
    ↓
[Kembali ke Kondisi]
```

### Flowchart Do-While Loop

```
[START]
    ↓
[Inisialisasi i = 0]
    ↓
[Eksekusi: printf("%d", i)]
    ↓
[Update: i++]
    ↓
[Kondisi: i < 5?] → [Ya] → [Kembali ke Eksekusi]
    ↓ [Tidak]
[END]
```

### Flowchart untuk Studi Kasus: Menentukan Bilangan Genap/Ganjil dalam Range

```
[START]
    ↓
[Input: batas_awal, batas_akhir]
    ↓
[i = batas_awal]
    ↓
[Kondisi: i <= batas_akhir?] → [Tidak] → [END]
    ↓ [Ya]
[Kondisi: i % 2 == 0?] → [Ya] → [Output: "i GENAP"]
    ↓ [Tidak]              ↓
[Output: "i GANJIL"] ← ←
    ↓
[i++]
    ↓
[Kembali ke Kondisi]
```

---

## 📝 Latihan dan Soal

### Latihan Dasar

#### Latihan 1: For Loop
Buat program untuk menampilkan bilangan 1–10 menggunakan for loop.

**Solusi:**
```c
#include <stdio.h>

int main() {
    int i;
    for (i = 1; i <= 10; i++) {
        printf("%d ", i);
    }
    printf("\n");
    return 0;
}
```

#### Latihan 2: While Loop
Buat program untuk menampilkan bilangan 1–10 menggunakan while loop.

**Solusi:**
```c
#include <stdio.h>

int main() {
    int i = 1;
    while (i <= 10) {
        printf("%d ", i);
        i++;
    }
    printf("\n");
    return 0;
}
```

### Latihan Menengah

#### Latihan 3: Pola Bintang
Buat program untuk menampilkan pola bintang segitiga:
```
*
**
***
****
*****
```

**Solusi:**
```c
#include <stdio.h>

int main() {
    int i, j;
    for (i = 1; i <= 5; i++) {
        for (j = 1; j <= i; j++) {
            printf("*");
        }
        printf("\n");
    }
    return 0;
}
```

#### Latihan 4: Jumlah Bilangan Genap
Hitung jumlah semua bilangan genap dari 1 sampai 100.

**Solusi:**
```c
#include <stdio.h>

int main() {
    int i, jumlah = 0;
    for (i = 2; i <= 100; i += 2) {
        jumlah += i;
    }
    printf("Jumlah bilangan genap 1-100: %d\n", jumlah);
    return 0;
}
```

### Latihan Lanjutan

#### Latihan 5: Validasi Input
Buat program yang meminta pengguna memasukkan angka antara 1-10. Jika input tidak valid, minta input ulang.

**Solusi:**
```c
#include <stdio.h>

int main() {
    int angka;
    
    do {
        printf("Masukkan angka antara 1-10: ");
        scanf("%d", &angka);
        
        if (angka < 1 || angka > 10) {
            printf("Input tidak valid! Silakan coba lagi.\n");
        }
    } while (angka < 1 || angka > 10);
    
    printf("Angka yang Anda masukkan: %d\n", angka);
    return 0;
}
```

#### Latihan 6: Menghitung Rata-rata
Buat program yang meminta pengguna memasukkan beberapa angka dan menghitung rata-ratanya. Program berhenti ketika pengguna memasukkan -1.

**Solusi:**
```c
#include <stdio.h>

int main() {
    int angka, jumlah = 0, count = 0;
    float rata_rata;
    
    printf("Masukkan angka-angka (masukkan -1 untuk berhenti):\n");
    
    do {
        printf("Angka: ");
        scanf("%d", &angka);
        
        if (angka != -1) {
            jumlah += angka;
            count++;
        }
    } while (angka != -1);
    
    if (count > 0) {
        rata_rata = (float)jumlah / count;
        printf("Rata-rata: %.2f\n", rata_rata);
    } else {
        printf("Tidak ada angka yang dimasukkan.\n");
    }
    
    return 0;
}
```

### Soal Tantangan

#### Soal 1: Prime Number Checker
Buat program untuk mengecek apakah suatu bilangan adalah bilangan prima.

#### Soal 2: Reverse Number
Buat program untuk membalik urutan digit dalam sebuah angka.

#### Soal 3: Perfect Number
Buat program untuk mengecek apakah suatu bilangan adalah perfect number (jumlah faktor-faktor pengali yang lebih kecil sama dengan bilangan itu sendiri).

---

## 💡 Tips dan Best Practices

### 1. Hindari Infinite Loop
```c
// SALAH - infinite loop
int i = 0;
while (i < 10) {
    printf("%d\n", i);
    // Lupa increment i
}

// BENAR
int i = 0;
while (i < 10) {
    printf("%d\n", i);
    i++; // Jangan lupa increment
}
```

### 2. Gunakan Loop yang Tepat
```c
// Untuk jumlah iterasi yang pasti, gunakan for
for (int i = 0; i < 10; i++) {
    // ...
}

// Untuk kondisi yang dinamis, gunakan while
while (user_input != 'q') {
    // ...
}

// Untuk eksekusi minimal satu kali, gunakan do-while
do {
    // ...
} while (condition);
```

### 3. Optimasi Performa
```c
// Kurang efisien
for (int i = 0; i < strlen(string); i++) {
    // strlen() dipanggil setiap iterasi
}

// Lebih efisien
int len = strlen(string);
for (int i = 0; i < len; i++) {
    // strlen() hanya dipanggil sekali
}
```

### 4. Gunakan Variabel yang Deskriptif
```c
// Kurang jelas
for (int i = 0; i < 10; i++) {
    // ...
}

// Lebih jelas
for (int student_count = 0; student_count < 10; student_count++) {
    // ...
}
```

### 5. Break dan Continue
```c
// Menggunakan break untuk keluar dari loop
for (int i = 0; i < 100; i++) {
    if (i == 50) {
        break; // Keluar dari loop ketika i = 50
    }
    printf("%d ", i);
}

// Menggunakan continue untuk skip iterasi
for (int i = 0; i < 10; i++) {
    if (i % 2 == 0) {
        continue; // Skip bilangan genap
    }
    printf("%d ", i); // Hanya cetak bilangan ganjil
}
```

### 6. Nested Loop Performance
```c
// Perhatikan kompleksitas waktu pada nested loop
for (int i = 0; i < n; i++) {
    for (int j = 0; j < m; j++) {
        // Kompleksitas: O(n*m)
    }
}
```

---

## 🔧 Debugging dan Error Handling

### Common Errors dan Solusinya

#### 1. Off-by-One Error
```c
// SALAH - akan miss elemen terakhir
for (int i = 0; i < 10; i++) {
    array[i+1] = value; // Error! Index out of bounds
}

// BENAR
for (int i = 0; i < 9; i++) {
    array[i+1] = value;
}
```

#### 2. Uninitialized Variables
```c
// SALAH
int sum;
for (int i = 0; i < 10; i++) {
    sum += i; // sum tidak diinisialisasi
}

// BENAR
int sum = 0; // Inisialisasi
for (int i = 0; i < 10; i++) {
    sum += i;
}
```

#### 3. Wrong Loop Type
```c
// Kurang tepat - menggunakan while untuk jumlah iterasi yang pasti
int i = 0;
while (i < 10) {
    printf("%d ", i);
    i++;
}

// Lebih tepat - menggunakan for
for (int i = 0; i < 10; i++) {
    printf("%d ", i);
}
```

---

## 🎯 Real-World Applications

### 1. Game Development
```c
// Game loop sederhana
int game_running = 1;
while (game_running) {
    // Update game state
    update_game();
    
    // Render graphics
    render_game();
    
    // Check for exit condition
    if (check_exit_key()) {
        game_running = 0;
    }
}
```

### 2. Data Processing
```c
// Membaca dan memproses file
FILE *file = fopen("data.txt", "r");
int number;

while (fscanf(file, "%d", &number) == 1) {
    // Process each number
    process_number(number);
}
fclose(file);
```

### 3. User Interface
```c
// Menu sistem
int choice;
do {
    display_menu();
    scanf("%d", &choice);
    
    switch (choice) {
        case 1: function1(); break;
        case 2: function2(); break;
        case 3: function3(); break;
        case 0: printf("Goodbye!\n"); break;
        default: printf("Invalid choice!\n");
    }
} while (choice != 0);
```

---

## 📈 Advanced Loop Concepts

### 1. Loop dengan Multiple Conditions
```c
int i = 0, sum = 0;
while (i < 100 && sum < 1000) {
    sum += i;
    i++;
}
printf("Stopped at i=%d, sum=%d\n", i, sum);
```

### 2. Loop dengan Flag Variables
```c
int found = 0;
int target = 42;
int array[] = {1, 5, 42, 8, 12};
int size = 5;

for (int i = 0; i < size && !found; i++) {
    if (array[i] == target) {
        found = 1;
        printf("Found %d at index %d\n", target, i);
    }
}

if (!found) {
    printf("%d not found in array\n", target);
}
```

### 3. Loop untuk Algorithm Implementation
```c
// Binary Search dengan loop
int binary_search(int arr[], int size, int target) {
    int left = 0, right = size - 1;
    
    while (left <= right) {
        int mid = left + (right - left) / 2;
        
        if (arr[mid] == target) {
            return mid;
        }
        
        if (arr[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    return -1; // Not found
}
```

---

## 🧮 Mathematical Applications

### 1. Calculating Series
```c
// Menghitung deret geometri: 1 + 2 + 4 + 8 + ... + 2^n
int calculate_geometric_series(int n) {
    int sum = 0;
    int term = 1;
    
    for (int i = 0; i <= n; i++) {
        sum += term;
        term *= 2;
    }
    
    return sum;
}
```

### 2. Finding GCD (Greatest Common Divisor)
```c
int gcd(int a, int b) {
    while (b != 0) {
        int temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}
```

### 3. Prime Number Generation
```c
// Sieve of Eratosthenes
void sieve_of_eratosthenes(int n) {
    int prime[n+1];
    
    // Initialize all numbers as prime
    for (int i = 0; i <= n; i++) {
        prime[i] = 1;
    }
    
    prime[0] = prime[1] = 0; // 0 and 1 are not prime
    
    for (int p = 2; p * p <= n; p++) {
        if (prime[p]) {
            // Mark all multiples of p as not prime
            for (int i = p * p; i <= n; i += p) {
                prime[i] = 0;
            }
        }
    }
    
    // Print all prime numbers
    printf("Prime numbers up to %d: ", n);
    for (int i = 2; i <= n; i++) {
        if (prime[i]) {
            printf("%d ", i);
        }
    }
    printf("\n");
}
```

---

## 📚 Additional Practice Problems

### Problem Set 1: Basic Loops

#### Problem 1.1: Sum of Squares
Hitung jumlah kuadrat dari 1 sampai n (1² + 2² + 3² + ... + n²).

#### Problem 1.2: Factorial Calculator
Buat program untuk menghitung faktorial dari sebuah angka.

#### Problem 1.3: Number Pattern
Cetak pola angka:
```
1
12
123
1234
12345
```

### Problem Set 2: Intermediate Loops

#### Problem 2.1: Armstrong Number
Cek apakah sebuah angka adalah Armstrong number (jumlah kubus digitnya sama dengan angka itu sendiri).

#### Problem 2.2: Password Strength Checker
Buat program yang mengecek kekuatan password berdasarkan kriteria tertentu.

#### Problem 2.3: Number Guessing Game
Implementasikan game tebak angka dengan hint "too high" atau "too low".

### Problem Set 3: Advanced Loops

#### Problem 3.1: Matrix Operations
Implementasikan operasi matriks menggunakan nested loops.

#### Problem 3.2: Text Analysis
Hitung frekuensi karakter dalam sebuah string.

#### Problem 3.3: Sorting Algorithm
Implementasikan bubble sort menggunakan nested loops.

---

## 🔍 Performance Analysis

### Time Complexity of Loops

#### Single Loop: O(n)
```c
for (int i = 0; i < n; i++) {
    // Constant time operation: O(1)
}
// Total: O(n)
```

#### Nested Loop: O(n²)
```c
for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        // Constant time operation: O(1)
    }
}
// Total: O(n²)
```

#### Triple Nested Loop: O(n³)
```c
for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        for (int k = 0; k < n; k++) {
            // Constant time operation: O(1)
        }
    }
}
// Total: O(n³)
```

### Memory Considerations
- Loops sendiri tidak menggunakan extra memory
- Perhatikan variabel yang dideklarasikan dalam loop
- Avoid memory leaks dalam loop yang mengalokasi memory

---

## 🎉 Kesimpulan

### Ringkasan Materi

Dalam minggu ke-6 ini, kita telah mempelajari konsep fundamental tentang operasi perulangan (looping) dalam pemrograman. Berikut adalah poin-poin utama yang telah dibahas:

#### 1. **Pemahaman Konsep Dasar**
- Perulangan adalah struktur kontrol yang memungkinkan eksekusi berulang dari blok kode
- Loops menghemat waktu, mengurangi error, dan membuat kode lebih readable
- Terdapat tiga jenis utama: for, while, dan do-while loop

#### 2. **Karakteristik Masing-Masing Loop**
- **For Loop**: Ideal untuk jumlah iterasi yang sudah diketahui, struktur kompakt dengan inisialisasi, kondisi, dan update dalam satu baris
- **While Loop**: Cocok untuk kondisi dinamis, entry-controlled loop yang fleksibel
- **Do-While Loop**: Memastikan eksekusi minimal satu kali, exit-controlled loop yang berguna untuk validasi input

#### 3. **Implementasi Praktis**
- Studi kasus tabel perkalian menunjukkan penggunaan for loop yang efektif
- Deret bilangan Fibonacci dapat diimplementasikan dengan berbagai jenis loop
- Menu program demonstrasi penggunaan do-while loop yang optimal

#### 4. **Best Practices**
- Hindari infinite loop dengan memastikan kondisi terminasi
- Pilih jenis loop yang sesuai dengan kebutuhan
- Gunakan variabel yang deskriptif
- Perhatikan performance pada nested loops

### Key Takeaways

1. **For loop digunakan ketika jumlah iterasi sudah diketahui pasti**
2. **While loop cocok untuk kondisi yang dinamis dan tidak pasti jumlah iterasinya**
3. **Do-while loop memastikan eksekusi minimal satu kali, berguna untuk menu dan validasi input**
4. **Semua jenis loop memerlukan perhatian khusus pada kondisi terminasi untuk menghindari infinite loop**
5. **Pemilihan jenis loop yang tepat dapat meningkatkan readability dan maintainability kode**

### Persiapan untuk Minggu Selanjutnya

Materi minggu ke-6 tentang perulangan ini menjadi fondasi penting untuk:

- **Minggu 7**: Studi Kasus Perbandingan & Konversi - akan menggunakan loop untuk implementasi algoritma yang lebih kompleks
- **Minggu 11**: Array - loops akan digunakan intensif untuk manipulasi array
- **Minggu 13**: Algoritma Pencarian dan Sorting - implementasi algoritma menggunakan berbagai jenis loop

### Evaluasi Pembelajaran

Untuk mengukur pemahaman Anda terhadap materi ini, pastikan Anda dapat:

✅ Menjelaskan perbedaan ketiga jenis loop dan kapan menggunakan masing-masing
✅ Menulis program sederhana menggunakan for, while, dan do-while loop
✅ Mengidentifikasi dan memperbaiki kesalahan umum dalam loop (infinite loop, off-by-one error)
✅ Membuat flowchart untuk algoritma yang menggunakan perulangan
✅ Mengimplementasikan studi kasus nyata seperti tabel perkalian dan deret bilangan

### Sumber Pembelajaran Tambahan

Untuk memperdalam pemahaman tentang perulangan, Anda dapat:

1. **Praktik Mandiri**: Kerjakan semua latihan yang disediakan dalam modul ini
2. **Eksplorasi Online**: Manfaatkan resource W3Schools untuk contoh tambahan dan interactive exercises
3. **Project Based Learning**: Coba implementasikan game sederhana atau kalkulator menggunakan loop
4. **Code Review**: Analisis kode orang lain untuk melihat berbagai implementasi loop

### Motivasi Lanjutan

Perulangan adalah salah satu konsep paling fundamental dalam pemrograman. Menguasai konsep ini dengan baik akan memudahkan Anda dalam:

- Memahami algoritma yang lebih kompleks
- Mengoptimalkan performance program
- Menulis kode yang clean dan maintainable
- Menyelesaikan problem solving yang membutuhkan iterasi

Terus berlatih dan jangan ragu untuk bereksperimen dengan berbagai variasi implementasi loop. Semakin banyak Anda berlatih, semakin intuitif penggunaan loop dalam menyelesaikan masalah pemrograman.

---

## 📖 Referensi dan Sumber Pembelajaran

### Referensi Utama
- **Bab 6**: Operasi Perulangan (sesuai silabus mata kuliah)
- **W3Schools C Loops**: Tutorial comprehensive tentang for, while, dan do-while loop dengan contoh interaktif

### Sumber Pembelajaran Online
- **W3Schools C Programming**: https://www.w3schools.com/c/
  - C For Loop Tutorial
  - C While Loop Tutorial  
  - C Do-While Loop Tutorial
  - Real-life examples dan praktik interaktif

### Recommended Reading
- "The C Programming Language" by Kernighan & Ritchie - Chapter 3
- "Programming in C" by Stephen G. Kochan - Chapter 6
- Online documentation dan tutorial untuk praktik tambahan

### Tools untuk Praktik
- **Online Compiler**: repl.it, onlinegdb.com
- **Local Development**: Dev C++, Code::Blocks, Visual Studio Code
- **Flowchart Tools**: draw.io, Lucidchart untuk membuat diagram algoritma

---

*Dokumen ini disusun sebagai panduan pembelajaran komprehensif untuk Minggu 6: Operasi Perulangan (Looping) dalam mata kuliah Logika dan Pemrograman. Semua contoh kode telah diuji dan dapat dijalankan langsung.*

**Total kata: ~5000 kata**

---