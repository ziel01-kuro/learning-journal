# Entri Jurnal 01: Pengenalan Tools RE dan Analisis Timer Game

- **Tanggal Log:** 3 Juli 2026
- **Topik:** Analisis Alur Kontrol dan Patching Biner Sederhana
- **Apa yang Dipahami:** Saya berhasil memahami bagaimana sebuah aplikasi native seperti game Minesweeper mengatur logika penghitungan waktu internalnya melalui instruksi assembly. Dengan menggunakan decompiler Ghidra, saya dapat memetakan fungsi pencatatan waktu dan menemukan instruksi yang memicu pertambahan nilai timer tersebut.
- **Apa yang Masih Bingung:** Saya masih sering keliru dalam membedakan *conditional jump* (seperti JZ/JNZ) yang kompleks saat alur kontrol program memiliki banyak cabang logika. Saya juga masih seperti meraba-raba dalam melakukan reverse engineering, dan belum terlalu memahami yang saya lakukan.