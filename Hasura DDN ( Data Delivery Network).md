# Hasura DDN ( Data Delivery Network)

## 1. Understanding DDN (Data Delivery Network)

- Data Delivery Network (DDN) juga dikenal sebagai Content Delivery Network (CDN).
DDN adalah system yang dirancang untuk meningkatkan pengiriman Digital Content melalui internet.
System ini mengurangi Latency (waktu yang dibutuhkan untuk mengirimkan Data), mempercepat Loading Times (waktu pemuatan), dan meningkatkan User Experience untuk aplikasi/website, terutama yang melayani Large Volume of Data (Volume Data yang besar).

- Data Delivery Network (DDN) dirancang khusus untuk pengiriman "Large Volumes of Data" (jumlah data secara besar).
DDN dibangun untuk mendukung :

  [1] High-Speed Data Transfer (Transfer Data berkecepatan Tinggi)
  
  [2] Large-Scale Content Distribution (Distribusi Konten berskala besar)
  
  [3] High Availability

Sehingga DDN sangat bermanfaat untuk Aplikasi yang mempunyai Jumlah Data yang besar.

- "Large-Scale Content Distribution" : 
merupakan pengiriman Digital Content dalam jumlah besar (Digital Content tersebut seperti Web Pages, Video, images, Software, dan Data lainnya).
Pengiriman Digital Content ini didistribusikan ke sejumlah besar User ke berbagai wilayah Geografis.

- High Availability (HA) :
merupakan Desain & Implementasi System, Network, dan Services, 
untuk memastikan Komponen-komponen tersebut tetap bisa beroperasi & bisa diakses dengan minimal Downtime.
"High Availability" bertujuan untuk memastikan bahwa Applications & Services tersedia setiap saat, atau dengan Downtime yang sangat minimal,
yang mana seringkali diukur dengan Uptime Percentage (persentase Waktu Aktif), seperi 99.99% 

### A. Fungsi Utama DDN (atau CDN) : 
#### (1) Caching Content at Edge Servers :

-> DDN menggunakan Distributed Server Network yang terletak di berbagai Geographical Locations, server dinamakan "Edge Server".
Edge Server menyimpan sementara Salinan Content (seperti Image, Videos, dan Web Page).

"Edge Server" merupakan tempat penyimpanan sementara (temporary storage), tetapi Perannya lebih dari sekedar tempat penyimpanan sementara.

Saat User melakukan "Request Content", DDN menyajikan "Request Content" tersebut dari "Edge Server" terdekat, untuk mengurangi jarak yang harus ditempuh untuk pengiriman Data, yang mana hal ini bertujuan untuk mengurangi Latency (waktu yang dibutuhkan untuk mengirimkan Data).

(yang dilakukan Edge Server ini merupakan Caching Strategy)


-> "Edge Server" berfungsi sebagai "Temporary Storage" (tempat penyimpanan sementara),
tetapi peran dari "Edge Server" lebih dari sekedar tempat penyimpanan sementara.
Fungsi utama "Edge Server" adalah menyimpan Data yang sering diakses agar Data tersebut dekat ke End-User untuk mengurangi Latency & meningkatkan performance.
(Data yang sering diakses tersebut seperti Web Pages, images, Videos, atau Content lainnya)

-> Arsitektur "Edge Server" di-desain untuk membawa Storage, Processing, dan Delivery lebih dekat ke End-User, yang mana hal ini untuk memastikan "Response Time" yang lebih cepat, dan Network Bandwith yang lebih optimal.

-> "Edge Server" merupakan Komponen Inti (Core Component) dari "Edge Computing" & "Content Delivery Network".
Arsitektur "Edge-Server" melibatkan multiple layers & component yang bekerja sama untuk mengurangi Latency, mendistribusikan Workloads (beban kerja), dan memungkinkan Real-time Data Processing.


#### (2) Load Balancing : 

-> "Load Balancing" berperan untuk mendistribusikan Traffic ke beberapa Server,
karena "Data Delivery Network" (DDN) mencegah adanya Server yang kelelahan oleh Traffic yang tinggi.
yang mana hal ini mencegah Slowdown (pelambatan) & Outage (Pemadaman) pada System, bahkan selama lonjakan Traffic (Traffic Spikes). 


#### {3] Improved Scalabilty :

- DDN di-desain untuk menangani Traffic dalam jumlah besar.
- DDN memastikan Performance yang lancar untuk Website & Service yang mengalami lonjakkan Traffic.

