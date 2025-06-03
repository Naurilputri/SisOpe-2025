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

Pada ilustrasi ini, proses-proses datang di waktu yang berbeda-beda, sehingga pemilihan proses oleh scheduler tidak hanya memperhatikan burst time, tapi juga arrival time.

Ketika sistem mulai berjalan di t = 0, hanya P1 yang sudah masuk ke ready queue. Meskipun P1 memiliki burst time yang cukup lama (8 unit waktu), karena belum ada proses lain yang tersedia, CPU langsung mengeksekusi P1. Karena ini adalah SJF non-preemptive, P1 akan terus berjalan sampai selesai di t = 8, meskipun proses lain masuk di tengah-tengah eksekusinya.

Setelah P1 selesai, dua proses lain (P2 dan P3) sudah tersedia:

P2 datang di t = 0.4 (BT = 4)

P3 datang di t = 1.0 (BT = 1)

Pada titik ini, scheduler akan memilih proses dengan burst time terpendek. Karena P3 hanya membutuhkan 1 unit waktu, maka P3 dijalankan lebih dahulu. Setelah P3 selesai di t = 9, proses yang tersisa hanya P2, yang kemudian dieksekusi dari t = 9 hingga t = 13.

Urutan Eksekusi:
P1: t = 0 → t = 8

P3: t = 8 → t = 9

P2: t = 9 → t = 13

**Ringkasan:**
Penjadwalan mengutamakan proses dengan burst time terpendek yang sudah tersedia saat CPU siap.
Karena sifatnya non-preemptive, proses yang sedang berjalan tidak akan dihentikan meskipun ada proses baru yang lebih singkat.
Hal ini menyebabkan P1 tetap berjalan penuh, walaupun P3 seharusnya bisa selesai jauh lebih cepat jika preemption diperbolehkan.
