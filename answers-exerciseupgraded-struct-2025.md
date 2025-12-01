## 1) Nilai Tugas Mahasiswa – + Search by ID / Nama

Perubahan utama:

* Tambah `#include <string.h>`
* Tambah dua fungsi:

  * `cari_index_by_id`
  * `cari_index_by_nama`
* Di `main`, setelah statistik, ada loop kecil untuk fitur pencarian.

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

typedef struct {
    int  id;
    char nama[30];
    int  nilai;
} Mahasiswa;

void input_mahasiswa(Mahasiswa *mhs, int n) {
    int i;
    printf("\n--- Input Data Mahasiswa ---\n");
    for (i = 0; i < n; i++) {
        printf("\nMahasiswa ke-%d\n", i + 1);
        printf("ID   : ");
        scanf("%d", &mhs[i].id);
        printf("Nama (tanpa spasi): ");
        scanf("%s", mhs[i].nama);
        printf("Nilai (0-100)     : ");
        scanf("%d", &mhs[i].nilai);
    }
}

void tampil_daftar(Mahasiswa *mhs, int n) {
    int i;
    printf("\nID      %-15s Nilai\n", "Nama");
    for (i = 0; i < n; i++) {
        printf("%-7d %-15s %3d\n",
               mhs[i].id, mhs[i].nama, mhs[i].nilai);
    }
}

int hitung_total(Mahasiswa *mhs, int n) {
    int i, total = 0;
    for (i = 0; i < n; i++) {
        total += mhs[i].nilai;
    }
    return total;
}

int cari_index_max(Mahasiswa *mhs, int n) {
    int i, idx_max = 0;
    for (i = 1; i < n; i++) {
        if (mhs[i].nilai > mhs[idx_max].nilai) {
            idx_max = i;
        }
    }
    return idx_max;
}

int cari_index_min(Mahasiswa *mhs, int n) {
    int i, idx_min = 0;
    for (i = 1; i < n; i++) {
        if (mhs[i].nilai < mhs[idx_min].nilai) {
            idx_min = i;
        }
    }
    return idx_min;
}

/* Bubble sort descending */
void sort_descending(Mahasiswa *mhs, int n) {
    int i, j;
    for (i = 0; i < n - 1; i++) {
        for (j = 0; j < n - 1 - i; j++) {
            if (mhs[j].nilai < mhs[j + 1].nilai) {
                Mahasiswa temp = mhs[j];
                mhs[j] = mhs[j + 1];
                mhs[j + 1] = temp;
            }
        }
    }
}

/* ========== Fitur Pencarian ========== */

/* Cari index mahasiswa berdasarkan ID (linear search) */
int cari_index_by_id(Mahasiswa *mhs, int n, int id_cari) {
    int i;
    for (i = 0; i < n; i++) {
        if (mhs[i].id == id_cari) {
            return i;
        }
    }
    return -1;
}

/* Cari index mahasiswa berdasarkan nama (exact match) */
int cari_index_by_nama(Mahasiswa *mhs, int n, const char *nama_cari) {
    int i;
    for (i = 0; i < n; i++) {
        if (strcmp(mhs[i].nama, nama_cari) == 0) {
            return i;
        }
    }
    return -1;
}

int main() {
    Mahasiswa *kelas = NULL;
    int n;
    int total;
    int idx_max, idx_min;
    float rata_rata, rata_drop;

    printf("Masukkan jumlah mahasiswa: ");
    scanf("%d", &n);

    if (n < 1) {
        printf("Jumlah mahasiswa harus >= 1.\n");
        return 0;
    }

    /* Alokasi dinamis */
    kelas = (Mahasiswa *) malloc(n * sizeof(Mahasiswa));
    if (kelas == NULL) {
        printf("Alokasi memori gagal.\n");
        return 0;
    }

    input_mahasiswa(kelas, n);

    printf("\n=== Daftar Mahasiswa (sebelum sort) ===\n");
    tampil_daftar(kelas, n);

    total     = hitung_total(kelas, n);
    idx_max   = cari_index_max(kelas, n);
    idx_min   = cari_index_min(kelas, n);
    rata_rata = (float) total / n;

    printf("\n=== Statistik Awal ===\n");
    printf("Total nilai   = %d\n", total);
    printf("Rata-rata     = %.2f\n", rata_rata);

    printf("Nilai tertinggi: %d (ID: %d, Nama: %s)\n",
           kelas[idx_max].nilai, kelas[idx_max].id, kelas[idx_max].nama);

    printf("Nilai terendah : %d (ID: %d, Nama: %s)\n",
           kelas[idx_min].nilai, kelas[idx_min].id, kelas[idx_min].nama);

    sort_descending(kelas, n);

    printf("\n=== Daftar Mahasiswa (setelah sort descending) ===\n");
    tampil_daftar(kelas, n);

    if (n > 1) {
        int total_drop = total - kelas[n - 1].nilai;
        rata_drop = (float) total_drop / (n - 1);
        printf("Rata-rata setelah drop 1 nilai terendah = %.2f\n", rata_drop);
    } else {
        printf("Tidak bisa drop nilai karena hanya ada 1 mahasiswa.\n");
    }

    /* ========== Mode Pencarian ========== */
    while (1) {
        int mode;
        printf("\nPencarian (1=by ID, 2=by Nama, 0=keluar): ");
        scanf("%d", &mode);

        if (mode == 0) {
            break;
        } else if (mode == 1) {
            int id_cari;
            printf("Masukkan ID yang dicari: ");
            scanf("%d", &id_cari);
            int idx = cari_index_by_id(kelas, n, id_cari);
            if (idx == -1) {
                printf("Mahasiswa dengan ID %d tidak ditemukan.\n", id_cari);
            } else {
                printf("Ditemukan: ID=%d, Nama=%s, Nilai=%d\n",
                       kelas[idx].id, kelas[idx].nama, kelas[idx].nilai);
            }
        } else if (mode == 2) {
            char nama_cari[30];
            printf("Masukkan Nama (tanpa spasi) yang dicari: ");
            scanf("%s", nama_cari);
            int idx = cari_index_by_nama(kelas, n, nama_cari);
            if (idx == -1) {
                printf("Mahasiswa dengan nama %s tidak ditemukan.\n", nama_cari);
            } else {
                printf("Ditemukan: ID=%d, Nama=%s, Nilai=%d\n",
                       kelas[idx].id, kelas[idx].nama, kelas[idx].nilai);
            }
        } else {
            printf("Mode pencarian tidak valid.\n");
        }
    }

    /* Bebaskan memori */
    free(kelas);

    return 0;
}
```

---

## 2) Kehadiran Mingguan – + Search by ID

Di sini logisnya pencarian **by ID** untuk lihat rekap hadir satu mahasiswa.

Perubahan:

* Tambah fungsi `cari_index_by_id`.
* Tambah menu kecil di akhir untuk mencari 1 mahasiswa.

```c
#include <stdio.h>
#include <stdlib.h>

#define MAX_HARI 7

typedef struct {
    int  id;
    char nama[30];
    int  hadir[MAX_HARI];
} Mahasiswa;

void input_data(Mahasiswa *kelas, int m, int h) {
    int i, j;
    printf("\n--- Input Data Mahasiswa dan Kehadiran ---\n");
    for (i = 0; i < m; i++) {
        printf("\nMahasiswa ke-%d\n", i + 1);
        printf("ID   : ");
        scanf("%d", &kelas[i].id);
        printf("Nama (tanpa spasi): ");
        scanf("%s", kelas[i].nama);

        for (j = 0; j < h; j++) {
            int status;
            do {
                printf("Hari ke-%d (1=hadir, 0=tidak): ", j + 1);
                scanf("%d", &status);
                if (status != 0 && status != 1) {
                    printf("Input harus 0 atau 1.\n");
                }
            } while (status != 0 && status != 1);

            kelas[i].hadir[j] = status;
        }
    }
}

int hitung_hadir_mahasiswa(Mahasiswa *kelas, int index, int h) {
    int j, total = 0;
    for (j = 0; j < h; j++) {
        total += kelas[index].hadir[j];
    }
    return total;
}

int hitung_hadir_hari(Mahasiswa *kelas, int m, int hari_index) {
    int i, total = 0;
    for (i = 0; i < m; i++) {
        total += kelas[i].hadir[hari_index];
    }
    return total;
}

int hitung_total_hadir(Mahasiswa *kelas, int m, int h) {
    int i, j, total = 0;
    for (i = 0; i < m; i++) {
        for (j = 0; j < h; j++) {
            total += kelas[i].hadir[j];
        }
    }
    return total;
}

/* ========== Fitur Pencarian ========== */

int cari_index_by_id(Mahasiswa *kelas, int m, int id_cari) {
    int i;
    for (i = 0; i < m; i++) {
        if (kelas[i].id == id_cari) {
            return i;
        }
    }
    return -1;
}

int main() {
    Mahasiswa *kelas = NULL;
    int m, h;
    int i;
    int total_hadir;
    float persentase;

    printf("Masukkan jumlah mahasiswa: ");
    scanf("%d", &m);
    if (m < 1) {
        printf("Jumlah mahasiswa harus >= 1.\n");
        return 0;
    }

    printf("Masukkan jumlah hari/pertemuan (1-%d): ", MAX_HARI);
    scanf("%d", &h);
    if (h < 1 || h > MAX_HARI) {
        printf("Jumlah hari tidak valid.\n");
        return 0;
    }

    kelas = (Mahasiswa *) malloc(m * sizeof(Mahasiswa));
    if (kelas == NULL) {
        printf("Alokasi memori gagal.\n");
        return 0;
    }

    input_data(kelas, m, h);

    printf("\n=== Rekap Kehadiran per Mahasiswa ===\n");
    for (i = 0; i < m; i++) {
        int hadir_mhs = hitung_hadir_mahasiswa(kelas, i, h);
        printf("ID: %-5d Nama: %-15s -> %d hadir dari %d\n",
               kelas[i].id, kelas[i].nama, hadir_mhs, h);
    }

    printf("\n=== Rekap Kehadiran per Hari ===\n");
    for (i = 0; i < h; i++) {
        int hadir_hari = hitung_hadir_hari(kelas, m, i);
        printf("Hari ke-%d: %d mahasiswa hadir\n", i + 1, hadir_hari);
    }

    total_hadir = hitung_total_hadir(kelas, m, h);
    persentase = (float) total_hadir / (m * h) * 100.0f;

    printf("\nPersentase kehadiran rata-rata kelas = %.2f %%\n",
           persentase);

    /* ========== Mode Pencarian by ID ========== */
    while (1) {
        int id_cari;
        printf("\nMasukkan ID mahasiswa untuk lihat detail (atau -1 untuk keluar): ");
        scanf("%d", &id_cari);

        if (id_cari == -1) {
            break;
        }

        int idx = cari_index_by_id(kelas, m, id_cari);
        if (idx == -1) {
            printf("Mahasiswa dengan ID %d tidak ditemukan.\n", id_cari);
        } else {
            int hadir_mhs = hitung_hadir_mahasiswa(kelas, idx, h);
            printf("Detail kehadiran ID=%d, Nama=%s:\n",
                   kelas[idx].id, kelas[idx].nama);
            for (i = 0; i < h; i++) {
                printf(" Hari ke-%d: %s\n",
                       i + 1, kelas[idx].hadir[i] ? "Hadir" : "Tidak");
            }
            printf(" Total hadir: %d dari %d\n", hadir_mhs, h);
        }
    }

    free(kelas);
    return 0;
}
```

---

## 3) Inventaris Kantin – + Search by Nama (Menu tambahan)

Perubahan:

* Tambah `#include <string.h>`.
* Tambah fungsi `cari_index_by_nama`.
* Tambah menu `[6] Cari item berdasarkan nama`.

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

typedef struct {
    char nama[30];   // nama item, tanpa spasi
    int  harga;      // harga satuan
    int  stok;       // stok tersedia
} Item;

void input_awal_item(Item *daftar, int jumlah_item) {
    int i;
    printf("\n--- Input Data Awal Item Kantin ---\n");
    for (i = 0; i < jumlah_item; i++) {
        printf("\nItem ke-%d\n", i + 1);
        printf("Nama (tanpa spasi): ");
        scanf("%s", daftar[i].nama);
        printf("Harga satuan       : ");
        scanf("%d", &daftar[i].harga);
        printf("Stok awal          : ");
        scanf("%d", &daftar[i].stok);
    }
}

void tampilkan_semua_item(Item *daftar, int jumlah_item) {
    int i;
    printf("\nDaftar Item Kantin:\n");
    printf("Index  %-15s %-10s %-10s\n", "Nama", "Harga", "Stok");
    for (i = 0; i < jumlah_item; i++) {
        printf("%5d  %-15s %-10d %-10d\n",
               i, daftar[i].nama, daftar[i].harga, daftar[i].stok);
    }
}

void tambah_stok_item(Item *daftar, int jumlah_item) {
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

    daftar[index].stok += tambah;
    printf("Stok item '%s' sekarang = %d\n",
           daftar[index].nama, daftar[index].stok);
}

void jual_item(Item *daftar, int jumlah_item, int *total_pemasukan) {
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

    if (jumlah > daftar[index].stok) {
        printf("Stok tidak mencukupi. Stok saat ini: %d\n",
               daftar[index].stok);
        return;
    }

    daftar[index].stok -= jumlah;
    *total_pemasukan += daftar[index].harga * jumlah;

    printf("Berhasil menjual %d '%s'. Stok tersisa = %d\n",
           jumlah, daftar[index].nama, daftar[index].stok);
}

/* ========== Fitur Pencarian Nama ========== */

int cari_index_by_nama(Item *daftar, int jumlah_item, const char *nama_cari) {
    int i;
    for (i = 0; i < jumlah_item; i++) {
        if (strcmp(daftar[i].nama, nama_cari) == 0) {
            return i;
        }
    }
    return -1;
}

void cari_item_nama(Item *daftar, int jumlah_item) {
    char nama_cari[30];
    printf("Masukkan nama item (tanpa spasi) yang dicari: ");
    scanf("%s", nama_cari);

    int idx = cari_index_by_nama(daftar, jumlah_item, nama_cari);
    if (idx == -1) {
        printf("Item '%s' tidak ditemukan.\n", nama_cari);
    } else {
        printf("Ditemukan pada index %d:\n", idx);
        printf("Nama : %s\n", daftar[idx].nama);
        printf("Harga: %d\n", daftar[idx].harga);
        printf("Stok : %d\n", daftar[idx].stok);
    }
}

void tampilkan_menu() {
    printf("\n=== MENU KANTIN ===\n");
    printf("1. Tampilkan semua item\n");
    printf("2. Tambah stok item\n");
    printf("3. Jual item\n");
    printf("4. Tampilkan total pemasukan\n");
    printf("5. Keluar\n");
    printf("6. Cari item berdasarkan nama\n");
    printf("Pilih menu: ");
}

int main() {
    Item *daftar = NULL;
    int jumlah_item;
    int total_pemasukan = 0;

    int pilihan;
    int selesai = 0;

    printf("Masukkan jumlah item kantin: ");
    scanf("%d", &jumlah_item);

    if (jumlah_item < 1) {
        printf("Jumlah item harus >= 1.\n");
        return 0;
    }

    daftar = (Item *) malloc(jumlah_item * sizeof(Item));
    if (daftar == NULL) {
        printf("Alokasi memori gagal.\n");
        return 0;
    }

    input_awal_item(daftar, jumlah_item);

    while (!selesai) {
        tampilkan_menu();
        scanf("%d", &pilihan);

        switch (pilihan) {
            case 1:
                tampilkan_semua_item(daftar, jumlah_item);
                break;
            case 2:
                tambah_stok_item(daftar, jumlah_item);
                break;
            case 3:
                jual_item(daftar, jumlah_item, &total_pemasukan);
                break;
            case 4:
                printf("\nTotal pemasukan = %d\n", total_pemasukan);
                break;
            case 5:
                selesai = 1;
                break;
            case 6:
                cari_item_nama(daftar, jumlah_item);
                break;
            default:
                printf("Pilihan menu tidak valid.\n");
        }
    }

    printf("\nProgram selesai.\n");
    free(daftar);

    return 0;
}
```

---
