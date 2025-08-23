# Modul Pembelajaran Minggu 15
**Topik: Review & Studi Kasus Besar – Sistem Nilai Mahasiswa**

---

## 1. Pendahuluan

### 1.1 Tujuan Minggu 15
Minggu 15 merupakan tahap penting dalam perkuliahan **Logika & Algoritma**. Setelah mahasiswa belajar teori dan praktik dari Minggu 1 sampai Minggu 14, kini saatnya mengintegrasikan semua konsep ke dalam **satu studi kasus besar**.

Tujuannya:
1. Menggabungkan berbagai konsep pemrograman dasar.
2. Menerapkan algoritma searching dan sorting.
3. Melatih berpikir sistematis membangun aplikasi sederhana.
4. Melatih kerja tim (presentasi kelompok).

### 1.2 Menghubungkan Materi Sebelumnya
- Minggu 1–7: logika dasar, flowchart, tipe data, operator, seleksi, perulangan.  
- Minggu 9–13: bahasa C, fungsi, array, struct, searching, sorting.  
- Minggu 14: OOP (Java).  

---

## 2. Konsep Dasar Studi Kasus Terpadu

### 2.1 Apa itu Studi Kasus Besar?
Studi kasus besar adalah **mini-project** yang mengintegrasikan berbagai konsep algoritma dan pemrograman.

### 2.2 Mengapa Sistem Nilai Mahasiswa?
- Familiar dan relevan.  
- Membutuhkan data kompleks.  
- Membutuhkan fungsi: input, tampilkan, cari, urutkan.  

### 2.3 Keterkaitan dengan Dunia Nyata
Dasar dari aplikasi akademik nyata (SIAKAD, KRS online).  

---

## 3. Perancangan Sistem Nilai Mahasiswa

### 3.1 Identifikasi Kebutuhan
1. Input data mahasiswa.  
2. Input data mata kuliah.  
3. Input nilai.  
4. Tampilkan daftar nilai.  
5. Cari mahasiswa.  
6. Urutkan mahasiswa.  

### 3.2 Data yang Dikelola
- Mahasiswa (NIM, Nama, IPK).  
- Mata Kuliah (kode, nama, SKS).  
- Nilai (relasi mahasiswa-matakuliah).  

### 3.3 Struktur Data
- Array.  
- Struct.  
- Fungsi.  

---

## 4. Implementasi Modular

### 4.1 Struct

```c
struct Mahasiswa {
    char nim[15];
    char nama[50];
    float ipk;
};
```

### 4.2 Fungsi Input & Tampil

```c
void inputMahasiswa(struct Mahasiswa *m) {
    printf("Masukkan NIM: "); scanf("%s", m->nim);
    printf("Masukkan Nama: "); scanf(" %[^
]", m->nama);
    printf("Masukkan IPK: "); scanf("%f", &m->ipk);
}

void tampilMahasiswa(struct Mahasiswa m) {
    printf("NIM: %s, Nama: %s, IPK: %.2f\n", m.nim, m.nama, m.ipk);
}
```

---

## 5. Searching & Sorting

### 5.1 Searching

```c
int cariMahasiswa(struct Mahasiswa daftar[], int n, char nimCari[]) {
    for (int i = 0; i < n; i++) {
        if (strcmp(daftar[i].nim, nimCari) == 0) {
            return i;
        }
    }
    return -1;
}
```

### 5.2 Sorting

```c
void urutMahasiswa(struct Mahasiswa daftar[], int n) {
    for (int i = 0; i < n-1; i++) {
        for (int j = 0; j < n-i-1; j++) {
            if (daftar[j].ipk < daftar[j+1].ipk) {
                struct Mahasiswa temp = daftar[j];
                daftar[j] = daftar[j+1];
                daftar[j+1] = temp;
            }
        }
    }
}
```

---

## 6. Studi Kasus Program

### Pseudocode
```
Mulai
Tampilkan menu
Jika pilih 1: input mahasiswa
Jika pilih 2: tampilkan mahasiswa
Jika pilih 3: keluar
Selesai
```

### Implementasi

```c
#include <stdio.h>
#include <string.h>

struct Mahasiswa {
    char nim[15];
    char nama[50];
    float ipk;
};

void inputMahasiswa(struct Mahasiswa *m) {
    printf("Masukkan NIM: "); scanf("%s", m->nim);
    printf("Masukkan Nama: "); scanf(" %[^
]", m->nama);
    printf("Masukkan IPK: "); scanf("%f", &m->ipk);
}

void tampilMahasiswa(struct Mahasiswa m) {
    printf("NIM: %s, Nama: %s, IPK: %.2f\n", m.nim, m.nama, m.ipk);
}

int main() {
    struct Mahasiswa daftar[100];
    int n = 0, pilihan;
    do {
        printf("\nMenu:\n1. Input Mahasiswa\n2. Tampil\n3. Keluar\nPilih: ");
        scanf("%d", &pilihan);
        if (pilihan == 1) {
            inputMahasiswa(&daftar[n]);
            n++;
        } else if (pilihan == 2) {
            for (int i=0; i<n; i++) tampilMahasiswa(daftar[i]);
        }
    } while (pilihan != 3);
    return 0;
}
```

---

## 7. Analisis Program
- Fungsi modular memisahkan tugas.  
- Searching linear O(n), bubble sort O(n²).  
- Bisa ditingkatkan ke database atau OOP.  

---

## 8. Presentasi Kelompok
- Bagi tugas (analisis, coding, testing).  
- Demo program langsung.  

---

## 9. Ringkasan
- Studi kasus = integrasi array, struct, fungsi, searching, sorting.  
- Modularisasi membuat kode rapi.  
- Searching & sorting sangat penting.  

---

## 10. Soal Latihan

### Individu
- Tambah fitur hapus mahasiswa.  
- Cari berdasarkan nama.  
- Urutkan berdasarkan nama.  

### Kelompok
- Buat sistem lengkap multi-mata kuliah.  
- Tampilkan laporan nilai.  
- Implementasi dengan Java OOP.  

---

## 11. Referensi
- Programiz: Arrays, Struct, Searching, Sorting.  
- W3Schools: C Tutorial.  
- Silabus Logika & Algoritma – Bab 9–13.  
