## Pembentukan koneksi dengan Three-Way Handshaking

    Nama		: Rizal Maulana
    NRP		: 3122600004
    Kelas		: 2 D4 Teknik Informatika A
    Mata Kuliah	: Konsep Jaringan
    Dosen Pengampu	: Dr. Ferry Astika Saputra ST, M.Sc

Three-Way Handshaking adalah proses yang terjadi saat dua perangkat (misalnya, komputer dan server) ingin memulai koneksi TCP (Transmission Control Protocol) satu sama lain dalam jaringan komputer. Tujuan dari Three-Way Handshaking adalah untuk memastikan bahwa kedua perangkat mengakui kesiapan mereka untuk memulai komunikasi, membangun parameter koneksi, dan memastikan sinkronisasi yang benar sebelum pertukaran data dimulai. Proses ini terdiri dari tiga langkah yang dilakukan dalam urutan tertentu:

1. **Langkah 1 - Permintaan Koneksi (SYN):**
   - Perangkat A (biasanya disebut sebagai pengirim) ingin memulai koneksi dengan Perangkat B (penerima).
   - Perangkat A mengirimkan paket dengan flag SYN (Synchronize) ke Perangkat B. Paket ini berisi nomor urutan acak (ISN - Initial Sequence Number) yang akan digunakan untuk mengidentifikasi dan mengurutkan data dalam koneksi.

2. **Langkah 2 - Persetujuan Koneksi (SYN-ACK):**
   - Perangkat B menerima paket SYN dari Perangkat A.
   - Perangkat B kemudian merespon dengan paket yang mengandung flag SYN dan ACK (Acknowledgment) ke Perangkat A. Dalam paket ini, Perangkat B juga menetapkan nomor urutan acak sendiri (BSN - B's Sequence Number) dan mengonfirmasi nomor urutan dari Perangkat A (A's Sequence Number + 1).

3. **Langkah 3 - Konfirmasi Koneksi (ACK):**
   - Perangkat A menerima paket SYN-ACK dari Perangkat B.
   - Perangkat A kemudian mengirimkan paket ACK ke Perangkat B untuk mengonfirmasi bahwa mereka menerima pesan SYN-ACK. Nomor urutan dalam paket ACK adalah BSN + 1.

Setelah langkah tiga selesai, koneksi TCP resmi dibangun antara Perangkat A dan Perangkat B, dan keduanya dapat mulai bertukar data. Proses Three-Way Handshaking ini mengatur parameter koneksi seperti nomor urutan awal dan ukuran jendela pengiriman, serta memastikan bahwa keduanya siap untuk berkomunikasi.

Three-Way Handshaking juga memiliki peran penting dalam mengatasi masalah pengiriman ganda atau tidak dalam urutan (out-of-order) paket. Dengan mengurutkan nomor urutan dan mengonfirmasi pesan, perangkat dapat dengan andal mengontrol aliran data dan memastikan bahwa paket-paket yang dikirimkan dan diterima sesuai urutan.

Namun, penting untuk diingat bahwa proses ini bisa melibatkan sedikit penundaan dalam memulai koneksi, terutama jika ada jarak fisik antara perangkat-perangkat tersebut. Namun, keandalan dan sinkronisasi yang dihasilkan dari Three-Way Handshaking adalah komponen penting dalam kehandalan koneksi TCP.