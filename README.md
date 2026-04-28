# UTS Pemrograman Web2 -SQL Injection Demo

## Tentang Project
Project ini dibuat untuk memenuhi tugas UTS Pemrograman Web.
Tujuan dari project ini adalah untuk memahami bagaimana SQL Injection bekerja serta bagaimana cara mencegahnya.

Dalam project ini, saya melakukan simulasi sederhana pada sistem login untuk melihat bagaimana celah keamanan bisa dimanfaatkan, dan bagaimana solusi yang lebih aman dapat diterapkan.

Di sini saya mencoba:

- Membuat sistem login sederhana
- Menguji apakah sistem bisa ditembus
- Memperbaiki celah keamanan tersebut

## Apa itu SQL Injection?

SQL Injection adalah teknik serangan yang dilakukan dengan cara menyisipkan kode SQL ke dalam input user.
Serangan ini biasanya terjadi pada form login atau input data lainnya.

Contoh input berbahaya:
```
Username: lola
Password: ' OR '1'='1
```

Jika sistem tidak aman, maka login bisa berhasil tanpa password yang benar.

## Cara Kerja 

Sistem login biasanya menggunakan query seperti ini:

```
SELECT * FROM users_lola 
WHERE username = '$user_lola' 
AND password = '$pass_lola';
```
Masalahnya, input dari user langsung dimasukkan ke query tanpa filter

## Hasil Percobaan
1. versi Tidak Aman
Login bisa ditembus
Password tidak perlu benar
Sistem rentan

2. Versi Aman
Menggunakan prepared statement:

```
$stmt = $conn->prepare("SELECT * FROM users_lola WHERE username=? AND password=?");
$stmt->bind_param("ss", $user_lola, $pass_lola);
$stmt->execute();
```

Hasil:

Serangan gagal
Data lebih aman

## Insight yang Didapat
- Jangan pernah langsung pakai input user ke query
- Validasi input itu penting
- Prepared statement wajib digunakan

Teknologi
- PHP
- MySQL
- XAMPP / Localhost

## Tujuan

Project ini dibuat untuk:

- Memenuhi tugas UTS
- Belajar keamanan web dasar
- Memahami cara kerja serangan SQL Injection

## Hasil Publikasi dan pengecekan plagiasi
https://medium.com/@lolavikav/sql-injection-cara-kerjanya-bahayanya-dan-pengalaman-mencoba-sendiri-a13d4f40fecc

Link Plagiasi:
https://submitin.id/status?order=SC-66005C76 


