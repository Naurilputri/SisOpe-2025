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

# Analisis Logika Code - SJF Scheduling (Non-Preemptive)

kode program : [SJF Scheduling Algorithm](https://github.com/ferryastika/Scheduling-Algorithms/blob/master/SJF%20Scheduling%20Algorithm.c)

Output: 
<img src="https://github.com/Naurilputri/SisOp-2025/blob/main/img/sjf-2.png">


contoh kasus dipractice exercise:
<img src="https://github.com/Naurilputri/SisOp-2025/blob/main/img/sjf2contoh.png">

**analisis dari:**
# Penyelesaian SJF (Shortest Job First) Non-Preemptive Dengan Arrival Time

## Input
Jumlah proses: **3**

### Tabel Proses:
| Proses | Arrival Time (AT) | Burst Time (BT) |
|--------|-------------------|-----------------|
| P1     | 6                 | 4               |
| P2     | 2                 | 3               |
| P3     | 4                 | 2               |

---

## Langkah Penyelesaian
SJF Non-Preemptive dijalankan dengan memperhatikan waktu kedatangan:

1. **Waktu = 0 - 1** → Belum ada proses datang.
2. **Waktu = 2** → P2 datang → *dipilih* karena hanya satu yang tersedia.
3. **Waktu = 5** → P3 sudah datang → *dipilih* karena BT lebih kecil dari P1.
4. **Waktu = 7** → P1 masuk dan dieksekusi terakhir.

---

## Tabel Perhitungan

| Proses | AT | BT | CT  | TAT | WT  |
|--------|----|----|-----|-----|-----|
| P2     | 2  | 3  | 5   | 3   | 0   |
| P3     | 4  | 2  | 7   | 3   | 1   |
| P1     | 6  | 4  | 11  | 5   | 1   |

Keterangan:
- **CT (Completion Time)**: Waktu proses selesai dieksekusi
- **TAT (Turnaround Time)** = CT - AT
- **WT (Waiting Time)** = TAT - BT

---

## Gantt Chart 


