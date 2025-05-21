# LAPORAN TUGAS
## MATAKULIAH SISTEM OPERASI
### Scheduling Algorithm
Dosen Pengampu:

**Dr. Ferry Astika Saputra ST, M.Sc**

Disusun Oleh:

**Nauril Putri Hadining Tyas (3124521012)**

**PROGRAM STUDI D3 TEKNIK INFORMATIKA PSDKU LAMONGAN**

**POLITEKNIK ELEKTRONIKA NEGERI SURABAYA**

# Analisis Logika Code - SRTF (Shortest Remaining Time First)

Kode ini mengimplementasikan algoritma penjadwalan CPU **Shortest Remaining Time First (SRTF)**, yaitu versi _preemptive_ dari Shortest Job First (SJF). Berikut ini adalah analisis logika secara sistematis:

---

## 🧱 Struktur Data

```c
struct proc {
    int no, at, bt, rt, ct, tat, wt;
};
```

### Keterangan:
- `no`: Nomor proses
- `at`: Arrival Time (waktu kedatangan)
- `bt`: Burst Time (lama eksekusi)
- `rt`: Remaining Time (sisa eksekusi)
- `ct`: Completion Time (waktu selesai)
- `tat`: Turnaround Time = `ct - at`
- `wt`: Waiting Time = `tat - bt`

---

## 🧩 Fungsi `read()`

Fungsi ini membaca data proses dari input:
- Mengisi `no`, `at`, `bt`
- Menyalin `bt` ke `rt` (remaining time)

---

## ⚙️ Proses Penjadwalan

### 1. Input dan Inisialisasi
- Penggunadiminta memasukkan jumlah proses.
- Data proses dibaca satu per satu.
- Proses diurutkan berdasarkan arrival time (`at`) menggunakan bubble sort.

### 2. Simulasi Waktu
```c
for(time=0; remain != n; time++)
```
- Variabel `time` disimulasikan satuan per satuan.
- Loop berlanjut sampai semua proses (`remain == n`).

### 3. Pemilihan Proses
```c
if(p[i].at <= time && p[i].rt < p[s].rt && p[i].rt > 0)
```
- Memilih proses `i` yang:
  - Sudah datang
  - Belum selesai (`rt > 0`)
  - Memiliki `remaining time` terkecil

### 4. Eksekusi Proses
- `p[s].rt--` mengurangi sisa waktu proses.
- Jika `rt == 0`, proses dianggap selesai:
  - `ct` dicatat
  - `tat` dan `wt` dihitung
  - Total TAT dan WT diakumulasi

### 5. Rata-Rata
- Setelah semua proses selesai, dihitung:
  - `avg_tat = total_tat / n`
  - `avg_wt = total_wt / n`

---
# ⏱️ Gantt Chart - SRTF Scheduling

## Gantt Chart:
```yaml
| P1 | P2 | P3 | P2 | P1 |
0    2    4    5    9   16
```

## 📊 Proses Eksekusi:

| Proses | Arrival Time (AT) | Burst Time (BT) | Completion Time (CT) | Turnaround Time (TAT) | Waiting Time (WT) |
|--------|-------------------|-----------------|-----------------------|------------------------|--------------------|
| P1     | 0                 | 7               | 16                    | 16                     | 9                  |
| P2     | 2                 | 4               | 9                     | 7                      | 3                  |
| P3     | 4                 | 1               | 5                     | 1                      | 0                  |

## 📈 Rata-Rata:
- **Average Turnaround Time:** 8.00
- **Average Waiting Time:** 4.00

## 📌 Catatan:
- Proses dijalankan berdasarkan waktu sisa burst time terpendek (*Shortest Remaining Time First*).
- Proses dapat mengalami preemption jika ada proses baru dengan burst time lebih kecil.
---

