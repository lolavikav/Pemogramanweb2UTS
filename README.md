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
