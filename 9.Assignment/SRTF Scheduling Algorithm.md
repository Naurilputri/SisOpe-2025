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

kode program : [SJF Scheduling Algorithm Without Arrival Time](https://github.com/ferryastika/Scheduling-Algorithms/blob/master/SRTF%20Scheduling%20Algorithm.c)

Output: 
<img src="https://github.com/Naurilputri/SisOp-2025/blob/main/img/srtf.png">

contoh kasus dari practice exercise:
<img src="https://github.com/Naurilputri/SisOp-2025/blob/main/img/sjf3contoh.png">

**analisis dari:**

Dalam algoritma SRTF, proses yang memiliki waktu eksekusi tersisa paling sedikit akan selalu diprioritaskan. Karena ini adalah varian preemptive dari SJF, CPU dapat menghentikan proses yang sedang berjalan jika ada proses baru yang datang dengan waktu eksekusi lebih pendek.

Di awal waktu (t = 0), hanya P1 yang tersedia, jadi CPU memulai eksekusi P1. Namun, saat P2 datang di t = 1 dengan burst time 4 (lebih pendek dari sisa P1 = 7), P1 akan langsung dihentikan dan digantikan oleh P2.

Selama P2 berjalan, proses P3 dan P4 masuk ke sistem. Tapi karena sisa waktu P2 selalu lebih kecil dari burst time proses baru tersebut, P2 tetap berjalan hingga selesai di t = 5.

Setelah P2 selesai, scheduler memilih proses dengan waktu tersisa paling kecil dari antrean:

P1: sisa 7

P3: 9

P4: 5
Karena P4 memiliki waktu tersisa paling sedikit, maka dijalankan dari t = 5 hingga t = 10.

Lalu P1 kembali dilanjutkan (sisa 7) dan dijalankan dari t = 10 hingga t = 18. Terakhir, P3 dieksekusi tanpa gangguan dari t = 18 hingga t = 27.

Urutan Eksekusi (dalam Gantt Chart kira-kira):
plaintext
Copy
Edit
| P1 | P2       | P4       | P1       | P3       |
 0   1         5         10        18        27

**Ringkasan:**
Proses selalu bisa digantikan jika ada proses lain dengan waktu lebih pendek.

Ini membuat algoritma sangat efisien dalam menurunkan average waiting time, terutama bila banyak proses pendek datang setelah proses panjang sudah dimulai.

Namun, proses panjang bisa terus tertunda bila proses-proses pendek terus berdatangan (disebut starvation).
