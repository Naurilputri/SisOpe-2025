# LAPORAN TUGAS
## MATAKULIAH SISTEM OPERASI
### Fork : Parent - Child Process
Dosen Pengampu:

**Dr. Ferry Astika Saputra ST, M.Sc**

Disusun Oleh:

**Nauril Putri Hadining Tyas (3124521012)**

**PROGRAM STUDI D3 TEKNIK INFORMATIKA PSDKU LAMONGAN**

**POLITEKNIK ELEKTRONIKA NEGERI SURABAYA**


## Soal 5.17 - Analisis Penjadwalan CPU

Diberikan kumpulan proses berikut dengan panjang CPU burst dalam milidetik:

| Proses | Burst Time | Prioritas |
|--------|------------|-----------|
| P1     | 5 ms       | 4         |
| P2     | 3 ms       | 1         |
| P3     | 1 ms       | 2         |
| P4     | 7 ms       | 2         |
| P5     | 4 ms       | 3         |

Semua proses datang pada waktu 0 dan urutannya adalah: P1, P2, P3, P4, P5.

#### Pertanyaan:
1. Buat Gantt Chart untuk algoritma FCFS, SJF, Non-preemptive Priority, RR (quantum = 2)
2. Hitung turnaround time untuk setiap proses
3. Hitung waiting time untuk setiap proses
4. Tentukan algoritma dengan rata-rata waiting time paling kecil

---

### a. Gantt Chart

#### FCFS
Urutan: P1 → P2 → P3 → P4 → P5
```
| P1 | P2 | P3 | P4 | P5 |
0    5   8   9  16  20
```

#### SJF
Urutan berdasarkan burst terkecil: P3 → P2 → P5 → P1 → P4
```
| P3 | P2 | P5 | P1 | P4 |
0    1   4   8  13  20
```

#### Non-preemptive Priority
Prioritas tertinggi ke terendah: P1 → P5 → P3 → P4 → P2
```
| P1 | P5 | P3 | P4 | P2 |
0    5   9  10 17  20
```

#### RR (Quantum = 2)
```
|P1|P2|P3|P4|P5|P1|P2|P4|P5|P1|P4|
0  2  4  5  7  9 11 12 14 16 17 20
```

---

### b. Turnaround Time (TAT = Finish Time - Arrival Time)

| Proses | FCFS | SJF | Priority | RR |
|--------|------|-----|----------|----|
| P1     | 5    | 13  | 5        | 17 |
| P2     | 8    | 4   | 20       | 12 |
| P3     | 9    | 1   | 10       | 5  |
| P4     | 16   | 20  | 17       | 20 |
| P5     | 20   | 8   | 9        | 16 |

---

### c. Waiting Time (WT = TAT - Burst Time)

| Proses | FCFS | SJF | Priority | RR |
|--------|------|-----|----------|----|
| P1     | 0    | 8   | 0        | 12 |
| P2     | 5    | 1   | 17       | 9  |
| P3     | 8    | 0   | 9        | 4  |
| P4     | 9    | 13  | 10       | 13 |
| P5     | 16   | 4   | 5        | 12 |

---

### d. Rata-rata Waiting Time

- FCFS: (0 + 5 + 8 + 9 + 16) / 5 = **7.6 ms**
- SJF: (8 + 1 + 0 + 13 + 4) / 5 = **5.2 ms**
- Priority: (0 + 17 + 9 + 10 + 5) / 5 = **8.2 ms**
- RR: (12 + 9 + 4 + 13 + 12) / 5 = **10.0 ms**

**Kesimpulan:** Algoritma **SJF** menghasilkan rata-rata waktu tunggu paling kecil (**5.2 ms**).

---

## Soal 5.18 - Penjadwalan Preemptive Priority dengan Round Robin

### Data Proses:

| Proses | Prioritas | Burst | Arrival |
|--------|-----------|-------|---------|
| P1     | 8         | 15    | 0       |
| P2     | 3         | 20    | 0       |
| P3     | 4         | 20    | 20      |
| P4     | 4         | 20    | 25      |
| P5     | 5         | 5     | 45      |
| P6     | 5         | 15    | 55      |

### Aturan:
- Skema preemptive priority dengan time quantum 10.
- Proses dengan prioritas lebih tinggi (angka lebih besar) akan men-*preempt* proses lainnya.
- Jika prioritas sama, gunakan round-robin dengan quantum 10.
- Proses yang di-preempt dikembalikan ke akhir antrean.

### a. Gantt Chart Penjadwalan
```
| P1 | P1 | P2 | P2 | P3 | P4 | P5 | P6 | P6 |
0   10  20  30  40  50  70  75  90  100
```
Rincian:
- P1 (prioritas 8): dijalankan penuh 15ms tapi dipecah 10 + 5.
- P2 (prio 3): tidak dipotong tapi terbagi dua karena datangnya P3, P4.
- P3 & P4 (prio 4): berbagi dengan RR 10.
- P5 & P6 (prio 5): P5 habis 5ms, P6 dibagi jadi dua.

### b. Turnaround Time (Finish Time - Arrival)

| Proses | Finish | Arrival | Turnaround |
|--------|--------|---------|------------|
| P1     | 20     | 0       | 20         |
| P2     | 40     | 0       | 40         |
| P3     | 60     | 20      | 40         |
| P4     | 75     | 25      | 50         |
| P5     | 80     | 45      | 35         |
| P6     | 100    | 55      | 45         |

### c. Waiting Time (Turnaround - Burst)

| Proses | Turnaround | Burst | Waiting Time |
|--------|------------|-------|---------------|
| P1     | 20         | 15    | 5             |
| P2     | 40         | 20    | 20            |
| P3     | 40         | 20    | 20            |
| P4     | 50         | 20    | 30            |
| P5     | 35         | 5     | 30            |
| P6     | 45         | 15    | 30            |

### Kesimpulan:
Penjadwalan dengan preemptive priority dan round-robin menghasilkan efisiensi dalam merespons proses prioritas tinggi, namun proses dengan prioritas rendah bisa menunggu lama. Rata-rata waiting time:

(5 + 20 + 20 + 30 + 30 + 30) / 6 = **22.5 ms**
