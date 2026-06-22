# Security Checklist — Pertemuan 14
## Mobile Programming Lanjutan | INF2.62.6005 | Universitas Negeri Padang
**Nama:** Wahyu Abdil Afif | **NIM:** 23343085

---

## Ringkasan OWASP Mobile Top 10 (2024) yang Relevan untuk Repo Ini

| Kode | Kategori | Status di Repo Ini |
|------|----------|--------------------|
| M1 | Improper Credential Usage | ⚠️ Perlu verifikasi — token jangan di SharedPreferences |
| M3 | Insecure Authentication/Authorization | ⚠️ Pastikan JWT memiliki field `exp` & divalidasi di server |
| M5 | Insecure Communication | ⚠️ Pastikan semua API call pakai HTTPS |
| M4 | Insufficient Input/Output Validation | ⚠️ Tambahkan validasi form sebelum request dikirim |
| M9 | Insecure Data Storage | ⚠️ Data sensitif harus dienkripsi |

---

## Checklist Keamanan Pra-Rilis

### ■ Penyimpanan Data
- [ ] Token autentikasi tersimpan di `flutter_secure_storage`, BUKAN `SharedPreferences`
- [ ] Tidak ada data sensitif yang dicetak lewat `print()` atau `debugPrint()`
- [ ] Database lokal dienkripsi jika menyimpan data pribadi pengguna
- [ ] Cache tidak menyimpan data sensitif tanpa enkripsi

### ■ Komunikasi Jaringan
- [ ] Semua base URL menggunakan `https://` (tidak ada `http://`)
- [ ] `android:usesCleartextTraffic="false"` sudah dikonfigurasi di AndroidManifest.xml
- [ ] Certificate pinning diimplementasikan untuk endpoint login/transaksi
- [ ] API key tidak ditulis langsung (hardcoded) di kode sumber atau file `.env` yang di-commit

### ■ Autentikasi & Token
- [ ] JWT memiliki field `exp` dengan durasi wajar (15–60 menit untuk access token)
- [ ] Refresh token rotation diimplementasikan
- [ ] Logout menghapus token dari device DAN menginvalidasi di server
- [ ] Interceptor Dio digunakan untuk menyertakan token otomatis di setiap request

### ■ Validasi Input
- [ ] Semua form input divalidasi sebelum dikirim ke API (whitelist validation)
- [ ] Pesan error dari server tidak ditampilkan mentah ke pengguna
- [ ] Tidak ada SQL/command injection vector di query lokal

### ■ Build & Rilis
- [ ] `flutter build apk --obfuscate --split-debug-info=./debug-info` dijalankan saat rilis
- [ ] Folder `debug-info/` masuk `.gitignore`
- [ ] `flutter pub outdated` dijalankan dan dependency kritis sudah diperbarui
- [ ] Permission di `AndroidManifest.xml` dan `Info.plist` sudah diminimalkan

---

## Referensi
- [OWASP Mobile Top 10 (2024)](https://owasp.org/www-project-mobile-top-10/)
- [OWASP MASTG](https://mas.owasp.org/MASTG/)
- [flutter_secure_storage](https://pub.dev/packages/flutter_secure_storage)
- [Gojek Tech — How to Secure a SuperApp](https://blog.gojek.io/how-to-secure-a-superapp/)
- [Zimperium 2026 Banking Heist Report](https://zimperium.com/resources/new-zimperium-report-finds-banking-malware-expands-global-reach-targeting-1200-financial-apps)
