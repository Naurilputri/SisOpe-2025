# 🔍 Analisis Logika Kode - SJF (Tanpa Arrival Time) Non-Preemptive

Kode ini mengimplementasikan algoritma **Shortest Job First (SJF)** _Non-Preemptive_ **tanpa mempertimbangkan Arrival Time**, sehingga diasumsikan semua proses datang bersamaan di waktu 0.

---

## 🧱 Struktur Data

```c
struct proc {
    int no, bt, ct, tat, wt;
};
```

### Keterangan:
- `no`: Nomor proses
- `bt`: Burst Time (lama eksekusi)
- `ct`: Completion Time (waktu selesai)
- `tat`: Turnaround Time = `ct` (karena `at` = 0)
- `wt`: Waiting Time = `tat - bt`

---

## 🧩 Fungsi `read()`

Fungsi untuk membaca burst time dari masing-masing proses:
- Input dari pengguna
- `no` diisi sesuai urutan input
- Return struct `proc`

---

## ⚙️ Logika Penjadwalan SJF

### 1. Input dan Inisialisasi
- Program meminta jumlah proses (`n`)
- Input burst time setiap proses
- Semua proses diasumsikan tiba di waktu 0

### 2. Sortir Proses Berdasarkan Burst Time
```c
if(p[j].bt > p[j+1].bt)
```
- Menggunakan bubble sort
- Tujuan: Proses dengan burst time terpendek dikerjakan terlebih dahulu

### 3. Eksekusi dan Perhitungan
- Waktu berjalan (`ct`) diakumulasi dengan burst time setiap proses
- Karena semua proses tiba di waktu 0:
  - `tat = ct`
  - `wt = tat - bt`
- Nilai `tat` dan `wt` dikumpulkan untuk perhitungan rata-rata

---

## 📋 Output

- Output mencetak tabel:
  - Proses, BT, CT, TAT, WT, dan RT (sama dengan WT karena non-preemptive)

- Rata-rata TAT dan WT dihitung

---

## 📈 Gantt Chart (Contoh)

Misalkan input:

| Proses | BT |
|--------|----|
| P1     | 6  |
| P2     | 8  |
| P3     | 7  |
| P4     | 3  |

### Setelah diurutkan berdasarkan BT:
| P4 | P1 | P3 | P2 |
|----|----|----|----|

### Gantt Chart:
```yaml
| P4 | P1 | P3 | P2 |
0    3    9   16   24
```

---

## ✅ Kesimpulan

- Kode mengimplementasikan SJF Non-Preemptive dengan asumsi semua proses datang pada waktu 0.
- Algoritma bekerja optimal untuk skenario sederhana tanpa arrival time.

---

## 🛠️ Saran Peningkatan
- Tambahkan validasi input.
- Tambahkan visualisasi Gantt Chart langsung dalam program.
- Pisahkan logika sorting dan perhitungan agar modular.
