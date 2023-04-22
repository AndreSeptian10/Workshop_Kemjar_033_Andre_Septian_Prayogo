**PRAKTIKUM KEAMANAN JARINGAN**

**“Cryptographic Failures”**

<img src="./media/image1.png" style="width:2.83472in;height:2.69583in"
alt="Hasil gambar untuk logo pens png HD" />

**Oleh :**

**Andre Septian Prayogo**

**D4 LJ Teknik Informatika B**

**3122640033**

**POLITEKNIK ELEKTRONIKA NEGERI SURABAYA**

**TAHUN AJARAN**

**2023**

Kegagalan kriptografi adalah kerentanan keamanan aplikasi web kritis
yang memaparkan data aplikasi sensitive pada algoritma kriptografi yang
lebah atau tidak ada. Itu bisa berupa kata sandi, catatan
kesehatanpasien, rahasia bisnis, informasi kartu kredit dan informasi
pribadi lainnya.

Aplikasi web modern memproses data saat diam dan transit, yang memrlukan
control keamanan yang ektat untuk mitigasi ancaman yang komperhensif.
Berberapa penerapan menggunakan Teknik kroptografi lebah yang dapat
dipecahkan dalam jangka waktu yang wajar. Bahkan dengan penerapan tekink
kroptografi yang sempurna, pengguna dapat menghindari penerapan praktif
terbaik pelindungan data, yang selanjutnya membuat informasi sensitive
rentan terhadap pencurian data sensitive.

Berikut macam macam cryptographic failures yang berhasil ditemukan pada
website OWASP juice shop.

**Nested Easter Egg**

Easter Egg merupakan pesan tersembunyi yang telah disisipkan kedalam
website

Berikut adalah caranya:

1\. Pergi ke halaman github yang ada pada bagian sidebar menu website
OWASP juice Shop

<img src="./media/image2.png"
style="width:6.26806in;height:3.18333in" /><img src="./media/image3.png"
style="width:6.26806in;height:3.18958in" />

2\. selanjutnya pergi ke folder <http://ftp/eastere.gg> maka akan
melihat kode seperti pada gambar dibawah ini

<img src="./media/image4.png"
style="width:6.26806in;height:2.52986in" />

3\. selanjutnya buka website CyberChef

<img src="./media/image5.png"
style="width:6.26806in;height:3.39861in" />

4\. masukkan operasi “Form Base 64” dan ROT 13

<img src="./media/image6.png"
style="width:3.49171in;height:4.03771in" />

5\. masukkan kode yang kita dapatkan dari github tadi pada input yang
nantinya kita mendapat string seperti URL website

<img src="./media/image7.png"
style="width:6.26806in;height:4.60347in" />

6\. kita coba masukkan URL tersebut ke web OWASP juice shop kita, maka
akan memunculkan halaman website seperti pada gambar dibawah ini

<img src="./media/image8.png"
style="width:6.26806in;height:2.70972in" />

**B. Wired Crypto**

Memberi tahu took tentang algoritma atau library enkripsi yang
seharusnya tidak digunakan

1\. pada Web OWASP, pergi ke halaman customer feedback yang berada di
sidebar menu

<img src="./media/image9.png"
style="width:4.91082in;height:5.05173in" />

<img src="./media/image10.png"
style="width:6.26806in;height:2.57569in" />

2\. masukkan comment dengan imputan “MD5” lalu submit jawaban. Maka
setelah itu akan mencul notifikasi menyelesaikan challenge wired crypto.

<img src="./media/image11.png"
style="width:6.26806in;height:5.60694in" />

<img src="./media/image12.png"
style="width:6.26806in;height:2.51528in" />

Pesan yang ingin disampaikan dari challenge Wired Crypto ini adalah kita
sudah harus tau algoritma atau library enkripsi apa yang sebaiknya kita
gunakan dan yang sudah harus kita tinggalkan. Salah satu kontoh
algoritma yang sebaiknya sudah ditinggalkan adalah MD5.

MD5 adalah versi lama dari algoritma kriptografi, dimana kata kunci
masih bisa menggunakan 4 huruf. Didesain oleh Ronald Rivest pada 1991.
Lima tahun kemudian pada 1996 ditentukan cacat dalam desainnya sehingga
mulai ditinggalkan dan digantikan dengan alogoritma baru seperti SHA-1
dan SHA-2. Saat ini, di pasaran juga tersedia aplikasi untuk membuka
enkripsi MD5 yang disebut “MD5 Hash Generator”. Secara teori enkripsi
MD5 memang kurang aman disbanding SHA2 sebab hanya memiliki Panjang 128
bit.
