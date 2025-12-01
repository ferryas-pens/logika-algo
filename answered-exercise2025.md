
## 1) Analisis Nilai Tugas (Array + Sorting + Statistik)

```c
#include <stdio.h>

#define MAX_MHS 50

void input_nilai(int nilai[], int n) {
    int i;
    for (i = 0; i < n; i++) {
        printf("Nilai mahasiswa ke-%d: ", i + 1);
        scanf("%d", &nilai[i]);
    }
}

void tampil_nilai(int nilai[], int n) {
    int i;
    for (i = 0; i < n; i++) {
        printf("%d ", nilai[i]);
    }
    printf("\n");
}

int hitung_total(int nilai[], int n) {
    int i, total = 0;
    for (i = 0; i < n; i++) {
        total += nilai[i];
    }
    return total;
}

int cari_max(int nilai[], int n) {
    int i, max = nilai[0];
    for (i = 1; i < n; i++) {
        if (nilai[i] > max) {
            max = nilai[i];
        }
    }
    return max;
}

int cari_min(int nilai[], int n) {
    int i, min = nilai[0];
    for (i = 1; i < n; i++) {
        if (nilai[i] < min) {
            min = nilai[i];
        }
    }
    return min;
}

/* Bubble sort descending */
void sort_descending(int nilai[], int n) {
    int i, j;
    for (i = 0; i < n - 1; i++) {
        for (j = 0; j < n - 1 - i; j++) {
            if (nilai[j] < nilai[j + 1]) {
                int temp = nilai[j];
                nilai[j] = nilai[j + 1];
                nilai[j + 1] = temp;
            }
        }
    }
}

int main() {
    int nilai[MAX_MHS];
    int n;
    int total;
    int max, min;
    float rata_rata;
    float rata_drop;

    printf("Masukkan jumlah mahasiswa (1-%d): ", MAX_MHS);
    scanf("%d", &n);

    if (n < 1 || n > MAX_MHS) {
        printf("Jumlah mahasiswa tidak valid.\n");
        return 0;
    }

    printf("\n--- Input Nilai ---\n");
    input_nilai(nilai, n);

    printf("\nNilai sebelum diurutkan: ");
    tampil_nilai(nilai, n);

    total = hitung_total(nilai, n);
    max   = cari_max(nilai, n);
    min   = cari_min(nilai, n);
    rata_rata = (float) total / n;

    printf("\n=== Statistik Awal ===\n");
    printf("Total nilai      = %d\n", total);
    printf("Rata-rata        = %.2f\n", rata_rata);
    printf("Nilai tertinggi  = %d\n", max);
    printf("Nilai terendah   = %d\n", min);

    /* Urutkan secara menurun (descending) */
    sort_descending(nilai, n);

    printf("\nNilai setelah diurutkan (descending): ");
    tampil_nilai(nilai, n);

    if (n > 1) {
        /* Drop satu nilai terendah: total_drop = total - min */
        rata_drop = (float)(total - min) / (n - 1);
        printf("Rata-rata setelah drop 1 nilai terendah = %.2f\n", rata_drop);
    } else {
        printf("Tidak bisa drop nilai karena hanya ada 1 mahasiswa.\n");
    }

    return 0;
}
```

---

## 2) Rekap Kehadiran Kuliah Mingguan (Array 2D)

```c
#include <stdio.h>

#define MAX_MHS  30
#define MAX_HARI 7

void input_kehadiran(int hadir[][MAX_HARI], int m, int h) {
    int i, j;

    printf("\n--- Input Kehadiran (1=hadir, 0=tidak) ---\n");
    for (i = 0; i < m; i++) {
        for (j = 0; j < h; j++) {
            int status;
            do {
                printf("Mahasiswa ke-%d, Hari ke-%d (1=hadir, 0=tidak): ",
                       i + 1, j + 1);
                scanf("%d", &status);
                if (status != 0 && status != 1) {
                    printf("Input harus 0 atau 1.\n");
                }
            } while (status != 0 && status != 1);

            hadir[i][j] = status;
        }
    }
}

int hitung_hadir_mahasiswa(int hadir[][MAX_HARI], int h, int index_mhs) {
    int j, total = 0;
    for (j = 0; j < h; j++) {
        total += hadir[index_mhs][j];
    }
    return total;
}

int hitung_hadir_hari(int hadir[][MAX_HARI], int m, int index_hari) {
    int i, total = 0;
    for (i = 0; i < m; i++) {
        total += hadir[i][index_hari];
    }
    return total;
}

int hitung_total_hadir(int hadir[][MAX_HARI], int m, int h) {
    int i, j, total = 0;
    for (i = 0; i < m; i++) {
        for (j = 0; j < h; j++) {
            total += hadir[i][j];
        }
    }
    return total;
}

int main() {
    int hadir[MAX_MHS][MAX_HARI];
    int m, h;
    int i;
    int total_hadir;
    float persentase;

    printf("Masukkan jumlah mahasiswa (1-%d): ", MAX_MHS);
    scanf("%d", &m);

    if (m < 1 || m > MAX_MHS) {
        printf("Jumlah mahasiswa tidak valid.\n");
        return 0;
    }

    printf("Masukkan jumlah hari/pertemuan (1-%d): ", MAX_HARI);
    scanf("%d", &h);

    if (h < 1 || h > MAX_HARI) {
        printf("Jumlah hari tidak valid.\n");
        return 0;
    }

    input_kehadiran(hadir, m, h);

    printf("\n=== Rekap Kehadiran per Mahasiswa ===\n");
    for (i = 0; i < m; i++) {
        int hadir_mhs = hitung_hadir_mahasiswa(hadir, h, i);
        printf("Mahasiswa ke-%d: %d hadir dari %d\n",
               i + 1, hadir_mhs, h);
    }

    printf("\n=== Rekap Kehadiran per Hari ===\n");
    for (i = 0; i < h; i++) {
        int hadir_hari = hitung_hadir_hari(hadir, m, i);
        printf("Hari ke-%d: %d mahasiswa hadir\n", i + 1, hadir_hari);
    }

    total_hadir = hitung_total_hadir(hadir, m, h);
    persentase = (float) total_hadir / (m * h) * 100.0f;

    printf("\nPersentase kehadiran rata-rata kelas = %.2f %%\n",
           persentase);

    return 0;
}
```

---

## 3) Inventaris Kantin Kampus (Array Paralel + Menu)

```c
#include <stdio.h>

#define MAX_ITEM 50

void input_awal_item(char nama[][30], int harga[], int stok[], int jumlah_item) {
    int i;
    printf("\n--- Input Data Awal Item Kantin ---\n");
    for (i = 0; i < jumlah_item; i++) {
        printf("\nItem ke-%d\n", i + 1);
        printf("Nama (tanpa spasi): ");
        scanf("%s", nama[i]);          /* contoh sederhana: tanpa spasi */
        printf("Harga satuan: ");
        scanf("%d", &harga[i]);
        printf("Stok awal: ");
        scanf("%d", &stok[i]);
    }
}

void tampilkan_semua_item(char nama[][30], int harga[], int stok[], int jumlah_item) {
    int i;
    printf("\nDaftar Item Kantin:\n");
    printf("Index  %-15s %-10s %-10s\n", "Nama", "Harga", "Stok");
    for (i = 0; i < jumlah_item; i++) {
        printf("%5d  %-15s %-10d %-10d\n",
               i, nama[i], harga[i], stok[i]);
    }
}

void tambah_stok_item(char nama[][30], int stok[], int jumlah_item) {
    int index, tambah;

    printf("Masukkan index item yang akan ditambah stok: ");
    scanf("%d", &index);

    if (index < 0 || index >= jumlah_item) {
        printf("Index item tidak valid.\n");
        return;
    }

    printf("Masukkan jumlah stok yang akan ditambah: ");
    scanf("%d", &tambah);

    if (tambah < 0) {
        printf("Jumlah tidak boleh negatif.\n");
        return;
    }

    stok[index] += tambah;
    printf("Stok item '%s' sekarang = %d\n", nama[index], stok[index]);
}

void jual_item(char nama[][30], int harga[], int stok[],
               int jumlah_item, int *total_pemasukan) {
    int index, jumlah;

    printf("Masukkan index item yang akan dijual: ");
    scanf("%d", &index);

    if (index < 0 || index >= jumlah_item) {
        printf("Index item tidak valid.\n");
        return;
    }

    printf("Masukkan jumlah yang dijual: ");
    scanf("%d", &jumlah);

    if (jumlah < 1) {
        printf("Jumlah harus minimal 1.\n");
        return;
    }

    if (jumlah > stok[index]) {
        printf("Stok tidak mencukupi. Stok saat ini: %d\n", stok[index]);
        return;
    }

    stok[index] -= jumlah;
    *total_pemasukan += harga[index] * jumlah;

    printf("Berhasil menjual %d '%s'. Stok tersisa = %d\n",
           jumlah, nama[index], stok[index]);
}

void tampilkan_menu() {
    printf("\n=== MENU KANTIN ===\n");
    printf("1. Tampilkan semua item\n");
    printf("2. Tambah stok item\n");
    printf("3. Jual item\n");
    printf("4. Tampilkan total pemasukan\n");
    printf("5. Keluar\n");
    printf("Pilih menu: ");
}

int main() {
    char nama[MAX_ITEM][30];
    int harga[MAX_ITEM];
    int stok[MAX_ITEM];
    int jumlah_item;
    int total_pemasukan = 0;

    int pilihan;
    int selesai = 0;

    printf("Masukkan jumlah item kantin (1-%d): ", MAX_ITEM);
    scanf("%d", &jumlah_item);

    if (jumlah_item < 1 || jumlah_item > MAX_ITEM) {
        printf("Jumlah item tidak valid.\n");
        return 0;
    }

    input_awal_item(nama, harga, stok, jumlah_item);

    while (!selesai) {
        tampilkan_menu();
        scanf("%d", &pilihan);

        switch (pilihan) {
            case 1:
                tampilkan_semua_item(nama, harga, stok, jumlah_item);
                break;
            case 2:
                tambah_stok_item(nama, stok, jumlah_item);
                break;
            case 3:
                jual_item(nama, harga, stok, jumlah_item, &total_pemasukan);
                break;
            case 4:
                printf("\nTotal pemasukan = %d\n", total_pemasukan);
                break;
            case 5:
                selesai = 1;
                break;
            default:
                printf("Pilihan menu tidak valid.\n");
        }
    }

    printf("\nProgram selesai.\n");
    return 0;
}
