
# LAPORAN TUGAS
## MATAKULIAH SISTEM OPERASI
### SINGLE THREAD & MULTITHREAD


Dosen Pengampu:
**Dr. Ferry Astika Saputra ST, M.Sc**

Disusun Oleh:
**Nauril Putri Hadining Tyas (3124521012)**


**PROGRAM STUDI D3 TEKNIK INFORMATIKA PSDKU LAMONGAN**

**POLITEKNIK ELEKTRONIKA NEGERI SURABAYA**


## Single Thread


Single-thread berarti sebuah program hanya memiliki satu aliran eksekusi. Semua tugas dikerjakan secara berurutan: satu instruksi dijalankan, baru setelah selesai lanjut ke instruksi berikutnya. Jika satu tugas membutuhkan waktu lama (seperti membaca file besar atau menunggu respon jaringan), maka seluruh program harus menunggu sampai tugas itu selesai sebelum melanjutkan ke tugas lain. Single-thread lebih sederhana untuk dikembangkan karena tidak ada masalah sinkronisasi data, namun performanya bisa menjadi kurang optimal pada program yang perlu menangani banyak pekerjaan sekaligus.

Kelebihan lain dari single-thread adalah konsumsi resource yang lebih ringan dan debugging yang relatif mudah, karena tidak ada persaingan antar thread. Namun, kekurangannya adalah kurang efektif untuk aplikasi yang membutuhkan banyak operasi paralel, seperti game, server web, atau aplikasi real-time lainnya. Pada sistem modern dengan banyak inti CPU, program single-thread tidak bisa memanfaatkan semua inti tersebut secara maksimal, karena hanya satu inti yang digunakan dalam satu waktu.

**Gambar konsep Single Thread**

* **Single thread**: Eksekusi tugas berurutan, satu per satu.

![Screenshot 2025-04-18 195656](https://github.com/user-attachments/assets/662d1ee3-8dc6-40fc-bf49-2927a2836751)

## Multithread

Multithread berarti sebuah program memiliki beberapa aliran eksekusi (thread) yang berjalan bersamaan. Setiap thread bisa mengerjakan tugas berbeda secara paralel, memungkinkan program menjadi lebih responsif dan cepat. Misalnya, satu thread bisa menangani input pengguna, thread lain memproses data, dan thread lainnya lagi melakukan penyimpanan file — semuanya dalam waktu hampir bersamaan. Dengan memanfaatkan kemampuan CPU multi-core, multithreading bisa meningkatkan kinerja aplikasi secara signifikan.

Namun, pengembangan program multithread lebih kompleks. Programmer harus memastikan sinkronisasi antar thread agar tidak terjadi konflik saat mereka mengakses data yang sama (race condition). Selain itu, masalah seperti deadlock (thread saling menunggu satu sama lain) bisa muncul jika manajemen thread tidak dirancang dengan hati-hati. Walaupun lebih sulit, multithreading menjadi standar dalam banyak aplikasi modern yang membutuhkan kecepatan dan efisiensi tinggi.

**Gambar konsep Multithread**
* **Multithread**: Eksekusi tugas secara paralel, beberapa tugas dapat berjalan bersamaan.

![Screenshot 2025-04-18 195645](https://github.com/user-attachments/assets/4ce98a3c-e096-4b19-8c9a-a6ce77c66e9e)

