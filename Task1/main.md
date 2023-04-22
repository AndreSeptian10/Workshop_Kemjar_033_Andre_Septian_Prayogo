**PRAKTIKUM KEAMANAN JARINGAN**

**“BROKEN ACCESS CONTROL”**

<img src="./media/image1.png" style="width:2.83472in;height:2.69583in"
alt="Hasil gambar untuk logo pens png HD" />

**Oleh :**

**Andre Septian Prayogo**

**D4 LJ Teknik Informatika B**

**3122640033**

**POLITEKNIK ELEKTRONIKA NEGERI SURABAYA**

**TAHUN AJARAN**

**2023**

Broken Access Control atau disebut juga sebagai Broken Access Management
adalah suatu kerentanan keamanan yang terjadi pada aplikasi web atau
sistem yang dapat memungkinkan pengguna tidak sah untuk mendapatkan
akses yang tidak seharusnya pada sumber daya yang dilindungi atau fitur
yang terbatas.

Secara umum, Access Control adalah proses untuk memastikan bahwa hanya
pengguna yang diizinkan atau memiliki otoritas untuk melakukannya yang
dapat mengakses sumber daya atau fitur tertentu. Jika mekanisme Access
Control tidak dirancang atau diimplementasikan dengan benar, hal ini
dapat mengakibatkan celah keamanan yang memungkinkan pengguna tidak sah
atau penyerang untuk mengakses sumber daya atau fitur yang dilindungi
tersebut.

Berikut adalah cara pent test untuk mengetahui tentang Broken Access
management

Dalam pen test ini membutuhkan aplikasi Burpsuite, namun sebelum install
aplikasi tersebut cek versi java kalian karena burpsuite hanya akan
beroperasi pada versi java 17 ke atas.

1\. lakukan pengecekan versi java.

<img src="./media/image2.png" style="width:6.26806in;height:1.41944in"
alt="Text Description automatically generated" />

Pada OS saya sudah terinstal java versi 17 maka minimum requirement
sudah terpenuhi.

2\. lakukan instalasi Burpsuite

<img src="./media/image3.png" style="width:6.26806in;height:1.10069in"
alt="A computer screen capture Description automatically generated with medium confidence" />

3\. Jalankan OWASP Juice Shop

<img src="./media/image4.png" style="width:6.26806in;height:5.4625in" />

4\. buka aplikasi burpsuite

<img src="./media/image5.png" style="width:4.4835in;height:3.15524in"
alt="Graphical user interface, text, application Description automatically generated" />

Pada pengetesan pertama saya akan mengtrace dari HTTP request. Silahkan
memilih proxy dan pilih HTTP History. Setelah itu buka browser dan buka
halaman juice shop

<img src="./media/image6.png" style="width:6.26806in;height:3.11389in"
alt="Graphical user interface Description automatically generated" />

Setelah login saya akan menambahkan 1 apple juice dan1 apple pomace
kedalam basket

<img src="./media/image7.png"
style="width:6.26806in;height:2.19375in" />

Terlihat isi basket saya adalah 2 item di atas, sekarang coba buka burp
suite dan trace http requestnya.

<img src="./media/image9.png" style="width:6.26806in;height:2.37917in"
alt="Graphical user interface, table Description automatically generated" />

Saat salah satunya di tekan maka akan keluar informasi sebagai berikut

<img src="./media/image12.png"
style="width:6.26806in;height:4.48403in" />

Jika dilihat dari request ini sebenarnya ini menggunakan API dan angka 6
sepertinya adalah nomer dari user yang sudah terdaftar untuk memanggil
isi basket.

Mari kita kirim request di atas ke repeater dan liat apa yang akan
terjadi

<img src="./media/image15.png" style="width:4.72176in;height:4.3744in"
alt="Text Description automatically generated" />

Disini bisa dilihat terdapat 2 item yaitu apel penance dan apple juice
yang mana kedua item tersebut adalah item yang ada di dalam basket kita
tadi.

Selanjutnya apa yang akan terjadi jika kita mengubah angka dari API
request

<img src="./media/image16.png" style="width:4.45773in;height:3.1129in"
alt="Text Description automatically generated" />

Dengan mengubah basket number ke angka 2 maka kita akan bisa melihat
basket dari user lain dengan basket number 2.

Berikutnya kita akan mencoba menggunakan fitur intercept yang ada di
burpsuite

<img src="./media/image17.png" style="width:4.22976in;height:2.3024in"
alt="Graphical user interface, application Description automatically generated" />

Aktifkan fitur tersebut dan di juice shop tekan home page dan tekan
basket

<img src="./media/image18.png" style="width:6.26806in;height:3.21736in"
alt="Graphical user interface, text, application, email Description automatically generated" />

Terlihat itu adalah request ke basket, akan saya ubah nomer dari user ke
nomer 2 dan klik forward

<img src="./media/image19.png" style="width:6.26806in;height:2.69653in"
alt="Graphical user interface, application Description automatically generated" />

Maka di browser akan tertampil basket dari user dengan nomor 2.
(**BROKEN ACCESS CONTROL VIEW BASKET)**

Selanjutnya menambahkan atau mengubah basket dari user lain **( BROKEN
ACCESS CONTROL BASKET MANIPULATE)**

<img src="./media/image21.png" style="width:6.26806in;height:2.21111in"
alt="A screenshot of a computer Description automatically generated" />

Sekarang user tersebut mempunyai 3 raspberry juice setelah tadinya hanya
2 buah. Untuk menampilkah hasil dari modifikasi di atas dapat mengulangi
step dari intercept.

Selanjutnya menggunakan metode Burte Force untuk melakukan login Admin
**(BROKEN ACCESS CONTROL ADMIN SECTION)**

Hal pertama yang harus dilakukan adalah mengetahui email dari admin
terlebih dahulu

<img src="./media/image23.png" style="width:6.26806in;height:3.70208in"
alt="Graphical user interface, application, website Description automatically generated" />

Dengan membuka informasi dari item maka kita akan menemukan informasi
email dari admin

Selanjutnya tambahkan URL dari juice shop ke target site

<img src="./media/image25.png" style="width:6.26806in;height:4.55417in"
alt="Graphical user interface, application Description automatically generated" />

Pada proxy seting centang “Is In Target Scope”

<img src="./media/image27.png" style="width:4.98738in;height:3.4032in"
alt="Graphical user interface, text, application Description automatically generated" />

Kembali ke halaman login, masukkan email dari admin dengan password
random

<img src="./media/image28.png" style="width:6.26806in;height:4.52639in"
alt="A screenshot of a computer Description automatically generated with medium confidence" />

Sebelum itu siapkan intercept di burpsuite, aktifkan dan tekan login

Pada intercept klik forward sampai muncul username admin dan password
yang kita inputkan tadi

<img src="./media/image30.png" style="width:5.71954in;height:3.61004in"
alt="Graphical user interface, text, application, email Description automatically generated" />

Kemudian kirim ke intruder

<img src="./media/image32.png" style="width:6.26806in;height:2.7625in"
alt="Graphical user interface, text, application, email Description automatically generated" />

Bersihkan target untuk semua burte force dengan menekan clear

Setelah itu pilih target burteforce yang mana ini adalah password dan
tekan add

<img src="./media/image36.png" style="width:6.26806in;height:2.11389in"
alt="Graphical user interface, text, application, email Description automatically generated" />

Pada menu playload, muat file berformat .txt sebagai password bank yang
nantinya akan di gunakan untuk burte force

<img src="./media/image39.png" style="width:6.26806in;height:4.86944in"
alt="Graphical user interface, text, application, email Description automatically generated" />

Disini saya sudah menyiapkan file tersebut

<img src="./media/image41.png" style="width:6.26806in;height:2.38819in"
alt="Graphical user interface, text, application, Teams Description automatically generated" />

Setelah password sudah di load tekan start attack

<img src="./media/image44.png" style="width:6.17683in;height:3.30193in"
alt="Table Description automatically generated" />

Pada data set password di atas terdapat 2 jenis HTTP status yaitu 401
dan 200, 401 sendiri terjadi karena saat permintaan browser ke server
tidak memiliki kredensial autentik yang valid, untuk HTTP request 200
server berhasil menerima request dari browser yang kita gunakan dapat
diartikan OK.

Login dengan password dari hasil brute force

<img src="./media/image45.png" style="width:4.25195in;height:4.20243in"
alt="Graphical user interface Description automatically generated" />

<img src="./media/image46.png" style="width:5.59453in;height:5.42784in"
alt="Graphical user interface, application Description automatically generated" />

Burte force memiliki kaitan dengan Broken access control yang tertulis
di CWE-922 Insecure Storage of Sensitive Informasion, dalam CWE 922
relevan dengan CWE-312 [Cleartext Storage of Sensitive
Information](https://cwe.mitre.org/data/definitions/312.html), dapam CWE
312 memiliki kaitan dengan CWE-11 Missing Encryption of Sensitive Data.

<img src="./media/image48.png"
style="width:6.26806in;height:1.36458in" />

Kode di atas sama seperti kode dari header HTTP di Burp Suite tadi
dimana data dari user tertampil. Ini akan mengekspos informasi dari user
jika computer mereka di serang oleh hacker.
