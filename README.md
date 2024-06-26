Tutorial 6

Shanahan Danualif Erwin - 2206817420- Adpro B

__1. Commit 1__

What does handle_connection do?

handle_connection berfungsi untuk memproses TCPstream yang masuk. Pertama ada
BufReader yang membungkus TCPstream yang diberikan dengan buffer. Kemudian dilakukan iterasi
melalui setiap baris dari BufReader hingga menemukan baris kosong. Nantinya baris-baris ini dikumpulkan
ke dalam sebuah Vector yang mewakili permintaan HTTP. Terakhir, fungsi akan mencetak permintaan HTTP ke konsol





__2. Commit 2__

![Commit 2 screen capture](assets/images/commit2.png)

What does the additional line of code in handle_connection do?

- Pertama, kode akan memberikan status respons HTTP, kode 200 disini berarti "OK"
- Kedua, baris akan membaca file yang bernama hello.html menggunakan fs::read_to_string()
- Ketiga, menghitung panjang baris dari konten yang akan dikirim dalam tubuh respons HTTP
- Keempat, memformat respons HTTP yang mencakup baris status, header panjang konten, dan sebagainya
- Terakhir, respons HTTP akan ditulis kepada TCPstream dengan write_all

__Commit 3__

![Commit 3 picture](assets/images/commit3.png)

Saya menggunakan if-else conditional yang akan membaca request_line. Kalau request_line
berisi "GET / HTTP/1.1" maka kode akan memberikan file hello.html. Sebaliknya, jika
tidak memberikan request sesuai makan akan menampilkan file bad.html. Refactoring kode dilakukan agar
kode menjadi lebih mudah dibaca dan lebih mudah dimodifikasi di masa depan. Hal ini akan meningkatkan maintainability
dari kode ini

__Commit 4__

Saat mengakses endpoint /sleep, aplikasi membutuhkan waktu yang lama (10 detik) untuk memprosesnya. Ketika kita mencoba
mengakses endpoint lain pada tab browser baru, aplikasi harus menyelesaikan proses loading di endpoint /sleep dulu.
Hal ini membuat endpoint lain harus menunggu /sleep selesai loading dulu agar bisa diproses. Padahal endpoint selain /sleep
dapat diproses oleh mesin secara cepat. Secara keseluruhan, ini membuat masalah performa karena 
saat mengakses endpoint /sleep yang membutuhkan banyak waktu akan memperlambat performa aplikasi.

__Commit 5__

Thread pool adalah kumpulan thread yang di-spawned dan akan menunggu untuk meng-handle sebah task.
Program akan memberikan task ke salah satu thread pada thread pool ketika mendapatkan task baru.
Thread lain yang belum mendapatkan task dalam thread pool tetap tersedia untuk menyelesaikan task baru lain yang masuk.
Jika sebuah thread menyelesaikan task-nya, dia kembali menjadi thread idle yang dapat dipakai kembali.
Thread pool membuat server dapat memproses secara bersamaan sehingga meningkatkan throughput aplikasi

__Commit Bonus Reflection notes__

Perbedaan new dan build function adalah saat mereka mengurus kasus saat size Threadpool 0.
Function new akan menghentikan program jika size Thread pool 0 dan memberikan error message. Sedangkan,
function build mengembalikan Err(PoolCreationError) dengan message yang menginfokan bahwa ukuran Thread pool
masih 0. Jadi perbedaan keduanya terletak pada cara menangani situasi dimana size Thread pool adalah 0. Fungsi build 
yang menggunakan Err(PoolCreationError) memberi opsi tambahan bagi programmer, seperti membuat predefined error message
kemudian menghentikan program

