## Tutorial 10
### Broadcast Chat


![Screenshot 1](images/Screenshot_1.png)
![Screenshot 2](images/Screenshot_2.png)
![Screenshot 3](images/Screenshot_3.png)
![Screenshot 4](images/Screenshot_4.png)

Secara garis besar, program _broadcast chat_ ini bekerja dengan mengirim, menerima, dan menyiarkan pesan secara asinkronus dan sisi server dan klien. Kedua sisi dijalankan menggunakan `cargo run --bin server` dan `cargo run --bin client`, di mana server dan klien akan terhubung pada _localhost_ port 2000. Tiap klien yang terhubung ke _channel_ tersebut akan terdeteksi dan ditampilkan pada server. Klien bisa menerima input pesan yang dimasukkan _user_ yang kemudian akan dikirim ke server melalui WebSocket (`ws_stream.send()`). Secara bersamaan, klien juga bisa menerima pesan yang datang dari server melalui WebSocket (`ws_stream.next()`) dan mencetaknya di konsol. Sementara itu, server menyediakan _channel_ dengan kapasitas 16 _message_ yang memungkinkan beberapa klien untuk menerima pesan secara _concurrent_. Secara asinkronus, server berfungsi untuk menangani pesan yang dikirim oleh klien dengan mencetaknya di konsol dan menyiarkan pesan tersebut. Selain itu, server juga menerima pesan yang disiarkan melalui _broadcast receiver_ (`bcast_rx`) dan mengirimnya ke klien melalui WebSocket (`ws_stream.send()`).