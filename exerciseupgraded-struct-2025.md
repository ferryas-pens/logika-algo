Kalau nanti sistemnya dibesarkan, apa yang perlu disiapkan? --> Pakai `struct` (bukan sekadar array primitif),
---

## Soal 1 (Struct) – Analisis Nilai Tugas Mahasiswa

**Konteks lama:** rekap nilai tugas kelas.
**Upgrade:** tiap mahasiswa sekarang punya **ID** dan **nama** selain nilai.

### Spesifikasi Struct

Definisikan tipe struct:

```c
typedef struct {
    int  id;          // NIM sederhana (bilangan bulat)
    char nama[30];    // nama singkat (tanpa spasi boleh, atau boleh dengan fgets)
    int  nilai;       // 0 - 100
} Mahasiswa;
```

### Tugas Program

1. Minta input:

   * `n` = jumlah mahasiswa (1 ≤ n ≤ 50).
2. Deklarasikan:

   ```c
   Mahasiswa kelas[50];
   ```
3. Untuk setiap mahasiswa, input:

   * `id`
   * `nama`
   * `nilai`
4. Program harus bisa:

   a. **Menampilkan daftar mahasiswa** sebelum diurutkan:
   Format kira-kira:

   ```text
   ID    Nama       Nilai
   101   Andi       80
   102   Budi       75
   ...
   ```

   b. **Mencari statistik dasar**:

   * Nilai tertinggi dan data mahasiswanya (ID + nama + nilai).
   * Nilai terendah dan data mahasiswanya.
   * Rata-rata nilai kelas.

   c. **Mengurutkan mahasiswa berdasarkan nilai (descending)**:

   * Implementasi sorting manual (bubble sort / selection sort) di atas array `Mahasiswa`, bukan array `int`.
   * Setelah diurutkan, tampilkan lagi daftar mahasiswa.

   d. **Kebijakan “drop lowest”**:

   * Hitung rata-rata **setelah mengabaikan satu mahasiswa dengan nilai terendah** (jika `n > 1`).
   * Gunakan array yang sudah diurutkan (nilai tertinggi → terendah).

### Dynamic Thinking (untuk soal / diskusi kelas)

* “Kalau nanti kita mau simpan **dua nilai tugas** per mahasiswa (misal `tugas1`, `tugas2`), apa yang berubah di struct dan di perhitungan rata-rata?”
* Bisa ditambah pertanyaan lanjutan (opsional di soal):

  * Tambah menu: cari data mahasiswa berdasarkan `id` lalu tampilkan profil nilai.

---

## Soal 2 (Struct + Array 2D) – Rekap Kehadiran Mahasiswa per Minggu

**Konteks lama:** array 2D `hadir[m][h]`.
**Upgrade:** tiap mahasiswa jadi objek (`struct`) dengan nama dan array kehadiran sendiri.

### Spesifikasi Struct

Definisikan tipe:

```c
#define MAX_HARI 7

typedef struct {
    int  id;                 // ID mahasiswa (NIM simple)
    char nama[30];           // nama singkat
    int  hadir[MAX_HARI];    // 1=hadir, 0=tidak, per hari
} Mahasiswa;
```

### Tugas Program

1. Minta input:

   * `m` = jumlah mahasiswa (1 ≤ m ≤ 30),
   * `h` = jumlah hari/pertemuan (1 ≤ h ≤ 7).

2. Deklarasikan:

   ```c
   Mahasiswa kelas[30];
   ```

3. Untuk setiap mahasiswa:

   * Input `id` dan `nama`.
   * Untuk setiap hari `1..h`, input status kehadiran (`0` atau `1`) dan simpan ke `hadir[j]`.

4. Program harus dapat:

   a. **Menampilkan rekap per mahasiswa**:

   * Untuk tiap mahasiswa, hitung berapa kali hadir dari `h` hari.
   * Tampilkan: `ID, Nama, jumlah hadir`.

   b. **Rekap per hari** (tanpa struct tambahan, cukup loop):

   * Untuk setiap hari `k`, hitung berapa mahasiswa yang hadir pada hari tersebut.

   c. **Persentase kehadiran rata-rata kelas**:

   * Total semua nilai `1` di semua `Mahasiswa.hadir[]`,
   * Dibagi `(m * h)`, kali 100%.

### Dynamic Thinking (untuk soal / diskusi kelas)

* “Kalau satu mahasiswa ikut **2 mata kuliah** dan kita ingin simpan kehadiran per mata kuliah, apakah kita perlu struct di dalam struct (misal `struct MataKuliah`)? Bagaimana desainnya?”
* Tambahkan fitur: cari mahasiswa dengan kehadiran **paling tinggi** dan **paling rendah**, tampilkan ID + nama.

---

## Soal 3 (Struct + Menu) – Sistem Inventaris FoodLab Kampus

**Konteks lama:** tiga array paralel (`nama[]`, `harga[]`, `stok[]`).
**Upgrade:** gabungkan ke struct `Item`, dan buat desain yang mudah dikembangkan (misal nanti mau tambah kategori, diskon, dsb.).

### Spesifikasi Struct

Definisikan tipe:

```c
typedef struct {
    char nama[30];   // nama item, contoh: "NasiGoreng"
    int  harga;      // harga satuan
    int  stok;       // stok tersedia
} Item;
```

### Tugas Program

1. Di awal:

   * Minta input `jumlah_item` (1 ≤ jumlah_item ≤ 50).
   * Deklarasikan:

     ```c
     Item daftar[50];
     ```

2. Input data awal untuk tiap item:

   * `nama`, `harga`, `stok`.

3. Program menampilkan menu berulang:

   ```text
   MENU KANTIN
   1. Tampilkan semua item
   2. Tambah stok item
   3. Jual item
   4. Tampilkan total pemasukan
   5. Keluar
   Pilih menu:
   ```

4. Rinci setiap pilihan:

   **[1] Tampilkan semua item**

   * Tampilkan tabel:

     ```text
     Index  Nama           Harga   Stok
     0      NasiGoreng     15000   10
     1      EsTeh          5000    20
     ...
     ```
   * Data diambil langsung dari array `Item daftar[]`.

   **[2] Tambah stok item**

   * Minta `index` item dan `jumlah` stok yang akan ditambah.
   * Update `daftar[index].stok`.

   **[3] Jual item**

   * Minta `index` item dan `jumlah` yang dijual.
   * Jika `stok` cukup:

     * Kurangi `daftar[index].stok`.
     * Tambah `total_pemasukan` dengan `daftar[index].harga * jumlah`.
   * Jika stok kurang, tampilkan pesan error.

   **[4] Tampilkan total pemasukan**

   * Cetak nilai `total_pemasukan`.

   **[5] Keluar**

   * Program berhenti.

### Dynamic Thinking

1. Jika ke depan kantin ingin mendukung **kategori item** (misal: `MAKANAN`, `MINUMAN`), bagaimana Anda akan mengubah `struct Item`?
2. Jika jumlah item bisa berubah-ubah selama program berjalan (tambah item baru), apa keuntungan memakai:

   * array `Item`,
   * dibandingkan `Item *` dengan alokasi dinamis (`malloc`)?
3. Bagaimana menambahkan fitur pencarian:

   * Cari item berdasarkan nama,
   * Tampilkan hanya item dengan stok di bawah batas tertentu (misal low stock alert)?

---


