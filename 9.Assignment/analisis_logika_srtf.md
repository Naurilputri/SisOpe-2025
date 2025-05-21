# 🔍 Analisis Logika Code - SRTF Scheduling Algorithm

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

## ⚠️ Catatan Potensial

- **Hardcoded Sentinel**:
  - `p[9].rt = MAX` digunakan sebagai proses dummy.
  - Akan error jika jumlah proses lebih dari 9.

- **Idle Time Tidak Dicetak**:
  - Jika tidak ada proses yang bisa dijalankan, waktu tetap berjalan tanpa log.

- **Tidak Ada Gantt Chart**:
  - Versi asli tidak mencetak urutan proses per waktu.

---

## 💡 Saran Peningkatan
- Tambahkan Gantt Chart untuk visualisasi.
- Gunakan struktur data seperti min-heap atau priority queue untuk efisiensi.
- Validasi agar `n <= 9` atau alokasi dinamis array.
- Tampilkan log preemption untuk debugging dan pemahaman.

---

## ✅ Kesimpulan
Kode ini menjalankan algoritma SRTF secara fungsional dan benar, namun memiliki keterbatasan dari sisi efisiensi, skalabilitas, dan visualisasi. Cocok untuk pembelajaran, namun perlu dioptimasi untuk skenario riil.
