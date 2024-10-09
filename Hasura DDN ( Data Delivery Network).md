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

-> Data Delivery Network (DDN) mempercepat distribusi data di seluruh jaringan internet dengan menggunakan "Edge Server" yang di-distribusikan secara geografis.

#### (2) Load Balancing : 

-> "Load Balancing" berperan untuk mendistribusikan Traffic ke beberapa Server,
karena "Data Delivery Network" (DDN) mencegah adanya Server yang kelelahan oleh Traffic yang tinggi.
yang mana hal ini mencegah Slowdown (pelambatan) & Outage (Pemadaman) pada System, bahkan selama lonjakan Traffic (Traffic Spikes). 


#### {3] Improved Scalabilty :

- DDN di-desain untuk menangani Traffic dalam jumlah besar.
- DDN memastikan Performance yang lancar untuk Website & Service yang mengalami lonjakkan Traffic.

#### [4] Reduce Bandwith Costs :

(Mengurangi Biaya Bandwith)

-> Dengan menggunakan Strategi "Caching Content", yakni menyimpan konten di "Temporary Storage" agar lebih dekat ke User,
dengan cara ini, DDN mengurangi workload "Server Origin" untuk menangani Request berulang untuk mengenai konten yang sama.
yang mana, ini dapat membantu organisasi untuk mengurangi konsumsi Bandwith, dan membantu menurunkan biaya.

### B. Contoh penggunaan Data Delivery Network (DDN) :

#### (1) Video Streaming :
DDN mengirim High-Quality Video Content (seperti Youtube & Netflix) dengan mengurangi waktu buffering dan memastikkan pemutaran video yang lancar.

#### (2) E-Commerce :
Website seperti Amazon & E-bay menggunakan DDN untuk memastikkan Loading halaman yang cepat dan Performance yang konsisten, bahkan dengan Global Traffic

#### (3) Online Gaming :
DDN mengurangi Latency (waktu pengiriman data) dan meingkatkan responsiveness dalam Online Multiplayer Gaming, yang memastikkan Data permainan secara capat dikrimkan ke User di seluruh dunia

#### (4) Software Downloads :
Company mendistribusikan File Besar menggunakan DDN,
untuk memastikkan Download yang lebih cepat dan megurangi beban server.


### C. Jenis Content yang dikirim oleh DDN (Data Delivery Network) :

#### [1] Static Content :

Static Content merupakan tipe media yang tidak sering berubah.
Contoh Static Content adalah : Images, CSS Files, JavaScript File, Videos, dan lain lain

#### [2] Dynamic Content :

-> merupakan Content yang di-generate secara Real-Time.
-> "Dynamic Content" merupakan Data yang dibuat secara Real-Time berdasarkan interaksi pengguna, preferensi pengguna, atau Variabel lainnya.
yang mana, Dynamic Content seringkali dipersonalisasi dan dapat berubah secara berkala.

-> Real-Time Generation :
Dynamic Content dibuat atau dimodifikasi pada saat Request,
yang mana hal ini berarti bahwa Content tersebut dapat mencerminkan informasi up-to-date yang tersedia.

-> Personalization :
Dynamic Content seringkali disesuaikan untuk masing-masing User berdasarkan behavior, Preferences, Location, dan faktor lainnya.
Penyesuaian ini meningkatkan keterlibatan dan kepuasan User.




## 2. Understanding Hasura DDN (Data Delivery Network)
