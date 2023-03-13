**PRAKTIKUM KEAMANAN JARINGAN “BROKEN ACCESS CONTROL”** 

![](Aspose.Words.c3c0bf6b-5dea-4c84-a4f2-ea84df35dfd1.001.png)

**Oleh  :** 

**Andre Septian Prayogo** 

**D4 LJ Teknik Informatika B 3122640033** 

**POLITEKNIK ELEKTRONIKA NEGERI SURABAYA TAHUN AJARAN** 

**2023** 

Broken Access Control atau disebut juga sebagai Broken Access Management adalah suatu  kerentanan  keamanan  yang  terjadi  pada  aplikasi  web  atau  sistem  yang  dapat memungkinkan pengguna tidak sah untuk mendapatkan akses yang tidak seharusnya pada sumber daya yang dilindungi atau fitur yang terbatas. 

Secara  umum,  Access  Control  adalah  proses  untuk  memastikan  bahwa  hanya pengguna yang diizinkan atau memiliki otoritas untuk melakukannya yang dapat mengakses sumber  daya  atau  fitur  tertentu.  Jika  mekanisme  Access  Control  tidak  dirancang  atau diimplementasikan  dengan  benar,  hal  ini  dapat  mengakibatkan  celah  keamanan  yang memungkinkan pengguna tidak sah atau penyerang untuk mengakses sumber daya atau fitur yang dilindungi tersebut. 

Berikut adalah cara pent test untuk mengetahui tentang Broken Access management 

Dalam pen test ini membutuhkan aplikasi Burpsuite, namun sebelum install aplikasi tersebut cek versi java kalian karena burpsuite hanya akan beroperasi pada versi java 17 ke atas. 

1. lakukan pengecekan versi java. 

![](Aspose.Words.c3c0bf6b-5dea-4c84-a4f2-ea84df35dfd1.002.png)

Pada OS saya sudah terinstal java versi 17 maka minimum requirement sudah terpenuhi. 

2. lakukan instalasi Burpsuite 

![](Aspose.Words.c3c0bf6b-5dea-4c84-a4f2-ea84df35dfd1.003.jpeg)

3. Jalankan OWASP Juice Shop 
3. buka aplikasi burpsuite 

![](Aspose.Words.c3c0bf6b-5dea-4c84-a4f2-ea84df35dfd1.004.jpeg)

Pada pengetesan pertama saya akan mengtrace dari HTTP request. Silahkan memilih proxy dan pilih HTTP History. Setelah itu buka browser dan buka halaman juice shop 

![](Aspose.Words.c3c0bf6b-5dea-4c84-a4f2-ea84df35dfd1.005.jpeg)

Setelah login saya akan menambahkan 1 apple juice dan1  apple pomace kedalam basket 

![](Aspose.Words.c3c0bf6b-5dea-4c84-a4f2-ea84df35dfd1.006.jpeg)

Terlihat isi basket saya adalah 2 item di atas, sekarang coba buka burp suite dan trace http requestnya. 

![](Aspose.Words.c3c0bf6b-5dea-4c84-a4f2-ea84df35dfd1.007.png)

Saat salah satunya di tekan maka akan keluar informasi sebagai berikut 

![](Aspose.Words.c3c0bf6b-5dea-4c84-a4f2-ea84df35dfd1.008.png)

Jika dilihat dari request ini sebenarnya ini menggunakan API dan angka 6 sepertinya adalah nomer dari user yang sudah terdaftar untuk memanggil isi basket. 

Mari kita kirim request di atas ke repeater dan liat apa yang akan terjadi 

![](Aspose.Words.c3c0bf6b-5dea-4c84-a4f2-ea84df35dfd1.009.png)

Disini bisa dilihat terdapat 2 item yaitu apel penance dan apple juice yang mana kedua item tersebut adalah item yang ada di dalam basket kita tadi. 

Selanjutnya apa yang akan terjadi jika kita mengubah angka dari API request 

![](Aspose.Words.c3c0bf6b-5dea-4c84-a4f2-ea84df35dfd1.010.jpeg)

Dengan mengubah basket number ke angka 2 maka kita akan bisa melihat basket dari user lain dengan basket number 2. 

Berikutnya kita akan mencoba menggunakan fitur intercept yang ada di burpsuite 

![](Aspose.Words.c3c0bf6b-5dea-4c84-a4f2-ea84df35dfd1.011.png)

Aktifkan fitur tersebut dan di juice shop tekan home page dan tekan basket 

![](Aspose.Words.c3c0bf6b-5dea-4c84-a4f2-ea84df35dfd1.012.jpeg)

Terlihat itu adalah request ke basket, akan saya ubah nomer dari user ke nomer 2 dan  klik forward  

![](Aspose.Words.c3c0bf6b-5dea-4c84-a4f2-ea84df35dfd1.013.jpeg)Maka di browser akan tertampil basket dari user dengan nomor 2. (**BROKEN ACCESS CONTROL VIEW BASKET)** 

Selanjutnya  menambahkan  atau  mengubah  basket  dari  user  lain  **(  BROKEN  ACCESS CONTROL BASKET MANIPULATE)** 

![](Aspose.Words.c3c0bf6b-5dea-4c84-a4f2-ea84df35dfd1.014.png)

Sekarang user tersebut mempunyai 3 raspberry juice setelah tadinya hanya 2 buah. Untuk menampilkah hasil dari modifikasi di atas dapat mengulangi step dari intercept. 

Selanjutnya menggunakan metode Burte Force untuk melakukan login Admin **(BROKEN ACCESS CONTROL ADMIN SECTION)** 

Hal pertama yang harus dilakukan adalah mengetahui email dari admin terlebih dahulu 

![](Aspose.Words.c3c0bf6b-5dea-4c84-a4f2-ea84df35dfd1.015.png)

Dengan  membuka  informasi  dari  item  maka  kita  akan  menemukan  informasi  email  dari admin 

Selanjutnya tambahkan URL dari juice shop ke target site  

![](Aspose.Words.c3c0bf6b-5dea-4c84-a4f2-ea84df35dfd1.016.png)

Pada proxy seting centang “Is In Target Scope” 

![](Aspose.Words.c3c0bf6b-5dea-4c84-a4f2-ea84df35dfd1.017.png)

Kembali ke halaman login, masukkan email dari admin dengan password random 

![](Aspose.Words.c3c0bf6b-5dea-4c84-a4f2-ea84df35dfd1.018.jpeg)

Sebelum itu siapkan intercept di burpsuite, aktifkan dan tekan login 

Pada intercept klik forward sampai muncul username admin dan password yang kita inputkan tadi 

![](Aspose.Words.c3c0bf6b-5dea-4c84-a4f2-ea84df35dfd1.019.png)

Kemudian kirim ke intruder 

![](Aspose.Words.c3c0bf6b-5dea-4c84-a4f2-ea84df35dfd1.020.png)

Bersihkan target untuk semua burte force dengan menekan clear 

Setelah itu pilih target burteforce yang mana ini adalah password dan tekan add 

![](Aspose.Words.c3c0bf6b-5dea-4c84-a4f2-ea84df35dfd1.021.png) ![](Aspose.Words.c3c0bf6b-5dea-4c84-a4f2-ea84df35dfd1.022.png)![](Aspose.Words.c3c0bf6b-5dea-4c84-a4f2-ea84df35dfd1.023.png)

Pada menu playload, muat file berformat .txt sebagai password bank yang nantinya akan di gunakan untuk burte force 

![](Aspose.Words.c3c0bf6b-5dea-4c84-a4f2-ea84df35dfd1.024.png)![](Aspose.Words.c3c0bf6b-5dea-4c84-a4f2-ea84df35dfd1.025.png)

Disini saya sudah menyiapkan file tersebut 

![](Aspose.Words.c3c0bf6b-5dea-4c84-a4f2-ea84df35dfd1.026.png)

Setelah password sudah di load tekan start attack 

![](Aspose.Words.c3c0bf6b-5dea-4c84-a4f2-ea84df35dfd1.027.png)![](Aspose.Words.c3c0bf6b-5dea-4c84-a4f2-ea84df35dfd1.028.png)

Pada data set password di atas terdapat 2 jenis HTTP status yaitu 401 dan 200, 401 sendiri terjadi karena saat permintaan browser ke server tidak memiliki kredensial autentik yang valid,  untuk  HTTP request  200 server  berhasil menerima request  dari browser yang kita gunakan dapat diartikan OK. 

Login dengan password dari hasil brute force 

![](Aspose.Words.c3c0bf6b-5dea-4c84-a4f2-ea84df35dfd1.029.jpeg)

![](Aspose.Words.c3c0bf6b-5dea-4c84-a4f2-ea84df35dfd1.030.jpeg)
