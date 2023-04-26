**PRAKTIKUM KEAMANAN JARINGAN**

**“Security Misconfiguration”**

<img src="./media/image1.png" style="width:2.83472in;height:2.69583in"
alt="Hasil gambar untuk logo pens png HD" />

**Oleh :**

**Andre Septian Prayogo**

**D4 LJ Teknik Informatika B**

**3122640033**

**POLITEKNIK ELEKTRONIKA NEGERI SURABAYA**

**TAHUN AJARAN**

**2023**

Security misconfiguration adalah kelemahan yang paling sering terjadi di
antara kelemahan lain di daftar ini. Biasanya kesalahan terjadi jika
hanya menggunakan default configuration tanpa melihat kebutuhan website

**Error Handling**

Memunculkan error, tetapi error yang ditampilkan tidak bagus dan
konsisten

Nyalakan burp suite

<img src="./media/image2.png"
style="width:6.26806in;height:2.20556in" />

Buka browser dan pergi ke halaman utama website owasp juice shop

<img src="./media/image3.png"
style="width:6.26806in;height:3.08125in" />

Buka Kembali burp suite maka akan muncul request baru yaitu
/rest/product/search

<img src="./media/image4.png"
style="width:6.26806in;height:1.96875in" />

Masukkan playload /rest/product/search tadi ke repeater lalu ubah
endpointnya menjadi text random lalu klik send

<img src="./media/image5.png"
style="width:6.26806in;height:4.40625in" />

Maka yang terjadi adalah response error 500 atau internal server error
yang begitu Panjang dan tidak tertata
