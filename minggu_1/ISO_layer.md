## Apa itu OSI Layer

Setiap komputer dalam jaringan memiliki cara berkomunikasinya masing-masing. Komputer bermerek A memiliki bahasa sendiri, dan hanya bisa berkomunikasi dengan perangkat lain yang bermerek sama. Hal tersebut juga terjadi pada sistem jaringan. Di mana pertukaran informasi antar jaringan tidak bisa terjalin dengan baik. Sementara tentu saja proses komunikasi dibutuhkan tidak hanya oleh komputer dalam satu sistem jaringan tertentu.

Maka, dibutuhkan standar khusus untuk memungkinkan komunikasi dapat terjalin secara menyeluruh. Oleh karena itulah, kemudian ISO (International Standart Organization) menetapkan standar OSI Layer tentang protokol komunikasi untuk segala jenis sistem jaringan.

Dari sini dapat disimpulkan bahwa OSI Layer adalah sebuah konsep yang memungkinkan pertukaran informasi terjadi antara berbagai jenis sistem komunikasi komputer, dengan menggunakan protokol standar, yaitu TCP/IP.

Protokol sendiri merupakan format aturan tentang proses pertukaran informasi antarkomputer menggunakan TCP (Transmission Control Protocol) dan IP (Internet Protocol). Sementara, IP adalah sistem alamat dalam jaringan internet yang dihubungkan oleh TCP.

## Fungsi OSI Layer

![Gambar Memotret](https://i.postimg.cc/KjcXwskQ/cover.jpg)

Pengembangan konsep OSI Layer sebenarnya ditujukan agar produsen komputer serta pengembang jaringan dan perangkat lunak dapat membuat produk yang bisa saling terhubung tanpa memaksa pengguna melakukan usaha lebih.

Dalam perjalanannya, para produsen komputer dan pengembang jaringan internet tidak menerapkan protokol model OSI Layer secara baku. Pasalnya tidak semua proses komunikasi memerlukan prosedur OSI Layer karena dapat menggunakan protokol yang lebih sederhana.

Namun, konsep OSI Layer tidak serta merta ditinggalkan begitu saja. Model prosedur ini masih banyak digunakan, terutama dalam melacak permasalahan yang mengakibatkan gagalnya fungsi jaringan. Sehingga, kemudian dapat diatasi dan komunikasi berjalan normal kembali.

OSI Layer bekerja melewati tujuh lapisan prosedur yang berurutan. Ketika seseorang tidak bisa mengakses internet dengan laptopnya, berarti ada masalah yang mungkin terjadi pada salah satu lapisan prosedur tersebut.

Konsep OSI Layer memudahkan proses pencarian titik awal permasalahan, sehingga memangkas waktu yang diperlukan untuk melacak problem jaringan. Dengan begitu, usaha untuk mengatasi masalah jaringan pun berjalan lebih mudah dan singkat.

## 7 OSI Layer dan Penjelasannya

![Gambar Memotret](https://i0.wp.com/salamadian.com/wp-content/uploads/2021/03/7-tingkatan-osi-layer.jpg?w=700&ssl=1)

Standar OSI Layer bekerja dalam prosedur yang sistematis. Konsep ini membagi alur sistem komunikasi secara runtut ke dalam tujuh lapisan abstrak (layer) dengan peranannya masing-masing. Berikut penjelasan mengenai tujuh lapisan dalam konsep OSI Layer.

1. Application
Tahapan ini berhubungan langsung dengan pengguna. Application Layer merupakan prosedur penyambungan komunikasi dari perangkat. Artinya, Application Layer adalah penghubung antara perangkat dan sistem komunikasi.
Contohnya saat mengirim surel. Program e-mail, seperti Gmail, akan memulai komunikasi dengan jaringan sebelum pesan bisa dikirim. Di sinilah Application Layer berlangsung melibatkan protokol HTTP, SMTP, FTP, dan telnet.

2. Presentation
Presentation Layer bertanggung jawab untuk mempersiapkan data agar bisa digunakan dengan program tertentu. Atau dengan kata lain, mempresentasikan data agar program tersebut dapat menyerap, mengakses, dan menggunakannya.
Presentation Layer berperan sebagai penerjemah bahasa komunikasi yang berbeda antara dua perangkat komputer. Melakukan enkripsi data dari perangkat sumber, lalu men-dekripsi-nya pada perangkat penerima.

3. Session
Durasi waktu yang diperlukan untuk berkomunikasi disebut Session atau sesi. Lapisan ini bertanggung jawab untuk membuka jaringan dalam durasi waktu yang cukup agar pertukaran data berjalan dengan baik.
Session Layer mengirimkan data melalui pos-pos. Contohnya, untuk mengirim 100 data, Session Layer bisa mengatur penempatan pos setiap 10. Jika setelah mencapai 50 tiba-tiba jaringan putus, maka pengiriman data bisa diulangi dari pos terakhir.

4. Transport
Transport Layer berperan sebagai penanggung jawab kiriman pesan antara dua perangkat. Mengambil data dari layer sebelumnya dan meneruskannya ke lapisan berikutnya, sekaligus memastikan bahwa data tersampaikan dengan baik.
Lapisan ini juga bertanggung jawab mengendalikan alur komunikasi antara dua perangkat yang kecepatan internetnya berbeda agar dapat saling mengoptimalkan. Juga, memastikan data tersampaikan secara lengkap dan meminta kiriman ulang jika gagal.

5. Network
Network berarti jaringan. Dalam hal ini, Network Layer bertugas untuk memberikan jalur, sebagai fasilitas bagi proses pertukaran informasi antara dua jaringan berbeda. Network Layer tidak diperlukan pada komunikasi perangkat di jaringan yang sama.
Network Layer mencari jalur komunikasi terbaik antarjaringan (routing). Lapisan ini menyalurkan data kiriman dari perangkat sumber dengan cara membaginya dalam paket-paket kecil. Lalu menyusunnya kembali ketika telah sampai pada perangkat penerima.

6. Data Link
Jika Network Layer adalah penyalur informasi antarjaringan, Data Link merupakan pemberi jalur komunikasi di dalam jaringan yang sama. Tugas-tugasnya hampir sama dengan Network Layer dan Transport Layer, hanya saja internal dalam satu jaringan.

7. Physical
Lapisan paling dasar dari ketujuh OSI Layer. Bertanggung jawab mentransmisikan data dalam bentuk bit stream. Physical Layer mencakup segala peranti pertukaran informasi yang dimiliki oleh dua perangkat yang melakukannya, termasuk  kabel dan tombol-tombol.
Bit stream bisa dikatakan sebagai data digital. Bentuknya tak kasat mata dan berurutan melalui alur tertentu yang bisa ditransmisikan melalui media fisik. Contoh data digital, seperti tegangan listrik, frekuensi radio, frekuensi internet, cahaya, dan lain-lain.
E-mail yang Anda kirimkan bergerak melalui ketujuh lapisan OSI Layer di atas. Proses yang cukup panjang, bukan? Sebelumnya mungkin Anda tak pernah membayangkan bagaimana proses itu berjalan.

## Cara Kerja OSI Layer

![Gambar Memotret](https://i0.wp.com/salamadian.com/wp-content/uploads/2021/03/cara-kerja-osi-layer.jpg?w=700&ssl=1)

Prosedur OSI Layer berlaku, baik di perangkat pengirim maupun perangkat penerima. Artinya, data dari perangkat pengirim akan melewati layer 1 sampai 7. Sebelum sampai ke perangkat penerima, data tersebut masih harus melewati tujuh layer yang sama, tetapi urutannya terbalik.

Suatu ketika, Anda menggunakan aplikasi pengolah pesan untuk mengirim surel kepada adik. Selesai mengetik, Anda menekan tombol “kirim”. Lalu aplikasi pengolah pesan akan memanggil Application Layer untuk memilih protokol (dalam hal ini SMTP) untuk menyampaikan data.

Presentation Layer terlebih dahulu memampatkan data dan meneruskannya ke Session Layer untuk  memulai proses pengiriman. Kiriman diproses oleh Transportation Layer dalam bentuk segmen, kemudian dipecah lagi dalam potongan-potongan kecil pada Network Layer.

Network Layer menyampaikan adanya potongan-potongan data ke Data Link Layer. Di Data Link Layer ini, data tersebut masih akan dipecah-pecah kembali agar bisa dikirimkan melalui perangkat keras pada Physical Layer.

Physical Layer mengonversi data ke dalam bentuk bit stream lalu diteruskan melalui media fisik, seperti modem, kabel, fiber optik, atau perangkat konektivitas jaringan lainnya. Perangkat inilah yang pertama kali menerima paket bit stream data di alamat e-mail adik Anda.

E-mail kiriman Anda masih harus melewati tujuh OSI Layer lagi, sebelum adik Anda dapat membacanya seperti biasa. Namun kali ini prosesnya berlangsung secara terbalik. Pertama, Physical Layer akan memproses bitstream menjadi data yang bisa disalurkan oleh Data Link.

Data Link kemudian akan menyusun kembali potongan-potongan data ke dalam paket untuk Network Layer. Network Layer memprosesnya dalam bentuk segmen untuk disampaikan ke Transportation Layer, yang kemudian akan menggabungkan data sehingga utuh kembali.

Data utuh tersebut masih mentah dan akan mengalir melewati Session Layer di jaringan komputer adik Anda. Session Layer meneruskannya ke Presentation Layer yang juga membersihkannya dari kompresi-kompresi.

Selanjutnya, Presentation Layer menyampaikannya ke Application Layer yang kemudian akan memproses data mentah dalam bentuk yang bisa dibaca oleh program e-mail di komputer adik Anda. Adik Anda pun menerima surel tersebut sesuai dengan bentuk yang Anda kirimkan.
