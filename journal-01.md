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