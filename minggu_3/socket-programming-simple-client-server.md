# Pemrograman Socket Sederhana menggunakan C

    Nama		: Rizal Maulana
    NRP		: 3122600004
    Kelas		: 2 D4 Teknik Informatika A
    Mata Kuliah	: Konsep Jaringan
    Dosen Pengampu	: Dr. Ferry Astika Saputra ST, M.Sc

### Membuat socket untuk sisi server

```c
#include <stdio.h>
#include <stdlib.h>

#include <netdb.h>
#include <netinet/in.h>

#include <string.h>
#include <unistd.h>
#include <stdbool.h>
#include <time.h>


struct sockaddr_in *init_sockaddr_in(uint16_t port_number)
{
    struct sockaddr_in *socket_address = malloc(sizeof(struct sockaddr_in));
    memset(socket_address, 0, sizeof(*socket_address));
    socket_address->sin_family = AF_INET;
    socket_address->sin_addr.s_addr = htonl(INADDR_ANY);
    socket_address->sin_port = htons(port_number);
    return socket_address;
}

char *process_operation(char *input)
{
    size_t n = strlen(input) * sizeof(char);
    char *output = malloc(n);
    memcpy(output, input, n);
    return output;
}

int main(int argc, char *argv[])
{

    const uint16_t port_number = 5001;
    int server_fd = socket(AF_INET, SOCK_STREAM, 0);

    struct sockaddr_in *server_sockaddr = init_sockaddr_in(port_number);
    struct sockaddr_in *client_sockaddr = malloc(sizeof(struct sockaddr_in));
    socklen_t server_socklen = sizeof(*server_sockaddr);
    socklen_t client_socklen = sizeof(*client_sockaddr);

    if (bind(server_fd, (const struct sockaddr *)server_sockaddr, server_socklen) < 0)
    {
        printf("Error! Bind has failed\n");
        exit(0);
    }
    if (listen(server_fd, 3) < 0)
    {
        printf("Error! Can't listen\n");
        exit(0);
    }

    const size_t buffer_len = 256;
    char *buffer = malloc(buffer_len * sizeof(char));
    char *response = NULL;
    time_t last_operation;
    pid_t pid = -1;
    // __pid_t pid = -1;

    while (1)
    {
        int client_fd = accept(server_fd, (struct sockaddr *)&client_sockaddr, &client_socklen);

        pid = fork();

        if (pid == 0)
        {
            close(server_fd);

            if (client_fd == -1)
            {
                exit(0);
            }

            printf("Connection with `%d` has been established and delegated to the process %d.\nWaiting for a query...\n", client_fd, getpid());

            last_operation = clock();

            while (1)
            {
                read(client_fd, buffer, buffer_len);

                if (buffer == "close")
                {
                    printf("Process %d: ", getpid());
                    close(client_fd);
                    printf("Closing session with `%d`. Bye!\n", client_fd);
                    break;
                }

                if (strlen(buffer) == 0)
                {
                    clock_t d = clock() - last_operation;
                    double dif = 1.0 * d / CLOCKS_PER_SEC;

                    if (dif > 5.0)
                    {
                        printf("Process %d: ", getpid());
                        close(client_fd);
                        printf("Connection timed out after %.3lf seconds. ", dif);
                        printf("Closing session with `%d`. Bye!\n", client_fd);
                        break;
                    }

                    continue;
                }

                printf("Process %d: ", getpid());
                printf("Received `%s`. Processing... ", buffer);

                free(response);
                response = process_operation(buffer);
                bzero(buffer, buffer_len * sizeof(char));

                send(client_fd, response, strlen(response), 0);
                printf("Responded with `%s`. Waiting for a new query...\n", response);

                last_operation = clock();
            }
            exit(0);
        }
        else
        {
            close(client_fd);
        }
    }
}
```

Program diatas adalah sebuah program socket sederhana yang mengimplementasikan layanan server berbasis socket menggunakan bahasa pemrograman C. Mari kita lakukan analisis program ini langkah demi langkah:

1. **Include Header**: Program dimulai dengan beberapa pernyataan `#include` untuk mengimpor pustaka yang diperlukan.

2. **`init_sockaddr_in` Function**: Ini adalah fungsi yang digunakan untuk menginisialisasi struktur `sockaddr_in`, yang digunakan untuk menentukan alamat dan port yang akan digunakan oleh server.

3. **`process_operation` Function**: Fungsi ini digunakan untuk memproses operasi yang diterima dari klien. Pada dasarnya, ini hanya mengalokasikan memori untuk string input, menyalin input ke dalamnya, dan mengembalikan string tersebut.

4. **`main` Function**: Ini adalah fungsi utama dari program.

   - Program pertama-tama membuat socket menggunakan fungsi `socket`, yang akan digunakan untuk menerima koneksi dari klien.

   - Kemudian, program menginisialisasi alamat server menggunakan fungsi `init_sockaddr_in`.

   - Setelah itu, program mencoba melakukan binding socket server ke alamat yang telah diinisialisasi. Jika binding gagal, program keluar.

   - Program kemudian memanggil fungsi `listen` untuk memulai mendengarkan koneksi masuk. Jika ini juga gagal, program keluar.

   - Selanjutnya, program memasuki loop utama yang akan menerima koneksi dari klien. Setiap koneksi dari klien akan di-handle oleh proses anak (child process).

   - Dalam proses anak, program menerima koneksi dari klien dan mulai menerima pesan dari klien menggunakan `read`.

   - Program memeriksa pesan yang diterima dan merespons sesuai. Jika pesan adalah "close", proses anak akan menutup koneksi dan keluar. Jika pesan adalah string kosong, program memeriksa apakah sudah melewati batas waktu tertentu dan menutup koneksi jika ya. Jika pesan adalah operasi lain, program memproses operasi tersebut dan mengirimkan responsnya ke klien.

   - Proses anak terus berjalan dalam loop hingga pesan "close" diterima atau batas waktu tercapai.

   - Proses anak kemudian akan keluar.

   - Proses induk (parent process) menutup koneksi dengan klien (jika belum ditutup oleh proses anak) dan kemudian kembali ke awal loop untuk menerima koneksi dari klien berikutnya.

Program ini menerapkan konsep sederhana untuk menerima dan memproses pesan dari klien menggunakan socket. Setiap koneksi dari klien diproses oleh proses anak yang berjalan dalam proses terpisah, sehingga server dapat menerima dan menghandle banyak koneksi secara bersamaan.

Namun, ada beberapa perbaikan dan penyesuaian yang perlu dipertimbangkan, tergantung pada kebutuhan Anda dan situasi penggunaan yang lebih kompleks, seperti mengelola penanganan kesalahan lebih baik atau meningkatkan keamanan. Selain itu, perlu diingat bahwa program ini hanya bersifat demonstratif dan mungkin perlu dikembangkan lebih lanjut untuk keperluan produksi yang lebih serius.

Program di atas tidak melakukan penanganan koneksi setengah tertutup (half-closed) secara eksplisit. Koneksi dianggap tertutup secara penuh (full-closed) saat close(client_fd) dipanggil dalam loop yang berjalan di dalam proses anak (child process). Ini mengakibatkan koneksi client-server ditutup sepenuhnya saat suatu kondisi terpenuhi, seperti ketika pesan "close" diterima atau ketika koneksi telah berlangsung melebihi batas waktu tertentu (5 detik dalam contoh ini).

### Membuat socket untuk sisi client

```c
#include <stdio.h>
#include <stdlib.h>

#include <netdb.h>
#include <netinet/in.h>

#include <string.h>

#include <unistd.h>
int main(int argc, char *argv[])
{
    int sockfd, portno, n;
    struct sockaddr_in serv_addr;

    struct hostent *server;

    char buffer[256];
    portno = 5001;

    // create socket and get file descriptor
    sockfd = socket(AF_INET, SOCK_STREAM, 0);

    server = gethostbyname("127.0.0.1");

    if (server == NULL)
    {
        fprintf(stderr, "ERROR, no such host\n");
        exit(0);
    }

    bzero((char *)&serv_addr, sizeof(serv_addr));
    serv_addr.sin_family = AF_INET;
    bcopy((char *)server->h_addr, (char *)&serv_addr.sin_addr.s_addr, server->h_length);
    serv_addr.sin_port = htons(portno);

    // connect to server with server address which is set above (serv_addr)

    if (connect(sockfd, (struct sockaddr *)&serv_addr, sizeof(serv_addr)) < 0)
    {
        perror("ERROR while connecting");
        exit(1);
    }

    // inside this while loop, implement communicating with read/write or send/recv function
    while (1)
    {
        printf("What do you want to say? ");
        bzero(buffer, 256);
        scanf("%s", buffer);

        n = write(sockfd, buffer, strlen(buffer));

        if (n < 0)
        {
            perror("ERROR while writing to socket");
            exit(1);
        }

        bzero(buffer, 256);
        n = read(sockfd, buffer, 255);

        if (n < 0)
        {
            perror("ERROR while reading from socket");
            exit(1);
        }
        printf("server replied: %s \n", buffer);

        // escape this loop, if the server sends message "quit"

        if (!bcmp(buffer, "quit", 4))
            break;
    }
    return 0;
}

```


Program diatas adalah program klien sederhana yang berkomunikasi dengan server menggunakan soket (socket) TCP/IP. Program ini digunakan untuk mengirim pesan ke server dan menerima respons dari server.

Berikut adalah analisis singkat dari program ini:

1. **Include Header**: Program dimulai dengan beberapa pernyataan `#include` untuk mengimpor pustaka yang diperlukan.

2. **Deklarasi Variabel**: Program mendeklarasikan beberapa variabel yang akan digunakan, termasuk `sockfd` (file descriptor soket), `portno` (nomor port server), dan `serv_addr` (struktur alamat server).

3. **Membuat Soket**: Program menggunakan fungsi `socket` untuk membuat soket. Hasil dari pemanggilan ini adalah `sockfd`, yang merupakan file descriptor yang digunakan untuk mengidentifikasi soket.

4. **Resolusi Alamat Server**: Program menggunakan fungsi `gethostbyname` untuk mengonversi alamat IP numerik "127.0.0.1" menjadi informasi alamat server yang dapat digunakan oleh soket. Hasilnya disimpan dalam variabel `server`.

5. **Inisialisasi Struktur Alamat Server**: Program mengisi struktur `serv_addr` dengan informasi alamat server yang telah diperoleh dari langkah sebelumnya, termasuk alamat IP dan nomor port yang telah ditentukan.

6. **Koneksi ke Server**: Program menggunakan fungsi `connect` untuk terhubung ke server dengan alamat yang telah diinisialisasi. Jika koneksi berhasil, program akan melanjutkan.

7. **Komunikasi dengan Server**: Program memasuki loop yang memungkinkan pengguna untuk memasukkan pesan yang akan dikirim ke server. Pesan yang dimasukkan oleh pengguna disimpan dalam buffer `buffer`, kemudian dikirim ke server menggunakan `write`. Program kemudian membaca respons dari server menggunakan `read` dan menampilkannya di layar.

8. **Pengecekan Pesan "quit"**: Program memeriksa apakah respons dari server adalah pesan "quit". Jika ya, program akan keluar dari loop dan menyelesaikan eksekusi.

Program ini adalah contoh sederhana dari klien soket yang berkomunikasi dengan server menggunakan protokol TCP/IP. Ini dapat digunakan sebagai dasar untuk mengembangkan aplikasi klien yang lebih kompleks. Sebagai catatan, dalam pengembangan yang lebih lanjut, Anda mungkin ingin menangani kesalahan dengan lebih baik dan memberikan lebih banyak fitur kepada pengguna, seperti mengelola koneksi, menggabungkan protokol komunikasi yang lebih canggih, atau menambahkan enkripsi komunikasi.

## Percobaan

Dalam percobaan ini saya mencoba untuk mengirim pesan string 'a' dengan panjang 4 dan 5. Pesan tersebut diterima server lalu dikirimkan lagi ke client dengan sukses.

<img src="./asset/socket.png">

## Weireshark Analisis

Diabawah ini adalah perncoba mengirim pesan sebanyak 5000 karakter dari client ke server.

<img src="./asset/terminaluntilN.png">

<img src="./asset/serverUntilN.png">

Satu request dalam dua segmen TCP terjadi karena data yang ingin dikirimkan oleh pengirim (host sumber) melebihi ukuran maksimum yang dapat diakomodasi dalam satu segmen TCP atau Maximum Segment Size (MSS). Segmen TCP adalah unit data dalam protokol TCP, dan ukurannya terbatas oleh beberapa faktor, termasuk Maximum Segment Size yang ditentukan selama penegosiasian koneksi TCP dan ukuran jendela (window size) yang tersedia di kedua ujung koneksi.

Berikut adalah beberapa alasan mengapa request dapat dibagi menjadi dua segmen TCP:

1. **MSS Terbatas:** Maximum Segment Size (MSS) adalah ukuran maksimum data yang dapat dikirim dalam satu segmen TCP. Nilai MSS ini dapat bervariasi tergantung pada implementasi dan konfigurasi TCP. Jika ukuran data yang ingin dikirim melebihi nilai MSS, maka data harus dibagi menjadi beberapa segmen yang lebih kecil.
   
2. **Penggunaan PSH:** PSH (Push) adalah salah satu flag dalam header TCP yang mengindikasikan bahwa data perlu segera disampaikan ke aplikasi penerima. Jika aplikasi pengirim menetapkan flag PSH, maka segmen akan dikirim secepat mungkin. Ini bisa menyebabkan pengiriman lebih cepat dari segmen pertama yang berisi data yang telah di-push, dan segmen kedua untuk data tambahan.
   
3. **Optimasi dan Pengiriman Efisien:** Terkadang, pembagian data menjadi segmen yang lebih kecil dapat memungkinkan pengiriman yang lebih efisien. Segmen yang lebih kecil dapat meminimalkan overhead dalam jaringan dan memungkinkan pengiriman data secepat mungkin jika ada kebutuhan mendesak untuk menerima data oleh penerima.
   
4. **Ukuran Jendela (Window Size):** Ukuran jendela (window size) TCP diatur oleh kedua ujung koneksi. Jika ukuran jendela kecil, maka penerima akan memberi tahu pengirim untuk mengurangi laju pengiriman data. Dalam situasi ini, pengirim dapat membagi data menjadi segmen yang lebih kecil agar sesuai dengan ukuran jendela yang tersedia.

Dalam kasus ini, request TCP dibagi menjadi dua segmen karena beberapa faktor di atas yang mengharuskan pembagian data menjadi lebih kecil agar sesuai dengan batasan-batasan yang ada dalam protokol TCP dan konfigurasi jaringan.