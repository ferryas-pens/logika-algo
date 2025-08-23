---

# 📘 Modul Pembelajaran Minggu 14

**Topik: Pemrograman Berbasis Objek (Object-Oriented Programming / OOP)**

---

## 1. Pendahuluan

### 1.1 Latar Belakang

Sejak awal perkembangan komputer, bahasa pemrograman selalu berevolusi untuk menyesuaikan dengan kompleksitas masalah yang harus diselesaikan. Generasi awal bahasa pemrograman bersifat sangat sederhana, berorientasi pada instruksi mesin (assembly). Kemudian muncul bahasa prosedural (misalnya C, Pascal, Fortran) yang memungkinkan programmer menulis program dengan struktur yang lebih jelas.

Namun, semakin besar aplikasi yang dibuat, semakin terasa keterbatasan paradigma prosedural. Program prosedural biasanya terdiri dari sekumpulan fungsi (prosedur) yang memanipulasi data. Akibatnya, data dan fungsi terpisah, sulit untuk mengontrol akses, serta menyulitkan kolaborasi tim.

Untuk mengatasi hal tersebut, muncullah paradigma baru: **Pemrograman Berbasis Objek (Object-Oriented Programming, OOP)**. Paradigma ini menyatukan data dan fungsi dalam satu kesatuan yang disebut **objek**. Dengan OOP, program menjadi lebih modular, mudah dipelihara, dapat digunakan kembali, dan mendekati cara manusia berpikir tentang dunia nyata.

### 1.2 Perbandingan Pemrograman Prosedural vs OOP

* **Pemrograman Prosedural**

  * Fokus pada *fungsi* (procedure) yang memproses data.
  * Data cenderung bersifat global.
  * Contoh: Bahasa C, Pascal.

* **Pemrograman Berbasis Objek (OOP)**

  * Fokus pada *objek* yang memiliki atribut (data) dan method (fungsi).
  * Data dan fungsi dibungkus dalam objek, dengan kontrol akses.
  * Contoh: Java, C++, Python.

Analogi:

* Prosedural = dapur besar, semua koki bisa menyentuh semua bahan.
* OOP = restoran modern, setiap chef punya stasiun dengan bahan tertentu, ada manajer yang mengatur alur kerja.

---

## 2. Konsep Dasar Pemrograman Berbasis Objek

### 2.1 Apa itu Class dan Object?

* **Class** → cetak biru (blueprint) untuk membuat objek. Mendefinisikan atribut (variabel) dan method (fungsi) yang dimiliki.
* **Object** → instansi nyata dari sebuah class.

Contoh analogi:

* Class = “Desain rumah” (blueprint).
* Object = “Rumah nyata” yang dibangun berdasarkan blueprint.

### 2.2 Atribut dan Method

* **Atribut (Properties, Fields, Variables)** → menyimpan data.
* **Method (Fungsi)** → perilaku yang dimiliki objek.

Contoh dalam Java:

```java
class Mahasiswa {
    String nama;
    String nim;

    void tampilkanInfo() {
        System.out.println("Nama: " + nama + ", NIM: " + nim);
    }
}
```

### 2.3 Constructor

**Constructor** adalah method khusus yang dipanggil saat objek dibuat untuk menginisialisasi nilai awal.

```java
class Mahasiswa {
    String nama;
    String nim;

    // Constructor
    Mahasiswa(String n, String ni) {
        nama = n;
        nim = ni;
    }

    void tampilkanInfo() {
        System.out.println("Nama: " + nama + ", NIM: " + nim);
    }
}

public class Main {
    public static void main(String[] args) {
        Mahasiswa m1 = new Mahasiswa("Andi", "12345");
        m1.tampilkanInfo();
    }
}
```

Output:

```
Nama: Andi, NIM: 12345
```

### 2.4 Destructor

Java memiliki *garbage collector* sehingga tidak ada destructor eksplisit. Namun dalam C++ ada destructor (`~ClassName()`).

---

## 3. Empat Pilar OOP

### 3.1 Encapsulation

**Encapsulation** adalah membungkus data dan method dalam class, serta membatasi akses dengan `private`, `protected`, `public`.

Contoh:

```java
class Mahasiswa {
    private String nama;
    private String nim;

    public Mahasiswa(String nama, String nim) {
        this.nama = nama;
        this.nim = nim;
    }

    // Getter
    public String getNama() {
        return nama;
    }

    // Setter
    public void setNama(String nama) {
        this.nama = nama;
    }
}
```

### 3.2 Inheritance

**Inheritance (pewarisan)** → class baru dapat mewarisi atribut dan method dari class lain.
Digunakan untuk mengurangi duplikasi kode.

```java
class Mahasiswa {
    String nama;
    String nim;

    void belajar() {
        System.out.println(nama + " sedang belajar.");
    }
}

class MahasiswaS1 extends Mahasiswa {
    String jurusan;
}
```

### 3.3 Polymorphism

**Polymorphism** = kemampuan objek memiliki banyak bentuk.
Contoh: Method overriding.

```java
class Hewan {
    void bersuara() {
        System.out.println("Hewan bersuara...");
    }
}

class Kucing extends Hewan {
    @Override
    void bersuara() {
        System.out.println("Meong!");
    }
}

class Anjing extends Hewan {
    @Override
    void bersuara() {
        System.out.println("Guk guk!");
    }
}
```

### 3.4 Abstraction

**Abstraction** = menyembunyikan detail implementasi, hanya menampilkan fitur penting.
Dapat dibuat dengan **abstract class** atau **interface**.

```java
abstract class Bentuk {
    abstract void gambar();
}

class Lingkaran extends Bentuk {
    void gambar() {
        System.out.println("Menggambar lingkaran");
    }
}
```

---

## 4. Java sebagai Bahasa OOP

### 4.1 Sejarah dan Posisi Java

* Dikembangkan oleh Sun Microsystems (1995).
* Platform independen: “Write Once, Run Anywhere”.
* Bahasa OOP murni (semua harus di dalam class).

### 4.2 Struktur Dasar Program Java

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

* Semua kode berada dalam class.
* Fungsi utama adalah `public static void main(String[] args)`.

---

## 5. Studi Kasus: Class Mahasiswa dan MataKuliah

### 5.1 Desain Class

* `Mahasiswa` → atribut: nama, nim, ipk. Method: tampilkanInfo.
* `MataKuliah` → atribut: kode, nama, sks. Method: tampilkanInfo.

### 5.2 Implementasi Java

```java
class Mahasiswa {
    String nama;
    String nim;
    double ipk;

    Mahasiswa(String nama, String nim, double ipk) {
        this.nama = nama;
        this.nim = nim;
        this.ipk = ipk;
    }

    void tampilkanInfo() {
        System.out.println("Nama: " + nama + ", NIM: " + nim + ", IPK: " + ipk);
    }
}

class MataKuliah {
    String kode;
    String nama;
    int sks;

    MataKuliah(String kode, String nama, int sks) {
        this.kode = kode;
        this.nama = nama;
        this.sks = sks;
    }

    void tampilkanInfo() {
        System.out.println("Kode: " + kode + ", Nama: " + nama + ", SKS: " + sks);
    }
}

public class Main {
    public static void main(String[] args) {
        Mahasiswa m = new Mahasiswa("Budi", "2021001", 3.5);
        m.tampilkanInfo();

        MataKuliah mk = new MataKuliah("IF101", "Algoritma", 3);
        mk.tampilkanInfo();
    }
}
```

---

## 6. Praktik Modularisasi dengan OOP

### 6.1 Membuat Objek

Objek dibuat dengan kata kunci `new`.

```java
Mahasiswa m1 = new Mahasiswa("Citra", "2021002", 3.8);
```

### 6.2 Memanggil Method

Objek memanggil method dengan titik (`.`).

```java
m1.tampilkanInfo();
```

### 6.3 Mengelola Banyak Objek

Kita dapat menyimpan objek dalam array atau ArrayList.

```java
Mahasiswa[] daftar = new Mahasiswa[3];
daftar[0] = new Mahasiswa("Ali", "2021003", 3.6);
daftar[1] = new Mahasiswa("Rina", "2021004", 3.7);
daftar[2] = new Mahasiswa("Tono", "2021005", 3.4);

for (Mahasiswa m : daftar) {
    m.tampilkanInfo();
}
```

---

## 7. Studi Kasus Lanjutan: Sistem Nilai Mahasiswa

### 7.1 Desain

* `Mahasiswa` menyimpan data mahasiswa.
* `MataKuliah` menyimpan data mata kuliah.
* `Nilai` menghubungkan mahasiswa dan mata kuliah dengan nilai.

### 7.2 Implementasi

```java
class Nilai {
    Mahasiswa mahasiswa;
    MataKuliah matakuliah;
    double nilai;

    Nilai(Mahasiswa m, MataKuliah mk, double n) {
        this.mahasiswa = m;
        this.matakuliah = mk;
        this.nilai = n;
    }

    void tampilkanInfo() {
        System.out.println(mahasiswa.nama + " mendapat " + nilai +
                           " pada mata kuliah " + matakuliah.nama);
    }
}

public class Main {
    public static void main(String[] args) {
        Mahasiswa m1 = new Mahasiswa("Ani", "2021006", 3.3);
        MataKuliah mk1 = new MataKuliah("IF102", "Struktur Data", 3);

        Nilai n1 = new Nilai(m1, mk1, 85);
        n1.tampilkanInfo();
    }
}
```

Output:

```
Ani mendapat 85.0 pada mata kuliah Struktur Data
```

---

## 8. Ringkasan Materi

1. OOP lahir untuk mengatasi keterbatasan pemrograman prosedural.
2. Konsep utama: **class**, **object**, **atribut**, **method**.
3. Empat pilar OOP: **encapsulation, inheritance, polymorphism, abstraction**.
4. Java adalah contoh bahasa OOP murni.
5. Studi kasus mahasiswa dan mata kuliah menunjukkan penerapan OOP.
6. OOP mempermudah modularisasi, reusability, dan pemeliharaan kode.

---

## 9. Soal Latihan Mandiri

### Level Dasar

1. Buat class `Mobil` dengan atribut `merek`, `tahun`, dan method `tampilkanInfo()`.
2. Buat class `Segitiga` dengan atribut `alas`, `tinggi`, method `hitungLuas()`.

### Level Menengah

3. Buat class `Pegawai` dan turunkan menjadi `PegawaiTetap` dan `PegawaiHonorer` (inheritance).
4. Buat class `RekeningBank` dengan atribut `saldo`. Terapkan encapsulation (getter & setter).

### Level Lanjut

5. Buat abstract class `BangunDatar` dengan method `hitungLuas()`. Turunkan menjadi `Persegi`, `Lingkaran`.
6. Buat program sistem sederhana: mahasiswa mengambil mata kuliah, dan ditampilkan transkrip nilai.

---

## 10. Referensi

* W3Schools Java Tutorial
* Programiz Java OOP Tutorial
* Silabus Kuliah Logika & Algoritma – Bab 14&#x20;
* James Gosling, *The Java Language Specification*
* Herbert Schildt, *Java: The Complete Reference*

---
