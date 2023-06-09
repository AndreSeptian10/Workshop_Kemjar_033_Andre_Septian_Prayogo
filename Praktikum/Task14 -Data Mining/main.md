**PRAKTIKUM KEAMANAN JARINGAN**

**“DataMining”**

<img src="./media/image1.png" style="width:2.83472in;height:2.69583in"
alt="Hasil gambar untuk logo pens png HD" />

**Oleh :**

**Andre Septian Prayogo**

**D4 LJ Teknik Informatika B**

**3122640033**

**POLITEKNIK ELEKTRONIKA NEGERI SURABAYA**

**TAHUN AJARAN**

**2023**

DATA MINING USING KNIME

1\. Bagi File menjadi 5 bagian : init.pcap, init2.pcap, init3.pcap,
init4.pcap, init5.pcap

<img src="./media/image2.png"
style="width:3.47917in;height:1.51389in" />

2\. Kemudian buka file tersebut secara bergantian menggunakan Wireshark.
Pada langkah ini kita gunakan file init.pcap

<img src="./media/image3.png"
style="width:6.26806in;height:3.27361in" />

3\. Untuk proses analisis yang akan dilakukan nantinya, kita akan
mengambil data dengan ip versi 4 (ipv4) dan protocol TCP, DNS saja.
Untuk proses tersebut dapat dilakukan pada wireshark menggunakan
perintah ip.version==4 && tcp \|\| dns pada kolom display filter tepat
dibawah toolbar

<img src="./media/image4.png"
style="width:6.26806in;height:2.64583in" />

4\. Untuk mendapatkan delta time dan delta time dan delta time display,
klik Edit – Preferences – Column

<img src="./media/image5.png"
style="width:6.26806in;height:2.47917in" />

Hasilnya

<img src="./media/image6.png"
style="width:6.26806in;height:2.57639in" />

5\. Export file pcap tersebut keformat Comma-separated Value (.csv)
dengan cara klik File – Export Packet Dissections – As CSV. Yang perlu
diperhatikan yaitu pada Pacet Range, pastikan yang terpilih yaitu
Displayed, karena data pada Displayed ini sudah terfilter denga nip
version 4

<img src="./media/image7.png"
style="width:4.46528in;height:4.61111in" />

<img src="./media/image8.png"
style="width:5.35417in;height:2.81944in" />

6\. Membuat workflow/project baru. Dengan cara klik File – New – New
Knime Workflow – Tulis Nama workflow dan Lokasi workflow tersebut – Klik
Finish

<img src="./media/image9.png"
style="width:6.26806in;height:3.25694in" />

**7.** Tambahkan data ke dalam file reader

<img src="./media/image10.png"
style="width:6.26806in;height:3.28333in" />

8\. Gabungkan kelima data dengan menggunakan concatenate dan data reader
seperti gambar di bawah

<img src="./media/image11.png"
style="width:6.26806in;height:3.22222in" />

9\. Untuk melakukan labeling data normal kita akan menggunakan Node
Missing Value. Node ini digunakan untuk mengisi data kosong

<img src="./media/image12.png"
style="width:6.26806in;height:3.26042in" />

10\. Untuk memastikan bahwa kolom label sudah terisi dengan value
Malicious atau Normal, dapat menggunakan node Value Counter. Node ini
berfungsi untuk menghitung jumlah seluruh value pada kolom terpilih.

<img src="./media/image13.png"
style="width:6.26806in;height:3.27083in" />

11\. Export file ke dalam format .csv dengan menggunakan node CSV Writer

<img src="./media/image14.png"
style="width:6.26806in;height:3.28333in" />

Data diletakkan di dalam file hasil.csv

<img src="./media/image15.png"
style="width:6.26806in;height:3.07431in" />

12\. **Data pre-processing**

Proses dimana data akan dibersihkan (cleaning) karena biasanya didalam
suatu data terdapat nilai-nilai yang tidak sempurna atau bahkan terdapat
nilai-nilai yang hilang atau kosong yang nantinya akan dapat
mempengaruhi proses kedepannya. Pada proses ini kita membutuhkan
Node-node berikut : File Reader, Column Filter, Missing Value.

<img src="./media/image16.png"
style="width:6.26806in;height:3.29931in" />

13\. Proses data transformation, pada proses ini data akan diubah ke
format yang sesuai untuk proses data mining. Node yang digunakan pada
tahap ini yaitu Normalizer. Berikut konfigurasinya:

<img src="./media/image17.png"
style="width:6.26806in;height:3.26458in" />

14\. **Data Mining**

Setelah menyelesaikan tahap data transformation, kita akan menjalankan
proses Data Mining, dalam proses ini kita akan menggunakan Metode
Klasifikasi Decision Tree dengan teknik Cross Validation. Pada proses
ini kita membutuhkan Node-node berikut : X-Partitioner, Decision Tree
Learner, Decision Tree Predictor, X-Aggregator Sehingga akan membentuk
flow seperti ini

<img src="./media/image18.png"
style="width:6.26806in;height:3.27083in" />

15\. Node Scorer yang didalamnya terdapat perhitungan untuk melihat
seberapa baik model ini dengan menggunakan teknik confusion matrix.
Berikut konfigurasinya.

<img src="./media/image19.png"
style="width:6.26806in;height:3.26458in" />

16\. Hasil prediksi

<img src="./media/image20.png"
style="width:6.26806in;height:3.24861in" />
