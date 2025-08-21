# **Minggu 8: Review Komprehensif Persiapan UTS**

---

## 1. Tujuan Pembelajaran

* Mahasiswa mampu merefleksi kembali materi dari minggu 1–7.
* Mahasiswa mampu mengerjakan soal yang terintegrasi (logika, algoritma, pemrograman dasar).
* Mahasiswa siap menghadapi UTS dengan pemahaman menyeluruh.

---

## 2. Ringkasan Materi Minggu 1–7

* **Minggu 1**: Pengenalan logika & algoritma.
* **Minggu 2**: Struktur dasar algoritma (sekuensial).
* **Minggu 3**: Tipe data & variabel.
* **Minggu 4**: Operator aritmetika & logika.
* **Minggu 5**: Percabangan (if, else, switch).
* **Minggu 6**: Perulangan (for, while, do-while).
* **Minggu 7**: Array dasar & pengolahan data sederhana.

---

## 3. Simulasi Soal UTS

### **Bagian A – Teori Singkat**

1. Jelaskan perbedaan algoritma dengan program.
2. Apa ciri-ciri algoritma yang baik?
3. Berikan contoh kasus sehari-hari yang bisa dimodelkan dengan percabangan.

---

### **Bagian B – Algoritma & Flowchart**

1. Buat algoritma & flowchart untuk menentukan bilangan terbesar dari 3 angka input.
2. Buat algoritma menghitung rata-rata nilai mahasiswa menggunakan array.

---

### **Bagian C – Pemrograman Dasar**

1. Buat program (C) untuk menampilkan bilangan genap dari 1 sampai 100.
2. Buat program menghitung nilai rata-rata mahasiswa, lalu menampilkan grade:

   * ≥ 80 = A, ≥ 70 = B, ≥ 60 = C, < 60 = D.
3. Buat program sederhana yang meminta user memasukkan password. Jika benar → tampilkan “Akses diterima”, jika salah → “Akses ditolak”.

---

## 4. Pembahasan Soal

### Contoh Soal: Bilangan Terbesar dari 3 Angka

**Algoritma**:

1. Input a, b, c.
2. Jika a ≥ b dan a ≥ c → terbesar = a.
3. Jika b ≥ a dan b ≥ c → terbesar = b.
4. Jika c ≥ a dan c ≥ b → terbesar = c.
5. Output terbesar.

**Program (C):**

```c
#include <stdio.h>
int main() {
    int a, b, c, max;
    printf("Masukkan tiga bilangan: ");
    scanf("%d %d %d", &a, &b, &c);
    if (a >= b && a >= c) max = a;
    else if (b >= a && b >= c) max = b;
    else max = c;
    printf("Bilangan terbesar = %d\n", max);
    return 0;
}
```

---

### Contoh Soal: Menentukan Grade

**Algoritma**:

1. Input nilai.
2. Jika nilai ≥ 80 → A.
3. Jika nilai ≥ 70 → B.
4. Jika nilai ≥ 60 → C.
5. Jika nilai < 60 → D.

**Program (C):**

```c
#include <stdio.h>
int main() {
    int nilai;
    printf("Masukkan nilai: ");
    scanf("%d", &nilai);
    if (nilai >= 80) printf("Grade A");
    else if (nilai >= 70) printf("Grade B");
    else if (nilai >= 60) printf("Grade C");
    else printf("Grade D");
    return 0;
}
```

---

## 5. Tips Strategi UTS

* Pahami **konsep dasar**: jangan hanya menghafal kode.
* Latih soal algoritma → flowchart → program.
* Fokus pada percabangan, perulangan, array.
* Manajemen waktu ujian: kerjakan yang mudah dulu.

---

## 6. Referensi

* Jogianto H.M. *Konsep Dasar Pemrograman Bahasa C*.
* [W3Schools – C Programming](https://www.w3schools.com/c/c_intro.php)
* [Programiz – C Tutorials](https://www.programiz.com/c-programming)

---



