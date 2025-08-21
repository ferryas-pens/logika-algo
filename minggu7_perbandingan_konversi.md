# Minggu 7: Studi Kasus Perbandingan & Konversi
## Logika dan Pemrograman

---

## 🎯 Tujuan Pembelajaran

Setelah mempelajari materi ini, mahasiswa diharapkan mampu:

1. **Menguasai operator perbandingan** (relational operators) dalam bahasa C secara komprehensif
2. **Memahami dan mengimplementasikan algoritma konversi** khususnya konversi suhu dari Celsius ke Fahrenheit
3. **Mengintegrasikan konsep flowchart dan pseudocode** dengan implementasi program nyata
4. **Menerapkan pengetahuan dari minggu 4-6** untuk membangun aplikasi yang lebih kompleks
5. **Mengembangkan kemampuan problem solving** melalui studi kasus praktis
6. **Memahami type conversion** dan aplikasinya dalam pemrograman
7. **Membuat program dengan validasi input** dan error handling yang proper

---

## 📊 Konsep Dasar Operator Perbandingan

### Pengertian Operator Perbandingan

Dalam C, relational operators adalah simbol-simbol yang digunakan untuk perbandingan antara dua nilai untuk memahami jenis hubungan yang dimiliki sepasang angka. Hasil yang kita dapatkan setelah operasi relational adalah nilai boolean, yang menunjukkan apakah perbandingan tersebut true atau false. Relational operators terutama digunakan dalam conditional statements dan loops untuk memeriksa kondisi dalam pemrograman C.

### Jenis-Jenis Relational Operators

Ada total 6 relational operators dalam bahasa C:

#### 1. Equal to operator (==)

Equal to operator dalam C (==) adalah relational operator yang digunakan untuk memeriksa apakah dua operand yang diberikan sama atau tidak. Equal to operator adalah binary operator sehingga membutuhkan dua operand untuk melakukan perbandingan. Jika kedua nilai sama, maka mengembalikan true. Jika tidak, maka mengembalikan false. Ini tidak berfungsi untuk string atau array.

**Sintaks:**
```c
operand1 == operand2
```

**Contoh:** 5==5 akan mengembalikan true.

**Implementasi:**
```c
#include <stdio.h>
int main() {
    int a = 10, b = 10, c = 5;
    
    printf("=== EQUAL TO OPERATOR (==) ===\n");
    printf("a = %d, b = %d, c = %d\n\n", a, b, c);
    
    // Perbandingan dengan hasil true
    if (a == b) {
        printf("a == b: TRUE (%d sama dengan %d)\n", a, b);
    } else {
        printf("a == b: FALSE\n");
    }
    
    // Perbandingan dengan hasil false
    if (a == c) {
        printf("a == c: TRUE\n");
    } else {
        printf("a == c: FALSE (%d tidak sama dengan %d)\n", a, c);
    }
    
    return 0;
}
```

#### 2. Not equal to operator (!=)

Not equal to operator dalam C (!=) adalah relational operator lain yang digunakan untuk memeriksa apakah dua operand yang diberikan sama atau tidak. Ini juga binary operator, membutuhkan dua operand untuk melakukan perbandingan. Ini adalah boolean complement dari operator '==' yang mengembalikan true jika kedua nilai tidak sama, false jika sebaliknya.

**Sintaks:**
```c
operand1 != operand2
```

**Contoh:** 5!=5 akan mengembalikan false.

#### 3. Greater than operator (>)

Greater than operator adalah relational operator dalam C yang memeriksa apakah operand pertama lebih besar dari operand kedua atau tidak. Ini adalah binary operator. Jika operand pertama lebih besar dari operand2, maka mengembalikan true. Jika tidak, maka mengembalikan false.

**Sintaks:**
```c
operand1 > operand2
```

**Contoh:** 6>5 akan mengembalikan true.

#### 4. Less than operator (<)

Less than operator adalah relational operator dalam C yang memeriksa apakah operand pertama lebih kecil dari operand kedua. Ini adalah binary operator. Jika operand pertama lebih kecil dari operand2, maka mengembalikan true. Jika tidak, maka mengembalikan false.

**Sintaks:**
```c
operand1 < operand2
```

**Contoh:** 6<5 akan mengembalikan false.

#### 5. Greater than or equal to operator (>=)

Greater than or equal to operator adalah relational operator dalam C yang memeriksa apakah operand pertama lebih besar dari atau sama dengan operand kedua. Ini adalah binary operator. Jika operand pertama lebih besar dari atau sama dengan operand kedua, maka mengembalikan true. Jika tidak, maka mengembalikan false.

**Sintaks:**
```c
operand1 >= operand2
```

**Contoh:** 5>=5 akan mengembalikan true.

#### 6. Less than or equal to operator (<=)

Less than or equal to operator adalah relational operator dalam C yang memeriksa apakah operand pertama lebih kecil dari atau sama dengan operand kedua. Ini adalah binary operator. Jika operand pertama lebih kecil dari atau sama dengan operand kedua, maka mengembalikan true. Jika tidak, maka mengembalikan false.

**Sintaks:**
```c
operand1 <= operand2
```

**Contoh:** 5<=5 juga akan mengembalikan true.

### Contoh Demonstrasi Lengkap Relational Operators

Contoh berikut mendemonstrasikan penggunaan semua relational operators:

```c
// Program C untuk mendemonstrasikan cara kerja relational operators
#include <stdio.h>
int main() {
    int a = 10, b = 4;
    
    printf("=== DEMONSTRASI RELATIONAL OPERATORS ===\n");
    printf("a = %d, b = %d\n\n", a, b);
    
    // greater than example
    if (a > b)
        printf("a > b: TRUE - a lebih besar dari b\n");
    else
        printf("a > b: FALSE - a tidak lebih besar dari b\n");
    
    // greater than equal to
    if (a >= b)
        printf("a >= b: TRUE - a lebih besar dari atau sama dengan b\n");
    else
        printf("a >= b: FALSE - a tidak lebih besar dari atau sama dengan b\n");
    
    // less than example
    if (a < b)
        printf("a < b: TRUE - a lebih kecil dari b\n");
    else
        printf("a < b: FALSE - a tidak lebih kecil dari b\n");
    
    // lesser than equal to
    if (a <= b)
        printf("a <= b: TRUE - a lebih kecil dari atau sama dengan b\n");
    else
        printf("a <= b: FALSE - a tidak lebih kecil dari atau sama dengan b\n");
    
    // equal to
    if (a == b)
        printf("a == b: TRUE - a sama dengan b\n");
    else
        printf("a == b: FALSE - a tidak sama dengan b\n");
    
    // not equal to
    if (a != b)
        printf("a != b: TRUE - a tidak sama dengan b\n");
    else
        printf("a != b: FALSE - a sama dengan b\n");
    
    return 0;
}
```

**Output:**
```
=== DEMONSTRASI RELATIONAL OPERATORS ===
a = 10, b = 4

a > b: TRUE - a lebih besar dari b
a >= b: TRUE - a lebih besar dari atau sama dengan b
a < b: FALSE - a tidak lebih kecil dari b
a <= b: FALSE - a tidak lebih kecil dari atau sama dengan b
a == b: FALSE - a tidak sama dengan b
a != b: TRUE - a tidak sama dengan b
```

---

## 🔄 Konsep Type Conversion

### Pengertian Type Conversion

Dalam C, type conversion mengacu pada proses mengkonversi satu tipe data ke tipe data lainnya. Ini dapat dilakukan secara otomatis oleh compiler atau secara manual oleh programmer. Type conversion hanya dilakukan pada tipe data di mana konversi dimungkinkan.

### Jenis Type Conversion

#### 1. Implicit Type Conversion (Automatic)
Konversi yang dilakukan secara otomatis oleh compiler ketika operasi melibatkan tipe data yang berbeda.

```c
#include <stdio.h>
int main() {
    int integer = 10;
    float floating = 3.14f;
    double result = integer + floating;  // Automatic conversion
    
    printf("Integer: %d\n", integer);
    printf("Float: %.2f\n", floating);
    printf("Result (double): %.2f\n", result);
    
    return 0;
}
```

#### 2. Explicit Type Conversion (Type Casting)
Konversi yang dilakukan secara manual oleh programmer menggunakan cast operator.

```c
#include <stdio.h>
int main() {
    float temperature = 37.8f;
    int temp_integer = (int)temperature;  // Explicit casting
    
    printf("Temperature (float): %.1f°C\n", temperature);
    printf("Temperature (int): %d°C\n", temp_integer);
    
    // Konversi ini memotong bagian desimal, menghasilkan nilai integer yang diberikan ke n2
    
    return 0;
}
```

---

## 🌡️ Studi Kasus Utama: Konversi Suhu Celsius ke Fahrenheit

### Formula Konversi Suhu

Formula untuk mengkonversi skala Celsius ke skala Fahrenheit adalah: T(°F) = T(°C) × 9/5 + 32

### Algoritma Konversi Celsius ke Fahrenheit

**Pseudocode:**
```
BEGIN
    INPUT celsius
    SET fahrenheit = (celsius * 9/5) + 32
    OUTPUT fahrenheit
END
```

**Flowchart:**
```
[START]
    ↓
[INPUT: celsius]
    ↓
[PROSES: fahrenheit = (celsius * 9/5) + 32]
    ↓
[OUTPUT: fahrenheit]
    ↓
[END]
```

### Implementasi Program Dasar

Berikut adalah implementasi dari ide di atas:

```c
/* Program C untuk mengkonversi suhu dari Celsius ke Fahrenheit */
#include <stdio.h>

// function untuk konversi
float celsius_to_fahrenheit(float N) {
    return ((N * 9.0 / 5.0) + 32.0);
}

// Driver code
int main() {
    float N = 20.0;
    
    // Function call
    printf("Temperature in Fahrenheit : %.2f", celsius_to_fahrenheit(N));
    return 0;
}
```

### Implementasi Program Komprehensif dengan Validasi

```c
#include <stdio.h>
#include <stdlib.h>

// Function prototypes
float celsius_to_fahrenheit(float celsius);
float fahrenheit_to_celsius(float fahrenheit);
float celsius_to_kelvin(float celsius);
float kelvin_to_celsius(float kelvin);
float fahrenheit_to_kelvin(float fahrenheit);
float kelvin_to_fahrenheit(float kelvin);

int validate_temperature_input(float temp, int scale);
void display_menu();
void display_temperature_info();

int main() {
    int choice;
    float input_temp, output_temp;
    char continue_choice;
    
    printf("=== SISTEM KONVERSI SUHU LENGKAP ===\n");
    display_temperature_info();
    
    do {
        display_menu();
        printf("Pilih jenis konversi (1-6): ");
        
        // Validasi input menu
        if (scanf("%d", &choice) != 1) {
            printf("Input tidak valid! Masukkan angka.\n");
            while(getchar() != '\n'); // Clear input buffer
            continue;
        }
        
        if (choice < 1 || choice > 6) {
            printf("Pilihan tidak valid! Pilih antara 1-6.\n\n");
            continue;
        }
        
        printf("Masukkan suhu: ");
        if (scanf("%f", &input_temp) != 1) {
            printf("Input suhu tidak valid!\n");
            while(getchar() != '\n');
            continue;
        }
        
        // Validasi dan konversi berdasarkan pilihan
        switch(choice) {
            case 1: // Celsius to Fahrenheit
                if (!validate_temperature_input(input_temp, 1)) break;
                output_temp = celsius_to_fahrenheit(input_temp);
                printf("\n=== HASIL KONVERSI ===\n");
                printf("%.2f°C = %.2f°F\n", input_temp, output_temp);
                
                // Informasi tambahan
                if (input_temp == 0)
                    printf("Info: Titik beku air pada tekanan standar\n");
                else if (input_temp == 100)
                    printf("Info: Titik didih air pada tekanan standar\n");
                else if (input_temp == 37)
                    printf("Info: Suhu normal tubuh manusia\n");
                break;
                
            case 2: // Fahrenheit to Celsius
                if (!validate_temperature_input(input_temp, 2)) break;
                output_temp = fahrenheit_to_celsius(input_temp);
                printf("\n=== HASIL KONVERSI ===\n");
                printf("%.2f°F = %.2f°C\n", input_temp, output_temp);
                break;
                
            case 3: // Celsius to Kelvin
                if (!validate_temperature_input(input_temp, 1)) break;
                output_temp = celsius_to_kelvin(input_temp);
                printf("\n=== HASIL KONVERSI ===\n");
                printf("%.2f°C = %.2f K\n", input_temp, output_temp);
                break;
                
            case 4: // Kelvin to Celsius
                if (!validate_temperature_input(input_temp, 3)) break;
                output_temp = kelvin_to_celsius(input_temp);
                printf("\n=== HASIL KONVERSI ===\n");
                printf("%.2f K = %.2f°C\n", input_temp, output_temp);
                break;
                
            case 5: // Fahrenheit to Kelvin
                if (!validate_temperature_input(input_temp, 2)) break;
                output_temp = fahrenheit_to_kelvin(input_temp);
                printf("\n=== HASIL KONVERSI ===\n");
                printf("%.2f°F = %.2f K\n", input_temp, output_temp);
                break;
                
            case 6: // Kelvin to Fahrenheit
                if (!validate_temperature_input(input_temp, 3)) break;
                output_temp = kelvin_to_fahrenheit(input_temp);
                printf("\n=== HASIL KONVERSI ===\n");
                printf("%.2f K = %.2f°F\n", input_temp, output_temp);
                break;
        }
        
        printf("\nLakukan konversi lagi? (y/n): ");
        scanf(" %c", &continue_choice);
        printf("\n");
        
    } while (continue_choice == 'y' || continue_choice == 'Y');
    
    printf("Terima kasih telah menggunakan sistem konversi suhu!\n");
    return 0;
}

// Function implementations
float celsius_to_fahrenheit(float celsius) {
    return ((celsius * 9.0 / 5.0) + 32.0);
}

float fahrenheit_to_celsius(float fahrenheit) {
    return ((fahrenheit - 32.0) * 5.0 / 9.0);
}

float celsius_to_kelvin(float celsius) {
    return (celsius + 273.15);
}

float kelvin_to_celsius(float kelvin) {
    return (kelvin - 273.15);
}

float fahrenheit_to_kelvin(float fahrenheit) {
    return (((fahrenheit - 32.0) * 5.0 / 9.0) + 273.15);
}

float kelvin_to_fahrenheit(float kelvin) {
    return (((kelvin - 273.15) * 9.0 / 5.0) + 32.0);
}

int validate_temperature_input(float temp, int scale) {
    // scale: 1=Celsius, 2=Fahrenheit, 3=Kelvin
    switch(scale) {
        case 1: // Celsius
            if (temp < -273.15) {
                printf("Error: Suhu tidak boleh di bawah -273.15°C (absolute zero)\n");
                return 0;
            }
            break;
        case 2: // Fahrenheit
            if (temp < -459.67) {
                printf("Error: Suhu tidak boleh di bawah -459.67°F (absolute zero)\n");
                return 0;
            }
            break;
        case 3: // Kelvin
            if (temp < 0) {
                printf("Error: Suhu Kelvin tidak boleh di bawah 0 K (absolute zero)\n");
                return 0;
            }
            break;
    }
    return 1;
}

void display_menu() {
    printf("--- MENU KONVERSI SUHU ---\n");
    printf("1. Celsius ke Fahrenheit\n");
    printf("2. Fahrenheit ke Celsius\n");
    printf("3. Celsius ke Kelvin\n");
    printf("4. Kelvin ke Celsius\n");
    printf("5. Fahrenheit ke Kelvin\n");
    printf("6. Kelvin ke Fahrenheit\n");
}

void display_temperature_info() {
    printf("\nINFORMASI SKALA SUHU:\n");
    printf("- Celsius (°C): Titik beku air = 0°C, Titik didih air = 100°C\n");
    printf("- Fahrenheit (°F): Titik beku air = 32°F, Titik didih air = 212°F\n");
    printf("- Kelvin (K): Absolute zero = 0K, Titik beku air = 273.15K\n\n");
}
```

---

## 📊 Studi Kasus Perbandingan: Sistem Analisis Nilai

### Program Perbandingan Nilai Mahasiswa

```c
#include <stdio.h>
#include <string.h>

#define MAX_STUDENTS 50
#define MAX_NAME_LENGTH 50

typedef struct {
    char name[MAX_NAME_LENGTH];
    float nilai1, nilai2, nilai3;
    float average;
    char grade;
    int status; // 1 = lulus, 0 = tidak lulus
} Student;

// Function prototypes
void input_student_data(Student *student, int index);
void calculate_statistics(Student *student);
void assign_grade(Student *student);
void display_student_info(Student student, int index);
void compare_and_analyze(Student students[], int count);
void sort_students_by_average(Student students[], int count);
void display_grade_distribution(Student students[], int count);
float calculate_class_average(Student students[], int count);

int main() {
    Student students[MAX_STUDENTS];
    int num_students;
    
    printf("=== SISTEM ANALISIS DAN PERBANDINGAN NILAI MAHASISWA ===\n\n");
    
    // Validasi jumlah mahasiswa
    do {
        printf("Masukkan jumlah mahasiswa (1-%d): ", MAX_STUDENTS);
        if (scanf("%d", &num_students) != 1) {
            printf("Input tidak valid! Masukkan angka.\n");
            while(getchar() != '\n');
            continue;
        }
        
        if (num_students < 1 || num_students > MAX_STUDENTS) {
            printf("Jumlah mahasiswa harus antara 1-%d!\n", MAX_STUDENTS);
        }
    } while (num_students < 1 || num_students > MAX_STUDENTS);
    
    // Input data mahasiswa
    for (int i = 0; i < num_students; i++) {
        input_student_data(&students[i], i + 1);
        calculate_statistics(&students[i]);
        assign_grade(&students[i]);
    }
    
    // Display hasil input
    printf("\n=== DAFTAR MAHASISWA DAN NILAI ===\n");
    printf("%-3s %-20s %-8s %-8s %-8s %-10s %-6s %-8s\n", 
           "No", "Nama", "Nilai1", "Nilai2", "Nilai3", "Rata-rata", "Grade", "Status");
    printf("-------------------------------------------------------------------\n");
    
    for (int i = 0; i < num_students; i++) {
        display_student_info(students[i], i + 1);
    }
    
    // Analisis dan perbandingan
    compare_and_analyze(students, num_students);
    
    // Sorting dan ranking
    printf("\n=== RANKING MAHASISWA (Berdasarkan Rata-rata) ===\n");
    sort_students_by_average(students, num_students);
    
    printf("%-4s %-20s %-10s %-6s\n", "Rank", "Nama", "Rata-rata", "Grade");
    printf("----------------------------------------\n");
    for (int i = 0; i < num_students; i++) {
        printf("%-4d %-20s %-10.2f %-6c\n", 
               i + 1, students[i].name, students[i].average, students[i].grade);
    }
    
    // Distribusi grade
    display_grade_distribution(students, num_students);
    
    return 0;
}

void input_student_data(Student *student, int index) {
    printf("\n--- Input Data Mahasiswa ke-%d ---\n", index);
    
    printf("Nama: ");
    scanf(" %[^\n]", student->name);  // Read string with spaces
    
    // Validasi nilai 1
    do {
        printf("Nilai 1 (0-100): ");
        if (scanf("%f", &student->nilai1) != 1) {
            printf("Input tidak valid! Masukkan angka.\n");
            while(getchar() != '\n');
            continue;
        }
        if (student->nilai1 < 0 || student->nilai1 > 100) {
            printf("Nilai harus antara 0-100!\n");
        }
    } while (student->nilai1 < 0 || student->nilai1 > 100);
    
    // Validasi nilai 2
    do {
        printf("Nilai 2 (0-100): ");
        if (scanf("%f", &student->nilai2) != 1) {
            printf("Input tidak valid! Masukkan angka.\n");
            while(getchar() != '\n');
            continue;
        }
        if (student->nilai2 < 0 || student->nilai2 > 100) {
            printf("Nilai harus antara 0-100!\n");
        }
    } while (student->nilai2 < 0 || student->nilai2 > 100);
    
    // Validasi nilai 3
    do {
        printf("Nilai 3 (0-100): ");
        if (scanf("%f", &student->nilai3) != 1) {
            printf("Input tidak valid! Masukkan angka.\n");
            while(getchar() != '\n');
            continue;
        }
        if (student->nilai3 < 0 || student->nilai3 > 100) {
            printf("Nilai harus antara 0-100!\n");
        }
    } while (student->nilai3 < 0 || student->nilai3 > 100);
}

void calculate_statistics(Student *student) {
    student->average = (student->nilai1 + student->nilai2 + student->nilai3) / 3.0;
}

void assign_grade(Student *student) {
    if (student->average >= 85) {
        student->grade = 'A';
    } else if (student->average >= 70) {
        student->grade = 'B';
    } else if (student->average >= 55) {
        student->grade = 'C';
    } else if (student->average >= 40) {
        student->grade = 'D';
    } else {
        student->grade = 'F';
    }
    
    // Determine status (lulus/tidak lulus)
    student->status = (student->average >= 55) ? 1 : 0;
}

void display_student_info(Student student, int index) {
    printf("%-3d %-20s %-8.1f %-8.1f %-8.1f %-10.2f %-6c %-8s\n",
           index, student.name, student.nilai1, student.nilai2, student.nilai3,
           student.average, student.grade, 
           (student.status == 1) ? "LULUS" : "GAGAL");
}

void compare_and_analyze(Student students[], int count) {
    printf("\n=== ANALISIS PERBANDINGAN ===\n");
    
    // Find highest and lowest
    int highest_index = 0, lowest_index = 0;
    
    for (int i = 1; i < count; i++) {
        if (students[i].average > students[highest_index].average) {
            highest_index = i;
        }
        if (students[i].average < students[lowest_index].average) {
            lowest_index = i;
        }
    }
    
    printf("Nilai Tertinggi: %s (%.2f)\n", 
           students[highest_index].name, students[highest_index].average);
    printf("Nilai Terendah: %s (%.2f)\n", 
           students[lowest_index].name, students[lowest_index].average);
    
    // Calculate class average
    float class_average = calculate_class_average(students, count);
    printf("Rata-rata Kelas: %.2f\n", class_average);
    
    // Above/below average analysis
    int above_average = 0, below_average = 0, at_average = 0;
    
    for (int i = 0; i < count; i++) {
        if (students[i].average > class_average) {
            above_average++;
        } else if (students[i].average < class_average) {
            below_average++;
        } else {
            at_average++;
        }
    }
    
    printf("Mahasiswa di atas rata-rata: %d (%.1f%%)\n", 
           above_average, (above_average * 100.0) / count);
    printf("Mahasiswa di bawah rata-rata: %d (%.1f%%)\n", 
           below_average, (below_average * 100.0) / count);
    printf("Mahasiswa dengan rata-rata sama: %d (%.1f%%)\n", 
           at_average, (at_average * 100.0) / count);
    
    // Pass/fail analysis
    int passed = 0;
    for (int i = 0; i < count; i++) {
        if (students[i].status == 1) {
            passed++;
        }
    }
    
    printf("\nAnalisis Kelulusan:\n");
    printf("Lulus: %d mahasiswa (%.1f%%)\n", passed, (passed * 100.0) / count);
    printf("Tidak Lulus: %d mahasiswa (%.1f%%)\n", 
           count - passed, ((count - passed) * 100.0) / count);
}

void sort_students_by_average(Student students[], int count) {
    // Bubble sort implementation
    for (int i = 0; i < count - 1; i++) {
        for (int j = 0; j < count - i - 1; j++) {
            if (students[j].average < students[j + 1].average) {
                Student temp = students[j];
                students[j] = students[j + 1];
                students[j + 1] = temp;
            }
        }
    }
}

void display_grade_distribution(Student students[], int count) {
    printf("\n=== DISTRIBUSI GRADE ===\n");
    
    int grade_count[5] = {0}; // A, B, C, D, F
    
    for (int i = 0; i < count; i++) {
        switch(students[i].grade) {
            case 'A': grade_count[0]++; break;
            case 'B': grade_count[1]++; break;
            case 'C': grade_count[2]++; break;
            case 'D': grade_count[3]++; break;
            case 'F': grade_count[4]++; break;
        }
    }
    
    char grades[] = {'A', 'B', 'C', 'D', 'F'};
    char *descriptions[] = {"Sangat Baik", "Baik", "Cukup", "Kurang", "Gagal"};
    
    printf("%-6s %-10s %-15s %-10s\n", "Grade", "Jumlah", "Keterangan", "Persentase");
    printf("--------------------------------------------\n");
    
    for (int i = 0; i < 5; i++) {
        printf("%-6c %-10d %-15s %-10.1f%%\n", 
               grades[i], grade_count[i], descriptions[i],
               (grade_count[i] * 100.0) / count);
    }
}

float calculate_class_average(Student students[], int count) {
    float total = 0;
    for (int i = 0; i < count; i++) {
        total += students[i].average;
    }
    return total / count;
}
```

---

## 💰 Studi Kasus: Konversi Mata Uang

### Sistem Konversi Mata Uang dengan Multiple Currency

```c
#include <stdio.h>
#include <string.h>

#define MAX_CURRENCIES 10

typedef struct {
    char code[4];
    char name[30];
    double rate_to_usd;
} Currency;

// Database mata uang
Currency currencies[MAX_CURRENCIES] = {
    {"USD", "US Dollar", 1.0},
    {"IDR", "Indonesian Rupiah", 15000.0},
    {"EUR", "Euro", 0.85},
    {"GBP", "British Pound", 0.73},
    {"JPY", "Japanese Yen", 110.0},
    {"SGD", "Singapore Dollar", 1.35},
    {"MYR", "Malaysian Ringgit", 4.12},
    {"CNY", "Chinese Yuan", 6.45},
    {"KRW", "South Korean Won", 1200.0},
    {"THB", "Thai Baht", 33.5}
};

int currency_count = 10;

// Function prototypes
void display_available_currencies();
int find_currency_index(char* code);
double convert_currency(double amount, int from_index, int to_index);
void display_conversion_result(double amount, int from_index, int to_index, double result);
void convert_to_string_upper(char* str);

int main() {
    double amount, result;
    char from_currency[4], to_currency[4];
    int from_index, to_index;
    char continue_choice;
    
    printf("=== SISTEM KONVERSI MATA UANG ===\n");
    
    do {
        display_available_currencies();
        
        // Input amount
        do {
            printf("\nMasukkan jumlah uang: ");
            if (scanf("%lf", &amount) != 1) {
                printf("Input tidak valid! Masukkan angka.\n");
                while(getchar() != '\n');
                continue;
            }
            if (amount <= 0) {
                printf("Jumlah harus lebih besar dari 0!\n");
            }
        } while (amount <= 0);
        
        // Input source currency
        printf("Mata uang asal (kode): ");
        scanf("%s", from_currency);
        convert_to_string_upper(from_currency);
        
        // Input target currency
        printf("Mata uang tujuan (kode): ");
        scanf("%s", to_currency);
        convert_to_string_upper(to_currency);
        
        // Find currency indices
        from_index = find_currency_index(from_currency);
        to_index = find_currency_index(to_currency);
        
        // Validate currencies
        if (from_index == -1) {
            printf("Error: Mata uang '%s' tidak ditemukan!\n", from_currency);
            continue;
        }
        
        if (to_index == -1) {
            printf("Error: Mata uang '%s' tidak ditemukan!\n", to_currency);
            continue;
        }
        
        if (from_index == to_index) {
            printf("Error: Mata uang asal dan tujuan tidak boleh sama!\n");
            continue;
        }
        
        // Perform conversion
        result = convert_currency(amount, from_index, to_index);
        
        // Display result
        display_conversion_result(amount, from_index, to_index, result);
        
        printf("\nKonversi lagi? (y/n): ");
        scanf(" %c", &continue_choice);
        
    } while (continue_choice == 'y' || continue_choice == 'Y');
    
    printf("Terima kasih telah menggunakan sistem konversi mata uang!\n");
    return 0;
}

void display_available_currencies() {
    printf("\n--- MATA UANG YANG TERSEDIA ---\n");
    printf("%-4s %-25s %-15s\n", "Kode", "Nama", "Rate ke USD");
    printf("----------------------------------------------\n");
    
    for (int i = 0; i < currency_count; i++) {
        printf("%-4s %-25s %.4f\n", 
               currencies[i].code, 
               currencies[i].name, 
               currencies[i].rate_to_usd);
    }
}

int find_currency_index(char* code) {
    for (int i = 0; i < currency_count; i++) {
        if (strcmp(currencies[i].code, code) == 0) {
            return i;
        }
    }
    return -1;
}

double convert_currency(double amount, int from_index, int to_index) {
    // Convert to USD first (base currency)
    double usd_amount = amount / currencies[from_index].rate_to_usd;
    // Convert from USD to target currency
    double target_amount = usd_amount * currencies[to_index].rate_to_usd;
    return target_amount;
}

void display_conversion_result(double amount, int from_index, int to_index, double result) {
    printf("\n=== HASIL KONVERSI ===\n");
    printf("Jumlah Asal: %.2f %s (%s)\n", 
           amount, 
           currencies[from_index].code, 
           currencies[from_index].name);
    
    printf("Hasil Konversi: %.2f %s (%s)\n", 
           result, 
           currencies[to_index].code, 
           currencies[to_index].name);
    
    // Calculate exchange rate
    double exchange_rate = currencies[to_index].rate_to_usd / currencies[from_index].rate_to_usd;
    printf("Nilai Tukar: 1 %s = %.6f %s\n", 
           currencies[from_index].code, 
           exchange_rate, 
           currencies[to_index].code);
    
    // Additional information
    double difference = result - amount;
    if (difference > 0) {
        printf("Info: Mata uang tujuan memiliki nilai nominal yang lebih tinggi\n");
    } else if (difference < 0) {
        printf("Info: Mata uang tujuan memiliki nilai nominal yang lebih rendah\n");
    } else {
        printf("Info: Nilai nominal sama\n");
    }
}

void convert_to_string_upper(char* str) {
    for (int i = 0; str[i]; i++) {
        if (str[i] >= 'a' && str[i] <= 'z') {
            str[i] = str[i] - 'a' + 'A';
        }
    }
}
```

---

## 📏 Studi Kasus: Konversi Satuan Panjang

### Sistem Konversi Multi-Unit Panjang

```c
#include <stdio.h>

typedef enum {
    MILLIMETER,
    CENTIMETER, 
    METER,
    KILOMETER,
    INCH,
    FOOT,
    YARD,
    MILE
} LengthUnit;

typedef struct {
    char name[15];
    char symbol[5];
    double factor_to_meter;
} UnitInfo;

UnitInfo units[] = {
    {"Millimeter", "mm", 0.001},
    {"Centimeter", "cm", 0.01},
    {"Meter", "m", 1.0},
    {"Kilometer", "km", 1000.0},
    {"Inch", "in", 0.0254},
    {"Foot", "ft", 0.3048},
    {"Yard", "yd", 0.9144},
    {"Mile", "mi", 1609.344}
};

int unit_count = 8;

// Function prototypes
void display_unit_menu();
double convert_length(double value, int from_unit, int to_unit);
void display_conversion_table(double value, int from_unit);
int validate_unit_choice(int unit);

int main() {
    double input_value, result;
    int from_unit, to_unit;
    char continue_choice;
    
    printf("=== SISTEM KONVERSI SATUAN PANJANG ===\n");
    
    do {
        display_unit_menu();
        
        // Input source unit
        do {
            printf("Unit asal (0-%d): ", unit_count - 1);
            if (scanf("%d", &from_unit) != 1) {
                printf("Input tidak valid! Masukkan angka.\n");
                while(getchar() != '\n');
                continue;
            }
            if (!validate_unit_choice(from_unit)) {
                printf("Unit tidak valid! Pilih antara 0-%d\n", unit_count - 1);
            }
        } while (!validate_unit_choice(from_unit));
        
        // Input target unit
        do {
            printf("Unit tujuan (0-%d): ", unit_count - 1);
            if (scanf("%d", &to_unit) != 1) {
                printf("Input tidak valid! Masukkan angka.\n");
                while(getchar() != '\n');
                continue;
            }
            if (!validate_unit_choice(to_unit)) {
                printf("Unit tidak valid! Pilih antara 0-%d\n", unit_count - 1);
            }
        } while (!validate_unit_choice(to_unit));
        
        // Input value
        do {
            printf("Masukkan nilai: ");
            if (scanf("%lf", &input_value) != 1) {
                printf("Input tidak valid! Masukkan angka.\n");
                while(getchar() != '\n');
                continue;
            }
            if (input_value < 0) {
                printf("Nilai tidak boleh negatif!\n");
            }
        } while (input_value < 0);
        
        // Convert
        result = convert_length(input_value, from_unit, to_unit);
        
        // Display result
        printf("\n=== HASIL KONVERSI ===\n");
        printf("%.6f %s = %.6f %s\n", 
               input_value, units[from_unit].symbol,
               result, units[to_unit].symbol);
        
        // Display conversion factor
        double factor = units[to_unit].factor_to_meter / units[from_unit].factor_to_meter;
        printf("Faktor konversi: 1 %s = %.9f %s\n", 
               units[from_unit].symbol, factor, units[to_unit].symbol);
        
        // Show conversion table
        printf("\nTabel konversi untuk %.6f %s:\n", input_value, units[from_unit].symbol);
        display_conversion_table(input_value, from_unit);
        
        printf("\nKonversi lagi? (y/n): ");
        scanf(" %c", &continue_choice);
        printf("\n");
        
    } while (continue_choice == 'y' || continue_choice == 'Y');
    
    printf("Terima kasih!\n");
    return 0;
}

void display_unit_menu() {
    printf("\n--- UNIT PANJANG YANG TERSEDIA ---\n");
    printf("%-2s %-12s %-6s %-15s\n", "No", "Nama", "Simbol", "Faktor ke Meter");
    printf("--------------------------------------\n");
    
    for (int i = 0; i < unit_count; i++) {
        printf("%-2d %-12s %-6s %-15.9f\n", 
               i, units[i].name, units[i].symbol, units[i].factor_to_meter);
    }
}

double convert_length(double value, int from_unit, int to_unit) {
    // Convert to meters first (base unit)
    double meters = value * units[from_unit].factor_to_meter;
    // Convert from meters to target unit
    double result = meters / units[to_unit].factor_to_meter;
    return result;
}

void display_conversion_table(double value, int from_unit) {
    printf("%-12s | %-15s\n", "Unit", "Nilai");
    printf("%-12s | %-15s\n", "----", "-----");
    
    for (int i = 0; i < unit_count; i++) {
        if (i != from_unit) {
            double converted = convert_length(value, from_unit, i);
            printf("%-12s | %.9f\n", units[i].name, converted);
        }
    }
}

int validate_unit_choice(int unit) {
    return (unit >= 0 && unit < unit_count);
}
```

---

## 📊 Flowchart untuk Algoritma Perbandingan dan Konversi

### Flowchart Algoritma Konversi Suhu

```
[START]
    ↓
[DISPLAY Menu Konversi]
    ↓
[INPUT pilihan konversi]
    ↓
[VALIDATE pilihan] → [Invalid] → [DISPLAY error] → [Kembali ke INPUT]
    ↓ [Valid]
[INPUT nilai suhu]
    ↓
[VALIDATE nilai suhu] → [Invalid] → [DISPLAY error] → [Kembali ke INPUT]
    ↓ [Valid]
[SWITCH pilihan konversi]
    ↓
[CASE 1: Celsius to Fahrenheit]
    ↓
[HITUNG: F = (C * 9/5) + 32]
    ↓
[DISPLAY hasil konversi]
    ↓
[INPUT: konversi lagi?] → [Ya] → [Kembali ke DISPLAY Menu]
    ↓ [Tidak]
[END]
```

### Flowchart Algoritma Perbandingan Nilai

```
[START]
    ↓
[INPUT jumlah mahasiswa]
    ↓
[VALIDATE jumlah] → [Invalid] → [DISPLAY error] → [Kembali ke INPUT]
    ↓ [Valid]
[LOOP i = 0 to jumlah-1]
    ↓
[INPUT data mahasiswa ke-i]
    ↓
[HITUNG rata-rata mahasiswa ke-i]
    ↓
[TENTUKAN grade mahasiswa ke-i]
    ↓
[i++]
    ↓
[i < jumlah?] → [Ya] → [Kembali ke INPUT data]
    ↓ [Tidak]
[CARI nilai tertinggi dan terendah]
    ↓
[HITUNG rata-rata kelas]
    ↓
[SORT data berdasarkan rata-rata]
    ↓
[DISPLAY hasil analisis]
    ↓
[DISPLAY ranking mahasiswa]
    ↓
[DISPLAY distribusi grade]
    ↓
[END]
```

---

## 📝 Latihan dan Soal

### Latihan Dasar

#### Latihan 1: Konversi Celsius ke Fahrenheit
Sesuai requirement silabus, buat algoritma konversi suhu dari Celsius ke Fahrenheit.

**Solusi Singkat:**
Konversi: F = (C*9/5)+32

**Implementasi:**
```c
#include <stdio.h>
int main() {
    float celsius, fahrenheit;
    
    printf("Masukkan suhu dalam Celsius: ");
    scanf("%f", &celsius);
    
    fahrenheit = (celsius * 9.0/5.0) + 32.0;
    
    printf("%.2f°C = %.2f°F\n", celsius, fahrenheit);
    
    return 0;
}
```

#### Latihan 2: Perbandingan Tiga Bilangan
Buat program untuk menentukan bilangan terbesar dari tiga bilangan.

**Solusi:**
```c
#include <stdio.h>
int main() {
    int a, b, c, terbesar;
    
    printf("Masukkan tiga bilangan: ");
    scanf("%d %d %d", &a, &b, &c);
    
    terbesar = a;
    if (b > terbesar) {
        terbesar = b;
    }
    if (c > terbesar) {
        terbesar = c;
    }
    
    printf("Bilangan terbesar: %d\n", terbesar);
    
    return 0;
}
```

### Latihan Menengah

#### Latihan 3: Kalkulator dengan Menu
Buat kalkulator sederhana dengan menu operasi.

**Solusi:**
```c
#include <stdio.h>

int main() {
    int choice;
    float num1, num2, result;
    
    printf("=== KALKULATOR SEDERHANA ===\n");
    printf("1. Penjumlahan\n");
    printf("2. Pengurangan\n");
    printf("3. Perkalian\n");
    printf("4. Pembagian\n");
    printf("Pilih operasi: ");
    scanf("%d", &choice);
    
    printf("Masukkan bilangan pertama: ");
    scanf("%f", &num1);
    printf("Masukkan bilangan kedua: ");
    scanf("%f", &num2);
    
    switch(choice) {
        case 1:
            result = num1 + num2;
            printf("%.2f + %.2f = %.2f\n", num1, num2, result);
            break;
        case 2:
            result = num1 - num2;
            printf("%.2f - %.2f = %.2f\n", num1, num2, result);
            break;
        case 3:
            result = num1 * num2;
            printf("%.2f * %.2f = %.2f\n", num1, num2, result);
            break;
        case 4:
            if (num2 != 0) {
                result = num1 / num2;
                printf("%.2f / %.2f = %.2f\n", num1, num2, result);
            } else {
                printf("Error: Pembagian dengan nol!\n");
            }
            break;
        default:
            printf("Pilihan tidak valid!\n");
    }
    
    return 0;
}
```

#### Latihan 4: Konversi Waktu
Buat program konversi detik ke jam:menit:detik.

**Solusi:**
```c
#include <stdio.h>

int main() {
    int total_detik, jam, menit, detik;
    
    printf("Masukkan total detik: ");
    scanf("%d", &total_detik);
    
    jam = total_detik / 3600;
    menit = (total_detik % 3600) / 60;
    detik = total_detik % 60;
    
    printf("%d detik = %02d:%02d:%02d (jam:menit:detik)\n", 
           total_detik, jam, menit, detik);
    
    return 0;
}
```

### Latihan Lanjutan

#### Latihan 5: Sistem Grading Mahasiswa
Buat program untuk menentukan grade berdasarkan nilai dan bandingkan dengan rata-rata kelas.

**Solusi:**
```c
#include <stdio.h>

int main() {
    int n, i;
    float nilai[100], total = 0, rata_rata;
    char grade;
    
    printf("Jumlah mahasiswa: ");
    scanf("%d", &n);
    
    // Input dan hitung total
    for (i = 0; i < n; i++) {
        printf("Nilai mahasiswa %d: ", i + 1);
        scanf("%f", &nilai[i]);
        total += nilai[i];
    }
    
    rata_rata = total / n;
    printf("\nRata-rata kelas: %.2f\n\n", rata_rata);
    
    // Analisis per mahasiswa
    for (i = 0; i < n; i++) {
        // Tentukan grade
        if (nilai[i] >= 85) grade = 'A';
        else if (nilai[i] >= 70) grade = 'B';
        else if (nilai[i] >= 55) grade = 'C';
        else if (nilai[i] >= 40) grade = 'D';
        else grade = 'F';
        
        printf("Mahasiswa %d: %.1f (Grade %c) ", i + 1, nilai[i], grade);
        
        // Perbandingan dengan rata-rata
        if (nilai[i] > rata_rata) {
            printf("- Di atas rata-rata\n");
        } else if (nilai[i] < rata_rata) {
            printf("- Di bawah rata-rata\n");
        } else {
            printf("- Sama dengan rata-rata\n");
        }
    }
    
    return 0;
}
```

#### Latihan 6: Konverter Suhu Multi-Scale
Buat program konversi suhu yang support Celsius, Fahrenheit, dan Kelvin.

**Solusi:**
```c
#include <stdio.h>

float celsius_to_fahrenheit(float c) {
    return (c * 9.0/5.0) + 32.0;
}

float celsius_to_kelvin(float c) {
    return c + 273.15;
}

float fahrenheit_to_celsius(float f) {
    return (f - 32.0) * 5.0/9.0;
}

float kelvin_to_celsius(float k) {
    return k - 273.15;
}

int main() {
    int pilihan;
    float suhu, hasil;
    
    printf("=== KONVERTER SUHU MULTI-SCALE ===\n");
    printf("1. Celsius ke Fahrenheit\n");
    printf("2. Celsius ke Kelvin\n");
    printf("3. Fahrenheit ke Celsius\n");
    printf("4. Kelvin ke Celsius\n");
    printf("Pilihan: ");
    scanf("%d", &pilihan);
    
    printf("Masukkan suhu: ");
    scanf("%f", &suhu);
    
    switch(pilihan) {
        case 1:
            hasil = celsius_to_fahrenheit(suhu);
            printf("%.2f°C = %.2f°F\n", suhu, hasil);
            break;
        case 2:
            hasil = celsius_to_kelvin(suhu);
            printf("%.2f°C = %.2fK\n", suhu, hasil);
            break;
        case 3:
            hasil = fahrenheit_to_celsius(suhu);
            printf("%.2f°F = %.2f°C\n", suhu, hasil);
            break;
        case 4:
            hasil = kelvin_to_celsius(suhu);
            printf("%.2fK = %.2f°C\n", suhu, hasil);
            break;
        default:
            printf("Pilihan tidak valid!\n");
    }
    
    return 0;
}
```

---

## 💡 Tips dan Best Practices

### 1. Validasi Input yang Robust

```c
// BAIK - Validasi input dengan error handling
float get_valid_temperature() {
    float temp;
    int valid_input = 0;
    
    do {
        printf("Masukkan suhu: ");
        if (scanf("%f", &temp) != 1) {
            printf("Input tidak valid! Masukkan angka.\n");
            while(getchar() != '\n'); // Clear input buffer
        } else {
            valid_input = 1;
        }
    } while (!valid_input);
    
    return temp;
}
```

### 2. Penggunaan Konstanta untuk Formula

```c
// BAIK - Menggunakan konstanta untuk formula konversi
#define CELSIUS_TO_FAHRENHEIT_FACTOR 9.0/5.0
#define FAHRENHEIT_OFFSET 32.0
#define KELVIN_OFFSET 273.15

float celsius_to_fahrenheit(float celsius) {
    return (celsius * CELSIUS_TO_FAHRENHEIT_FACTOR) + FAHRENHEIT_OFFSET;
}
```

### 3. Fungsi Utility untuk Reusability

```c
// BAIK - Fungsi utility yang dapat digunakan berulang
int validate_range(float value, float min, float max, char* error_msg) {
    if (value < min || value > max) {
        printf("Error: %s (Range: %.2f - %.2f)\n", error_msg, min, max);
        return 0;
    }
    return 1;
}
```

### 4. Error Handling yang Comprehensive

```c
// BAIK - Error handling untuk operasi matematika
float safe_divide(float numerator, float denominator) {
    if (denominator == 0.0) {
        printf("Error: Pembagian dengan nol tidak diperbolehkan!\n");
        return 0.0;
    }
    return numerator / denominator;
}
```

### 5. Format Output yang User-Friendly

```c
// BAIK - Format output yang informatif
void display_conversion_result(float input, float output, char* from_unit, char* to_unit) {
    printf("\n=== HASIL KONVERSI ===\n");
    printf("Input: %.2f %s\n", input, from_unit);
    printf("Output: %.2f %s\n", output, to_unit);
    printf("Formula yang digunakan: lihat dokumentasi\n");
    printf("=======================\n");
}
```

---

## 🔍 Debugging dan Error Handling

### Common Errors dan Solusinya

#### 1. Floating Point Precision Issues

```c
// MASALAH - Perbandingan floating point yang tidak akurat
if (temperature == 0.0) {
    // Mungkin tidak bekerja dengan baik
}

// SOLUSI - Menggunakan toleransi
#define EPSILON 0.0001
if (fabs(temperature - 0.0) < EPSILON) {
    // Lebih reliable
}
```

#### 2. Input Buffer Issues

```c
// MASALAH - Input buffer tidak dibersihkan
scanf("%d", &choice);
scanf("%c", &continue_choice); // Mungkin skip input

// SOLUSI - Clear buffer
scanf("%d", &choice);
while(getchar() != '\n'); // Clear buffer
scanf("%c", &continue_choice);
```

#### 3. Range Validation

```c
// MASALAH - Tidak memvalidasi range input
float celsius = get_temperature();
float fahrenheit = celsius_to_fahrenheit(celsius);

// SOLUSI - Validasi range
float celsius = get_temperature();
if (celsius < -273.15) {
    printf("Error: Suhu di bawah absolute zero!\n");
    return -1;
}
float fahrenheit = celsius_to_fahrenheit(celsius);
```

---

## 🎯 Kesimpulan

### Ringkasan Materi

Dalam minggu ke-7 ini, kita telah mempelajari implementasi praktis dari operator perbandingan dan algoritma konversi melalui studi kasus nyata. Berikut adalah poin-poin utama:

#### 1. **Operator Perbandingan**
- Menguasai 6 jenis relational operators: ==, !=, >, <, >=, <=
- Implementasi dalam decision making dan validasi data
- Penggunaan dalam loop dan conditional statements

#### 2. **Type Conversion**
- Implicit conversion (automatic) oleh compiler
- Explicit conversion (type casting) manual
- Pentingnya memahami data loss dan precision

#### 3. **Studi Kasus Konversi Suhu**
- Implementasi formula: F = (C × 9/5) + 32
- Program komprehensif dengan multiple temperature scales
- Validasi input dan error handling

#### 4. **Studi Kasus Perbandingan**
- Sistem analisis nilai mahasiswa dengan statistical analysis
- Ranking dan grade distribution
- Perbandingan dengan rata-rata kelas

#### 5. **Aplikasi Lanjutan**
- Sistem konversi mata uang multi-currency
- Konversi satuan panjang dengan multiple units
- Integration dengan konsep dari minggu sebelumnya

### Key Takeaways

1. **Relational operators essential** untuk semua decision making
2. **Algorithm integration** dengan flowchart dan pseudocode
3. **Robust input validation** mencegah runtime errors
4. **Modular programming** meningkatkan code reusability
5. **Real-world applications** membutuhkan comprehensive error handling
6. **Mathematical formulas** harus diimplementasikan dengan precision
7. **User experience** penting dalam interface design

### Integrasi dengan Materi Sebelumnya

- **Minggu 4**: Tipe data dan operator untuk konversi mathematical
- **Minggu 5**: Decision making untuk validation dan menu systems
- **Minggu 6**: Looping untuk repetitive operations dan menu loops

### Persiapan untuk Minggu Selanjutnya

Minggu ke-7 mempersiapkan untuk:
- **Minggu 9**: Bahasa C/C++ dengan implementasi yang lebih advanced
- **Minggu 10**: Fungsi untuk modularisasi sistem yang kompleks
- **Minggu 11**: Array untuk handling multiple data efficiently

### Evaluasi Pembelajaran

✅ Dapat menggunakan semua relational operators dengan tepat  
✅ Memahami dan mengimplementasikan type conversion  
✅ Membuat algoritma konversi suhu sesuai requirement  
✅ Mengintegrasikan flowchart dengan implementasi program  
✅ Membuat sistem perbandingan dengan statistical analysis  
✅ Mengimplementasikan validation dan error handling yang robust

---

## 📖 Referensi dan Sumber Pembelajaran

### Referensi Utama
- **Bab 4-6**: Review materi tipe data, operator, seleksi, dan perulangan
- **GeeksforGeeks**: Comprehensive reference untuk relational operators dan temperature conversion

### Sumber Pembelajaran Online
- **GeeksforGeeks Relational Operators**: Tutorial lengkap tentang comparison operators
- **GeeksforGeeks Temperature Conversion**: Formula dan implementasi konversi suhu
- **GeeksforGeeks Type Conversion**: Penjelasan implicit dan explicit conversion

### Formula Referensi
- **Temperature Conversion Formulas**: Celsius, Fahrenheit, Kelvin conversions