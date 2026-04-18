# 🎬 Script Presentasi Video — Project RumahNusantara
> *Durasi estimasi: 3–5 menit | Gaya: santai, natural, mengalir*

---

## 🎤 PEMBUKAAN

Halo semuanya! Perkenalkan, kali ini saya akan mempresentasikan project web yang saya buat menggunakan framework Laravel, dengan nama **RumahNusantara**.

Jadi, RumahNusantara ini adalah website yang saya desain sebagai platform budaya — semacam portal untuk komunitas pecinta budaya Indonesia. Di sini user bisa mendaftar akun, login, dan menjelajahi konten seputar warisan budaya Nusantara. Konsepnya cukup sederhana, tapi saya coba bangun dengan struktur kode yang rapi menggunakan pola arsitektur **MVC** — yaitu Model, View, dan Controller.

Nah, mari kita bahas satu per satu.

---

## 🏗️ PENJELASAN MVC

Jadi, konsep MVC itu intinya adalah cara kita memisahkan tanggung jawab dalam sebuah aplikasi web. Biar kode kita rapi dan nggak campur-campur.

**Pertama, ada Route** — ini yang ada di file `routes/web.php`. Fungsinya sebagai penghubung antara alamat URL yang diakses user, ke Controller yang tepat. Jadi kalau user buka alamat `/register`, Laravel langsung tahu harus memanggil fungsi mana. Seperti ini contohnya di project saya:

```
Route::get('/register', [AuthController::class, 'showRegister']);
Route::post('/register', [AuthController::class, 'register']);
```

Dua baris itu artinya: kalau user buka halaman register, tampilkan formnya. Dan kalau user submit form-nya, jalankan proses penyimpanannya.

**Lalu ada Controller** — ini otaknya aplikasi. Di project saya ada dua controller utama: `HomeController` dan `AuthController`. `HomeController` tugasnya simpel, yaitu hanya menampilkan halaman utama. Sedangkan `AuthController` itu lebih kompleks — dia yang ngurusin login, register, sampai logout. Termasuk validasi data inputan user juga ada di sini.

**Kemudian ada Model** — ini yang bertugas berkomunikasi dengan database. Di project saya ada model `User`, yang menyimpan data seperti nama, email, password, jenis kelamin, dan agama. Model ini yang jadi "jembatan" antara Controller dan tabel database.

**Dan yang terakhir adalah View** — ini tampilan yang user lihat langsung di browser. View saya dibuat dengan Blade, yaitu template engine bawaan Laravel. Semua halaman seperti `home.blade.php`, `login.blade.php`, dan `register.blade.php` menggunakan satu layout bersama di `layouts/app.blade.php` — jadi navbar dan footer cukup ditulis sekali, dipake di semua halaman.

---

## ✨ PENJELASAN FITUR

Oke, sekarang kita lihat fitur-fiturnya.

**Landing Page** — ini halaman pertama yang muncul saat user membuka website. Ada hero section dengan tulisan "Keindahan yang Melampaui Waktu", ada statistik seperti 15 tahun berdiri, 500+ koleksi budaya, dan 12 ribu lebih pengunjung. Ada juga section Tentang Kami, Layanan, sampai Call to Action yang mengajak user untuk daftar. Tampilannya dibuat elegan dan profesional.

**Halaman Login** — desainnya split dua kolom. Di kiri ada visual branding RumahNusantara dengan quote budaya, dan di kanan ada form login dengan input email dan password. Ada juga fitur "Ingat saya" menggunakan checkbox, jadi sesi user bisa tersimpan.

**Halaman Register** — nah ini yang paling lengkap. Formulirnya terdiri dari beberapa jenis input:
- **Input text** biasa untuk nama lengkap, email, dan password
- **Radio button** bergaya kartu untuk memilih jenis kelamin — jadi user tinggal klik pilihan Laki-laki atau Perempuan
- **Select box** untuk memilih agama — ada enam pilihan sesuai agama resmi di Indonesia
- Dan ada juga checkbox persetujuan syarat dan ketentuan sebelum bisa submit

Semua input ini divalidasi di sisi server lewat `AuthController` — jadi kalau ada yang kosong atau formatnya salah, muncul pesan error yang jelas.

Satu hal lagi yang penting: **website ini sudah responsive**. Berkat Bootstrap 5, tampilan otomatis menyesuaikan di layar HP, tablet, maupun desktop.

---

## 🎨 PENJELASAN DESAIN

Dari sisi desain, saya sengaja pilih konsep yang elegan dengan nuansa **earthy** atau warna-warna alam. Palet warnanya dominan krem, coklat, dan gold — yang saya definisikan sebagai CSS custom properties seperti `--cream`, `--brown`, dan `--gold`. Tujuannya biar ada konsistensi warna di seluruh halaman.

Untuk font, saya pakai dua jenis: **Cormorant Garamond** yang terasa klasik dan mewah untuk judul-judul besar, dan **Nunito** yang lebih bersih untuk teks paragraf. Kombinasi ini bikin kesan elegan tapi tetap mudah dibaca.

Teknisnya, saya menggunakan **Bootstrap 5** sebagai fondasi layout dan komponen dasarnya, lalu dikustomisasi lebih jauh lewat file `style.css` saya sendiri. Jadi ada banyak class custom seperti `btn-earthy-primary`, `form-control-custom`, atau `auth-visual` yang saya buat sendiri buat menyesuaikan desain dengan tema RumahNusantara.

---

## 🔄 PENJELASAN ALUR WEBSITE

Sekarang kita bahas alur penggunaannya secara keseluruhan.

Pertama, user membuka website dan langsung disambut oleh **Landing Page** yang informatif — mereka bisa baca tentang RumahNusantara, melihat layanan yang ada, dan ada tombol "Mulai Perjalanan" yang mengajak untuk daftar.

Lalu user klik tombol **Daftar** — mereka diarahkan ke halaman register, mengisi data diri lengkap, pilih jenis kelamin lewat radio button, pilih agama lewat select box, centang persetujuan, lalu submit. Kalau semua valid, akun langsung dibuat dan user otomatis masuk ke halaman utama.

Selanjutnya, kalau user sudah punya akun dan kembali lagi, mereka tinggal klik **Masuk**, isi email dan password, lalu sistem akan memverifikasi. Kalau cocok, mereka langsung masuk dan di navbar akan muncul nama mereka. Kalau mau keluar, tinggal klik **Logout** dan sesi pun berakhir dengan aman.

---

## 🎯 PENUTUP

Jadi, itulah project **RumahNusantara** yang saya buat menggunakan Laravel dengan pola MVC. Mulai dari Route sebagai penghubung, Controller sebagai logika, Model sebagai pengelola data, sampai View sebagai tampilan — semuanya bekerja bersama membentuk sebuah aplikasi web yang utuh dan terstruktur.

Harapan saya, project ini nggak cuma jadi tugas kuliah, tapi juga jadi latihan nyata dalam membangun aplikasi web yang bersih, rapi, dan bisa dikembangkan lebih lanjut ke depannya — misalnya dengan menambahkan fitur dashboard, manajemen konten, atau bahkan sistem pemesanan.

Terima kasih sudah menyimak presentasi ini. Semoga bermanfaat, dan kalau ada pertanyaan seputar project ini, saya siap menjawab. Sampai jumpa! 🙏

---
*© Script Presentasi RumahNusantara — siap rekam*
