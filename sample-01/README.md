# Laporan Analisis Statis - Sampel 01 (DarkComet RAT)

## 🔬 1. Identitas & Integritas File
* **Nama File Masukan:** malware.exe.malz
* **Format File:** Portable Executable (PE32) - Windows 32-bit System
* **Arsitektur:** x86 Binary
* **Skor Intelijen Ancaman (VirusTotal via PEStudio):** 63/72 (Sangat Kuat Terdeteksi Sebagai Trojan/Malicious)

## 📊 2. Bedah Struktur PE Header & Anomali Section
Berdasarkan pengecekan menggunakan tools PEView dan PEStudio, ditemukan karakteristik berikut:
* **DOS Header:** Ditemukan signature valid "MZ" pada awal file, mengonfirmasi file ini adalah executable Windows.
* **Section .text & .itext:** Ukuran Virtual Size dan Raw Size seimbang, menandakan binary tidak di-pack menggunakan UPX atau sejenisnya. Namun, section `.itext` mengonfirmasi penggunaan compiler Borland Delphi.
* **Section .rsrc (Resource):** Memiliki ukuran yang sangat besar dan tidak wajar karena menyimpan aset visual tiruan (Ikon resmi Facebook) untuk kebutuhan rekayasa sosial (*masquerading*).
* **Section .tls (Thread Local Storage):** Ditemukan indikasi TLS Callbacks yang biasa dipakai malware untuk mengeksekusi kode sebelum menyentuh Entry Point utama (teknik evasi).

## 🛠️ 3. Analisis Import Address Table (IAT)
Ditemukan beberapa fungsi API Windows berbahaya yang dipanggil oleh binary ini:
1. `SetWindowsHookExA` (USER32.dll) -> Indikasi fitur spyware/keylogging global untuk merekam input keyboard.
2. `CreateProcessA` & `WriteProcessMemory` (KERNEL32.dll) -> Indikasi fitur *Process Injection* ke dalam proses sistem yang sah.
3. `avicap32.dll` & `winmm.dll` -> Digunakan untuk mengakses hardware multimedia secara diam-diam (webcam dan mikrofon).
