<div align="center">
  
# Laporan Tugas Sistem Operasi
</div>
<p align="center">
  <img src="https://github.com/Naurilputri/SisOp-2025/blob/main/logo.jpg.webp" width="500"/>
</p>

**Dosen Pengampu:** Dr. Ferry Astika Saputra ST, M.Sc  
**NIP:** 197708232001121002  

**Nama:** Nauril Putri Hadining Tyas  
**NRP:** 3124521012  

**Program Studi:** D3 Teknik Informatika PENS PSDKU LA  
**Mata Kuliah:** Sistem Operasi  
**Tahun Ajaran:** 2025  

---


# Analisis Logika Kode - SJF (Tanpa Arrival Time) Non-Preemptive

https://github.com/ferryastika/Scheduling-Algorithms/blob/master/SJF%20Scheduling%20Algorithm%20Without%20Arrival%20Time.c

---

##  Struktur Data

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

##  Fungsi `read()`

Fungsi untuk membaca burst time dari masing-masing proses:
- Input dari pengguna
- `no` diisi sesuai urutan input
- Return struct `proc`

---

## Logika Penjadwalan SJF

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

## Output

- Output mencetak tabel:
  - Proses, BT, CT, TAT, WT, dan RT (sama dengan WT karena non-preemptive)

- Rata-rata TAT dan WT dihitung

---

## Gantt Chart 

| Proses | BT |
|--------|----|
| P1     | 6  |
| P2     | 8  |
| P3     | 7  |
| P4     | 3  |


### Gantt Chart:
```yaml
| P4 | P1 | P3 | P2 |
0    3    9   16   24
```
---

### Rata-Rata:

- **Average Turnaround Time:** `(3 + 9 + 16 + 24)/4 = 13.00`
- **Average Waiting Time:** `(0 + 3 + 9 + 16)/4 = 7.00`

---
