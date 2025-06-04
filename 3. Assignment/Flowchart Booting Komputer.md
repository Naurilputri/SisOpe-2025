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

# Flowchart Booting Komputer
![flowbenar drawio](https://github.com/user-attachments/assets/e4ea9a1a-b9c7-4b4c-a5d2-b36853964145)



1.  **Mulai:** Proses dimulai ketika tombol power pada komputer ditekan.
2.  **Power Dihidupkan:** Sumber daya listrik mulai mengalir ke komponen komputer.
3.  **POST (Power-On Self Test):**
    * Komputer menjalankan serangkaian tes diagnostik untuk memeriksa perangkat keras (RAM, CPU, dll.).
    * **Jika ada kesalahan hardware:**
        * Sistem akan menampilkan pesan error yang mengindikasikan masalah.
    * **Jika tidak ada kesalahan:**
        * Proses booting akan dilanjutkan ke langkah berikutnya.
4.  **BIOS/UEFI:**
    * BIOS (Basic Input/Output System) atau UEFI (Unified Extensible Firmware Interface) dimuat.
    * BIOS/UEFI adalah perangkat lunak dasar yang menginisialisasi perangkat keras dan menyediakan layanan dasar.
5.  **Mencari Bootloader dan Memuat Sistem Operasi:**
    * BIOS/UEFI mencari bootloader (misalnya, GRUB, Windows Boot Manager) pada perangkat penyimpanan (hard disk, SSD).
    * Bootloader kemudian memuat kernel sistem operasi ke memori.
6.  **Sistem Operasi Dijalankan:**
    * Kernel sistem operasi mengambil alih kendali dan mulai menjalankan proses sistem.
    * Kernel adalah inti dari sistem operasi.
7.  **Tampilan Login atau Desktop Muncul:**
    * Setelah sistem operasi selesai diinisialisasi, tampilan login atau desktop environment akan muncul.
    * Pengguna dapat berinteraksi dengan komputer.
8.  **Komputer Siap Digunakan:**
    * Komputer siap digunakan oleh pengguna.
