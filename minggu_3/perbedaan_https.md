# Perbedaan versi versi HTTP

    Nama		: Rizal Maulana
    NRP		: 3122600004
    Kelas		: 2 D4 Teknik Informatika A
    Mata Kuliah	: Konsep Jaringan
    Dosen Pengampu	: Dr. Ferry Astika Saputra ST, M.Sc

![](asset/Comparison-of-HTTP-versions.jpg)

# HTTP 0.9:

Tidak ada header HTTP. Hanya ada perintah "GET" untuk mengambil dokumen HTML.

Tidak ada status kode HTTP.

Tidak ada dukungan untuk respons non-HTML seperti gambar atau file lainnya.

Tidak ada kemampuan untuk mengirimkan data tambahan dalam permintaan atau respons.

Sangat sederhana dan terbatas.

# HTTP 1.0:

Memperkenalkan header HTTP seperti "User-Agent" dan "Host".

Mendukung status kode HTTP seperti "200 OK" dan "404 Not Found".

Mendukung berbagai jenis dokumen dan sumber daya, seperti gambar, audio, dan teks.

Mendukung metode HTTP lainnya seperti POST, PUT, dan DELETE untuk mengirim data ke server.

Koneksi TCP ditutup setelah setiap permintaan/respons, yang dapat menjadi beban kinerja.

# HTTP 1.1:

Menggunakan koneksi persisten (Keep-Alive) secara default, sehingga mengurangi overhead koneksi.

Mendukung pipelining, yang memungkinkan klien mengirim beberapa permintaan tanpa menunggu respons pertama selesai.

Memperkenalkan kompresi header dan transfer chunked untuk mengurangi ukuran respons.

Mendukung host virtual, yang memungkinkan beberapa situs web berbagi alamat IP.

Maksimal 6 request dan response

# HTTP 2.0:

Menggunakan teknologi multiplexing, yang memungkinkan beberapa permintaan/respons berbagi satu koneksi TCP.

Menggunakan kompresi header dan data, mengurangi penggunaan bandwidth.

Mendukung server push, yang memungkinkan server mengirimkan sumber daya kepada klien tanpa permintaan sebelumnya.

Dirancang untuk meningkatkan kecepatan dan efisiensi.

# HTTP 3.0:

Menggantikan TCP dengan protokol QUIC, yang dirancang untuk mengurangi latensi dan meningkatkan keamanan.

Memperkenalkan multiplexing dan pemisahan antara data kontrol dan data aplikasi.

Dirancang untuk kinerja yang lebih baik di jaringan yang bermasalah dan koneksi seluler.

Menggunakan enkripsi TLS secara default.