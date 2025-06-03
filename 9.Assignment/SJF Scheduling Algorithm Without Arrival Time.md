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


contoh kasus didalam practice exercise ch 05:

<img src="https://github.com/Naurilputri/SisOp-2025/blob/main/img/sjfcontoh.png">

**analisis dari :** 
Pada kasus ini, seluruh proses (P1–P5) dianggap telah siap dijalankan sejak awal waktu (t=0), sehingga sistem tidak perlu mempertimbangkan arrival time. Algoritma SJF akan memilih proses dengan burst time terpendek yang tersedia saat itu.

Namun, karena yang digunakan adalah varian non-preemptive, begitu suatu proses telah dipilih dan dijalankan, ia akan terus berjalan hingga selesai, tanpa bisa diganggu oleh proses lain, meskipun ada proses baru dengan burst time yang lebih pendek.

Dalam kasus ini, pemilihan proses didasarkan pada urutan prioritas (1 adalah prioritas tertinggi). Bila terdapat dua proses dengan prioritas yang sama, maka urutan kemunculan dalam daftar yang akan dijadikan pembanding, menyerupai mekanisme FCFS (First-Come, First-Served).

**Urutan Eksekusi:**

P2: Memiliki prioritas tertinggi (1), dan burst time 1. Jadi, dieksekusi pertama (t=0–1).

P1 dan P4 memiliki prioritas sama (2). Karena P1 muncul lebih awal, ia dijalankan dari t=1–3.

Setelah itu, P4 dijalankan dari t=3–7.

P5 memiliki prioritas 3, dijalankan dari t=7–12.

Terakhir, P3 (prioritas 4) dijalankan dari t=12–20.

Ringkasan:
Algoritma ini bekerja cukup efisien ketika semua proses datang bersamaan. Dengan mengutamakan burst time dan menghindari preemption, proses dapat dijalankan secara berurutan tanpa gangguan, dan proses dengan waktu eksekusi lebih pendek akan menyelesaikan tugasnya lebih cepat.
---
