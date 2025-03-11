```
SisOp FLOWCHART
NAURIL PUTRI HADINING TYAS

3124521012

CLASS IT A

    A[Mulai: Tombol Power Ditekan] --> B{Power Supply Aktif?};
    B -- Ya --> C[POST (Power-On Self Test)];
    B -- Tidak --> D[Periksa Sumber Daya];
    C --> E{POST Berhasil?};
    E -- Ya --> F[BIOS/UEFI Memuat];
    E -- Tidak --> G[Tampilkan Pesan Error POST];
    F --> H[Pilih Perangkat Boot];
    H --> I[Bootloader Dimuat];
    I --> J[Kernel Sistem Operasi Dimuat];
    J --> K[Inisialisasi Perangkat dan Driver];
    K --> L[Proses Login/Desktop Dimulai];
    L --> M{Login Berhasil?};
    M -- Ya --> N[Komputer Siap Digunakan];
    M -- Tidak --> O[Tampilkan Layar Login];
    G --> P[Hentikan Proses Booting];
    D --> P;
    O --> M;
    N --> Q[Selesai];
    P --> Q;
