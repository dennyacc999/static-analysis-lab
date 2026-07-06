# Laporan Analisis Statis - Sampel 02 (Notepad Executable)

## 🔬 1. Identitas File
* **Nama File Masukan:** notepad.exe
* **Format File:** Portable Executable (PE32+) - Windows 64-bit System
* **Arsitektur:** x64 Binary
* **Compiler:** Microsoft Visual C++
* **Status:** Clean / Legitimate Windows OS Binary

## 📊 2. Struktur Section Standar
Sebagai pembanding dari sampel malware, struktur section pada file Notepad resmi ini terlihat sangat bersih dan sesuai standar dokumentasi Microsoft:
* **Section .text:** Berisi instruksi kode eksekusi utama aplikasi tanpa ada anomali ukuran atau tanda-tanda enkripsi.
* **Section .data:** Menyimpan data dan variabel global yang telah diinisialisasi secara aman.
* **Section .rsrc:** Berisi resource standar berupa ikon resmi Notepad, manifest file, serta dialog box untuk antarmuka pengguna.

## 🛠️ 3. Analisis Import Address Table (IAT)
Fungsi API yang diimport murni merepresentasikan fungsi dasar dari sebuah text editor, antara lain:
* `CreateFileW`, `ReadFile`, dan `WriteFile` (KERNEL32.dll) -> Digunakan untuk fungsionalitas dasar membuka, membaca, dan menyimpan file teks ke penyimpanan lokal.
* `GetClipboardData` & `SetClipboardData` (USER32.dll) -> Digunakan untuk memproses fitur copy-paste teks di dalam aplikasi.
