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
Client dapat hanya melakukan request untuk data user_name dan user_email.
yang mana hal ini mengurangi jumlah data yang di-transfer, sehingga meningkatkan Performance.

-> yang mana pada langkah ini, User melakukan Request Data, yang mana Request Data ini dibantu dengan teknologi GraphQL, sehingga Data yang diambil hanya data yang dibutuhkan oleh User, dan tidak perlu mengambil keseluruhan data, tetapi data tersebut tidak dibutuhkan.


-> "GraphQL API" itu seperti 'Pintu' yang Clients pakai untuk berkomunikasi dengan Engine.

-> "GraphQL API" merupakan 'Entry Point' (titik masuk) yang Clients gunakan untuk meminta Data (ask for Data)

(Clients itu seperti Aplikasi atau Website)

-> Apa yang dilakukan oleh "GraphQL API" :

(1) Sends Requests :
Clients 'mengirim Request' melalui GraphQL API untuk meminta Data.

(2) Single Access Point : 
GraphQL API memiliki "Single Access Point", yaitu hanya mempunyai satu pintu untuk membuat lebih Simple.
Dibandingkan dengan REST API yang mempunyai banyak pintu.

-> pada GraphQL API, "Single Access Point" berarti semua Request pada API melewati satu URL atau Endpoint.
Pada GraphQL, Endpoint ini adalah "/graphql".

Daripada kita harus mempunyai URL yang berbeda-beda untuk Resources yang berbeda seperti "/users", "/posts", dan sebagainya,
pada Single Access Point, kita hanya mempunyai satu endpoint,
yang mana Clients mengirimkan Request nya ke Single Location.

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

-> Real-Time Updates pada Hasura DDN (Data Delivery Network) 
memungkinkan applications untuk menerima "Live Data" secara instan tanpa harus melakukan refresh atau secara berulang melakukan Request untuk Update.

yang mana hal ini sangat bermanfaat untuk Aplikasi dimana User dapat melihat langsung perubahan pada aplikasi, sesegera mungkin setelah terdapat perubaha pada Data.
Aplikasi tersebut seperti Live Dashboards, Stock Updates, Gaming Apps, dan sebagainya.
 
#### [4] Security & Privacy :

-> Hasura DDN menyediakan Security Features seperti "Encryption" untuk menjaga data tetap aman saat Data di-transfer antar Server & User.

-> Hasura DDN juga melindungi dari serangan DDoS (yang menyerang dengan cara mengirim terlalu banyak Traffic ke Server, sehingga Server bisa Crash) 

### D. Architecture of Hasura DDN (Data Delivery Network)

- Architecture dari Hasura DDN itu seperti sebuah System yang terancang dengan baik untuk memastikkan Data dapat dikirim ke User dengan cepat, efficient, dan aman.

- berikut ini merupakan penjelasan mengenai **Cara kerja Arsitektur Hasura DDN** :

#### [1] Origin Server :
(Sumber Data yang utama)

-> "Origin Server" itu seperti Gudang besar yang menyimpan data penting.

-> Pada "Origin Server", terdapat Original Data dari Aplikasi, Website, Business, dan sebagainya.
yang dimaksud "Original Data" adalah Data Utama, bukan Data Salinan, 
karena kalau Data Salinan berada di "Edge Server".

-> Peran dari Origin Server : Menyimpan Data Utama
(menyimpan Data Original, bukan Data Salinan)

-> Location : biasanya berada pada Lokasi Pusat (Central Location) atau di sebuah Cloud			


#### [2] Edge Servers (Local Data Cache) : 

-> "Edge Server" merupakan Server-Server yang tersebar di berbagai Geographical Location yang memiliki jarak lebih dekat ke User.
("Edge Server" memiliki jarak yang lebih dekat ke User, dibandingkan dengan jarak antara "Origin Server" ke User)

-> "Edge Server" merupakan "Temporary Storage" yang menyimpan data sementara.
Data sementara yang disimpan merupakan Data yang sering diakses atau Data yang sering di-request oleh User.

-> Data yang sering diakses tersebut akan disalin dari Data Utama yang ada di "Origin Server", dan hasil Salinan Data tersebut akan disimpan di "Edge Servers".


-> Sehingga jika nanti User melakukan Request untuk Data yang sering diakses,
maka System dapat mengirimkan Data dari "Edge Server" yang berada pada Lokasi terdekat dengan User.
yang mana hal ini dapat membantu :

(1) Mengurangi Latency (Waktu Pengiriman Data):
karena Data dikrimkan dari Server yang lokasi nya lebih dekat dengan User,
sehingga Jarak pengiriman Datanya lebih dekat,
yang mana jarak yang lebih dekat ini dapat mengurangi waktu pengiriman data (Latency)
	
(2) Mengurangi beban kerja "Origin Server" :
Karena Pengiriman Data juga dilakukan dari "Edge Server" dan tidak hanya dari "Origin Server", maka hal ini dapat mengurangi beban kerja "Origin Server". 

(karena beban kerja di-distribusikan juga ke "Edge Server")

-> Kenapa menggunakan "Edge Server" ?

Misalnya kita adalah Cloud Company asal Indonesia,
yang mana "Origin Server" di Indonesia.
Dan kita mempunyai Customer di Japan, daripada kita mengirim data dari "Origin Server" di Indonesia, sebaiknya kita mengirim data dari "Edge Server" di Japan, agar kita bisa mengirim data dengan lebih cepat


#### [3] Caching Layer (Quick Access Storage) : 

-> "Caching Layer" bukan merupakan System yang mengelola "Edge Server",
tapi "Caching Layer" merupakan teknologi yang diandalkan "Edge Server" untuk mengirim dan menyimpan data secara efficient.

-> Caching Layer itu seperti "Temporary Storage System" (Sistem Penyimpanan Sementara),
yakni setiap kali User melakukan Request Data,
DDN pertama-tama memeriksa "Edge Server's Cache" untuk melihat apakah data sudah pernah disimpan di "Edge Server"

(Saat User melakukan Request Data, DDN memeriksa apakah Data yang di-request tersebut sudah pernah disimpan di Edge Server)

-> Kemudian, jika Data yang di-request oleh User sudah ada pada "Edge Server" (Cache Hit), maka Data tersebut akan langsung dikirim dari "Edge Server" ke User.

tetapi jika Data yang di-request oleh User tidak ada pada "Edge Server" (Cache Miss), 
maka DDN akan mengambil data dari "Origin Server", dan menyimpan data tersebut di "Edge Server" untuk Request di masa depan.

Proses "Cache Hit" & "Cache Miss" tersebut disebut "Caching Mechanism", yang mana hal ini mempercepat proses pengiriman data dan mengurangi beban pada "Origin Server".

-> Saat Data di-request oleh User, DDN akan melakukan pengecekkan apakah Data tersebut sudah pada "Edger Server", maka setelah itu akan terdapat salah satu kondisi, yaitu apakah kondisi "Cache Hit" atau kondisi "Cache Miss".
berikut penjelasannya : 

(1) "Cache Hit" :
merupakan kondisi saat Data yang di-request oleh Customer sudah ada pada "Edge Server",
sehingga data tersebut tidak perlu diambil lagi dari "Origin Server".

(2) "Cache Miss" :
merupakan kondisi saat Data yang di-request oleh Customer tidak ada pada "Edge Server",
sehingga data tersebut perlu diambil dari "Origin Server".

#### [4] GraphQL API Layer (Data Request) :

-> GraphQL adalah Query Language untuk API yang memungkinkan Client untuk meminta bagian data tertentu yang mereka butuhkan, daripada harus mengambil seluruh kumpulan Dataset seperti Tradional API. yang mana teknologi GraphQL ini memberikan pengambila Data yang lebih efisien.

Misalnya, daripada mengambil keseluruhan User Data, Client dapat hanya melakukan request untuk data user_name dan user_email. yang mana hal ini mengurangi jumlah data yang di-transfer, sehingga meningkatkan Performance.

#### [5] Load Balancing (Traffic Management) :

-> DDN menggunakan Load Balancing untuk memastikkan System tidak kelelahan dengan banyak orang yang melakukan Request Data pada waktu yang sama.

-> "Load Balancing" berperan untuk mendistribusikan Traffic ke beberapa Server, karena "Data Delivery Network" (DDN) mencegah adanya Server yang kelelahan oleh Traffic yang tinggi. yang mana hal ini mencegah Slowdown (pelambatan) & Outage (Pemadaman) pada System, bahkan selama lonjakan Traffic (Traffic Spikes).

-> Peran "Load Balancing" : 
Mendistribusikan "User Request" ke beberapa Servers, agar tidak ada Satu Server pun yang kelebihan beban.

-> Benefit menggunakan "Load Balancing" : 
Meningkatkan Performance & menghindari Server Crash saat High-Traffic

#### [6] Security Layer (Protecting the Data) :

-> Security pada Hasura DDN (Data Delivery Network) sangatlah penting,
karena berkaitan dengan Data Sensitive yang dikirim dan disimpan di berbagai lokasi.

-> Hasura DDN memilki beberapa Fitur keamanan untuk menjaga Data & User,
beberapa diantaranya adalah :

(1) DDoS Protection :
>> menghentikan Malicious Attacks (Serangan jahat) yang mencoba membanjiri Server dengan Traffic yang terlalu tinggi, dengan harapan Server akan Crash.

>> "DDoS" (Distributed Denial of Service) attack :
merupakan serangan dimana Hacker mencoba membanjiri System dengan Traffic yang sangat banyak, dengan harapan System tidak dapat menahan beban kerja, dan System akan Crash.


(2) SSL/TLS Encryption :
>> Memastikkan Data di-enkripsi dengan baik sata di-transfer, agar Hacker tidak dapat melakukan Intercept (mencegat) atau merusak datanya.

>> SSL dan TLS merupakan Protokol yang digunakan untuk mengamankan komunikasi antara Komputer dan Server,
yang mana ini merupakan cara untuk mengunci Pesan (Data) sehingga tidak ada orang lain yang dapat membacanya Pesan (Data) tersebut berpindah antara Komputer dan Server.


(3) Web Application Firewall (WAF) :

>> Memblokir Request yang berbahaya, seperti upaya peretasan atau virus, sebelum mencapai Server

>> "Web Application Firewall" (WAF) :
adalah sebuah System keamanan yang melakukan Filter, Monitor, dan Block HTTP Traffic Ke- dan Dari Web Application.
WAF itu seperti Penjaga Keamanan untuk Web Application kita yang mengawasi semua data yang masuk dan keluar.
WAF memastikkan Data yang berbahaya tidak masuk ke Web Application kita, dan hanya membiarkan masuk Data yang aman & telah disetujui.


#### [7] Real-Time Data Syncing (Staying Updated) :

-> Hasura DDN di-desain untuk menjaga Data tetap ter-update secara Real-Time.

-> Jika terdapat perubahan data pada "Origin Server", perubahan data tersebut secara cepat dikirim salinannya ke "Edge Server", agar User selalu mendapatkan Informasi yang up-to-date.

-> Contoh :
jika terdapat perubahan data pada Product's Price,
maka "Edge Server" akan menyinkronisasi informasi tersebut untuk memastikkan harga terbaru ditampilkan ke Customer tanpa Delay.


#### [8] Analytics and Monitoring (Keeping Track of Performance) :

-> System ini untuk melacak seberapa baik kinerja Network,
dan untuk memastikkan semuanya berjalan lancar, dan jika ada issue dapat dideteksi dan diperbaiki dengan cepat.

-> Hasura DDN terus memantau :

(1) Traffic : 
seberapa banyak orang meng-akses data

(2) Speed : 
Seberapa cepat data dikirim

(3) Security :
apakah ada aktifitas yang tidak biasa atau jahat terjadi.

### E. Apa yang terjadi saat User melakukan Request Data :

Saat User melakukan Request Data, inilah yang terjadi : 

#### [1] Request :
User melakukan Request Data,
seperti melakukan Request untuk menampilkan Webpage, Product Info melalui Aplikasi atau Browser.

#### [2] Routing :
Pada proses ini, Request User diarahkan ke "Edge Server" terdekat dengan User.

-> Jika Data yang di-request oleh User, sudah ada di "Edge Server", maka data tersebut akan langsung dikrimkan ke User 

-> tetapi jika Data yang di-request oleh User, tidak ada di "Edge Server", maka Data tersebut perlu diambil terlebih dahulu dari "Origin Server", kemudian salinan datanya disimpan pada "Edge Server", dan kemudian Data tersebut dikirim ke User.

#### [3] GraphQL : 
Permintaan diproses secara effiecient oleh GraphQL, 
yang mana GraphQL memastikkan agar hanya data yang diperlukan yang dikirim.


-> GraphQL API memungkinkan Client untuk meminta bagian data tertentu yang mereka butuhkan, daripada harus mengambil seluruh kumpulan Dataset seperti Tradional API. yang mana teknologi GraphQL ini memberikan pengambila Data yang lebih efisien.

Misalnya, daripada mengambil keseluruhan User Data, Client dapat hanya melakukan request untuk data user_name dan user_email. yang mana hal ini mengurangi jumlah data yang di-transfer, sehingga meningkatkan Performance.

#### [4] Security :
-> Security pada Hasura DDN (Data Delivery Network) sangatlah penting, karena berkaitan dengan Data Sensitive yang dikirim dan disimpan di berbagai lokasi.

-> Hasura DDN memilki beberapa Fitur keamanan untuk menjaga Data & User, beberapa diantaranya adalah "DDoS Protection", "SSL/TLS Encryption", dan"Web Application Firewall"

### E. Component of Hasura Architecture : 
- Core Component (Komponen Inti) dari Arsitektur Hasura adalah :

#### [1] Client Applications :
merupakan Frontend applications seperti Web atau Mobile, 
yang mana merupakan tempat untuk membuat "GraphQL Queries" dan "Mutations" untuk mengambil atau meng-update data



#### [2] Hasura GraphQL Engine :
"GraphQL Engine" berperan dalam :
(1) Memproses Query : 
-> Saat Request masuk, GraphQL Engine akan membaca dan memahaminya

(2) Fetches Data (Mengambil Data) :
"GraphQL Engine" menarik informasi dari Database atau Services lainnya

(3) Return Results : 
"GraphQL Engine" mengirim data yang diminta User


>> Summary :
>> 
>> - GraphQL Engine berperan dalam "Memproses & Menyediakan Data"
>>   
>> - GraphQL Engine berperan dalam "Memproses Request Query yang masuk",
"Mengambil Data dari Database, data yang diambil merupakan Data yang di-request oleh Query",
"Kemudian data yang diambil dari Database tersebut, dikirim oleh GraphQL Engine ke User"


#### [3] Database :
merupakan Database yang menyimpan data, seperti PostgreSQL


#### [4] CDN / Edge Servers :
"Edge Server" merupakan Tempat penyimpanan sementara untuk menyimpan Data yang sering diakses agar Data tersebut dekat ke End-User untuk mengurangi Latency & meningkatkan performance. 


#### [5] Authentication and Authorization Services :

>> **Authentication** : 

-> Authentication adalah Proses untuk pembuktian identitas kita.
seperti pertanyaan "Who are you ?" (Siapa anda ?)

-> Analogi nya seperti memasuki Gedung dan kita harus menunjukkan ID Card di pintu untuk membuktikkan Siapa kita.
Di dunia Digital, Authentication berarti "Log In" menggunakan Username & Password,
atau bentuk identifikasi lainnya untuk membuktikkan identitas.

-> Bagaimana Authentication bekerja di Hasura ? 

Hasura tidak secara langsung menangani Authentication (seperti mengelola Username atau Password), tetapi Hasura berkerja sama dengan layanan lainnya, seperti JWT (JSON Web Token), dan juga Third Party Services, seperti Auth0, Firebase Auth, atau Okta.


-> Langkah-langkah Proses Authentication :

(1) Login :
kita login menggunakan Third Party Services, seperti Auth0.
Third Party Services ini memverifikasi Credentials kita (seperti Email & Password)

(2) Token Generation :

Setiap kali identity User dikonfirmasi, User akan diberikan "JWT Token".
Token ini seperti digital ID yang mengatakan "This is who I am, and I'm allowed to access this System"
(inilah saya, dan saya boleh untuk mengakses System ini)

(3) Send Token to Hasura :

Setiap kali kita berinteraksi dengan Hasura (seperti membuat Request Data),
sebenarnya kita juga mengirim Token bersamaan dengan Request.

(ini seperti Menunjukkan ID Card kita setiap kali kita membuat Request Data)


(4) Hasura Memverifikasi Token :
Hasura mengecek apakah Token tersebut Valid,
Jika Valid, maka Hasura mengetahui bahwa anda adalah orang yang sama dengan Identitas yang anda Claim.


>> **Authorization** : 

-> Authorization merupakan Proses untuk menetukkan "apa yang boleh anda lakukan",
yang mana hal ini menjawab pertanyaan "Apa yang boleh kamu akses, setelah anda di-autentikasi ?"

-> bayangkan saat kita memasuki Gedung, kita memiliki Akses untuk lantai yang berbeda-beda.
Misalnya Rudi hanya memiliki akses untuk ke lantai 10 & 7,
sementara Jane memiliki akses untuk ke lantai 12, 8, dan 5.

yang mana, di dunia Digital, Authorization mengontrol Data dan Feature apa yang bisa kita akses berdasarkan Role (Peran) atau Permission (izin) kita.

-> Hasura menggunakan Authorization berupa "Role-Based Access Control" (RBAC).
RBAC menentukkan Data apa yang bisa kita akses dan Action apa yang bisa kita lakukan berdasarkan Role (peran) kita.

-> Langkah-langkah dalam Authorization Process :

(1) Token berisi Role / Claims :

JWT Token (yang didapat dari Authentication) mengandung informasi mengenai "Role" kita,
apakah Role kita sebagai "User", "Admin", atau sebagai role lainnya.
yang mana, informasi "JWT Token" mengenai Role ini, memberitahu Hasura jenis akses apa yang anda miliki.

(2) Hasura Checks your Role :

Hasura mengecek Role, dan memutuskan Data apa yang bisa diakses.
Jika Role kita mengizinkannya, kita dapat melakukan View, Modify, dan Delete pada Data,
tetapi jika Role kita tidak mengizinkannya, maka Hasura memblokir permintaan (Request) kita.

contoh :
Role "User" hanya boleh melihat data miliknya sendiri, tetapi Role "Admin" dapat mengakses Data milik semua orang.

(3) Custom Rules :

Kita bisa menyiapkan aturan baru untuk memberikan akses tertentu untuk suatu peran.


>> Combining Steps of Authentication & Authorization :
>> (Menggabungkan langkah-langkah dari Authentication & Authorization)

(1) Login :
(ini merupakan Proses Authentication)

Kita Login dengan Email & Password dengan menggunakan Third Party Services (misalnya Firebase Auth).



(2) Token Issued (Token diterbitkan) :
(ini merupakan Proses Authentication)

Setelah Login sukses, kita akan mendapatkan JWT Token yang berisi "ini [nama anda], dan mereka adalah User"

(3) Request Data : 
(ini merupakan Proses Authentication)

kita bisa Request Data yang ingin kita akses.
Request yang kita minta tersebut, dikirimkan beserta Token kita

(4) Hasura Checks Token :
(ini merupakan Proses Authorization)

Hasura mengecek Role kita, dan melihat aturan, apa saja yang boleh dilakukan oleh Role kita.

(5) Access Control : 

Hasura memberikan akses sesuai peraturan apa yang boleh diakses oleh Role kita


#### [6] Load Balancer :

-> Load Balancer mendistribusikan Traffic ke beberapa Server untuk menghindari bottlenecks (kemacetan) dan mengoptimalkan penggunaan Resources.

-> Load Balancing merupakan teknik yang digunakan untuk mendistribusikan Request atau Traffic ke beberapa Server, yang bertujuan untuk memastikkan agar tidak ada satu server pun yang kewelahan dengan terlalu banyak Request atau Traffic, sementara Server lainnya kurang dimanfaat dengan baik.
yang mana Teknik Load Balancing ini membantu mencegah System mengalami Crash



### F.  Gambar : "Architecture of Hasura Data Delivery Network"
![Arsitektur Hasura DDN (Data Delivery Network)](https://github.com/user-attachments/assets/841afeb2-b6aa-4d8b-b7b3-d954ab93a161)






### G. Workflow Explanation of "Hasura Data Delivery Network (DDN)" :


### H. Hasura Strategy to Decide which Data will be sent to "Edge Server" vs which Data that remain in "Origin Server" :


### I. Supergraph in Hasura : -> sepertinya di artikel terpisah

### J. Data Plane & Control Plane in Hasura : -> sepertinya di artikel terpisah

### K. GraphQL API in Hasura  -> sepertinya di artikel terpisah

### L. Federation Layer in Hasura  -> sepertinya di artikel terpisah

### M. Hasura Architecture  -> sepertinya di artikel terpisah

(urutannya mulai dari G perbaiki lagi)

## >>>>>For your information : <<<<<

### 1. Edge Server's Cache : 


### 2. Caching Layer : 

===

to do :

1) Analytic & Monitoring in Hasura
2) Security in Hasura DDN
3) Networking in Hasura
4) Architecture of Hasura
