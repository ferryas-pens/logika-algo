## Soal 1 – Analisis Nilai Tugas (Array + Sorting + Statistik)

**Konteks:**
Dosen ingin menganalisis nilai tugas satu kelas, tidak hanya rata-rata, tapi juga:

* Mengetahui nilai tertinggi & terendah,
* Mengurutkan nilai dari yang tertinggi ke terendah,
* Mengabaikan satu nilai terendah (misal kebijakan “drop lowest score”).

**Tugas:**

Buat program C yang:

1. Meminta input:

   * `n` = jumlah mahasiswa (1 ≤ n ≤ 50).
2. Mendeklarasikan array:

   ```c
   int nilai[50];
   ```
3. Menerima input `n` nilai (0–100) dan menyimpannya ke array.
4. Menghitung dan menampilkan:

   * Semua nilai **sebelum diurutkan**.
   * Nilai maksimum dan minimum.
   * Nilai rata-rata **tanpa drop** (pakai semua data).
5. Mengurutkan array **secara menurun (descending)**, misalnya pakai **bubble sort** manual.
6. Menampilkan:

   * Daftar nilai setelah diurutkan (descending).
   * Nilai rata-rata **setelah mengabaikan 1 nilai terendah** (jika `n > 1`):

     * Artinya, setelah sort descending, gunakan elemen indeks `0..n-2`.

**Spesifikasi teknis:**

* Wajib:

  * Gunakan array `nilai[]`.
  * Implementasi sorting **manual** (tanpa library), boleh bubble/selection.
* Opsional (kalau mau ditambah):

  * Validasi nilai harus 0–100, kalau di luar tampilkan pesan dan minta input ulang untuk mahasiswa tersebut.

---

## Soal 2 – Rekap Kehadiran Kuliah Mingguan (Array 2D)

**Konteks:**
Untuk 1 mata kuliah, dosen ingin tahu kehadiran mahasiswa selama **1 minggu** (misal 5 hari pertemuan intensif). Status kehadiran disimpan sebagai:

* `1` = hadir,
* `0` = tidak hadir.

**Tugas:**

Buat program C yang:

1. Meminta input:

   * `m` = jumlah mahasiswa (maks 30).
   * `h` = jumlah hari/pertemuan (maks 7).
2. Mendeklarasikan array 2D:

   ```c
   int hadir[30][7];
   ```
3. Untuk setiap mahasiswa `i` (0..m-1) dan setiap hari `j` (0..h-1), minta input:

   ```text
   Mahasiswa ke-i, Hari ke-j (1=hadir, 0=tidak): 
   ```
4. Setelah input selesai, program menghitung dan menampilkan:

   1. Untuk **setiap mahasiswa**:

      * Total kehadiran (berapa kali hadir dari `h` hari).
   2. Untuk **setiap hari**:

      * Berapa mahasiswa yang hadir.
   3. Persentase kehadiran rata-rata kelas:

      * Total `1` di seluruh array / (`m * h`) * 100%.

**Output :**

```text
Rekap per mahasiswa:
Mhs 1: 4 hadir dari 5
Mhs 2: 3 hadir dari 5
...

Rekap per hari:
Hari 1: 25 mahasiswa hadir
Hari 2: 27 mahasiswa hadir
...

Persentase kehadiran rata-rata kelas = 86.67 %
```

**Spesifikasi teknis:**

* Wajib:

  * Pakai array 2D `hadir[m][h]`.
  * Minimal 2 loop bersarang untuk input, lalu loop lagi untuk rekap per mahasiswa dan per hari.
* Opsional:

  * Validasi input hanya boleh 0 atau 1.

---

## Soal 3 – Inventaris FoodLab Kampus (Array + Menu)

**Konteks:**
FoodLab kampus punya beberapa item makanan/minuman. Untuk setiap item disimpan:

* Nama (string pendek, boleh pakai `char nama[50][20]` atau sederhanakan),
* Harga satuan,
* Jumlah stok.

Petugas ingin program sederhana dengan menu:

1. Menampilkan daftar item,
2. Menambah stok,
3. Menjual item (mengurangi stok, menghitung pemasukan),
4. Melihat total pemasukan.

**Tugas:**

Buat program C yang:

1. Menyimpan data maksimal 50 item dengan **array paralel**, misalnya:

   ```c
   char nama[50][30];   // nama item
   int harga[50];       // harga satuan
   int stok[50];        // stok tersisa
   int jumlah_item;     // banyak item yang terdaftar
   ```
2. Di awal program:

   * Minta input `jumlah_item` (misal 3–10).
   * Untuk tiap item, input:

     * `nama`,
     * `harga`,
     * `stok` awal.
3. Menampilkan menu berulang:

   ```text
   MENU KANTIN
   1. Tampilkan semua item
   2. Tambah stok item
   3. Jual item
   4. Tampilkan total pemasukan
   5. Keluar
   Pilih menu: 
   ```
4. Detail tiap menu:

   **[1] Tampilkan semua item**

   * Tampilkan daftar:

     ```text
     Index  Nama           Harga    Stok
     0      NasiGoreng     15000    10
     1      EsTeh          5000     20
     ...
     ```

   **[2] Tambah stok item**

   * Minta input `index` item (0 .. jumlah_item-1) dan jumlah stok yang akan ditambah.
   * Update `stok[index]`.

   **[3] Jual item**

   * Minta input:

     * `index` item,
     * `jumlah` yang dijual.
   * Jika `stok` cukup:

     * Kurangi `stok[index]`,
     * Tambahkan ke `total_pemasukan`:

       ```c
       total_pemasukan += harga[index] * jumlah;
       ```
   * Jika stok tidak cukup, tampilkan pesan: `Stok tidak mencukupi`.

   **[4] Tampilkan total pemasukan**

   * Cukup tampilkan nilai `total_pemasukan`.

   **[5] Keluar**

   * Mengakhiri program.

**Spesifikasi teknis:**

* Wajib:

  * Menggunakan **array**: `nama[]`, `harga[]`, `stok[]`.
  * Menggunakan **loop** untuk menampilkan daftar item.
  * Menggunakan **menu dalam loop** (`while` / `do-while`) dan `switch-case`.
* Boleh menyederhanakan input string (misal pakai nama tanpa spasi).

