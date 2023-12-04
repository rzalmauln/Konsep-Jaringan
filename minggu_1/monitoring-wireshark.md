## Monitoring Protocol HTTP, TELNET, DNS

    Nama		: Rizal Maulana
    NRP		: 3122600004
    Kelas		: 2 D4 Teknik Informatika A
    Mata Kuliah	: Konsep Jaringan
    Dosen Pengampu	: Dr. Ferry Astika Saputra ST, M.Sc

![gambar](./Screen%20Shot%202023-08-28%20at%2016.03.06.png)

Memantau protokol HTTP, Telnet, dan DNS menggunakan Wireshark melibatkan perekaman dan analisis paket jaringan yang melewati antarmuka jaringan Anda. Wireshark adalah alat analisis jaringan yang sangat kuat yang memungkinkan Anda untuk melihat detail paket jaringan dan menganalisis protokol yang digunakan. Berikut langkah-langkah umum untuk memantau protokol HTTP, Telnet, dan DNS menggunakan Wireshark:

1. **Unduh dan Instal Wireshark:**
   Jika Anda belum menginstal Wireshark, unduh dan instal versi yang sesuai untuk sistem operasi Anda dari situs resmi Wireshark (https://www.wireshark.org/).
2. **Mulai Perekaman:**
   - Buka Wireshark.
   - Pilih antarmuka jaringan yang ingin Anda monitor (misalnya, http.cap, telnet.cap atau dns.cap, bisa anda download di wireshark sample).
   - Klik tombol "Open a capture file" atau ikon mirip "file" untuk memulai perekaman paket.

3. **Filter Paket:**
   - Di bagian atas jendela Wireshark, Anda akan melihat sebuah kotak teks yang merupakan tempat Anda dapat memasukkan filter paket. Filter ini memungkinkan Anda untuk memilih jenis paket yang ingin Anda lihat.
   - Untuk HTTP, masukkan filter "http" untuk hanya menampilkan paket yang terkait dengan protokol HTTP.
   - Untuk Telnet, masukkan filter "telnet" untuk hanya menampilkan paket yang terkait dengan protokol Telnet.
   - Untuk DNS, masukkan filter "dns" untuk hanya menampilkan paket yang terkait dengan protokol DNS.

4. **Analisis Paket:**
   - Setelah perekaman dimulai dan filter diterapkan, Anda akan melihat daftar paket yang melewati antarmuka jaringan Anda.
   - Klik pada paket individual untuk melihat detailnya di bagian bawah jendela. Anda dapat melihat informasi seperti header protokol, payload, sumber, tujuan, TCP, dan sebagainya.

5. **Detail Protokol:**
   - Untuk menganalisis lebih lanjut, Anda dapat mengklik paket yang berkaitan dengan protokol tertentu (HTTP, Telnet, DNS) untuk melihat detail lebih lanjut tentang protokol tersebut.untuk protocol HTTP bisa klik kanan lalu klik follow lalu Stream HTTP, akan muncul detail request, respon client dan server. Wireshark akan mencoba untuk memecah dan menampilkan informasi protokol secara lebih terstruktur.

6. **Penyaringan Lebih Lanjut:**
   - Wireshark memiliki berbagai opsi penyaringan yang lebih kompleks. Anda dapat memperdalam pemahaman Anda tentang berbagai fitur ini dengan membaca dokumentasi Wireshark atau sumber daya online.

Ingatlah bahwa analisis jaringan dan penggunaan alat seperti Wireshark dapat memerlukan pemahaman yang baik tentang protokol dan jaringan. Selalu pastikan Anda memiliki izin yang sesuai untuk memantau jaringan, terutama jika Anda tidak mengelola jaringan Anda sendiri.