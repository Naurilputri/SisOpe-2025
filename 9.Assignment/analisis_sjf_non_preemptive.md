# 🧠 Analisis Logika Kode - SJF Scheduling (Non-Preemptive)

Kode ini mengimplementasikan algoritma **Shortest Job First (SJF) Non-Preemptive**, di mana proses dengan burst time terkecil dipilih berikutnya dari proses yang sudah tiba.

---

## 📦 Struktur Data

```c
struct proc {
    int no, at, bt, it, ct, tat, wt;
};
```

**Penjelasan:**
- `no`: Nomor proses
- `at`: Arrival Time
- `bt`: Burst Time
- `it`: Start Time (Idle/Initial Time)
- `ct`: Completion Time
- `tat`: Turnaround Time (`ct - at`)
- `wt`: Waiting Time (`tat - bt`)

---

## 🔁 Alur Program

### 1. Input
- Pengguna memasukkan jumlah proses dan nilai AT serta BT untuk masing-masing proses.

### 2. Sorting Proses Berdasarkan Arrival Time
```c
for(int i=0;i<n-1;i++)
    for(j=0;j<n-i-1;j++)    
        if(p[j].at>p[j+1].at)
```
- Mengurutkan proses berdasarkan waktu kedatangan.

### 3. Memilih Proses Pertama
```c
for(j=1;j<n && p[j].at==p[0].at;j++)
    if(p[j].bt<p[min].bt)
```
- Jika ada beberapa proses dengan arrival time yang sama, proses dengan burst time terkecil dijalankan lebih dulu.

### 4. Penjadwalan Proses Berikutnya
```c
for(j=i+1,min=i;j<n && p[j].at <= p[i-1].ct;j++)
    if(p[j].bt < p[min].bt)
```
- Dari proses yang sudah datang (`at <= waktu selesai proses sebelumnya`), pilih proses dengan BT terkecil.

### 5. Perhitungan Waktu
```c
p[i].it = max(p[i-1].ct, p[i].at);
p[i].ct = p[i].it + p[i].bt;
p[i].tat = p[i].ct - p[i].at;
p[i].wt = p[i].tat - p[i].bt;
```

---

## 🧮 Gantt Chart

### Contoh Asumsi Input:
| Proses | AT | BT |
|--------|----|----|
| P1     | 0  | 8  |
| P2     | 1  | 4  |
| P3     | 2  | 2  |
| P4     | 3  | 1  |

### Gantt Chart:
```yaml
| P1 | P4 | P3 | P2 |
0    8    9   11   15
```

---

## 📊 Tabel Hasil Eksekusi:

| Proses | AT | BT | CT | TAT | WT | RT |
|--------|----|----|----|-----|----|----|
| P1     | 0  | 8  | 8  | 8   | 0  | 0  |
| P4     | 3  | 1  | 9  | 6   | 5  | 5  |
| P3     | 2  | 2  | 11 | 9   | 7  | 7  |
| P2     | 1  | 4  | 15 | 14  | 10 | 10 |

---

## 📈 Rata-Rata:
- **Average Turnaround Time**: `(8 + 6 + 9 + 14)/4 = 9.25`
- **Average Waiting Time**: `(0 + 5 + 7 + 10)/4 = 5.5`

---

## ✅ Kesimpulan
- Proses dengan burst time terkecil dari yang sudah datang akan dipilih.
- Tidak ada preemption, proses berjalan sampai selesai.
- Algoritma ini cocok untuk sistem di mana waktu eksekusi proses diketahui dan tidak sering berubah.

