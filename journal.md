# Entri Jurnal 01: Pengenalan Tools RE dan Analisis Timer Game

- **Tanggal Log:** 3 Juli 2026
- **Topik:** Analisis Alur Kontrol dan Patching Biner Sederhana
- **Apa yang Dipahami:** Saya berhasil memahami bagaimana sebuah aplikasi native seperti game Minesweeper mengatur logika penghitungan waktu internalnya melalui instruksi assembly. Dengan menggunakan decompiler Ghidra, saya dapat memetakan fungsi pencatatan waktu dan menemukan instruksi yang memicu pertambahan nilai timer tersebut.
- **Apa yang Masih Bingung:** Saya masih sering keliru dalam membedakan *conditional jump* (seperti JZ/JNZ) yang kompleks saat alur kontrol program memiliki banyak cabang logika. Saya juga masih seperti meraba-raba dalam melakukan reverse engineering, dan belum terlalu memahami yang saya lakukan.

---

# Entri Jurnal 02: Instalasi Lingkungan Kerja Lab RE

- **Tanggal Log:** 14 Mei 2026
- **Topik:** Setup Virtual Machine dan Pemilihan Perangkat Lunak RE
- **Apa yang Dipahami:** Saya berhasil mengonfigurasi mesin virtual (VM) berbasis Windows Sandbox dan VMware sebagai lingkungan terisolasi untuk analisis biner yang aman. Saya juga memahami pentingnya memeriksa integritas berkas biner menggunakan nilai hash SHA-256 sebelum melakukan analisis statis mendalam.
- **Apa yang Masih Bingung:** Saya masih sedikit bingung dalam mengoptimalkan pengaturan jaringan internal VM agar benar-benar kedap (host-only) namun tetap efisien saat mentransfer file laporan kerja. Saya juga masih terbilang baru dalam menggunakan linux, jadi saya belum terlalu terbiasa.

---

# Entri Jurnal 03: Identifikasi Format Portable Executable (PE)

- **Tanggal Log:** 2 Juni 2026
- **Topik:** Struktur Header File PE dan Pustaka Impor (DLL)
- **Apa yang Dipahami:** Saya telah mempelajari struktur dasar file Portable Executable (PE), terutama bagian DOS Header, PE Header, dan Section Table (.text, .data, .rsrc). Mengetahui fungsi apa saja yang diimpor oleh aplikasi melalui Import Address Table (IAT) sangat membantu untuk menebak kapabilitas program sebelum membongkar kodenya.
- **Apa yang Masih Bingung:** Memahami pemetaan alamat dari *File Offset* (posisi di harddisk) ke *Relative Virtual Address / RVA* (posisi saat dimuat di memori RAM) masih terasa rumit dan membutuhkan ketelitian matematis. Saya masih merasa saya belum paham apa-apa disini dan seperti meraba-raba.

---

# Entri Jurnal 04: Analisis Statis vs Dinamis & Validasi Input Integer

- **Tanggal Log:** 5 Juli 2026
- **Topik:** Pembedahan biner Linux ELF (01-chaltu-access-me) menggunakan ltrace dan Ghidra untuk memahami validasi kata sandi berbasis integer.
- **Apa yang Dipahami:** Saya mempelajari dasar-dasar dari assembly, memahami cara kerja bahasa pemrograman C, dan juga logika pemecahan challenge crackme pemula. Saya belajar bahwa Assembly merupakan intruksi yang dieksekusi oleh CPU yang diterjemah ke bahasa pemrograman supaya manusia dapat mengerti lebih mudah tentang program tersebut. Saya belajar kantong register seperti RAX, RSI, RDX, dan RSI. Kemudian saya mengerti bahwa penting untuk kita memahami juga dasar-dasar dari Assembly untuk Reverse Engineering, tidak hanya belajar bahasa pemrogramannya saja. Melalui dekompilator Ghidra, saya memahami betapa pentingnya memeriksa tipe data pada deklarasi variabel (seperti int local_14); tipe data ini menjadi petunjuk utama bahwa fungsi scanf menggunakan format string %d (desimal), yang mengubah arah analisis dari pencarian teks string menjadi perhitungan konversi bilangan heksadesimal 0xb7b5 ke desimal 47029.
- **Apa yang Masih Bingung:** Saya masih merasa kebingungan dengan aturan Calling Convention pada arsitektur x86_64, terutama bagaimana prosesor menentukan kapan harus menggunakan register RDI, RSI, atau RDX saat menyusun argumen sebelum fungsi seperti scanf dipanggil. Saya juga masih perlu membiasakan diri membaca struktur assembly pada Ghidra agar tidak mudah bingung saat melihat nama-nama variabel acak seperti DAT_00102024 yang dihasilkan oleh compiler.

---

# Entri Jurnal 05: Pemanfaatan Fungsi Pustaka C (strlen, strtol, strcmp) dalam Analisis Dinamis

- **Tanggal Log:** 6 Juli 2026
- **Topik:** Membedah alur dekripsi string heksadesimal (hex obfuscation) pada biner Linux ELF (02-toronto-c) menggunakan log pemantauan dari ltrace.
- **Apa yang Dipahami:** Hari ini saya mempelajari dan memahami tiga fungsi krusial dari pustaka bahasa C yang sering digunakan oleh program dalam memvalidasi input pengguna, dimulai dari strlen yang bertugas menghitung jumlah karakter atau panjang teks sebelum program mulai memrosesnya. Saya juga mempelajari cara kerja fungsi strtol (String to Long) beserta komponen parameternya (seperti pointer alamat RAM 0x7ff... dan aturan bilangan basis 16), yang digunakan program untuk menerjemahkan sandi angka heksadesimal menjadi nilai karakter ASCII biasa di dalam memori. Setelah itu, saya memahami peran fungsi pembanding teks strcmp (String Compare), di mana pemantauan log ltrace pada parameter fungsi ini memungkinkan saya menyadap langsung kata sandi asli yang disimpan di memori ("Shake it, baby!") dan membuktikan bahwa string heksadesimal lain seperti "secret_key" hanyalah jebakan umpan (decoy) yang menghasilkan nilai selisih tidak nol (32).
- **Apa yang Masih Bingung:** Saya masih merasa belum terlalu tahu dan belum terbiasa mengenai karakteristik mendalam dari fungsi-fungsi bawaan bahasa C seperti strlen, strtol, dan strcmp yang baru saja saya temui dalam pengerjaan challenge crackme hari ini.

---

### Entri Jurnal 06: Analisis Statis Struktur Berkas Windows Portable Executable (PE)

- **Tanggal Log:** 7 Juli 2026
- **Topik:** Analisis statis artefak forensik dan pemetaan tabel impor pada berkas Windows Portable Executable (PE) di laboratorium rekayasa balik.
- **Apa yang Dipahami:** Hari ini saya mempelajari dan memahami struktur fundamental dari berkas berformat Portable Executable (PE) yang digunakan pada sistem operasi Windows. Saya memahami cara menggunakan alat triase seperti *Detect It Easy* (DIE) untuk mengidentifikasi tanda tangan kompilator serta mendeteksi apakah sebuah biner dibungkus oleh proteksi kemasan (*packer*). Selain itu, melalui inspeksi pada *Import Address Table* (IAT), saya memahami bagaimana biner Windows berinteraksi dengan API sistem operasi melalui pemanggilan pustaka dinamis (seperti `kernel32.dll` untuk manajemen memori atau `user32.dll` untuk antarmuka grafis), yang memungkinkan saya memetakan potensi perilaku dan kapabilitas biner tersebut secara statis tanpa perlu mengeksekusinya di dalam lingkungan Windows yang nyata.
- **Apa yang Masih Bingung:** Saya masih merasa bingung dan ingin mempelajari lebih lanjut mengenai bagaimana cara mengatasi biner PE modern yang menerapkan teknik *Anti-Debugging* dan *Anti-Analysis* tingkat lanjut, seperti manipulasi *Process Environment Block* (PEB) atau penyembunyian tabel impor (*import obfuscation*) yang sengaja dirancang oleh pengembang untuk mengecoh alat analisis statis dasar.

---

### Entri Jurnal 07: Resolusi Pemuat NixOS & Komparasi 64-bit Integer

- **Tanggal Log:** 7 Juli 2026
- **Topik:** Resolusi anomali pemuat sistem (*dynamic linker*) NixOS dan pembuktian komparasi integer 64-bit Little-Endian pada biner C++ Qt6 (03-james-portal).
- **Apa yang Dipahami:** Hari ini saya memahami kendala portabilitas biner Linux ELF yang dikompilasi di lingkungan non-standar seperti NixOS, di mana biner tersebut menanamkan jalur *hardcoded interpreter* khusus (`/nix/store/...`) yang memicu error *required file not found* saat dijalankan di Linux biasa. Saya berhasil mempelajari trik untuk memotong (*bypass*) limitasi tersebut dengan memanggil *dynamic linker* bawaan sistem (`/lib64/ld-linux-x86-64.so.2`) secara eksplisit via terminal. Selain itu, melalui jendela decompiler Ghidra, saya memahami teknik optimasi kompilator C++ di mana pengecekan string pendek tidak menggunakan fungsi pembanding teks biasa, melainkan dikonversi menjadi komparasi bilangan bulat 64-bit tunggal (`*local_a8 == 0x656f645f6e686f6a`). Saya juga memahami penerapan aturan tata letak memori **Little-Endian**, di mana nilai heksadesimal tersebut harus dibaca dari kanan ke kiri untuk menerjemahkannya kembali menjadi string ASCII yang sah (`"john_doe"`).
- **Apa yang Masih Bingung:** Saya masih merasa lambat dan cukup kesulitan ketika harus memetakan serta menerjemahkan konstanta integer heksadesimal dari memori ke dalam bentuk teks ASCII secara manual di dalam jendela dekompilasi Ghidra, terutama ketika kode C++ tersebut dipenuhi oleh simbol antarmuka grafis (*name mangling*) yang rumit. Saya ingin mempelajari cara menulis skrip otomatisasi di Ghidra (menggunakan Python atau Jython) agar proses konversi data heksadesimal ke teks ASCII dapat dilakukan secara instan.

---

### Entri Jurnal 08: Refleksi Akhir Metodologi Analisis Biner

- **Tanggal Log:** 7 Juli 2026
- **Topik:** Refleksi komprehensif dan evaluasi akhir metodologi analisis statis (Ghidra) versus dinamis (`ltrace`) dalam rekayasa balik (*reverse engineering*).
- **Apa yang Dipahami:** Melalui penyelesaian seluruh rangkaian tugas portofolio semester ini, saya memahami bahwa *reverse engineering* bukanlah sekadar aktivitas menebak kata sandi secara acak, melainkan proses investigasi forensik yang terstruktur untuk membedah logika berpikir mesin. Saya memahami kapan harus memprioritaskan analisis dinamis (seperti menggunakan `ltrace` untuk menyadap parameter fungsi eksternal secara *live* pada biner C sederhana) dan kapan harus beralih ke analisis statis (seperti menggunakan Ghidra ketika menghadapi biner GUI yang kompleks, algoritma enkripsi internal, atau ketika dependensi pustaka sistem gagal dijalankan). Saya menyadari bahwa penggabungan kedua metode ini merupakan strategi yang paling kuat dan efisien untuk menemukan solusi dari sebuah biner software.
- **Apa yang Masih Bingung:** Saya merasa fondasi pemahaman saya mengenai arsitektur prosesor tingkat rendah (seperti alokasi register x86_64 dan manipulasi *stack frame* secara mendetail) masih menjadi titik kelemahan utama, terutama ketika saya harus menganalisis biner yang seluruh simbol namanya telah dihapus (*stripped binary*). Untuk pengembangan diri selanjutnya, saya berencana mempelajari alat instrumentasi dinamis tingkat lanjut seperti *Frida* atau *Radare2* agar mampu menganalisis biner yang lebih kompleks di masa depan.