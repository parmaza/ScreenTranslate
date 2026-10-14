# Panduan ScreenTranslate — Windows 11 (Bahasa Indonesia)

## Tujuan
Tekan **Ctrl+Alt+Q**, pilih area layar, baca teks menggunakan Windows OCR lokal, dan tampilkan hasil terjemahan ke Bahasa Indonesia sebagai overlay.

## Cara mendapatkan aplikasi
Untuk sementara, gunakan build dari **Actions → Windows CI → Artifacts** pada fork ini, atau build sendiri dengan Visual Studio 2022+ (Desktop development with C++ dan Windows SDK). Jangan gunakan rilis dari fork sampai mekanisme updater yang masih terikat ke upstream diperbaiki dan diuji.

## Pengaturan
1. Jalankan ScreenTranslate.exe.
2. Klik kanan ikon tray → Settings.
3. Pilih **Windows OCR** untuk meminimalkan pengiriman gambar ke layanan luar.
4. Pilih **Indonesian (id)** sebagai bahasa tujuan, dan **Google web translation** untuk uji awal tanpa API key (layanan tidak resmi, tidak dijamin stabil).
5. Tekan **Ctrl+Alt+Q**, drag area teks, tunggu overlay.
6. Tekan Esc untuk menutup; Ctrl+Alt+W untuk menyembunyikan atau menampilkan hasil terakhir.

## Build
```powershell
powershell.exe -NoProfile -ExecutionPolicy Bypass -File .\scripts\build-native.ps1 -Configuration Release -RunSmokeTest
```

Hasil: `build\native\Release\ScreenTranslate.exe`.

## Validasi yang harus dilakukan pada Windows 11
- [ ] Build Windows CI sukses
- [ ] Smoke test sukses
- [ ] Shortcut aktif pada desktop dan browser
- [ ] OCR teks bahasa Inggris berhasil
- [ ] Hasil diterjemahkan ke Bahasa Indonesia
- [ ] Overlay, Esc, dan multi-monitor berjalan
- [ ] Tidak ada data sensitif dikirim ke layanan eksternal
- [ ] Installer dan pembaruan dari fork telah diaudit sebelum release

## Lisensi dan batasan
Kode proyek menggunakan MIT; pertahankan file LICENSE dan pemberitahuan pihak ketiga. Windows OCR memproses gambar secara lokal, tetapi layanan terjemahan online menerima teks hasil OCR. Jangan terjemahkan materi rahasia menggunakan layanan publik tanpa persetujuan.

**Catatan penting:** Workflow `.github/workflows/windows-release.yml` dan sistem update bawaan sengaja dibatasi pada `reevebyte/ScreenTranslate`. Fork belum siap membuat release mandiri tanpa penyesuaian keamanan dan pengujian.
