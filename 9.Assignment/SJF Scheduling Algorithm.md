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


##  Gantt Chart

### proses
| Proses | AT | BT |
|--------|----|----|
| P1     | 0  | 8  |
| P2     | 1  | 4  |
| P3     | 2  | 2  |
| P4     | 3  | 1  |

---

##  Tabel Hasil Eksekusi:

| Proses | AT | BT | CT | TAT | WT | RT |
|--------|----|----|----|-----|----|----|
| P1     | 0  | 8  | 8  | 8   | 0  | 0  |
| P4     | 3  | 1  | 9  | 6   | 5  | 5  |
| P3     | 2  | 2  | 11 | 9   | 7  | 7  |
| P2     | 1  | 4  | 15 | 14  | 10 | 10 |

---

### Gantt Chart:
```yaml
| P1 | P4 | P3 | P2 |
0    8    9   11   15
```

##  Rata-Rata:
- **Average Turnaround Time**: `(8 + 6 + 9 + 14)/4 = 9.25`
- **Average Waiting Time**: `(0 + 5 + 7 + 10)/4 = 5.5`

---

