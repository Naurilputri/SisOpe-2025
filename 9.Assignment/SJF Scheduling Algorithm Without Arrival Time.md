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

## proses

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
