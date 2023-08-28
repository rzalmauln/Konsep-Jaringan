## Kenapa 1 port FTP bisa memakai UDP atau TCP

Protokol FTP (File Transfer Protocol) secara tradisional menggunakan TCP (Transmission Control Protocol) sebagai protokol transportnya. Namun, seiring dengan perkembangan teknologi dan kebutuhan yang beragam, ada beberapa implementasi yang memungkinkan penggunaan protokol FTP melalui UDP (User Datagram Protocol). Tetapi perlu dipahami bahwa penggunaan UDP untuk FTP tidak umum dan biasanya lebih rumit.

Alasan mengapa protokol FTP dapat diimplementasikan menggunakan baik UDP maupun TCP adalah karena perbedaan sifat masing-masing protokol:

1. **TCP (Transmission Control Protocol):**
   - TCP adalah protokol berorientasi koneksi yang menjamin pengiriman paket dalam urutan yang benar dan tanpa kehilangan data.
   - Protokol FTP menggunakan TCP karena karakteristiknya yang andal dan menjamin pengiriman file yang akurat dan terjamin. FTP mengandalkan fitur ini karena pentingnya menjaga integritas file selama transfer.

2. **UDP (User Datagram Protocol):**
   - UDP adalah protokol tanpa koneksi yang lebih ringan dan cepat daripada TCP, tetapi tidak menjamin pengiriman paket dalam urutan yang benar dan dapat kehilangan paket.
   - Beberapa implementasi FTP menggunakan UDP untuk transfer data karena potensi kinerja yang lebih tinggi dan latensi yang lebih rendah. Namun, hal ini memerlukan manajemen tambahan untuk mengatasi masalah seperti kehilangan paket atau paket yang datang dalam urutan yang salah.

Penting untuk dicatat bahwa penggunaan UDP untuk protokol FTP lebih kompleks dan mungkin memerlukan pemecahan masalah yang lebih mendalam karena sifat tanpa koneksi dan kurangnya jaminan pengiriman data. Penggunaan protokol FTP dengan UDP mungkin lebih sesuai dalam kasus-kasus khusus di mana kinerja sangat penting, tetapi dalam banyak kasus, menggunakan TCP adalah pilihan yang lebih aman dan andal untuk mentransfer file melalui FTP.
