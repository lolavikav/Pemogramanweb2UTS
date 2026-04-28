# UTS Pemrograman Web2 -SQL Injection Demo

## Tentang Project

Project ini adalah simulasi sederhana untuk memahami salah satu celah keamanan paling umum di web, yaitu SQL Injection.

Di sini saya mencoba:

- Membuat sistem login sederhana
- Menguji apakah sistem bisa ditembus
- Memperbaiki celah keamanan tersebut

## Contoh Serangan

Input yang digunakan saat pengujian:

```
Username: lola
Password: ' OR '1'='1
```
Dengan input ini, sistem yang tidak aman bisa menganggap login berhasil walaupun password salah.

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

## Hasil pengecekan plagiasi (maksimal 30%)
<img width="740" height="671" alt="image" src="https://github.com/user-attachments/assets/7d851d2f-74a1-4793-ab9a-d0788599e5ca" />

LINK NYA:
https://submitin.id/status?order=SC-66005C76 


