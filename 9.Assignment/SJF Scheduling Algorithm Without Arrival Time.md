<div align="center">
  
# Laporan Tugas Sistem Operasi
</div>
<p align="center">
  <img src="https://github.com/Naurilputri/SisOp-2025/blob/main/img/logo.jpg" width="500"/>
</p>

**Dosen Pengampu:** Dr. Ferry Astika Saputra ST, M.Sc  
**NIP:** 197708232001121002  

**Nama:** Nauril Putri Hadining Tyas  
**NRP:** 3124521012  

**Program Studi:** D3 Teknik Informatika PSDKU LA  
**Mata Kuliah:** Sistem Operasi  
**Tahun Ajaran:** 2025  

---

# 1. Analisis Logika Kode - SJF (Tanpa Arrival Time) Non-Preemptive

kode program : [SJF Scheduling Algorithm Without Arrival Time](https://github.com/ferryastika/Scheduling-Algorithms/blob/master/SJF%20Scheduling%20Algorithm%20Without%20Arrival%20Time.c)

Output: 
<img src="https://github.com/Naurilputri/SisOp-2025/blob/main/img/sjf-1.png">


contoh kasus didalam practice exercise ch 05:

<img src="https://github.com/Naurilputri/SisOp-2025/blob/main/img/sjfcontoh.png">

**analisis dari :** 
Pada kasus ini, seluruh proses (P1–P5) dianggap telah siap dijalankan sejak awal waktu (t=0), sehingga sistem tidak perlu mempertimbangkan arrival time. Algoritma SJF akan memilih proses dengan burst time terpendek yang tersedia saat itu.

Namun, karena yang digunakan adalah varian non-preemptive, begitu suatu proses telah dipilih dan dijalankan, ia akan terus berjalan hingga selesai, tanpa bisa diganggu oleh proses lain, meskipun ada proses baru dengan burst time yang lebih pendek.

Dalam kasus ini, pemilihan proses didasarkan pada urutan prioritas (1 adalah prioritas tertinggi). Bila terdapat dua proses dengan prioritas yang sama, maka urutan kemunculan dalam daftar yang akan dijadikan pembanding, menyerupai mekanisme FCFS (First-Come, First-Served).

# Penyelesaian SJF (Shortest Job First) Non-Preemptive Tanpa Arrival Time

## Input
Jumlah proses: **4**

### Burst Time:
- P1 = 4
- P2 = 2
- P3 = 6
- P4 = 5

---

## Langkah Penyelesaian
Karena tidak ada Arrival Time, maka semua proses dianggap datang pada waktu 0. Urutkan proses berdasarkan Burst Time (dari yang terkecil ke terbesar):

1. P2 (BT=2)
2. P1 (BT=4)
3. P4 (BT=5)
4. P3 (BT=6)

---

## Tabel Perhitungan

| Proses | BT | CT  | TAT | WT  |
|--------|----|-----|-----|-----|
| P2     | 2  | 2   | 2   | 0   |
| P1     | 4  | 6   | 6   | 2   |
| P4     | 5  | 11  | 11  | 6   |
| P3     | 6  | 17  | 17  | 11  |

Keterangan:
- **CT (Completion Time)**: Waktu proses selesai dieksekusi
- **TAT (Turnaround Time)** = CT (Arrival Time dianggap 0)
- **WT (Waiting Time)** = TAT - BT

---

## Gantt Chart

<img src="https://github.com/Naurilputri/SisOp-2025/blob/main/img/gansjf1.png" width="500"/>
---

## Rata-Rata Waktu
- **Average Turnaround Time** = (2 + 6 + 11 + 17) / 4 = **9.00**
- **Average Waiting Time** = (0 + 2 + 6 + 11) / 4 = **4.75**

---
