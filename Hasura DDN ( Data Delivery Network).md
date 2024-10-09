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

### A. What is Hasura DDN (Data Delivery Network) ?

- Hasura DDN merupakan sistem pengiriman data yang di-desain untuk mempercepat proses pengiriman data.

- Hasura DDN di-desain untuk membuat pengiriman Data dalam jumlah besar (large amount of data) menjadi cepat, efficient, dan secure.
Dengan menggunakan "Edge Server" untuk "Cache Data", sehingga Data lebih dekat dengan Users.
"Cache Data" merupakan menyimpan data yang sering diakses ke Temporary Storage, agar jika butuh Request Data tersebut lagi, System hanya perlu melakukan Request ke Temporary Storage, dan tidak perlu Request ke Server utama (Origin Server), sehinga ini dapat mengurangi Traffic & mengurangi beban kerja dari Server Utama (Origin Server).

### B. Komponen Utama & Cara kerja Hasura DDN : 

#### [1] Origin Server :
(Starting Point / Titik awal)

-> Pada Origin Server, data utama disimpan.

-> Origin Server merupakan Server Utama yang menyimpan versi asli Data.
Origin Server bertugas menghasilkan Response terhadao Request Client mengenai Dataa/Content.

#### [2] Edge Servers :
(menyimpan data agar lebih dekat ke pengguna)

-> "Edge Server" merupakan Temporary Storage yang digunakan untuk menyimpan Data yang sering diakses, sehingga data tersebut di-Request, System hanya perlu mengambil dari "Edge Server" dan tidak perlu mengambil langsung dari "Origin Server",
yang mana hal ini dapat mengurangi beban dari "Origin Server"

-> yakni pada langkah ini, Data yang sering diakses, data tersebut dibuat salinan nya, dan disimpan di "Edge Server".

-> Data yang sering diakses tersebut, aslinya berasal dari "Origin Server".

-> Salinan Data yang disimpan pada "Edge Server", pada Step selanjutnya akan dipakai untuk proses "Data Caching"


#### [3] Data Caching :

-> "Data Caching" berarti menyimpan salinan data yang sering dipakai,
data yang sering dipakai itu seperti data yang sering di-request oleh User.
Salinan Data ini sudah sebelumnya disimpan di "Edge Server".

-> Pada Proses "Data Catching", jika User melakukan Request Data, dan data tersebut kita sudah punya salinan nya pada "Edge Server", maka System akan mengambil data dari "Edge Server", daripada harus mengambil data ke "Origin Server".
yang mana hal ini dapat membantu mengurangi beban kerja "Origin Server", karena beban kerja dapat di-distribusikan ke "Edge Server".

Selain itu, hal ini dapat membantu mengurangi Latency (waktu yang dibutuhkan untuk mengirim data) & mempercepat pengiriman data, karena "Edge Server" biasanya merupakan Server yang jarak geografis nya lebih dekat dengan User dibandingkan dengan "Origin Server",
karena jarak "Edge Server" yang lebih dekat, sehingga dapat membantu mempercepat pengiriman data.


#### [4] GraphQL API 
(Bagaimana data di-query)

-> Hasura menggunakan "GraphQL", yakni cara modern untuk melakukan Request Data,
membuatnya super-efficient, dibandingkan Request terlalu banyak data atau Request terlalu sedikit data.
GraphQL memungkinkan User untuk melakukan Request Data seperti apa yang mereka butuhkan,
yang mana hal ini mengurangi pengiriman Data yang tidak dibutuhkan,
membuat semuanya lebih cepat dan lebih ringan dalam penggunaan bandwith.

-> GraphQL adalah Query Language untuk API yang memungkinkan Client untuk meminta bagian data tertentu yang mereka butuhkan, 
daripada harus mengambil seluruh kumpulan Dataset seperti Tradional API.
yang mana teknologi GraphQL ini memberikan pengambila Data yang lebih efisien.

Misalnya, daripada mengambil keseluruhan User Data,
Client dapat hanya melakukan untuk data user_name dan user_email.
yang mana hal ini mengurangi jumlah data yang di-transfer, sehingga meningkatkan Performance.

-> yang mana pada langkah ini, User melakukan Request Data, yang mana Request Data ini dibantu dengan teknologi GraphQL, sehingga Data yang diambil hanya data yang dibutuhkan oleh User, dan tidak perlu mengambil keseluruhan data, tetapi data tersebut tidak dibutuhkan.

### C. Bagaimana Hasura DDN meningkatkan Pengiriman Data : 

#### [1] Faster Data Access :
(Akses Data yang lebih cepat)

-> dengan menempatkan "Edge Server" di Lokasi yang berbeda-beda,
yang mana Lokasi "Edge Server" tersebut mempunyai jarak yang lebih dekat dengan User 
(dibandingkan dengan jarak "Origin Server" dengan User), 
sehingga waktu Pengiriman Data ke User menjadi lebih cepat, karena data dikrim dari "Edge Server" terdekat, daripada harus dikrim dari "Origin Server" dengan jarak yang melintasi dunia.

#### [2] Reduced Server Load : 
(Beban Server Berkurang)

-> "Beban Server Berkurang" karena Beban di-distribusikan juga dengan "Edge Server"

-> Karena bayak data yang dikirm dari "Edge Servers", maka "Origin Server" tidak kelelahan dengan Request yang teralalu banyak.
yang mana hal ini membuat System menjadi lebih Efficient, dan mencegah adanya perlambatan (slowing down) saat Peak Traffic (Traffic Puncak)


#### [3] Real-Time Updates :

-> Saat Data baru atau Perubahan baru terjadi,
Hasura DDN dapat dengan cepat meng-update data di "Edge Server",
memastikkan User selalu mendapatkan Informasi paling up-to-date.



====

to do :

1) Security in Hasura DDN
