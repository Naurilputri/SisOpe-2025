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

# Analisis Logika Code - SRTF (Shortest Remaining Time First)



##  Proses Eksekusi:

| Proses | Arrival Time (AT) | Burst Time (BT) | Completion Time (CT) | Turnaround Time (TAT) | Waiting Time (WT) |
|--------|-------------------|-----------------|-----------------------|------------------------|--------------------|
| P1     | 0                 | 7               | 16                    | 16                     | 9                  |
| P2     | 2                 | 4               | 9                     | 7                      | 3                  |
| P3     | 4                 | 1               | 5                     | 1                      | 0                  |

## Gantt Chart:
```yaml
| P1 | P2 | P3 | P2 | P1 |
0    2    4    5    9   16
```

##  Rata-Rata:
- **Average Turnaround Time:**  = (16 + 7 + 1) / 3 = **8.00**
- **Average Waiting Time:** = (9 + 3 + 0) / 3 = **4.00**



