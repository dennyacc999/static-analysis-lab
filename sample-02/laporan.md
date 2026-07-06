# Analisis Statis Sample 02

## Informasi Umum

- Nama Sampel : Windows Notepad
- Tipe File : Portable Executable (PE)
- Sistem Operasi : Windows

## Tools

- PEStudio
- Detect It Easy
- Ghidra

## Hasil Analisis

### Header

File menggunakan format Portable Executable (PE) dan merupakan aplikasi bawaan Windows.

### Import Table

Import yang ditemukan menunjukkan penggunaan API Windows untuk membuat jendela aplikasi, mengelola file, serta berinteraksi dengan sistem operasi.

### Section

Section yang ditemukan meliputi:

- .text
- .rdata
- .data
- .pdata
- .rsrc
- .reloc

### Kesimpulan

Hasil analisis statis menunjukkan bahwa Notepad merupakan aplikasi Windows standar dengan struktur Portable Executable yang lengkap. Analisis dilakukan tanpa menjalankan program sehingga aman dilakukan.

## Catatan

Seluruh informasi diperoleh melalui analisis struktur file Portable Executable menggunakan tools Reverse Engineering.
