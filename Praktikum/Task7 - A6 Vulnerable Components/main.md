**PRAKTIKUM KEAMANAN JARINGAN**

**“Vulnerable Components”**

<img src="./media/image1.png" style="width:2.83472in;height:2.69583in"
alt="Hasil gambar untuk logo pens png HD" />

**Oleh :**

**Andre Septian Prayogo**

**D4 LJ Teknik Informatika B**

**3122640033**

**POLITEKNIK ELEKTRONIKA NEGERI SURABAYA**

**TAHUN AJARAN**

**2023**

A06:2001 tentang Vulnarable Component membahas tentang komponen yang
digunakan untuk membangun aplikasi kita telah usang atau memiliki
kerentanan. Masalah ini juga ada di daftar 10 Teratas tahun 2017 dan
telah mendapatkan posisi yang lebih baik: \#6, sementara itu berada di
posisi \#9 di tahun 2017 dan diberi nama Using Components with Known
Vulnerabilities. Percaya atau tidak, mengelola dependensi Anda adalah
pekerjaan yang berat. Ini tidak sesederhana menjalankan perintah
pembaruan atau mengunduh dependensi & paket yang diperbarui. Tapi lebih
dari ini: aplikasi Anda mungkin rusak dengan perubahan terbaru, beberapa
fitur mungkin tidak digunakan lagi, fungsi mungkin diganti namanya,
dependensi mungkin ditinggalkan, perbaikan mungkin tidak berfungsi pada
sistem Anda tanpa merusak beberapa dependensi lain, membuat malapetaka.
Anda mendapatkan ide yang benar

**Legacy Typosquatting**

Typosquatting , juga disebut URL hijacking, sting site, atau fake URL,
adalah bentuk cybersquatting , dan kemungkinan brandjacking yang
bergantung pada kesalahan seperti kesalahan ketik yang dibuat oleh
pengguna Internet saat memasukkan alamat situs web ke dalam browser web.
Jika pengguna secara tidak sengaja memasukkan alamat situs web yang
salah, mereka dapat diarahkan ke URL apa pun (termasuk situs web
alternatif yang dimiliki oleh cybersquatter). Ini bisa merujuk ke
goggle.com. Goggle.com adalah situs web berbahaya salah ketik yang
bahkan dapat membahayakan komputer Anda dan menghapus ROM Anda dalam 30
detik

1\. Langkah pertama kita pergi ke URL berikut http://localhost:3000/ftp

<img src="./media/image2.png"
style="width:6.26806in;height:1.87917in" />

2\. Setelah itu kita akan ditunjukkan list file yang ada pada directory
ftp ini seperti gambar diatas. Kita buka file yang bernama
package.json.bak

<img src="./media/image3.png"
style="width:6.26806in;height:2.21181in" />

3\. Setelah itu akana muncul tampilan seperti pada gambar diatas yang
menampilkan error bahwa file tersebut tidak bisa dibuka. Kita ubah
sedikit URL setelah pergi ke halaman package.json.bak menjadi seperti
berikut <http://localhost:3000/ftp/package.json.bak%2500.md>

<img src="./media/image4.png"
style="width:6.26806in;height:2.85278in" />

4\. Setelah menjalankan URL tersebut kita akan mendownload file yang
berisi package json aplikasi website tersebut

<img src="./media/image5.png"
style="width:3.91537in;height:4.27976in" />

5\. Dari file package json ini kita coba check dependencies apa saja
yang digunakan oleh aplikasi ini. Setelah itu kita melihat salah satu
dependencies yang sepertinya tidak seharusnya atau typo dalam
penulisannya tetapi dapat digunakan yaitu yang bernama epilogue-js.
Ketika kita buka pada website npm muncul tampilan sebagai berikut

<img src="./media/image6.png"
style="width:6.26806in;height:2.88264in" />

6\. Untuk package yang seharusnya digunakan adalah package epilogue
bukan epilogue-js

<img src="./media/image7.png"
style="width:6.26806in;height:4.38681in" />

7\. Kita informasikan temuan kita ini pada customer feedback untuk
menyelesaikan challange ini

<img src="./media/image8.png" style="width:6.26806in;height:5.4625in" />
<img src="./media/image9.png"
style="width:6.26806in;height:2.56597in" />
