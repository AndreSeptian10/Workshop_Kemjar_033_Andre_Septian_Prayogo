**PRAKTIKUM KEAMANAN JARINGAN**

**“Attack Scenario”**

<img src="./media/image1.png" style="width:2.83472in;height:2.69583in"
alt="Hasil gambar untuk logo pens png HD" />

**Oleh :**

**Andre Septian Prayogo**

**D4 LJ Teknik Informatika B**

**3122640033**

**POLITEKNIK ELEKTRONIKA NEGERI SURABAYA**

**TAHUN AJARAN**

**2023**

Pada percobaan kali ini, kita mencoba melakukan peretasan terhadap
sebuah virtual box image dengan OS Ubungu. Goal kali ini adalah kita
berhasil mengakses database dan mendapat user rootnya, untuk dapat
mengakses database kita akan menggunakan SQLmap dan untuk mendapatkan
akses user root kita akan menggunakan Nmap.

SQLmap merupakan alat (tool) bantu open source dalam melakukan tes
penetrasi yang mengotomasi proses deteksi dan eksploitasi kelemahan SQL
injection dan pengambil-alihan server basis data. SQLmap dilengkapi
dengan pendeteksi canggih, fitur-fitur handal bagi penetration tester,
beragam cara untuk mendeteksi basis data, hingga mengakses file system
dan mengeksekusi perintah dalam sistem operasi melalui koneksi
out-of-band

NMAP adalah singkatan dari Network Mapper yang merupakan sebuah tool
atau alat yang bersifat open source. Alat ini hanya digunakan secara
khusus untuk eksplorasi jaringan serta melakukan audit terhadap keamanan
dari jaringan.

Brute force adalah upaya mendapatkan akses sebuah akun dengan menebak
username dan password yang digunakan. Brute force attack sebenarnya
merupakan teknik lama dalam aksi cyber crime. Namun, ternyata masih
banyak digunakan karena dianggap masih efektif. Namun itu hanya langkah
awal metode serangan. Tujuan utama brute force adalah mengakses situs,
server yang menyimpan berbagai informasi dan aset penting lain. Setelah
masuk ke dalam sistem, hacker dapat mengendalikan website Anda hingga
mencuri data.

## **A. Mendapatkan user root**

1\. Langkah pertama kita akan mengecek IP dari device yang kita gunakan
dengan ifconfig

<img src="./media/image2.png"
style="width:6.26806in;height:3.77361in" />

2\. selanjutnya kita akan menggunakan ipclac “IP kita” untuk mengetahui
informasi yang lebih rinci tentang ip yang kita gunakan

<img src="./media/image3.png"
style="width:6.26806in;height:2.28264in" />

3\. kita akan melakukan scan menggunakan nmap -sT “network kita”

<img src="./media/image4.png"
style="width:6.26806in;height:2.52986in" />

Dalam command di atas -sT di artikan kita akan mengcek semua yang ada di
network kita, semua port yang terbuka missal port SSH http dan yang lain

<img src="./media/image5.png"
style="width:6.26806in;height:2.06667in" />

Dan di atas adalah informasi dari virtual box yang akan kita serang,
akan saya sederhanakan commandnya agar spesifik ke ip 19

<img src="./media/image6.png"
style="width:6.26806in;height:2.62917in" />

Terlihat port yang terbuka adalah 2 port yaitu port http dan ssh.

4\. setelah kita mendapatkan IP target selanjutnya kita akan menyiapkan
bahan untuk melakukan penyerangan, yaitu list dari username dan juga
password

<img src="./media/image7.png"
style="width:6.26806in;height:2.72778in" />

<img src="./media/image8.png"
style="width:6.26806in;height:3.57778in" />

<img src="./media/image9.png"
style="width:6.26806in;height:1.71597in" />

Kita akan menggunakan bruteforce yang menuju ke SSH, -p22 menjelaskan
tujuan penyerangan kita akan dilakukan di port 22 dimana port tersebut
adalah port SSH.

<img src="./media/image10.png"
style="width:5.10198in;height:4.67408in" />

Sayangnya pada step ini tidak ditemukan hasil dari username password
yang valid, dan juga sudah mencoba berbagai wordlist namun hasilnya
tetap sama.

## **B. Mengakses Database**

1\. Langkah pertama yang saya lakukan untuk mendapatkan akses database
adalah melakukan crawling untuk mendapatkan sitemap website yang akan
kita serang menggunakan skipfish

<img src="./media/image11.png"
style="width:6.26806in;height:5.75139in" />

Dan kita bisa melihat hasil dari skipfish dengan membuka direktori dari
skipfish

<img src="./media/image12.png"
style="width:6.26806in;height:3.18611in" />

3\. masukkan ip dari server ubuntu ke web

<img src="./media/image13.png"
style="width:6.26806in;height:3.04861in" />

<img src="./media/image14.png"
style="width:6.26806in;height:3.01944in" />

5\. setelah itu pilih vunlweb

<img src="./media/image15.png"
style="width:6.26806in;height:2.3375in" />

Lakukan pemanggilan database sqlmap -u
"http://192.168.1.10/?tampil=artikel_detail&id=83" -D idvulnewb --tables

<img src="./media/image16.png"
style="width:6.26806in;height:2.78889in" />

Lakukan command berikut untuk mengambil data user sqlmap -u
"http://192.168.1.10/?tampil=artikel_detail&id=83" -C
id_user,password,username --dump

<img src="./media/image17.png"
style="width:6.26806in;height:3.79792in" />

<img src="./media/image18.png"
style="width:6.26806in;height:1.60764in" />

File sudah ada di ditektori tersebut

<img src="./media/image19.png"
style="width:6.26806in;height:1.22222in" />

<img src="./media/image20.png"
style="width:5.43826in;height:2.48993in" />
