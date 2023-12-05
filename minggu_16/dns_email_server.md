    Nama		: Rizal Maulana
    NRP		: 3122600004
    Kelas		: 2 D4 Teknik Informatika A
    Mata Kuliah	: Konsep Jaringan
    Dosen Pengampu	: Dr. Ferry Astika Saputra ST, M.Sc

## Cara Kerja DNS (Domain Name System):

DNS (Domain Name System) adalah sistem yang mengonversi nama domain ke alamat IP numerik yang digunakan oleh komputer dalam jaringan. Tanpa DNS, kita harus mengingat alamat IP setiap situs web yang ingin kita kunjungi, yang tentu saja tidak efisien dan praktis. DNS berfungsi sebagai direktori telepon internet, menyediakan cara untuk mengaitkan nama domain yang mudah diingat dengan alamat IP yang sesungguhnya.

Proses kerja DNS melibatkan beberapa komponen, termasuk:

1. **Resolver**: Komputer atau server yang menginisiasi permintaan DNS. Resolver ini dapat berupa komponen perangkat keras atau perangkat lunak pada perangkat pengguna.

2. **Root DNS Server**: Server tingkat tertinggi dalam hierarki DNS. Root DNS Server memberikan informasi tentang lokasi authoritative DNS Server yang mengelola top-level domain (TLD), seperti .com, .org, .net, dll.

3. **TLD DNS Server**: Server yang mengelola top-level domain (TLD). Misalnya, .com, .org, .net, dll. TLD DNS Server memberikan informasi tentang lokasi authoritative DNS Server yang mengelola domain spesifik di bawah TLD tersebut.

4. **Authoritative DNS Server**: Server yang memiliki informasi lengkap tentang domain tertentu. Ketika resolver mencari alamat IP untuk suatu domain, server otoritatif memberikan jawaban yang akurat.

5. **Cache**: Sebagian besar DNS resolver menyimpan hasil pencarian (cache) untuk sementara waktu. Jika suatu domain telah dicari sebelumnya, resolver dapat menggunakan hasil cache daripada melakukan pencarian lagi.

Proses kerja DNS dimulai ketika pengguna memasukkan nama domain (misalnya, www.example.com) ke dalam browser. Resolver kemudian meminta Root DNS Server untuk informasi. Root DNS Server mengarahkan resolver ke TLD DNS Server yang bertanggung jawab untuk domain tersebut, dan seterusnya hingga resolver mendapatkan jawaban dari authoritative DNS Server yang benar.

## Cara Kerja Email Server:

Email Server adalah infrastruktur yang memungkinkan pengiriman, penerimaan, dan penyimpanan email. Proses pengiriman email melibatkan beberapa tahap, dan email server umumnya terdiri dari dua komponen utama: Mail Transfer Agent (MTA) dan Mail Delivery Agent (MDA).

1. **Mail Transfer Agent (MTA)**:

   - MTA bertanggung jawab untuk mengirim email dari server pengirim ke server penerima.
   - Proses ini melibatkan protokol seperti SMTP (Simple Mail Transfer Protocol) untuk pengiriman email.

2. **Mail Delivery Agent (MDA)**:

   - MDA menerima email dari MTA dan menyimpannya di kotak surat penerima.
   - Protokol seperti POP3 (Post Office Protocol) atau IMAP (Internet Message Access Protocol) digunakan untuk pengambilan email oleh pengguna.

3. **Domain Name System (DNS)**:

   - DNS juga berperan penting dalam pengiriman email. Mail servers menggunakan DNS untuk mencari alamat IP dari domain tujuan.

4. **Authentication Protocols**:

   - Protokol seperti SPF (Sender Policy Framework) dan DKIM (DomainKeys Identified Mail) digunakan untuk mengautentikasi email dan mencegah spam atau serangan phishing.

5. **Mailbox Storage**:
   - Email server menyimpan email di mailbox masing-masing pengguna, memungkinkan pengguna mengakses dan mengelola email mereka.

Proses pengiriman email melibatkan MTA yang mengirimkan email melalui internet, DNS yang memastikan pengiriman ke alamat yang benar, dan MDA yang menyimpan email di server penerima. Protokol tambahan dan keamanan juga diterapkan untuk melindungi integritas dan kerahasiaan email.

Keseluruhan, baik DNS maupun email server memainkan peran kritis dalam menyediakan layanan yang handal dan aman di internet, memfasilitasi komunikasi dan pertukaran informasi.