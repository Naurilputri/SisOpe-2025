# LAPORAN TUGAS
## MATAKULIAH SISTEM OPERASI
### RESUME Chapter1 Introduction

Dosen Pengampu:

**Dr. Ferry Astika Saputra ST, M.Sc**

Disusun Oleh:

**Nauril Putri Hadining Tyas (3124521012)**

## PROGRAM STUDI D3 TEKNIK INFORMATIKA PSDKU LAMONGAN

## POLITEKNIK ELEKTRONIKA NEGERI SURABAYA

**1.34 Proses Management - 1.40 caching**

## Manajemen Proses (Process Management)

* Proses adalah program yang sedang dieksekusi, unit kerja aktif dalam sistem.
* Proses memerlukan sumber daya seperti CPU, memori, I/O, file, dan data inisialisasi.
* Sistem operasi bertanggung jawab untuk membuat, menghapus, menangguhkan, melanjutkan proses, menyediakan mekanisme sinkronisasi, komunikasi, dan penanganan deadlock.
* Proses dapat berupa single-threaded (satu penghitung program) atau multi-threaded (banyak penghitung program).
* Konkurensi dicapai dengan memultipleks CPU di antara proses/thread.

## Manajemen Memori (Memory Management)

* Program dan data harus berada di memori untuk dieksekusi.
* Manajemen memori menentukan apa yang ada di memori dan kapan, mengoptimalkan pemanfaatan CPU dan respons pengguna.
* Aktivitas manajemen memori meliputi pelacakan penggunaan memori, pemindahan proses/data ke/dari memori, dan alokasi/dealokasi ruang memori.

## Manajemen Sistem File (File-system Management)

* Sistem operasi menyediakan tampilan logis seragam dari penyimpanan informasi (file).
* File diatur dalam direktori dengan kontrol akses.
* Aktivitas manajemen sistem file meliputi pembuatan/penghapusan file/direktori, manipulasi file/direktori, pemetaan file ke penyimpanan sekunder, dan pencadangan.

## Manajemen Penyimpanan Massal (Mass-Storage Management)

* Disk digunakan untuk menyimpan data yang tidak muat di memori utama atau yang perlu disimpan lama.
* Manajemen disk sangat penting untuk kinerja sistem.
* Aktivitas manajemen penyimpanan massal meliputi pemasangan/pelepasan, manajemen ruang kosong, alokasi penyimpanan, penjadwalan disk, partisi, dan perlindungan.
* Penyimpanan tersier (optik, pita magnetik) juga perlu dikelola.

## Caching

* Prinsip penting di berbagai tingkat komputasi.
* Informasi yang digunakan disalin dari penyimpanan lambat ke penyimpanan cepat (cache) sementara.
* Cache diperiksa terlebih dahulu; jika informasi ada, digunakan langsung dari cache.
* Cache lebih kecil dari penyimpanan yang di-cache.
* Manajemen cache melibatkan ukuran cache dan kebijakan penggantian.
