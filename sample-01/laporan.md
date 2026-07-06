# Analisis Statis Sample 01

## Informasi Umum

- Nama Sampel : DarkComet RAT (menyamar sebagai Facebook)
- Tipe File : Portable Executable (PE)
- Sistem Operasi : Windows

## Tools

- PEStudio
- Detect It Easy
- Ghidra

## Hasil Analisis

### Header

File menggunakan format Portable Executable (PE) dan dapat dikenali dengan baik oleh PEStudio.

### Import Table

Beberapa API Windows digunakan untuk melakukan akses proses, manipulasi memori, serta komunikasi dengan sistem operasi.

### Section

Section utama yang ditemukan meliputi:

- .text
- .data
- .rdata
- .idata
- .rsrc
- .reloc

### Kesimpulan

Analisis statis menunjukkan bahwa file memiliki karakteristik executable Windows dengan beberapa API yang mengindikasikan kemampuan akses terhadap sistem operasi. Analisis dilakukan tanpa mengeksekusi file sehingga aman dilakukan pada lingkungan laboratorium.
