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
