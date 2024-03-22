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

__Commit 4__

__Commit 5__



