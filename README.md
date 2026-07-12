# Chess WebView App

App Android sederhana (WebView) yang membuka chess.com secara fullscreen tanpa address bar.

## Cara build APK lewat GitHub (tanpa install apapun di HP)

1. Buat akun di https://github.com kalau belum punya.
2. Buat repository baru:
   - Klik tombol **+** di kanan atas → **New repository**
   - Beri nama misalnya `chess-webview-app`
   - Pilih **Public** atau **Private** (bebas)
   - Klik **Create repository**
3. Upload semua file dan folder di dalam folder ini ke repository:
   - Di halaman repo kosong, klik **uploading an existing file**
   - Drag & drop SEMUA file dan folder ini (termasuk folder `.github`, `app`, dll — pastikan strukturnya utuh)
   - Klik **Commit changes**

   > Catatan: kalau upload lewat browser HP, kadang folder `.github` (yang diawali titik) tersembunyi/susah di-drag.
   > Kalau begitu, upload dulu semua file selain `.github`, lalu buat file baru manual:
   > klik **Add file → Create new file**, ketik nama path lengkap: `.github/workflows/build.yml`,
   > lalu copy-paste isi file `build.yml` dari folder ini ke sana.

4. Setelah semua file ter-upload, buka tab **Actions** di repo kamu.
5. Kalau workflow belum otomatis jalan, klik **Build APK** di sidebar kiri → klik **Run workflow** → **Run workflow** (tombol hijau).
6. Tunggu proses build selesai (biasanya 2-5 menit, ada tanda centang hijau kalau sukses).
7. Klik run yang sudah selesai (centang hijau) → scroll ke bawah ke bagian **Artifacts** → download **chess-webview-apk** (dalam bentuk .zip).
8. Ekstrak zip tersebut di HP, dapat file `app-debug.apk` — tinggal install seperti biasa.

## Ganti target website

Kalau mau ganti dari chess.com ke situs lain (misal jagocatur.vercel.app), edit file:

```
app/src/main/java/com/chess/webview/MainActivity.java
```

Ubah baris ini sesuai URL yang diinginkan:

```java
private static final String TARGET_URL = "https://www.chess.com";
```

Setelah edit & commit, GitHub Actions otomatis build ulang APK-nya.

## Catatan

- APK hasil build ini APK "debug" — sudah otomatis ter-signed dengan debug key bawaan Android,
  jadi BISA langsung diinstall tanpa perlu sign manual lagi.
- Ukuran APK jauh lebih kecil/ringan dibanding app chess.com resmi karena cuma berisi WebView shell.
- Tampilan akan fullscreen tanpa address bar karena ini WebView native, bukan TWA/Custom Tab.
