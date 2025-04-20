# LAPORAN TUGAS
## MATAKULIAH SISTEM OPERASI  
### PRACTICE EXERCISE CH4

**Dosen Pengampu:**  
Dr Ferry Astika Saputra ST, M.Sc

**Disusun Oleh:**  
Nauril Putri Hadining Tyas (3124521012)

**Program Studi:** D3 Teknik Informatika PSDKU Lamongan  
**Departemen:** Teknik Informatika dan Komputer, Politeknik Elektronika Negeri Surabaya  
**Tahun Pelajaran:** 2025

---

## 4.1 Tiga contoh pemrograman di mana multithreading memberikan kinerja yang lebih baik daripada solusi single-threaded

**Jawaban:**  
1. **Server Web:** Menangani banyak permintaan klien secara bersamaan. Setiap permintaan dapat ditangani oleh thread terpisah, meningkatkan responsivitas.  
2. **Pengolahan Gambar/Video:** Membagi tugas pengolahan menjadi beberapa thread untuk memproses bagian-bagian gambar atau video secara paralel, mempercepat waktu pemrosesan.  
3. **Aplikasi GUI:** Menjaga antarmuka pengguna tetap responsif saat melakukan tugas latar belakang yang intensif, seperti perhitungan atau pengunduhan.  

---

## 4.2 Menggunakan Hukum Amdahl, hitung perolehan kecepatan aplikasi yang memiliki komponen paralel 60 persen untuk  
(a) dua inti pemrosesan dan (b) empat inti pemrosesan.

Hukum Amdahl:  
```
Speedup = 1 / [(1 - P) + (P / N)]
```
- P = proporsi kode yang dapat diparalelkan (60% atau 0.6)  
- N = jumlah inti pemrosesan  

**(a) Dua inti:**  
```
Speedup = 1 / [(1 - 0.6) + (0.6 / 2)] = 1.43
```

**(b) Empat inti:**  
```
Speedup = 1 / [(1 - 0.6) + (0.6 / 4)] = 1.82
```

---

## 4.3 Apakah server web multithread yang dijelaskan di Bagian 4.1 menunjukkan paralelisme tugas atau data?

**Jawaban:**  
Server web multithread menunjukkan *paralelisme tugas*. Setiap thread menangani tugas yang berbeda (permintaan klien), meskipun mungkin mengakses data yang sama.

---

## 4.4 Apa dua perbedaan antara thread level pengguna dan thread level kernel?

**Jawaban:**  
- Thread level pengguna lebih cepat tetapi kurang efisien dalam menangani pemblokiran I/O.  
- Thread level kernel lebih lambat tetapi lebih efisien dalam menangani pemblokiran I/O dan memanfaatkan multiprosesor.

---

## 4.5 Jelaskan tindakan yang diambil oleh kernel untuk melakukan context-switch antara thread level kernel.

**Jawaban:**  
1. Menyimpan status thread yang sedang berjalan (register, penghitung program, dll.).  
2. Memuat status thread berikutnya yang akan dijalankan.  
3. Memperbarui tabel thread.  
4. Melakukan flush TLB (Translation Lookaside Buffer).  

---

## 4.6 Sumber daya apa yang digunakan saat thread dibuat? Bagaimana perbedaannya dengan sumber daya yang digunakan saat proses dibuat?

**Jawaban:**  
- **Thread:** Memiliki penghitung program, register, dan tumpukan. Berbagi ruang alamat dan sumber daya OS dengan thread lain dalam proses yang sama.  
- **Proses:** Memiliki ruang alamat sendiri, sumber daya OS (file, perangkat), dan setidaknya satu thread.

---

## 4.7 Asumsikan bahwa sistem operasi memetakan thread level pengguna ke kernel menggunakan model many-to-many dan pemetaan dilakukan melalui LWP. Selain itu, sistem memungkinkan pengembang untuk membuat thread real-time untuk digunakan dalam sistem real-time. Apakah perlu mengikat thread real-time ke LWP? Jelaskan.

**Jawaban:**  
Ya, perlu mengikat thread real-time ke LWP. Ini memastikan bahwa thread real-time mendapatkan prioritas dan sumber daya yang diperlukan untuk memenuhi persyaratan waktu nyata. Tanpa pengikatan, penjadwal kernel mungkin mengalokasikan LWP ke thread lain, menyebabkan penundaan dan kegagalan dalam memenuhi batasan waktu nyata.

---

## 4.8 Berikan dua contoh pemrograman di mana multithreading tidak memberikan kinerja yang lebih baik daripada solusi single-threaded.

**Jawaban:**  
1. **Program yang sangat sederhana:** Jika program hanya melakukan satu tugas kecil, overhead pembuatan dan pengelolaan thread dapat melebihi manfaat paralelisme.  
2. **Program I/O-bound dengan sedikit komputasi:** Jika program menghabiskan sebagian besar waktunya menunggu operasi I/O, menambahkan thread tidak akan meningkatkan kinerja secara signifikan karena I/O adalah faktor pembatas.

---

## 4.9 Dalam keadaan apa solusi multithreaded menggunakan beberapa thread kernel memberikan kinerja yang lebih baik daripada solusi single-threaded pada sistem single-processor?

**Jawaban:**  
- **Menangani I/O yang memblokir:** Jika satu thread diblokir menunggu I/O, thread lain dapat terus berjalan, meningkatkan responsivitas keseluruhan.  
- **Menangani peristiwa asinkron:** Multithreading dapat memungkinkan program untuk merespons peristiwa asinkron (misalnya, input pengguna, data jaringan) tanpa mengganggu tugas utama.

---

## 4.10 Komponen status program mana yang dibagikan antar thread dalam proses multithreaded?

- **a. Nilai register**  
- **b. Memori heap**  
- **c. Variabel global**  
- **d. Memori stack**  

**Jawaban:**  
a, b, c dibagikan; d tidak dibagikan.

---

## 4.11 Dapatkah solusi multithreaded menggunakan beberapa thread level pengguna mencapai kinerja yang lebih baik pada sistem multiprosesor daripada pada sistem single-processor? Jelaskan.

**Jawaban:**  
Ya, mungkin saja. Meskipun thread level pengguna dikelola oleh pustaka pengguna dan tidak diketahui oleh kernel, pustaka dapat menjadwalkan thread pada prosesor yang berbeda, memungkinkan paralelisme.

---

## 4.12 Dalam Bab 3, kita membahas browser Chrome Google dan praktiknya membuka setiap tab baru dalam proses terpisah. Apakah manfaat yang sama akan tercapai jika, alih-alih, Chrome dirancang untuk membuka setiap tab baru dalam thread terpisah? Jelaskan.

**Jawaban:**  
Tidak, manfaat yang sama tidak akan tercapai. Proses terpisah memberikan isolasi memori dan perlindungan yang lebih kuat daripada thread terpisah. Jika satu tab mengalami crash dalam proses terpisah, itu tidak akan memengaruhi tab lain. Dengan thread, crash dapat memengaruhi seluruh aplikasi.

---

## 4.13 Apakah mungkin memiliki konkurensi tetapi bukan paralelisme? Jelaskan.

**Jawaban:**  
Ya, mungkin saja. Konkurensi berarti beberapa tugas dapat berjalan bersamaan, tetapi tidak harus secara paralel. Misalnya, penjadwalan round-robin pada single-processor memungkinkan konkurensi tetapi bukan paralelisme sejati.

---

## 4.14 Menggunakan Hukum Amdahl, hitung perolehan kecepatan untuk aplikasi berikut:

- **40% paralel:**  
  - (a) 8 inti: Speedup = 1.43  
  - (b) 16 inti: Speedup = 1.54  

- **67% paralel:**  
  - (a) 2 inti: Speedup = 1.51  
  - (b) 4 inti: Speedup = 2.01  

- **90% paralel:**  
  - (a) 4 inti: Speedup = 2.86  
  - (b) 8 inti: Speedup = 4.71  

---

## 4.15 Tentukan apakah masalah berikut menunjukkan paralelisme tugas atau data:

1. **Menggunakan thread terpisah untuk menghasilkan thumbnail untuk setiap foto dalam koleksi.**  
2. **Mentransposisi matriks secara paralel.**  
3. **Aplikasi jaringan di mana satu thread membaca dari jaringan dan thread lain menulis ke jaringan.**  
4. **Aplikasi penjumlahan array fork-join yang dijelaskan di Bagian 4.5.2.**  
5. **Sistem Grand Central Dispatch.**  

**Jawaban:**  
1. Paralelisme tugas  
2. Paralelisme data  
3. Paralelisme tugas  
4. Paralelisme data  
5. Paralelisme tugas  

---

## 4.16 Sistem dengan dua prosesor dual-core memiliki empat prosesor yang tersedia untuk penjadwalan. Aplikasi intensif CPU berjalan pada sistem ini. Semua input dilakukan saat program dimulai, ketika satu file harus dibuka. Demikian pula, semua output dilakukan tepat sebelum program berakhir, ketika hasil program harus ditulis ke satu file. Antara startup dan pengakhiran, program sepenuhnya terikat CPU. Tugas Anda adalah meningkatkan kinerja aplikasi ini dengan multithreading. Aplikasi berjalan pada sistem yang menggunakan model threading one-to-one (setiap thread pengguna dipetakan ke thread kernel).
**Berapa banyak thread yang akan Anda buat untuk melakukan input dan output? Jelaskan.**
   **Berapa banyak thread yang akan Anda buat untuk bagian aplikasi yang intensif CPU? Jelaskan.**


**Jawaban:**  
- **Input/Output:** Satu thread untuk input dan satu thread untuk output.  
- **CPU-intensif:** Empat thread, satu untuk setiap inti prosesor.  

---

## 4.17 Pertimbangkan segmen kode berikut:

```c
pid_t pid;

pid = fork();

if (pid == 0) { /* proses anak */
    /* ... */
    exit(0);
}

/* proses induk */
/* ... */
wait(NULL);
```

**a. Berapa banyak proses unik yang dibuat?** 
a. Jumlah proses unik yang dibuat:* Kode ini membuat *dua* proses unik: satu proses induk dan satu proses anak yang dibuat oleh panggilan fork().
**b. Berapa banyak thread unik yang dibuat?**  
b. Jumlah thread unik yang dibuat:* Kode ini membuat *satu* thread unik di setiap proses. Proses induk memiliki thread utamanya, dan proses anak juga memiliki thread utamanya setelah fork(). Panggilan fork() menduplikasi ruang alamat dan thread eksekusi proses induk.



---

## 4.18 Jelaskan perbedaan mendasar antara thread level pengguna dan thread level kernel. Di bawah sistem operasi mana satu jenis thread mungkin lebih disukai daripada yang lain?

**Jawaban:**  
* *Perbedaan Mendasar:*
    * *Thread Level Pengguna:* Dikelola oleh pustaka thread di ruang pengguna. Kernel tidak menyadari keberadaan thread ini. Peralihan antar thread level pengguna cepat karena tidak melibatkan intervensi kernel. Namun, jika satu thread level pengguna melakukan operasi pemblokiran, seluruh proses juga akan diblokir.
    * *Thread Level Kernel:* Dikelola langsung oleh kernel. Kernel menjadwalkan thread-thread ini. Peralihan antar thread level kernel lebih lambat daripada thread level pengguna karena melibatkan intervensi kernel. Namun, jika satu thread level kernel melakukan operasi pemblokiran, thread lain dalam proses yang sama dapat terus berjalan.

* *Sistem Operasi yang Lebih Memilih Satu Jenis:*
    * *Thread Level Pengguna Lebih Disukai:* Pada sistem operasi yang tidak mendukung multithreading tingkat kernel secara efisien atau di mana kinerja peralihan thread sangat kritis dan pemblokiran I/O jarang terjadi atau dapat dikelola oleh pengguna (misalnya, menggunakan I/O asinkron).
    * *Thread Level Kernel Lebih Disukai:* Pada sistem operasi modern yang mendukung multithreading tingkat kernel dengan baik, terutama pada sistem multiprosesor di mana paralelisme sejati dapat dicapai. Thread level kernel juga lebih unggul dalam menangani situasi di mana satu thread melakukan operasi pemblokiran tanpa memengaruhi seluruh proses.

---

## 4.19 Program yang ditunjukkan pada Gambar 4.23 menggunakan Pthreads. Apa yang akan menjadi output dari program tersebut?

**Jawaban:**  
CHILD: value = 0
PARENT: value = 5
``` :contentReference[oaicite:0]{index=0}
::contentReference[oaicite:1]{index=1}

---

## 4.20 Pertimbangkan implikasi kinerja dari model many-to-many dan model one-to-one untuk sistem multithreaded. Dalam keadaan apa model many-to-many mungkin memberikan kinerja yang lebih baik daripada jumlah thread pengguna yang lebih besar daripada jumlah inti pemrosesan? Jelaskan implikasi kinerja dari skenario berikut:

**Jawaban:**  
a.	Jumlah thread yang dialokasikan ke proses kurang dari jumlah inti pemrosesan.
Ini dapat menyebabkan kurangnya pemanfaatan sumber daya CPU. Beberapa inti pemrosesan mungkin menganggur meskipun ada thread level pengguna yang siap dijalankan. Kinerja paralel mungkin tidak optimal.
b.	Jumlah thread kernel yang dialokasikan ke proses sama dengan jumlah inti pemrosesan.
Ini berpotensi memberikan kinerja terbaik untuk aplikasi terikat CPU dalam model one-to-one. Setiap thread kernel dapat berjalan secara paralel pada inti yang berbeda, memaksimalkan pemanfaatan CPU.
c.	Jumlah thread kernel yang dialokasikan ke proses lebih besar daripada jumlah thread level pengguna.
* *c. Jumlah thread kernel lebih besar daripada jumlah thread level pengguna:* Ini dapat menyebabkan overhead penjadwalan kernel yang tidak perlu. Kernel harus mengelola lebih banyak thread daripada yang benar-benar digunakan oleh aplikasi secara bersamaan. Sumber daya kernel mungkin terbuang untuk mengelola thread-thread tambahan ini tanpa memberikan manfaat paralelisme tambahan.


---

## 4.21 Pthreads menyediakan API untuk pembatalan thread Fungsi pthread_setcancelstate() digunakan untuk mengatur status pembatalan thread. Prototipe fungsinya muncul sebagai berikut:

c
int pthread_setcancelstate(int state, int *oldstate);


Dua nilai yang mungkin untuk state adalah PTHREAD_CANCEL_ENABLE dan PTHREAD_CANCEL_DISABLE. Jelaskan mengapa aplikasi mungkin ingin menonaktifkan pembatalan thread untuk bagian kode tertentu. Berikan contoh dua operasi yang mungkin tidak aman untuk dibatalkan.
1.  *Memperbarui Struktur Data Bersama:* Jika sebuah thread sedang memperbarui struktur data yang diakses oleh thread lain (misalnya, linked list, tabel hash), pembatalan di tengah-tengah operasi ini dapat meninggalkan struktur data dalam keadaan rusak. Thread lain yang mencoba mengakses struktur data ini mungkin mengalami perilaku yang tidak benar atau bahkan crash. Untuk mencegah hal ini, pembatalan thread dapat dinonaktifkan selama bagian kode yang memodifikasi struktur data bersama, dan diaktifkan kembali setelah modifikasi selesai. Mekanisme sinkronisasi seperti mutex atau kunci biasanya digunakan bersamaan dengan penonaktifan pembatalan untuk memastikan akses eksklusif dan penyelesaian operasi kritis.

2.  *Operasi I/O Kritis:* Beberapa operasi input/output mungkin melibatkan beberapa langkah atau transfer data yang harus diselesaikan secara atomik. Misalnya, menulis blok data ke disk atau mengirim serangkaian paket jaringan. Jika sebuah thread dibatalkan di tengah-tengah operasi I/O seperti itu, data mungkin tertulis sebagian atau koneksi jaringan mungkin tertinggal dalam keadaan tidak stabil. Ini dapat menyebabkan kehilangan data, kerusakan file, atau masalah komunikasi. Menonaktifkan pembatalan selama operasi I/O kritis dan memastikan penyelesaian atau rollback yang tepat dapat mencegah masalah ini.

Dalam kedua contoh ini, menonaktifkan pembatalan thread memberikan jaminan bahwa operasi penting akan diselesaikan tanpa gangguan, menjaga konsistensi dan keandalan program. Setelah bagian kode kritis selesai, aplikasi harus mengaktifkan kembali pembatalan thread untuk memungkinkan thread merespons permintaan pembatalan di lain waktu.

