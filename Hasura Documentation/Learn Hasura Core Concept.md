
# Core Concepts

- Meluasnya Microservices & API yang harus dihubungkan ke setiap Produk agar dapat berfungsi, telah menimbulkan serangkaian tantangan baru bagi Developer & Architect.

- Di era modern dalam membangun aplikasi, Data Layer menjadi semakin kompleks; Data Layer tidak lagi sekadar Database, tetapi Collection of Database (Kumpulan Database), Services, dan API.

- Hasura DDN memperkenalkan konsep Data Supergraph untuk membantu Anda mengelola kompleksitas ini.

  ## A. The State of The Data Layer
  
Bayangkan beberapa Team berikut dalam sebuah Hypothtethical Company :

>> "Hypothetical" merupakan kondisi berdasarkan teori atau asumsi dan bukan berdasarkan keadaan sebenarnya (actual events). Seringkali digunakan untuk meng-eksplorasi kemungkinan yang terjadi pada situasi tertentu, yang mana pertanyaan tersebut seperti "apa yang anda lakukan jika memenangkan Lotere ?"

>> "Hypothetical Company" merupakan kondisi perumpamaan bisnis yang digunakan sebagai contoh untuk diskusi, analisis, dan sebagainya

(1) Product Management Team :

- bertanggung jawab atas 'Relational Database' yang menyimpan informasi Produk.
yang mana Team ini fokus pada Cataloging Products (Pengkatalogan Produk), Managing Inventory, dan memastikkan Detail Produk dalam keadaan Akurat & up-to-date dengan menggunakan Relational Database PostgreSQL.

(2) User Experience Team : 

- Mengelola Dokumen Database MongoDB dan API terkait untuk menyimpan User Information.
Fokusnya mereka adalah Maintaining User Profile, Preferences, dan memastikkan privasi dan Security dari data pengguna.

(3) Search Optimization Team : 

- Menangani integrasi Algolia Search Services untuk Product dan Partner Store. Mereka bekerja untuk mengoptimalkan algoritme pencarian, memastikan hasil pencarian yang relevan, dan meningkatkan pengalaman pencarian secara keseluruhan bagi User.

(4) Finance & Transactions Team : 

- Mengawasi Stripe Payment Service (layanan pembayaran Stripe) dan Relational Database yang mendasarinya untuk memproses pembayaran,
yang mana hal ini termasuk mengelola keamanan transaksi (Managing Transaction Security) , integrasi Payment Gateway, dan memastikan Transaksi Keuangan yang lancar.

- Payment Gateway itu seperti "Online Bridge" (jembatan Online) yang membantu kita melakukan pembelian di internet.

- Payment Gateway merupakan Technology yang memfasilitasi Online Transactions dengan mengirim informasi pembayaran secara aman antara Customer, Merchant (Pedagang), dan Bank.
Payment Gateway memastikkan bahwa Data Sensitif dilakukan enkripsi, dan diproses dengan aman.
(Data Sensitif tersebut seperti Credit Card Numbers, Credit Card Details)


(5) Logistics and Shipping Team : 

- Bertanggung jawab atas layanan pengiriman ShipStation, pemenuhan pesanan (Fulfilling Orders), dan Relational Database yang mendukung proses ini. Fokus utama mereka adalah logistik, pelacakan pesanan (Order Tracking) , dan memastikan pengiriman produk tepat waktu.


(6) Data Science and Recommendations Team :

- Mengelola Weaviate Vector Database untuk menyimpan User Recommendation. 
Mereka mengerjakan Personalization Algorithms, analisis User Behavior, dan memberikan Product Recommendations untuk meningkatkan User Experience.


>> --
>> --

Keragaman Team dalam perusahaan ini, masing-masing dengan fokus unik dan Data Service yang terspesialisasi, melambangkan Challenge yang terjadi dalam Pengelolaan Data secara modern dan Pengembangan API

Semua Team ini beroperasi dengan API, Schemas, dan Metodologi yang berbeda,
yang mana Fragmentasi atau Perbedaan ini tidak hanya memperumit Proses Pengembangan Aplikasi, tetapi juga memerlukan keterlibatan Data Architect & Data Engineer untuk mengintegrasikan dan memelihara berbagai sumber data secara efisien.

(Fragmentasi merupakan Perbedaan pada Aplikasi atau Software)


### 1. What is "The Data Layer" ?
>> Penjelasan tambahan di luar Dokumentasi Hasura

- Pada aplikasi apapun, "Data Layer" merupakan tempat aplikasi berinteraksi dengan Database.

- "Data Layer" menangani "Storage" (Penyimpanan), Retrieval (Pengambilan), and "Manipulation" (manipulasi) of Data

(Data Layer menangani Penyimpanan, Pengambilan, dan Manipulasi Data)

- "Data Layer" sangat penting, karena :

	(1) memastikkan  Aplikasi dapat memperoleh Data.

	(Data Layer makes sure "App can get Data")
	
	(2) memastikkan Aplikasi dapat mengirim Data baru ke Database

	(Data Layer makes sure "App can send new Data to the Database")


### 2. How Does Hasura Manage "The Data Layer" ?
### (Bagaimana Hasura mengelola "Data Layer" ? )
>> Penjelasan tambahan di luar Dokumentasi Hasura

- Hasura mengelola "Data Layer" dengan secara otomatis membuat "GraphQL API" untuk Database anda.
yang mana, ini berarti, pada saat kita membuat Database ke Hasura, 
Hasura membuat serangkaian alat yang memungkinkan anda membuat Query & memodifikasi Data tanpa perlu membuat API secara manual.

#### 2.1) Berikut ini yang dilakukan Hasura pada "Data Layer" :

##### [1] Instant API Generation : 

-> Begitu kita connect ke Database, Hasura secara otomatis membuat "GraphQL API".
yang mana kita bisa langsung membuat "Query" (asking for Data) dan Mutation (changing data) menggunakan API ini.

-> API (Application Programming Interface) merupakan cara berbagai Software yang berbeda untuk berkomunikasi dengan satu sama lain.

Pada konteks Hasura, API memungkinkan aplikasi kita (seperti Web atau Mobile App) untuk berkomunikasi dengan Database atau untuk mendapatkan Data atau Memperbarui Data.

-> Biasanya (pada case bukan Hasura), Developer perlu membuat API secara manual agar aplikasi bisa berinteraksi dengan Database.
yang mana hal ini melibatkan penulisan Backend Code, Setting Up Route (Pengatura Rute), dan memastikkan Keamanan, yang mana tugas-tugas tersebut dapat menyita banyak waktu dan tenaga.

-> Pada Hasura, "Instant API Generation" secara otomatis membuat API, segera setelah kita menghubungkan ke Database, tanpa kita perlu menulis Backend Code


##### [2] Permissions : 

-> Hasura memungkinkan kita untuk menetapkan "Fine-Grained" Access Control Rules (aturan kontrol Akses yang terperinci), sehingga User atau Role yang berbeda dapat memiliki tingkat akses yang berbeda ke Data kita.
yang mana, hal ini memastikkan Keamanan dengan hanya mengizinkan orang yang berwenang untuk melihat atau mengubah tertentu.

>> ^For your Information^ 
>>
>> {1} **Fine-Grained Access Control** :
>> 
>> -> "Fine-Grained Aceess Control" (FGAC) merupakan Security approach yang memungkinkan kita untuk menetapkan aturan yang "Sangat Spesifik" tentang siapa yang dapat mengakses Data atau Fitur dalam suatu System.

>> -> Keyword :
>> "Fine-Grained Aceess Control" (FGAC) = aturan Access Control yang sangat spesifik
 
>> -> berbeda dengan "Coarse-Grained Access Control" yang menyediakan izin yang luas tanpa aturan yang spesifik.
>> Seperti "Everyone can accesss the Data", "All Students can Access the book"

>> -> Contoh : School Library

>> (1) Coarse-Grained Access :
>> All Students dapat meminjam buku

>> (2) Fine-Grained Access Control : 

>> Elementary School Students (Siswa SD) hanya bisa meminjam buku dari Kid's Section.

>> Middle School Students (Siswa SMP) dapat meminjam buku dari Kid's Section & Young Adult Section.

>> Teachers (Guru) dapat mengakses semua Book Section.


>> -> Use Case (Kasus Penggunaan) :

>> (1) Database Security :
>> Membatasi akses pengguna ke Row (baris) atau Kolom yang spesifik pada Database Table.
>> seperti, ada Baris tertentu pada Database Table yang hanya boleh diakses oleh Admin.

>> (2) Application Security :
>> Mengontrol Akses berdasarkan User Roles.
>> yakni setiap Roles mempunyai izin yang berbeda untuk mengakses Fitur atau Data tertentu.

>> (3) Resource Management :
>> Mengelola akses ke File, Folder, atau Services berdasarkan User Roles, Location, atau Faktor lainnnya


##### [3] Real Time Data :

-> Hasura menawarkan "Subscription" di GraphQL yang menyediakan Real-Time Update.

Jika ada yang berubah pada Database, aplikasi yang terhubung ke Hasura dapat secara otomatis diperbarui dengan Data baru tanpa perlu melakukan Refresh secara manual.

>> ^For your Information^
>> 
>> {1} **Subscription** :
>> 
>> -> Subscription adalah fitur canggih yang memungkinkan kita mendapatkan "Real-Time Updates" dari Database.
artinya, saat terdapat perubahan pada Database, aplikasi kita akan secara otomatis menerima Update tanpda perlu melakukan Refresh atau Request tambahan lainnya.
>>
>> -> Contoh Query Subscription pada Hasura :
>>
>> misalnya kita mempunyai Table di Database yang bernama "Posts",
>> dan kita ingin menampilkan Real-Time Updates saat terdapat perubahan pada Tabel "Posts".
>>
>> (1)  Berikut ini adalah contoh Query untuk GraphQL Subscription ke Tabel Posts : 
>>
>>```graphql
>>subscription {
>>  posts {
>>    id
>>    title
>>    content
>>    created_at
>>  }
>>}
>>```
>><br/>
>> (2) Contoh Query untuk Subscribes ke Tabel Messages : <br/>
>> jika terdapat perubahan Data pada Tabel Messages (Seperti mendapatkan Pesan/Message baru), kita akan mendapatkan Update pada Data tersebut secara Real-Time.
>> 
>> ```
>> subscription {
>>  messages(where: { chat_room_id: { _eq: 1 } }) {
>>    id
>>    content
>>    user
>>    created_at
>>  }
>> }
>> ```
>> <br/>
>> <br/>
>> 
>> ````
>> (where: { chat_room_id: { _eq: 1 } })
>> ````
>> potongan Query diatas artinya "dimana nilai chat_room_id adalah 1",
>> yang mana ini berarti jika terdapat Messages baru pada "Chat Room 1", maka berikan notifikasi nya pada Aplikasi saya.
>> <br/>
>> <br/>
>> <br/>
>> (3) Contoh Query untuk Subscribes ke Tabel "StockPrices" (harga saham) : <br/>
>> Contoh Query untuk Subscribes ke Tabel StockPrices (harga Saham), tapi hanya ke Spesifik Saham, yaitu Saham AAPL.
>>yakni jika terdapat perubahan harga Saham pada sahama AAPL, kita akan mendapatkan notifikasi mengenai Update Data tersebut secara Real-Time.
>>
>> ```
>>subscription {
>>  stockPrices(where: { symbol: { _eq: "AAPL" } }) {
>>    symbol
>>    price
>>    updated_at
>>  }
>>}
>>```
>> <br/>
>> <br/>
>>
>> ```
>> (where: { symbol: { _eq: "AAPL" } })
>> ```
>>  <br/>
>>potongan Query diatas artinya "dimana nilai Symbol adalah AAPL", (AAPL itu merupakan kode untuk Saham Apple) <br/>
>> yang mana ini berarti berikan saya notifikasi nya jika terdapat perubahan harga pada Saham AAPL.
>> <br/>
>> <br/>
>> <br/>
>>  -> Cara Kerja "Subscription" di Hasura :

>> (1) Client Subscribes : <br/>
>> Client yang berupa Front-end Application pada Hasura, mengirim "Query GraphQL Subscription".
>> Query tersebut dibutuhkan untuk track changes (melacak perubahan). <br/>
>>Misalnya jika kita ingin mendapatkan Real-Time Update mengenai Tabel "Message",
>>maka kita akan Subscribe ke Tabel "Message" tersebut.
>>
>>  (2) Hasura Listens For Change : <br/>
>> Setelah Subscription aktif, <br/>
>> kemudian Hasura memantau Database untuk setiap perubahan (seperti New Messages, Updated Records, atau Deleted Data).
>>
>> (3) Real-Time Updates : <br/>
>> Saat terdapat perubahan pada Database, <br/>
>> Hasura secara otomatis "Push the updated Data" (Push data yang di-update) ke Aplikasi secara Real-Time.
>> yang mana dengan hal ini, Aplikasi tidak perlu mengirim Request baru atau melakukan Refresh Page untuk mendapatkan Data yang baru.
>> <br/>
>> <br/>
>> <br/>
>> <br/>
>> -> Contoh Penggunaan Subscription :
>>
>> Jika kita membangun Chat App (Aplikasi Chat),
>> kita bisa melakukan "Subscribe" ke Tabel "Messages",
>> sehingga kapanpun ada Pesan baru, maka Pesan tersebut akan langsung muncul ke Aplikasi tanpa harus Reload Page (memuat ulang halaman).
>> 
>> (Tabel "Messages" berisi data mengenai Pesan Chat, sehingga saat ada Pesan baru masuk, maka data pada Tabel "Messages" mengalami perubahan).
>>
>> -> How Hasura Manage Subscription :
>> (Cara Hasura mengelola Subscription)
>>
>> Hasura menangani Subscription menggunakan "WebSockets".
>>
>> WebSockets merupakan teknologi yang memungkinkan komunikasi dua arah (two-way communication) antara Server dan Client.
>> yang mana hal ini memungkinkan Hasura untuk menjaga Open Connection (komunikasi yang berkelanjutan untuk menerima informasi) dan melakukan Push Updates kapanpun terjadi >> perubahan pada Database.
>>
>>
>> -> begini cara kerja Subscription : 
>>
>> (1) Saat aplikasi kita memulai Subscription, maka koneksi WebSocket dibuka antara Hasura dan aplikasi kita.
>>
>> (2) Selama Koneksi WebSocket ini aktif, Hasura dapat mengirim Update ke aplikasi kapanpun data mengalami perubahan
>> 
>> (3) Jika Koneksi WebSocket nya Lost (terputus) atau Closed (ditutup),
>> maka aplikasi dapat melakukan Restart pada Subscription untuk bisa menerima Update (Perubahan Data).
>><br/>
>><br/>
>> <br/>
>>-> Use Case for Subscription :
>> (Kasus penggunaan untuk Subscription)
>> 
>> Subscriptions sangat berguna untuk fitur Real-Time pada Aplikasi.
>>
>> Beberapa contoh Use Case Subscription, yaitu : 
>>
>> (1) Live Chat : <br/>
>> Dapatkan Pesan baru secara instan dalam percakapan, tanpa harus melakukan Refresh pada halaman.
>> 
>> (2) Live Notifications : <br/>
>> Menampilkan Notifikasi segera setelah Event baru terjadi.
>> Event tersebut seperti Comments, Likes, Messages.
>>
>> (3) Collaborative Tools : <br/>
>> Jika beberapa orang sedang mengerjakkan sebuah dokumen yang sama,
>> maka Subscription dapat menunjukkan Real-Time Update dari User lain. <br/>
>> Contohnya seperti Google Doc.
>> Misalnya Putri dan Jane sedang mengerjakkan file yang sama pada Google Doc,
>> maka dengan Subscription, Putri dapat melihat perubahan data pada dokumen yang dilakukan oleh Jane. begitu juga sebaliknya, Jika Putri menambah tulisan pada Goolge Doc, >> maka Jane dapat melihat tulisan oleh yang diubah oleh Putri.
>> 
>> (4) Real-Time Dashboards : <br/>
>> Track (Melacak) Live Data pada sebuah Dashboard,
>> seperti Stock Prices, Metrices, atau Data dari Sensor.
>>
>>   -> Workflow of Subscriber in Hasura : <br/>
>> 	(Alur Kerja Subscriber di Hasura)
>> 
>> ![Cara Kerja of Subscriber in Hasura drawio](https://github.com/user-attachments/assets/930cf6bf-c8a9-4609-84fd-0aaf0746d003)
>> <br/>
>> Berikut ini Cara Kerja / Alur Kerja Subscriber di Hasura : <br/>
>> (Penjelasan Chart)
>> <br/>
>> <br/>
>> (1) Client 1 & Client 2 : <br/>
>> Bagian ini mewakili dua User (Client) yang berbeda dari aplikasi kita yang ingin menerima Real-Time Updates.  <br/>
>> Masing-masing Clients mempunyai "WebSocket" Connection ke Hasura Server.
>> 
>> (2) WebSocket Connection :  <br/>
>> Setiap Client memelihara koneksi WebSocket (WebSocket Connection) yang memungkinkan mereka untuk menerima Update secara Real-Time.  <br/>
>> (Client perlu menjaga Koneksi pada WebSocket tetap aktif untuk bisa menerima Update secara Real-Time).
>> 
>> (3) Subscribe to "The Data Changes" :  <br/>
>> Clients (baik Client 1, maupun Client 2 pada gambar) melakukan Subscribes untuk Perubahan Data tertentu (Data Changes tertentu),  <br/>
>> yang mana hal ini dilakukan dengan mengirimkan "Subscription Query" (Query untuk minta Subscription) ke Server Hasura. <br/>  <br/>
>> yang dimaksud dengan "Client Subscribes to Spesific Data Changes", <br/>
>> itu berarti Client memberitahu Server untuk segera memberikan Notifikasi saat terjadi perubahan mengenai Data Spesifik tersebut. <br/>
>> Contoh :  <br/>
>> Kita Subscribes ke Tabel "StockPrices" (harga saham), tapi hanya untuk spesifik Data, yaitu Saham Apple. <br/>
>> maka kita hanya akan diberi notifikasi jika terdapat perubahan harga pada saham Apple, <br/>
>> dan tidak diberi notifikasi jika terdapat perubahan harga pada saham lainnya. <br/>
>> <br/>
>> <br/>
>> (4) Hasura Server : 
>> <br/>
>> Hasura Server listens (mendengarkan) setiap Perubahan pada Data yang di-Subscribes.
>> yang mana, Hasura Server akan diberi tahu jika terdapat perubahan pada data tersebut.
>> <br/>
>> <br/>
>> (5) Data Changes : <br/>
>> Hasura Server mendeteksi adanya perubahan pada Database, <br/>
>> kemudian Hasura Server bersiap untuk mengirimkkan Update mengenai Perubahan Data.
>>  <br/>
>>  <br/>
>> (6) Updates Sent :  <br/>
>> Hasura Server mengirim Update ke semua Connected Clients yang melakukan Subscribes ke Data tersebut.
>> <br/>
>> <br/>
>> (7) Notify Clients :  <br/>
>> Client menerima Update Data melalui WebSocket Connection mereka masing-masing
>> (Setiap Client mempunyai WebSocket Connection),  <br/>
>> untuk memastikkan Data mereka tetap Sinkron dengan Server secara Real-Time
>> <br/>
>>  <br/>
>> -> Summary Cara Kerja Subscriber di Hasura :  <br/>
>> (1) Client menjaga agar "WebSocket Connection" tetap aktif agar bisa menerima Update Perubahan Data secara Real-Time  <br/>
>> (2) Client mengirimkan "Subscription Query" untuk melakukan Subscribes ke Perubahan Data tertentu.  <br/>
>> (3) Hasura Server "Listens" (mendengarkan) setiap perubahan pada Data yang di-subscribes.  <br/>
>> (4) Hasura Server mendeteksi adanya perubahan pada Data.  <br/>
>> (5) Hasura Server mengirim perubahan data ke semua Client yang terhubung (Connected Clients) yang melakukan Subscribes ke Data tersebut.  <br/>
>> (6) Setiap Client menerima Update Perubahan Data melalui WebSocket Connection mereka masing-masing  <br/>
>>
>>  -------
>> {2} **WebSocket**
>>
>>  -> WebSocket merupakan "Communication Protocol" yang memungkinkan interaksi dua arah (two-way communication) yang berkelanjutan antara Client dan Server. <br/>
>> tidak seperti metode komunikasi tradisional (Traditional Communication Method) seperti HTTP, dimana Client harus berulang kali membuat Request untuk mendapatkan Update >> dari Server.
>>
>> -> WebSocket menyediakan cara untuk menjaga Connection tetap Open dan Aktif, <br/>
>> agar Data bisa mengalir bebas di kedua arah.
>>
>> -> Cara Kerja WebSocket :  <br/>
>> (How WebSocket works)
>>
>> (1) Initial Connection (Koneksi awal) : <br/>
>> Initial Connection dimulai dengan Client (seperti "Web Browser") yang membuat HTTP Request Standard ke Server. <br/>
>> Request meminta untuk meningkatkan Connection ke WebSocket, <br/>
>> yang mana jika Server mendukung WebSocket, maka Server setuju untuk meningkatkan Connection ke WebSocket, dan Connection didirikan.
>> <br/>
>> <br/>
>> (2) Full-Duplex Communication : <br/>
>> "Full-Duplex" sendiri memiliki arti yaitu Data dapat dikirim & diterima dalam dua arah secara serentak,<br/>
>> yang mana contohnya adalah Telephone Conversations (Percakapan Dua arah).<br/>
>> <br/>
>> (for your information, "Half-Duplex" sendiri berarti Data dapat dikirim dalam dua arah, tetapi tidak secara serentak, contohnya adalah Percakapan Walki-Talkie) <br/>
>> <br/>
>> Setelah "WebSocket Connection" didirikan, Client & Server dapat mengirim dan menerima Data kapan saja.<br/>
>> Dan Client tidak perlu terus meminta Server untuk Update (seperti dalam "Traditional HTTP" yang perlu terus meminta Server untuk Update). <br/>
>> <br/>
>> WebSocket Connection tetap terbuka hingga Client atau Server memutuskan untuk menutupnya.
>> <br/>
>> <br/>
>> (3) Real-Time Data Exchange : <br/>
>> Karena WebSocket memiliki Connection yang selalu terbuka (Open), <br/>
>> maka WebSocket ideal untuk Aplikasi Real-Time yang mengharuskan Data untuk dikirim atau diterima secara instant.<br/>
>> <br/>
>> Aplikasi Real-Time tersebut seperti Online Games, Chat Applications, Live Sports Updates, Stock Trading Platform, Collaborative Tools (seperti Google Doc).
>> <br/>
>> <br/>
>> -> Key Features of WebSocket :<br/>
>> (Fitur Utama WebSocket)<br/>
>> <br/>
>> (1) Persistence Connection :<br/>
>> WebSocket memiliki Koneksi yang tetap terbuka.<br/>
>> Koneksi WebSocket tetap terbuka hingga Client atau Server memutuskan untuk menutup Koneksi tersebut.<br/>
>> <br/>
>> (tidak seperti HTTP yang Koneksi ditutup setelah setiap kali Server mengirim Response.
>> Sehingga pada HTTP, Koneksi baru harus selalu dibuat setiap kali Client melakukan Request ke Server )  <br/>
>>  <br/>
>> (2) Low Latency :  <br/>
>> Latency dapat dikurangi karena tidak perlu membuka Koneksi baru berkali-kali untuk Data yang dikrimkan,  <br/>
>> sehingga Data Transfer (pengiriman data menjadi lebih cepat). <br/>
>> <br/>
>> (3) Two- Way Communication : <br/>
>> Client & Server dapat mengirim message ke satu sama lain, kapanpun tanpa menunggu. <br/>
>> <br/>
>> (4) Efficient : <br/>
>> Menggunakan lebih sedikit overhead data dibandingkan dengan HTTP Request, sehingga lebih cocok untuk transfer data real-time dan frekuensi tinggi.<br/>
>> (Overhead Data adalah Extra Information yang dikirim bersama dengan Actual Content)
>>
>> -> Comparison with HTTP :  <br/>
>> (Perbandingan/Perbedaan WebSocket dengan HTTP) : <br/>
>>  <br/>
>> HTTP : <br/>
>> pada HTTP, Client harus berulang kali meminta Update (disebut Polling),  <br/>
>> yang mana hal ini dapat menyebabkan Delay & tidak efektif pada Real-Time Data. <br/>
>>  <br/>
>> WebSocket : <br/>
>> Server dapat langsung mengirim ke Client setelah segera Data baru tersedia, tanpa perlu Client me-request nya. <br/>
>>  <br/>
>>  <br/>
>>  -> Workflow of WebSocket in Hasura :  <br/>
>> (Alur Kerja WebSocket di Hasura)
>>
>>  ![WebsSocket WorkFlow in Hasura drawio](https://github.com/user-attachments/assets/269d4d9f-3b27-4b47-9f44-8f5563a16ced)
>> <br/>
>>  Workflow WebSocket itu mirip dengan Workflow Subscription :
>> <br/>
>><br/>
>> (1) Client 1 & Client 2 : <br/>
>> Bagian ini mewakili dua User (Client) yang berbeda dari aplikasi kita yang ingin menerima Real-Time Updates.  <br/>
>> Masing-masing Clients mempunyai "WebSocket" Connection ke Hasura Server.
>> 
>> (2) WebSocket Connection :  <br/>
>> Setiap Client memelihara koneksi WebSocket (WebSocket Connection) yang memungkinkan mereka untuk menerima Update secara Real-Time.  <br/>
>> (Client perlu menjaga Koneksi pada WebSocket tetap aktif untuk bisa menerima Update secara Real-Time).
>> 
>> (3) Subscribe to "The Data Changes" :  <br/>
>> Clients (baik Client 1, maupun Client 2 pada gambar) melakukan Subscribes untuk Perubahan Data tertentu (Data Changes tertentu),  <br/>
>> yang mana hal ini dilakukan dengan mengirimkan "Subscription Query" (Query untuk minta Subscription) ke Server Hasura. <br/>  <br/>
>> yang dimaksud dengan "Client Subscribes to Spesific Data Changes", <br/>
>> itu berarti Client memberitahu Server untuk segera memberikan Notifikasi saat terjadi perubahan mengenai Data Spesifik tersebut. <br/>
>> Contoh :  <br/>
>> Kita Subscribes ke Tabel "StockPrices" (harga saham), tapi hanya untuk spesifik Data, yaitu Saham Apple. <br/>
>> maka kita hanya akan diberi notifikasi jika terdapat perubahan harga pada saham Apple, <br/>
>> dan tidak diberi notifikasi jika terdapat perubahan harga pada saham lainnya. <br/>
>> <br/>
>> <br/>
>> (4) Hasura Server : 
>> <br/>
>> Hasura Server listens (mendengarkan) setiap Perubahan pada Data yang di-Subscribes.
>> yang mana, Hasura Server akan diberi tahu jika terdapat perubahan pada data tersebut.
>> <br/>
>> <br/>
>> (5) Data Changes : <br/>
>> Hasura Server mendeteksi adanya perubahan pada Database, <br/>
>> kemudian Hasura Server bersiap untuk mengirimkkan Update mengenai Perubahan Data.
>>  <br/>
>>  <br/>
>> (6) Updates Sent :  <br/>
>> Hasura Server mengirim Update ke semua Connected Clients yang melakukan Subscribes ke Data tersebut.
>> <br/>
>> <br/>
>> (7) Notify Clients :  <br/>
>> Client menerima Update Data melalui WebSocket Connection mereka masing-masing
>> (Setiap Client mempunyai WebSocket Connection),  <br/>
>> untuk memastikkan Data mereka tetap Sinkron dengan Server secara Real-Time
>> <br/>
>>  <br/>
>> -> Summary Cara Kerja WebSocket di Hasura :  <br/>
>> (1) Client menjaga agar "WebSocket Connection" tetap aktif agar bisa menerima Update Perubahan Data secara Real-Time  <br/>
>> (2) Client mengirimkan "Subscription Query" untuk melakukan Subscribes ke Perubahan Data tertentu.  <br/>
>> (3) Hasura Server "Listens" (mendengarkan) setiap perubahan pada Data yang di-subscribes.  <br/>
>> (4) Hasura Server mendeteksi adanya perubahan pada Data.  <br/>
>> (5) Hasura Server mengirim perubahan data ke semua Client yang terhubung (Connected Clients) yang melakukan Subscribes ke Data tersebut.  <br/>
>> (6) Setiap Client menerima Update Perubahan Data melalui WebSocket Connection mereka masing-masing  <br/>
>> <br/>
>> <br/>
>>  -> WebSocket Server :  <br/>
>>  WebSocket Server merupakan System yang menangani WebSocket Connection yang masuk dari Client.  <br/>
>>  WebSocket Server mendengarkan (Listens) WebSocket Request yang baru, menerima Connections, kemudian mengelola Real-Time Communications antara Server dan Client.  <br/>
>>   <br/>
>>  -> Fungsi WebSocket Server : <br/>  <br/>
>>  (1) Accepts Connection :  <br/>
>>  Saat Client mengirim WebSocket Connection Request,  <br/>
>>  WebSocket Server menerima atau menolak WebSocket Connection Request.  <br/>
>>   <br/>
>>  (2) Manages Communication :  <br/>
>>  Setelah Connection berhasil didirikan, WebSocket Server mengelola komunikasi antara dirinya dengan Client yang terhubung.  <br/>
>>  WebSocket Server dapat mengirim Pesan ke Client, menerima Pesan dari Client, dan menyiarkan (broadcast) updates ke Multiple Clients secara bersamaan.  <br/>
>>   <br/>
>>  (3) Handles Multiple Clients :  <br/>
>>  Sebuah WebSocket Server dapat menangani Beberapa WebSocket Connection dalam waktu yang sama.  <br/>
>>  yang mana ini berarti, banyak Clients dapat terkoneksi ke WebSocket Server secara bersamaan (simultaneously) untuk menerima Real-Time Updates.  <br/>
>>  (Lebih dari satu Client dapat terhubung ke satu WebSocket Server secara bersamaan )  <br/>
>>
>> -------
>> {3} **Traditional HTTP Response** <br/>
>> <br/>
>> -> "Traditional HTTP Request" merupakan cara bagi Client (seperti Web Browser) untuk berkomunikasi dengan Server untuk meminta Data atau mengirim Informasi. <br/>
>> "Traditional HTTP Request" mengikuti "Request-Response Model" dimana Client mengirimkan sebuah Request dan Server mengirim kembali sebuah Reponse.  <br/>
>>  <br/>
>> -> There are two-key players "Traditional HTTP Request" :  <br/>
>>  (Dua pemain kunci pada "Traditional HTTP Request")
>>   <br/>
>>   <br/>
>> (1) Client : <br/>
>>  Biasanya Client berupa Web Browser atau App (Front-End Applications yang biasa dipakai oleh User), <br/>
>>  yang Client tersebut ingin mengambil Data (Fetch Data) atau mengirim informasi ke Server.  <br/>
>>   <br/>
>>  (2) Server : <br/>
>>  Server menyimpan Resources (seperti Web Pages, Images, atau Data)  <br/>
>>  dan juga Server memproses Client's Request.
>> <br/>
>>  <br/>
>> -> Cara Kerja "Traditional HTTP Request" :  <br/>
>>  <br/>
>> (1) Client Sends a Request :  <br/>
>> Clent mengirim "HTTP Request" ke Server.  <br/>
>> Request dapat berupa hal yang berbeda, seperti :  <br/>
>>  <br/>
>> GET :  <br/>
>> untuk meminta Data (seperti Loading halaman Web. image, ataU API Data).  <br/>
>>  <br/>
>> POST : <br/>
>> untuk mengirim Data ke Server (seperti Mengumpulkan Form).  <br/>
>>  <br/>
>> PUT :  <br/>
>> untuk meng-update Data.  <br/>
>>  <br/>
>> DELETE :  <br/>
>> untuk menghapus Data
>>  <br/>
>>  <br/>
>> (2) Server Receives The Request :  <br/>
>> Server memproses Request dan menentukkan Data atau Resource yang mana yang akan dikembalikan ke Client.  <br/>
>>  <br/>
>> (3) Server Sends a Response :  <br/>
>> Setelah memproses Request, Server mengirim kembali sebuah Response.  <br/>
>> yang mana Response tersebut mengandung :  <br/>
>> (Response yang dikirim bali oleh Server ke Client, mengandung hal berikut ini : )  <br/>
>>  <br/>
>>	 - Status Code :  <br/>
>> 	Status Code mengindikasikan apakah Request nya berhasil, atau apakah Request Error.  <br/>
>> 	Contoh Status Code jika Request berhasil = 200 OK , dan sebagainya.  <br/>
>> 	Contoh Status Code jika Request error = 404 Not Found , dan sebagainya.  <br/>
>> 
>>	 - Data :   <br/>
>> 	Jika Request tersebut untuk meminta Data (seperti WebPage atau API),  <br/>
>> 	maka Server mengirim kembali Informasi yang di-request.  <br/>
>>  <br/>
>> (4) Connection Closes :  <br/>
>> Koneksi ditutup setelah Server memberikkan Responds.  <br/>
>> Sehingga Client harus membuat Request baru jika memerlukkan lebih banyak data. <br/>
>> <br/>
>>  <br/>
>> -> One-Time Request and Response : <br/>
>>   <br/>
>>  Pada "Traditional HTTP Request", Communication nya adalah "One-Time" (satu kali),  <br/>
>>  yang berarti :  <br/>
>>  
>>  - Client meminta Data, Server memberikan Reponse, kemudian Communication selesai.  <br/>
>> 
>>  - Jika Client membutuhkan Lebih banyak Data atau Informasi ter-Update,  <br/>
>>  maka Client harus mengirim Request Baru.  <br/>
>>   <br/>
>>  Sebagai contoh :  <br/>
>>  Jika kita ingin membaca Article pada 'Halaman Web', maka Browser (Client) kita mengirim sebuah Request ke Server untuk meminta Halaman Web tersebut,  <br/>
>>  Dan Server memberi Response dengan mengirim Data mengenai Article pada Halaman web tersebut, Kemudian Connection tertutup.  <br/>
>>  Sehingga jika terdapat "Page Update", kita harus melakukan "Refresh" pada Halaman Web untuk mengirim Request Baru,  <br/>
>>  setelah itu, baru kita mendapatkan Halaman Web dengan informasi yang sudah diperbarui.  <br/>
>>  <br/>
>>  <br/>
>> -> Stateless Communication :  <br/>
>>  <br/>
>> HTTP Request bersifat "Stateless",  <br/>
>> yang berarti setiap Request bersifat "Independent" yang artinya Server tidak ingat 'Request Sebelumnya'.  <br/>
>> sebagai contoh :  <br/>
>> Jika kita memuat satu halaman Web, kemudian kita Clik link pada halaman Web tersebut untuk memuat halaman Web yang berbeda,  <br/>
>> Kedua Request untuk memuat Halaman Web tersebut ditangani secara terpisah.  <br/>
>> yang mana Server tidak melacak Riwayat penelusuran kita, kecuali menggunakan Mekanisme khusus seperti "Cookies".  <br/>
>>   <br/>
>> -> Advantages of Traditional HTTP Requests :   <br/>
>> (Kelebihan "Traditional HTTP Requests")   <br/>
>>   <br/>
>> (1) Simple & Efficient :   <br/>
>> Bekerja sangat baik untuk Simple Actions (Actions sederhana) seperti Memuat Halaman Web atau Submitting a Form.  <br/>
>>   <br/>
>> (2) Wide Compatibility :   <br/>
>> merupakan Backbone (tulang punggung) bagaimana Web bekerja,   <br/>
>> dan semua Web Browser & Server memahami HTTP.   <br/>  <br/>
>>
>> -> Limitations of Traditional HTTP Request :  <br/>
>> (Keterbatasan "Traditional HTTP Request")  <br/>
>> 
>> (1) No Real-Time Updates :  <br/>
>> Setelah Server memberikan Respnse, maka Connection ditutup. <br/>
>> Jika terdapat Perubahan Data, maka Client harus mengirim "Request Baru" untuk medapatkan Data terbaru. <br/>
>> yang mana hal ini dapat menjadi inefficient untuk Aplikasi Real-Time. <br/> <br/>
>>
>> (2) Polling Needed for Updates : <br/>
>> (dibutuhkan "Polling" untuk Updates) <br/>
>> <br/>
>> Pada HTTP, jika membutuhkan Real-Time Data, biasanya digunakan "Polling" untuk mengecek Perubahan Data. <br/>
>> tetapi "Polling" dapat menambah beban pada Server dan tidak efficient.<br/>
>> <br/>
>> Polling pada HTTP merupakan sebuah Method yang digunakan oleh Client (seperti Web Browser) untuk memeriksa Pembaruan Data di Server secara berkala. <br/>
>> Client mengirim request ke Server secara berkala untuk melihat apakah ada Data baru, jika ada, maka Server melakukan Respond dengan memberi Updated Information. <br/>
>> 
>> Polling dapat menambah Beban Server (Server Load) dan Menyebabkan Inefficiency (ketidak efisienan) karena Server tidak selalu mempunyai Data terbaru saat Polling >> >> >> dilakukan, sehingga Polling dapat membuang Resources (seperti Bandwith) secara  Mubazir. <br/>
>> <br/>
>> Polling juga bisa menyebabkan Latency, yakni dalam hal keterlambatan pengiriman Update Data, karena Client hanya mengecek Data terbaru pada Spesifik Interval (jangka >> >> waktu tertentu). Sehingga jika kita menetapkan Pengecekkan dilakukan setiap Interval waktu yang panjang, maka Data terbaru tersebut dapat terlambat sampai ke User. <br/>
>> <br/>
>> Untuk mengatasi hal tersebut, terdapat beberapa Alternative, diantaranya adalah : <br/> 
>> 
>> - Long Polling : <br/>
>> Client membuat sebuah Request dan Server menahan untuk belum memberikan Response terhadap Request tersebut sampai terdapat Data baru. <br/>
>> hal ini bertujuan untuk mengurangi jumlah Request yang tidak perlu. <br/> <br/>
>> 
>> - WebSockets : <br/>
>> Cara yang lebih efisien untuk menjaga Koneksi tetap terjalin antara Client & Server, <br/>
>> sehingga memungkinkan agar Data Terbaru dapat langsung dikirimkan secara instan, tanpa perlu membuat Request yang berulang. <br/> <br/>
>>
>> -> Contoh "Traditional HTTP Request" : <br/> <br/>
>> 
>> Misalnya kita membuka Halaman Web : <br/>
>> 
>> (1) Kita (Client) mengetikkan URL ke Browser (seperti www.xyz.com). <br/>
>> (2) Browser mengirimkan "HTTP GET Request" ke Server yang meng-hosting Website tersebut. <br/>
>> (3) Server memproses Request dan memberikan Response dengan mengirim WebPage Content yang diminta oleh Client. <br/>
>> (4) Browser menampilkan Halaman Web, dan Connection ditutup. <br/>
>> karena Connection ditutup, sehingga jika terdapat Perubahan (Update) pada Content Halaman Website, kita perlu Refresh Halaman Web untuk mendapatkan Update pada Content >> halaman Web tersebut. <br/>
>>
--------

# B. Subgraphs

 -> Subgraph merupakan semua Metadata yang dibutuhkan untuk bertindak sebagai Self-Contained Entity (Entitas Mandiri) yang dapat dibuat, dimiliki, dipelihara, dan dibangun secara independen oleh Team Individu, untuk kemudian menjadi bagian yang saling terhubung dari Unified API

-> untuk API Authors (penulis API), ini berarti kemampuan untuk membangun API yang terdiri dari berbagai Sumber dengan cara yang sederhana dan deklaratif.
kita dapat memanfaatkann aturan kontrol akses (access-control) yang unik, Mekanisme Autentikasi, dan Custom Business Logic dalam Subgraph kita untuk membuat API yang aman & tangguh.

-> Setiap Subgraph (pada contoh kami) adalah Modular Component dari "Data Supergraph", <br/>
komponen-komponen ini bekerja sama dengan aman untuk mengatasi hambatan tradisional yang ditimbulkan oleh Isolated Data Source (Sumber data yang terisolasi), memfasilitasi lapisan data yang lebih lancar dan saling terhubung (interconnected). <br/>
Pendekatan Integrasi ini menyederhanakan pengembangan Aplikasi antar System Data, 
memungkinkan Iterasi yang lebih cepat dan Maintenance yang lebih cepat oleh Team Engineer.

## 1. How Do I Build a Subgraph ?
## (Bagaimana cara membuat Subgraph)

-> Subgraph tersusun dari Data Source terkait, baik sebagai Traditional Database, atau sebagai Custome Business Logic.
Dan Subgraph terkoneksi (connected) ke Data Layer menggunakan Data Connector.

Hasura DDN (Data Delivery Network) menggunakan sejumlah Data Connector yang bekerja dengan Database, Services, dan API Out-of-the-box atau membuat sendiri.
("API Out-of-the-box" merupakan API yang sudah dibuat sebelumnya yang siap digunakan segera tanpa memerlukan Pengaturan (Setup) atau Penyesuaian (Customization) yang ekstensif).

Subgraph ini bahkan dapat menyertakan Custom Business Logic Anda sendiri sebagai fungsi TypeScript yang mengembalikan atau mengubah data secara langsung melalui GraphQL API Anda. Ini menghemat waktu dan tenaga Anda dalam membangun dan memelihara API Anda sendiri untuk mengelola Data Source dan Microservices yang ada.


-> Setelah menghubungkan Data Source , Anda kemudian dapat membuat metadata Anda menggunakan Hasura CLI dan ekstensi Hasura VS Code. Metadata ini kemudian dibangun pada Hasura DDN Instance Anda, yang digunakan untuk serve GraphQL API Anda.

## 2. Understanding Subgraph in GraphQL
## (GraphQL in General, not only Hasura)
(Hasura merupakan produk GraphQL, tetapi Produk GraphQL tidak hanya Hasura) <br/>
(Penjelasan Konsep Subgraph tidak banyak dijelaskan di Dokumentasi Hasura, sehingga kita perlu memahami konsep Subgraph pada GraphQL secara general)

>> penjelasan ini diluar Dokumentasi Hasura

- Pada GraphQL, Subgraph merupakan komponen yang digunakan untuk memecah dan mengatur Data Kompleks menjadi bagian-bagian yang lebih kecil dan mudah dikelola, yang bertujuan untuk memudahkan Query & memudahkan Data Retrieval (Pengambilan Data).

- Subgraph memainkan Peran Penting dalam membuat Data Modular, Distributed (terdistribusi), dan Scalable.

### 2.1) What is Subgraph in GraphQL

- Pada System GraphQL, "Subgraph" merupakan bagian yang lebih kecil dari GraphQL Schema yang lebih besar.

- Saat kita mempunyai System yang besar, daripada mempunyai Satu Schema yang besar dan Complex, kita dapat membaginya menjadi beberapa Subgraph yang lebih kecil.

>> ^For your information^  <br/>
>> {1} **GraphQL Schema** : <br/>
>> GraphQL Schema itu seperti Blueprint untuk GraphQL API, <br/>
>> yakni mendefinisikan Types of Data (jenis data) yang dapat anda gunakan, bagaimana berbagai Type of Data (berbagai Jenis Data) saling terkait antara satu sama lain, dan Operations yang dapat anda lakukan. <br/>
>> istilahnya, GraphQL Schema itu seperti Kontrak antara Client & Server yang memberitahu Client data apa yang dapat diminta oleh Client.

- Subgraph berfokus pada Domain atau Area tertentu. <br/>
misalnya, pada System E-Commerce, kita mungkin memiliki : <br/>
(1) Users Subgraph :<br/>
Subgraph ini mengelola User Information,<br/>
seperti Profiles, Addresses, dan Data Login <br/>
(2) Products Subgraph : <br/>
Menangani Product Listing (Daftar Produk), Product Category, dan Product Inventory.<br/>
(3) Orders Subgraph :<br/>
Menangani Order Creation (Pembuatan Pesanan), Order Tracking (Pelacakan Pesanan) , dan Order Payments (Pembayaran Pesanan).<br/>

 
 ### 2.2) Why user Subgraphs in GraphQL ?
### (Kenapa menggunakan Subgraph pada GraphQL ?) <br/>
<br/>
[1] Modular Structure : <br/>
Membagi Large System (Sistem yang besar) menjadi Subgraph membuatnya "Modular", yang mana ini berarti setiap Subgraph menangani area atau domain nya sendiri, yang mana hal ini Menyederhanakan keseluruhan arsitektur. <br/>

>> ^For your information^  <br/>
>> {1} **Modular** :
>>  <br/>
>> Modular merupakan pendekatan desain dimana System atau Software dibagi menjadi Komponen atau Modul yang terpisah.  <br/>
>> yang mana setiap Modul menjalankan fungsi tertentu dan dapat beroperasi secara independen, sehingga memungkinkan Update, Maintenance, dan Skalability.  <br/>
>> Modularity (modularitas) ini memungkinkan Developer untuk menambah atau mengganti Komponen tanpa mempengaruhi Seluruh System,  <br/>
>> sehingga hal ini dapat meningkatkan Fleksibilitas & Efisiensi dalan Software Development dan Software Architecture.  <br/>
<br/>
[2] Better Performance : <br/>
Setiap Subgraph hanya menangani bagian tertentu (specific part) dari System, <br/>
yang mana ini dapat meningkatkan Performance (kinerja) karena dengan Modularity kita hanya meng-query Data yang kita butuhkan, tanpa harus membebani tanpa harus membebani keseluruhan Skema.

>> ^For your information^  <br/>
>> {1} **How Modularization in Subgraph can increase performance in GraphQL**  <br/>
>> **(Bagaimana Modularization pada Subgraph dapat meningkatkan Performance pada GraphQL)**  <br/> 
>> 
>> ->  "Modularization" berarti memecah sesuatu menjadi bagian yang lebih kecil dan independen (atau bisa kita sebut Modul-Modul) 
>> yang dapat beroperasi secara terpisah. <br/>
>> Dalam konteks GraphQL, Subgraph adalah bagian-bagian yang lebih kecil ini, <br/>
>> yang mana masing-masing bagian ini bertanggung jawab untuk Area Fungsionalitas tertentu atau Data tertentu,  <br/>
>> yaitu seperti Users, Products, atau Orders.  <br/>
>>  <br/>
>>   -> Bagaimana Modularization meningkatkan Performance : <br/>
>> <br/>
>> (1) Focused Queries : <br/>
>> 
>> - Arti "Focused Queries" : <br/>
>> Saat Client (seperti WebApp) menginginkan Data, Client mengrimkan Request berupa Query, yang mana Query tersebut hanya berisi Relevant Subgraph (Subgraph yang berkaitan >> dengan Data yang kita minta). <br/>
>> Misalnya jika Client meminta data "User Details", maka Query tersebut hanya berisi Subgraph User.  <br/>  <br/>
>> 
>> -  Performance Benefit :  <br/>
>> cara "Focused Queries" dapat mengurangi jumlah Data yang Server harus Proses dan kembalikan.  <br/>
>> yang mana, Jumlah Data yang lebih sedikit, berarti Response yang lebih cepat.  <br/>
>>  <br/>
>> (2) Optimized Data Fetching :  <br/>
>>  <br/>
>> - Setiap Subgraph dapat Fetch Data (Mengambil Data) dengan cara yang paling efisien untuk Domain (area) tertentu.  <br/>
>> yang mana hal ini menghasilkan Data Retrieval (Pengambilan Data) yang lebih cepat, karena setiap Subgraph sudah mengetahui harus mengambil dimana datanya.  <br/>  <br/>
>> 
>> - Misalnya, terdapat Sebuah Database PostgreSQL yang menyimpan Data kita,  <br/>
>> dan kita mempunyai beberapa Subgraph yang dipisah-pisah, dan masing-masing mempunyai peran yang berbeda-beda.  <br/>
>> contoh, beberapa Subgraph yang kita punya adalah :  <br/>
>> (1) User Subgraph :  <br/>
>> berperan mengelola Data User  <br/>
>> (2) Order Subgraph :  <br/>
>> berperan mengelola Data Pesanan (Data Order)  <br/>
>> (3) Product Subgraph :  <br/>
>> berperan mengelola Data Product  <br/>
>>  <br/>
>> Karena setiap Subgraph sudah mempunyai peranannya masing-masing, sehingga setiap Subgraph sudah mengetahui dimana harus meng-akses data yang diperlukan.  <br/>
>> Sehingga hal ini dapat mempercepat pengambilan data (Faster Data Retrieval).  <br/>
>>  <br/>
>> Istilahnya, jika kita mempunyai "Rak Buku" dan kita sudah mengatur penempatan Kategori buku yang ada di Rak tersebut, maka jika kita mencari buku dapat jadi lebih cepat. >>  <br/>
>> Misalnya, pada Rak Buku, laci paling atas (Nomor 1) merupakan tempat kita menyimpan buku kategori "Anak-anak",  <br/>
>> dan pada laci nomor 2, merupakan tempat kita menyimpan buku kategori "Science-Fiction".  <br/>
>> Sehingga jika kita ingin mencari buku kategori anak-anak, kita sudah tahu harus mencari di laci nomor 1.  <br/>
>> (hal ini dapat menghemat waktu, karena kita tidak harus mencari di seluruh Laci pada Rak Buku).   <br/>
>>  <br/>
>> (3) Independent Scalling :  <br/>
>>  
>>  - Secara umum, Scalling berarti meningkatkan jumlah Resources (seperti Server, Aplikasi, atau Database) yang digunakan System sehingga bisa menangani Workload (beban kerja) atau Traffic.  <br/>
>> 
>> - Setiap Subgraph dapat dapat dilakukan Scalling secara Independen berdasarkan penggunaannya.  <br/>
>> yang mana,  jika Area tertentu mendapatkan banyak Traffic, maka Subgraph yang dikhususkan untuk area tersebut tanpa ditingkatkan (Scale-Up) tanpa mempengaruhi yang lain.<br/>
>> 
>> - Contoh Independent Scalling :  <br/>
>> Jika Area Order (Pesanan) mendapatkan Traffic yang tinggi, maka "Order Subgraph" (Subgraph Pesanan) dapat ditingkatkan (Scale-Up) tanpa mempengaruhi Subgraph yang lain.  >> <br/>
>>  <br/>
>> (4) Paralel Processing :  <br/>
>> 
>> - Saat Client mengirim Query yang memerlukkan Data dari "Multiple Subgraphs" (beberapa Subgraph), <br/>
>> Multiple Subgraph tersebut dapat memproses Request dalam waktu yang sama (secara Paralel). <br/>
>>  <br/>
>> (Paralel Processing = Beberapa Subgraph dapat memproses Request dalam waktu yang sama).  <br/>
>> 
>> - Performance Benefit :  <br/>
>> Paralel Processing mengurangi waktu yang dibutuhkan untuk mendapatkan Response karena Multiple Operations (beberapa operasi) dapat terjadi dalam waktu yang sama (Simultaneously).  <br/>
>> 
>> - Contoh nya :  <br/>
>> Jika Client  menginginkan "User Information" dan "Order History",  <br/>
>> maka "User Subgraph" & "Order Subgraph" dapat bekerja secara serentak (pada waktu yang sama),  <br/>
>> yang mana hal ini mempercepat Response secara keseluruhan.  <br/>
>>  <br/>
>> [5] Reduced Network Overhead :  <br/>
>> 
>> - Karena Clients hanya Request Data dari Subgraph yang diperlukan,   <br/>
>> sehingga lebih sedikit data yang dikirim melalui Jaringan.  <br/>
>> yang mana hal ini, dapat menghasilkan Load Time yang lebih cepat, dan mengurangi Pemakaian Bandwith.  <br/>
>> 
>> - Contoh :  <br/>
>> Jika User hanya membutuhkan "informasi User",  <br/>
>> maka pada Query, User hanya menulis "User Subgraph" (dan User tidak perlu menulis Subgraph untuk selain User ),  <br/>
>> sehingga kita dapat menghindari Data Transfer yang tidak perlu.  <br/>
>>
 <br/>
  <br/>
 [3] Easier Maintenance : <br/>

- Subgraph memungkinkan Team untuk bekerja pada bagian tertentu dari suatu System secara mandiri.  <br/>
Misalnya, suatu Team mengelola "User Subgraph", sementara Team yang lainnya mengelola "Order Subgraph".  <br/>
<br/>
Contoh :  <br/>
Pada sebuah Online Store yang besar, terdapat : <br/>
<br/>
(1) User Subgraph :  <br/>
dikelola oleh "Team A". <br/>
yang mana Team ini mengelola User SignUp, Login, dan Profile Updates. <br/>
<br/>
(2) Order Subgraph :  <br/>
dikelola oleh "Team B".  <br/>
yang mana Team ini mengelola Placing Orders, Payment Processing, dan Tracking Shipments.  <br/>
<br/>
Jika "Team A" ingin menambahkan fitur baru yang memungkinkan User untuk mengubah Email Address mereka.  <br/>
yang mana, "Team A" dapat melakukannya tanpa perlu berkoordinasi dengan "Team B".  <br/>
Begitu juga sebaliknya, "Team B" dapat menambahkan Payment Method tanpa perlu berkoordinasi dengan "Team A".  <br/>  <br/>
	
	
- Managing Changes (Mengelola Perubahan) merupakan hal penting dalam Maintenance.  <br/>
Mengelola Perubahan (manage changes) menjadi lebih mudah Karena Team bekerja pada Subgraph yang berbeda secara independen. <br/>
<br/>
Berikut ini bagaimana Subgraph memudahkan Maintenance : <br/>
	
(1) Less Complexity (berkurangnya kompleksitas) :  <br/>
Setiap Team hanya perlu memahami bagian Subgraph mereka, sehingga mempermudah penerapan perubahan. <br/>
<br/>
(2) Faster Updates (Update yang lebih cepat) : <br/>
Misalnya, saat "Team A" perlu meng-update "User Subgraph" (seperti menambahkan Fitur baru),  <br/>
"Team A" dapat melakukannya tanpa menunggu Team lain untuk menyelesaikan pekerjaannya pada Subgraph lain. <br/>
yang mana hal ini dapat mempercepat Development Process (Proses Pengembangan). <br/>
<br/>
	
(3) Isolated Issues : <br/>
"Isolated Issues" berarti jika terdapat masalah pada suatu Subgraph, masalah tersebut tidak langsung mempengaruhi Subgraph lainnya.  <br/>
Misalnya, jika terdapat masalah pada "Order Subgraph", maka masalah tersebut tidak langsung mempengaruhi "User Subgraph".  <br/>
(secara umum, Isolated memiliki arti yaitu System, Process, atau Component yang dipisahkan dari yang lain)  <br/>
<br/>
>> .
<br/>
[4] Federation : <br/>
Subgraph sangat berguna pada "Federated GraphQL Architecture". <br/>
Pada Federated System, Multiple Subgraph (beberapa Subgraph) bekerja sama dibawah 'Unified Schema'. <br/>

<br/>
<br/>
<br/>

### 2.3) How Do Subgraphs Work in GraphQL Federation ? 
### (Bagaimana Subgraph bekerja pada GraphQL Federation)

- pada GraphQL Federation, kita memiliki Multiple Subgraphs (beberapa Subgraph) yang bekerja bersama untuk membuat 'Unified API'. <br/>

>> ^For your information^ <br/>
>> **Unified API** : <br/>
>> "Unified API" menggabungkan API untuk semua layanan menjadi satu, yang mana berarti kita hanya perlu menggunakan Satu API untuk banyak layanan. <br/>
>> Daripada memiliki API terpisah untuk setiap layanan (seperti satu API untuk Sistem Pembayaran, Satu API lainnya untuk Social Media, dan Satu API lagi untuk Data Storage),<br/>
>> Unified API menggabungkan semua layanan tersebut menjadi satu. <br/>

- Subgraphs dihubungkan oleh "Gateway" yang bertindak sebagai "Middle Layer" (Lapisan Tengah). <br/>
Gateway menggabungkan  Semua Subgraph (banyak Subgraph) menjadi satu skema (Single Schema) yang dapat di-Query oleh Client. <br/>
<br/>
Gateway berfungsi seperti "Central Hub" atau "Entry Point" (titik masuk) yang menggabungkan Semua Subgraph menjadi satu. <br/> <br/>

- Begini Cara Kerjanya : <br/>
<br/>
(1) Subgraph Definition : <br/>
Setiap Subgraph mendefinisikan jenis (Type), Query, dan Mutasi nya sendiri. <br/>
Misalnya, "Product Subgraph" memiliki jenis seperti 'Produk', 'Category', dan 'Inventaris'. <br/>
dan juga "Payment Subgraph" memiliki Jenis yang berbeda dari "Product Subgraph". <br/>
Jenis pada "Payment Subgraph" diantaranya adalah 'Saldo uang' dan 'Payment Method'. <br/>
<br/>
(2) Reference Between Subgraphs : <br/>
Subgraph dapat mereferensikan Data dari Subgraph lainnya. <br/>
contohnya : <br/>
"Order Subgraph" dapat merujuk data 'Product Types' dari "Product Subgraph" untuk menyertakan Detail Product pada Order (Pesanan). <br/>
<br/>
(3) Gateway : <br/>
Gateway menggabungkan Semua Subgraph dan menangani Query dari Client. <br/>
Saat Client membuat Query, Gateway membagi Query (splits the query) dan membaginya ke Subgraph yang sesuai (appropriate Subgraph). <br/>
Response dari banyak Subgraph ini, kemudian digabungkan menjadi Satu Response (Single Response) untuk Client. <br/> <br/>



### 2.4) Example : How Do Subgraphs Work in GraphQL Federation   <br/>
### (Contoh : Cara Kerja Subgraph pada GraphQL Federation)  <br/>  <br/>

- Bayangkan kita mempunyai Tiga Subgraph :  <br/>

(1) Users Subgraph :  <br/>
mengelola 'User Profile' dan 'Login Information'.  <br/>
 <br/>
(2) Products Subgraph :  <br/>
mengelola 'Product Listings' dan 'Inventory'. <br/>
 <br/>
(3) Order Subgraph : <br/>
Mengelola 'User Order', termasuk 'Payment' dan 'Shipping Details'. <br/>  <br/>


- "Gateway" menyatukan Semua Subgraph menjadi Satu.  <br/>
sehingga Client dapat meng-Query banyak Subgraph dalam Satu Request.  <br/> <br/>

- Client's Query (Federated GraphQL) : <br/>
contoh Query yang ditulis oleh Client (User) untuk request Data :
	
	```
	query {
	  user(id: 123) {
	    id
	    name
	    orders {
	      id
	      total
	      products {
	        id
	        name
	        price
	      }
	    }
	  }
	}
	
	```
 
-> Query yang dituliskan User diatas, terdiri dari beberapa Subgraph,
yang kalau dijabarkan seperti ini :  <br/>  <br/>

(1) User Subgraph :  <br/>
Berikut ini adalah bagian Query yang berisikan "User Subgraph" 
```
user(id: 123) {
	id
	name
```
(123 merupakan "User's ID")
 <br/>
 
(2) Orders Subgraph :  <br/>
Berikut ini adalah bagian Query yang berisikan "Orders Subgraph"  
```
orders {
	id
	total
```

 <br/>  
 
(3) Products Subgraph :  <br/>
Berikut ini adalah bagian Query yang berisikan "Products Subgraph"  
```
products {
	id
	name
	price
	}
```

 <br/> 
  <br/> 
-> Cara kerjanya :  <br/> 
 <br/> 
(1) User's Data :
Gateway memberi Rute untuk Query 'id' & 'name' untuk pergi ke "User Subgraph" 

	
	user(id: 123) {
	    id
	    name

<br/> 
(2) Order Data : <br/>
Gateway memberi Rute untuk Query 'Bagian Order' untuk pergi ke "Order Subgraph" 

	orders {
		id
		total


(3) Product Data :  <br/>
Gateway memberi Rute pada Query 'Bagian Product' untuk pergi ke "Product Subgraph"

	products {
		id
		name
		price
		}


 <br/>
(4) Unified Response :  <br/>
Gateway menggabungkan Data dari Semua Subraph, dan mengembalikkannya sebagai "Single Response" (Satu Reponse atau bisa kita sebut "Unified Response"). <br/>
 <br/>
Contoh "Unified Response" adalah seperti dibawah ini.  <br/>
Dapat kita lihat bahwa pada Unified Response, semua data dari semua Subgraph digabungkan menjadi satu Response.  <br/>
Dan "Unified Response" inilah yang akan dikirimkan ke Client.

	{
	  "data": {
	    "user": {
	      "id": 123,
	      "name": "John Doe",
	      "orders": [
	        {
	          "id": 1,
	          "total": 100,
	          "products": [
	            {
	              "id": "p1",
	              "name": "Laptop",
	              "price": 1000
	            }
	          ]
	        }
	      ]
	    }
	  }
	}


 
### 2.5) Unified API
>> Penjelasan ini diluar Dokumentasi
  <br/>   <br/>

- API (Application Programming Interface) merupakan tools yang memungkinkan Aplikasi atau System yang berbeda untuk berkomunikasi antara satu sama lain. <br/>
  
- Bayangkan kita memiliki aplikasi cuaca (Weather App), dan kita ingin mendapatkan informasi cuaca terkini.  <br/>
Aplikasi itu sendiri tidak memiliki semua data cuaca,  aplikasi tersebut perlu memintanya dari server yang menyimpan data ini. <br/>
yang mana, API meminta informasi cuaca ke server dan mendapatkan respons.  <br/>

- "Unified API" menggabungkan API untuk semua layanan menjadi satu, yang mana berarti kita hanya perlu menggunakan Satu API untuk banyak layanan. <br/>
Daripada memiliki API terpisah untuk setiap layanan (seperti satu API untuk Sistem Pembayaran, Satu API lainnya untuk Social Media, dan Satu API lagi untuk Data Storage),
Unified API menggabungkan semua layanan tersebut menjadi satu. <br/> <br/>
  
- "Unified API" adalah 'Single API' (API tunggal) yang menyediakan 'Central Access Point' (titik pusat) ke berbagai Data Source (Sumber Data) atau ke berbagai Services (Layanan). <br/>
<br/>
- Daripada Software harus berinteraksi dengan 'banyak API berbeda secara individual', <br/>
"Unified API" menyatukan semua API tersebut, yang mana hal ini memungkinkan Client (seperti User atau Front-End Application) untuk mengakses semua Data & Services (Layanan) yang dibutuhkan melalui 'Satu API yang terpadu'. <br/> <br/>


- Key Characteristic 'Unified API' : <br/>
(Kareteristik Utama API) <br/>

(1) Single Access Point (titik akses pusat) : <br/>
Menyediakan sebuah 'Central Point' (titik pusat) untuk mengakses berbagai Layanan atau Sumber Data. <br/> <br/>

(2) Simplifies Integration : <br/>
Client hanya perlu berinteraksi dengan 'Satu API' untuk mengakses berbagai layanan atau Sumber Data, bukan beberapa API. <br/>

(3) Abstraction of Complexity : <br/>
Menyembunyikan Kompleksitas dari berbagai Data Source atau Services, sehingga memudah Client untuk mengambil Data tanpa mengetahui dari mana data tersebut berasal. <br/>

Istilahnya, pada sebuah Restaurant, 'API' itu merupakan Pelayan, 'Client' merupakan Pelanggan yang memesan makanan, dan 'Database & Services'itu seperti Dapur yang membuat makanan. <br/>
yang mana Pelayan berperan untuk mengantarkan makanan ke pelanggan, sehingga Pelanggan tidak perlu mengetahui Kompleksitas Dapur dan Pelanggan tidak perlu mengetahui dari mana makanan tersebut berasal. <br/> <br/>

- How Does "Unified API" work ? <br/>
(Bagaimana Cara kerja "Unified API" ) <br/>

-> "Unified API" berperan sebagai "Middle Layer" (Lapisan Tengah) yang berkomunikasi dengan beberapa "Back-end Services" atau "Database" atas nama Client. <br/>
("atas nama Client" maksudnya adalah "Unified API" mewakili Client untuk berkomunikasi dengan "Back-End Services" & Database, yang mana artinya "Permintaan untuk berkomunikasi" itu sebenernya merupakan Permintaan Client ). <br/>
<br/>
Saat Client membuat Request, "Unified API" meneruskannya ke Service terkait, <br/>
Kemudian "Unified API" mengumpulkan Response, dan mengirimkan "Response yang sudah digabungkan & disederhanakan" ke Client. <br/>

-> Here is a Basic Flow : <br/>
(Berikut ini Alur Kerja Dasarnya) <br/>

(1) Client (seperti WebApp) membuat Request ke "Unified API". <br/>

(2) "Unified API" meng-analisa Request yang dikirimkan oleh Client, <br/>
yakni dengan cara Mengidentifikasi Service atau Database mana yang diperlukan untuk memenuhi Request. <br/>

(3) "Unified API" mem-forward (meneruskan) Request ke Services yang sesuai (seperti User Data, Product Data, dan sebagainya ). <br/>

(4) Services mengirimkan Response (berupa Data) yang diminta ke "Unified API". <br/>

(5) "Unified API" menggabungkan & menyederhanakan Response yang didapatkan dari berbagai Services dan mengirimkannya Response tersebut ke Client. <br/>

>> ^For your information^  <br/>
>> **Cara Unified API "Menggabungkan & Menyederhanakan Reponse"** :  <br/>
>>
>> (1) Response berupa Data User :
>> ```
>> 		  "user": {
>> 		      "id": 123,
>> 		      "name": "John Doe",
>> ```
>>
>> (2) Response berupa Data Orders :
>> 	```
>> 		  "orders": [
>> 		        {
>> 		          "id": 1,
>> 		          "total": 100,
>> 		          "products": [
>>  ```
>>
>>  (3) Response berupa Data Products :
>> ```
>>  			"products": [
>>  		            {
>>  		              "id": "p1",
>>  		              "name": "Laptop",
>>  		              "price": 1000
>> ```
>>
>>  (4) Unified Response (Response setelah digabungkan & disederhanakan ) :
>> ```
>>  		 	{
>>  			  "data": {
>>  			    "user": {
>>  			      "id": 123,
>>  			      "name": "John Doe",
>>  			      "orders": [
>>  			        {
>>  			          "id": 1,
>>  			          "total": 100,
>>  			          "products": [
>>			            {
>>			              "id": "p1",
>>			              "name": "Laptop",
>>			              "price": 1000
>>			            }
>>			          ]
>>			        }
>>			      ]
>>			    }
>>			  }
>>			}
>> ```
>>
>> 

- Misalnya pada E-Commerce Platform, kita mempunyai Data dengan kategori "Users", "Orders", dan "Products". <br/>
Pada "Traditional API", kita perlu mempunyai API terpisah untuk masing-masing kategori data, <br/>
yaitu API : <br/>

(1) sebuah "User API" = untuk menangani User Data <br/>
(2) sebuah "Order API" = untuk menangani Order Data <br/>
(3) sebuah "Product API = untuk menangani Product Data <br/>

Pada "Traditional API", setiap API memiliki Endpoint Sendiri, yang mengharuskan Client untuk berinteraksi dengan masing-masing API secara individual. <br/>
(Jika pada Traditional API, kita membutuhkan tiga Endpoint). <br/>
<br/>
"Unified API" menyatukan Semua API Individual, <br/>
sehingga Client hanya berinteraksi dengan Satu Endpoint (Single Endpoint) daripada perlu berinteraksi dengan Tiga Endpoint. <br/>


- Contoh Query menggunakan "Unified API" :

-> Misalnya Client menulis Query untuk meminta Data mengenai "User", dan "Order" yang dipesan, serta informasi "Product" pada setiap Order.
(berarti Client meminta tiga data, yaitu "User", "Order", dan "Order").

Berikut ini contoh Query yang dikirimkan Client :
```
		{
		  "data": {
		    "user": {
		      "id": 1,
		      "name": "Jane Doe",
		      "orders": [
		        {
		          "id": 101,
		          "date": "2024-01-15",
		          "products": [
		            {
		              "id": 1001,
		              "name": "Laptop",
		              "price": 1200
		            },
		            {
		              "id": 1002,
		              "name": "Mouse",
		              "price": 25
		            }
		          ]
		        }
		      ]
		    }
		  }
		}

 ```

-> Bagaimana "Unified API" memproses Query : <br/>

(1) "Unified API" menerima Request Query dari Client dan melihat Client membutuhkan "User Data", "Order Data", dan "Product Data".  <br/>

(2) "Unified API" mengirim Request ke "User Service" , "Order Service", dan "Product Service".  <br/>

(3) Setiap Service me-response dengan mengirimkan datanya masing-masing :  <br/>
[-] "User Service" mengirim data mengenai "Detail User"  <br/>
[-] "Order Service" mengirim data mengenai "Riwayat Order" (Riwayat Pemesanan)  <br/>
[-] "Product Service" mengirim data mengenai  "informasi Produk"  <br/>

(4) "Unified API" menggabungkan data-data yang dikirim dari Semua Service menjadi Satu Response.
Berikut ini Response yang sudah digabungkan oleh "Unified API" :

		{
		  "data": {
		    "user": {
		      "id": 1,
		      "name": "Jane Doe",
		      "orders": [
		        {
		          "id": 101,
		          "date": "2024-01-15",
		          "products": [
		            {
		              "id": 1001,
		              "name": "Laptop",
		              "price": 1200
		            },
		            {
		              "id": 1002,
		              "name": "Mouse",
		              "price": 25
		            }
		          ]
		        }
		      ]
		    }
		  }
		}


### 2.6) Gateway in GraphQL  <br/>  <br/>
>> Penjelasan ini diluar Dokumentasi
>>

- Gateway (pada Federated GraphQL) bertindak sebagai "Central Hub" yang mengelola komunikasi antara Client dan Multiple Subgraphs.  <br/>
Gateway menangani Query yang masuk dari Client, kemudian Gateway mencari tahu Subgraph mana yang berisi Data yang diperlukan oleh Client,  <br/>
kemudian menggabungkan Semua Results yang dikirimkan oleh Semua Subgraph menjadi "Single Response" (Satu Response).  <br/>  <br/>


- How the Gateway Works - Step by Step : <br/>
(Cara Kerja Gateway - Step by Step) <br/>

(1) Client Sends a Query : <br/>
-> Client mengirim GraphQL Query, yang mana Query tersebut mungkin memerlukan Data dari beberapa tempat (Subgraph). <br/>
<br/>
contohnya jika Client membuat Query untuk mengambil Data mengenai "User" & "Order" (Order yang dipesan oleh User). <br/>
Data mengenai User, disimpan pada "User Subgraph". <br/>
Sedangkan Data mengenai Order, disimpan pada "Order Subgraph". <br/>

-> Contoh Query yang dikirimkan oleh Client : 

```
	query {
	  user(id: 123) {
	    id
	    name
	    orders {
	      id
	      total
	      products {
	        id
	        name
	      }
	    }
	  }
	}
```

Query diatas meminta : <br/>
[-] User Data : 
Query diatas meminta User Data berupa id, name.
yang mana ini didapatkan dari "User Subgraph"

	```
	 user(id: 123) {
		    id
		    name
	```

[-] Orders Data :
Query diatas meminta Orders Data berupa id, total.
yang mana ini didapatkan dari "Orders Subgraph"
```
	    orders {
	      id
	      total
```

[-] Products Data : 
Query diatas meminta Products Data berupa id, name.
yang mana ini didapatkan dari "Products Subgraph".
```
	      products {
	        id
	        name
	      }
```


<br/>
<br/>
(2) Gateway Splits The Query :  <br/>
(Gateway Membagi Query) <br/>
<br/>
Gateway membagi Query yang masuk berdasarkan Subgraph mana yang berisi Data yang diminta.<br/>
<br/>
Contoh pembagian Subgraph berdasarkan query yang dikirimkan oleh Client diatas : <br/>
[-] User Subgraph : <br/>
bertanggung jawab atas Data yang terkait dengan User (misalnya id, name). <br/>
[-] Orders Subgraph : <br/>
bertanggung jawab atas Data yang terkait dengan Orders (misalnya id, total).<br/>
[-] Products Subgraph : <br/>
bertanggung jawab atas Data yang terkait dengan Products (misalnya id, name). <br/>
<br/>
Gateway Memberi Rute (Mengarahkan) bagian Query ke Subgraph yang sesuai.<br/>
Berarti Data User diarahkan ke "User Subgraph", <br/>
Data Order diarahkan ke  "Order Subgraph", <br/>
Data Products diarahkan ke "Products Subgraph". <br/> 
<br/>
<br/>

(3) Subgraph Process Their Part oF Query :  <br/>
(Subgraph memproses bagian Query mereka) <br/>
<br/>
Setiap Subgraph menerima bagian Query yang relevant bagi mereka : <br/>
[-] "User Subgraph" menerima permintaan Query untuk Data User (id, name). <br/>
[-] "Order Subgraph"  menerima permintaan Query untuk Data Order (id, total). <br/>
[-] "Product Subgraph"  menerima permintaan Query untuk Data Product (id, name). <br/>
<br/>
Setiap Subgraph memproses bagian Query secara independen, <br/>
yakni masing-masing Subgraph mengambil Data dari Data Source (seperti Database atau Service). <br/>

>> ^For your information^ <br/>
>> "Services" & "Database", keduanya dapat bertindak sebagai 'Data Source'.
>> 
 <br/>
 <br/>
(4) Subgraphs Return Their Responses to The Gateway :  <br/>
(Subgraph mengirimkan Response ke Gateway)  <br/>
 <br/>
Setelah memproses, Subgraph mengirimkan Response (berupa Data) ke Gateway.  <br/>
misalnya :  <br/>
[-] "User Subgraph" mengirim Response berupa Data 'id' dan 'name' dari user.  <br/>
[-] "Order Subgraph" mengirim Response berupa Data 'id' dan 'total' dari Order(pesanan).  <br/>
[-] "Product Subgraph" mengirim Response berupa Data 'id' dan 'name' dari Product.  <br/>

>> ^For your information^ <br/>
>> Semua Subgraph tersebut dapat mengambil Data dari Data Source yang sama atau Data Source yang berbeda. <br/>
>> (Misalnya "User Subgraph", "Order Subgraph", dan "Product Subgraph" mengambil Data dari Database yang sama, <br/>
>>  atau pada Skenario lain, Subgraph tersebut mengambil Data dari beberapa Database yang berbeda). <br/>

<br/>
<br/>
[5] Gateway Combines The Response : <br/>
Setelah Gateway menerima banyak Response dari masing-masing Subgraph, <br/>
Gateway menggabungkan berbagai Response tersebut menjadi "Single Response" (Satu Response). <br/>
<br/>
Pada contoh ini, Gateway mengambil Data yang dikirimkan oleh "User Subgraph", "Order Subgraph", "Product Subgraph" dan menggabungkannya menjadi satu. <br/>
<br/>
<br/>

[6] Gateway Sends The Final Response to The Client :  <br/>
(Gateway mengirim Response akhir ke Client) <br/>

Setelah menggabungkan Response dari berbagai Subgraph (berupa Data), Gateway mengirim "Response Lengkap" ke Client. <br/>

Berikut ini contoh "Unified Response" yang dikirim ke Client : <br/>

```
	{
	  "data": {
	    "user": {
	      "id": 123,
	      "name": "John Doe",
	      "orders": [
	        {
	          "id": 1,
	          "total": 150,
	          "products": [
	            {
	              "id": "p1",
	              "name": "Laptop"
	            },
	            {
	              "id": "p2",
	              "name": "Mouse"
	            }
	          ]
	        }
	      ]
	    }
	  }
	}

```

### 2.6) Federation Architecture in GraphQL  <br/>  <br/>
>> Penjelasan ini diluar Dokumentasi


- Federation Architecture adalah cara mengatur GraphQL API yang besar dengan memecahnya menjadi Service yang lebih kecil dan terfokus, dimana Semua Service tersebut dapat bekerja sama sebagai "Unified API" (API terpadu). <br/>
yang mana dengan memecahnya menjadi beberapa Service yang lebih kecil, dapat memudahkan berbagai Team yang berbeda untuk membangun & memelihara bagian-bagian terpisah dari sebuah GraphQL API yang besar,  <br/>
sehingga lebih mudah untuk dikelola & diskalakan. (easier to manage & Scalable)  <br/> 
Banyak Service yang lebih kecil tersebut merupakan Subgraph, dan Sistem menggabungkan Semua Subgraph menjadi "Unified API".  <br/>
>> ^For your information^  <br/>
>> Subgraph dapat dianggap sebagai Service karena meng-ekspos (memaparkan) Data melalui GraphQL Queries,  <br/>
>> yang memungkinkan Client untuk mengakses hanya Relevant Data yang dibutuhkan.  <br/>  <br/>
 <br/>
 <br/>


-  **Why Use Federation in GraphQL** :  <br/>
(Mengapa menggunakan Federation pada GraphQL)  <br/>

-> Misalnya terdapat suatu perusahaan besar, dan pada perusahaan tersebut terdapat berbagai Team yang menangani berbagai bagian berbeda, seperti 'Team A' menangani bagian User Account, 'Team B' menangani bagian Product, dan 'Team C' menangani Order. <br/>
Tanda Federation Architecture (tanpa memecah GraphQL API menjadi banyak Service yang lebih kecil), <br/>
maka hal ini dapat mengakibatkan : <br/>
[-] Complexity : <br/>
Sulit untuk mengelola atau meng-update satu skema yang besar. <br/> 

[-] Conflict : <br/>
Team mungkin secara tidak sengaja menganggu pekerjaan satu sama lain. <br/>

[-] Bottlenecks :  <br/>
Setiap perubahan kecil dapat memerlukan Update Penuh untuk keseluruhan Skema. <br/> <br/>


 "GraphQL Federation" mengatasi masalah ini dengan mengizinkan setiap tim untuk bekerja secara independen pada **subgraph** tertentu, kemudian sistem menggabungkan semua subgraph menjadi satu Unified API. <br/>

>> ^For your information^ <br/>
>> Secara umum, "Federation Architecture" merupakan Design Approach yang memungkinkan beberapa System atau beberapa Service yang independen untuk bekerja bersama sebagai satu kesatuan yang utuh. <br/> <br/>

- Key Components of GraphQL Federation : <br/>
(Komponen Utama pada GraphQL Federation) <br/>

Federation Architecture pada GraphQL, melibatkan Tiga Komponen Utama, <br/>
yaitu : "Subgraph", "Gateway", dan "Supergraph". <br/>

Berikut ini Pejelasannya : <br/>

[1] **Subgraph** : <br/>
Subgraph merupakan bagian-bagian kecil dari GraphQL API yang lebih kecil dan terfokus yang menangani Satu Area tertentu. <br/>

Contoh Subgraph : <br/>

[-] Users Subgraph : <br/>
Subgraph ini mengelola Data User, seperti User Information, <br/>
User Profiles, User Addresses, dan Data Login <br/>

[-] Products Subgraph : <br/>
Menangani Data Product, seperti Product Listing (Daftar Produk), Product Category, dan Product Inventory. <br/>

[-] Orders Subgraph : <br/>
Menangani Data Order, seperti Order Creation (Pembuatan Pesanan), Order Tracking (Pelacakan Pesanan) , dan Order Payments (Pembayaran Pesanan). <br/>
<br/>

Setiap subgraph dikelola dan diperbarui secara independen oleh tim yang bertanggung jawab atas Subgraph tersebut.

>> . <br/>


[2] **Gateway** : <br/>
<br/>
Gateway merupakan Komponen Khusus yang berada diantara Client dan Subgraph. <br/>

>> ^For your Information^ <br/>
>> "Client" itu seperti Front-End Application yang digunakan oleh User. <br/> 

Tugas Gateway adalah : <br/>
(1) Merge : <br/>
Menggabungkan semua Subgraph menjadi Satu Skema besar yang disebut Supergraph. <br/>
(2) Route Queries :<br/>
Mengarahkan atau memberi Rute pada Query ke Subgraph yang mana,  <br/>
yakni saat Gateway mengetahui Subgraph apa saja yang dibutuhkan oleh Query. <br/>
(3) Combine Response : <br/>
Gateway menarik data dari berbagai Subgraph, menggabungkan Data tersebut, dan Gateway mengirimkan Data yang sudah digabungkan tersebut ke Client. <br/>

>> .  <br/>


[3] **Supergraph** : <br/>
Supergraph adalah Schema Unified GraphQL, yang mana Client berinteraksi dengan Supergraph.  <br/>
Supergraph merupakan hasil dari penggabungan Semua Subgraph melalui Gateway.  <br/>
 <br/>
Bagi Client, Supergraph tampak seperti GraphQL API tunggal yang lengkap,  <br/>
walaupun GraphQL API tersebut dibangun dari beberapa bagian.   <br/>


>> .  <br/>
>> .  <br/>
>> .  <br/>

- **How GraphQL Federation Works - Step by Step** :  <br/>
(Cara Kerja GraphQL Federation)   <br/>
 <br/>
Contoh sederhana tentang cara kerja Federation GraphQL :  <br/>
 <br/>
Misalnya kita mempunyai Aplikasi E-Commerce dengan beberapa Subgraph berikut :  <br/>
[-] User Subgraph :  <br/>
Mengelola User Profile & Account Information.  <br/>
[-] Product Subgraph :  <br/>
Mengelola Product Listings & Details.  <br/>
[-] Order Subgraph :   <br/>
Mengelola Order yang dipesan oleh Customer.  <br/>

 <br/>
-> Misalnya Client ingin mengambil Data (Fetch Data) mengenai informasi User dan informasi Order yang telah mereka buat, dengan detail tentang setiap produk dalam pesanan. Query yang Client buat untuk Request Data mungkin terlihat seperti ini:  <br/>



```
	{
	  user(id: "1") {
	    name
	    orders {
	      date
	      product {
	        name
	        price
	      }
	    }
	  }
	}

```

 <br/>
-> Berikut ini cara Gateaway memproses Request dari Client :  <br/>

(1) Identify Subgraphs :  <br/>
(meng-identifikasi Subgraph)  <br/>
Gateway menganalisa Query dan menentukkan Subgraph mana yang bertanggung jawab untuk setiap bagian data.  <br/>
analisa nya seperti dibawah ini :   <br/>

[-] User Subgraph :  <br/>
informasi untuk `user(id: "1")` menjadi tanggung jawab "User Subgraph."  <br/>

	
	user(id: "1") {
	    name

 
<br/>
[-] Order Subgraph :  <br/>
informasi untuk `date` menjadi tanggung jawab "Order Subgraph"  <br/>

	
	 orders {
	      date

 
<br/>
[-] Product Subgraph :  <br/>
informasi untuk `name` & `price` menjadi tanggung jawab "Product Subgraph"  <br/>

	 product {
	        name
	        price



<br/>
(2) Fetch Data from Each Subraph : <br/>
(Mengambil Data dari Setiap Subgraph) <br/>
Gateway mengirim permintaan untuk mengambil Data ke setiap Subgraph berdasarkan tanggung jawab masing-masing Subgraph. <br/>
seperti berikut ini : <br/>
[-] Gateway meminta ke "User Subgraph" mengenai Informasi mengenai User. <br/>
[-] Gateway meminta ke "Order Subgraph" mengenai Informasi mengenai Order. <br/>
[-] Gateway meminta ke "Product Subgraph" mengenai Informasi mengenai Order. <br/>

 <br/>
  <br/>
(3) Combine The Response :  <br/>
(Menggabungkan Response)  <br/>
Gateway mengumpulkan Data dari semua Subgraph dan menggabungkannya untuk membuat "Unified Respons" (satu response terpadu).   <br/>
  <br/>

(4) Return The Response to The Client :  <br/>
Gateway mengirim "Unified Response" ke Client  <br/>

---------
# C. Supergraph

>> ini dari Dokumentasi

<br/>
Data Supergraph adalah Framework yang menyatukan semua Subgraph Anda ke dalam satu API yang aman. <br/>
Orkestrasi ini memungkinkan pembuatan aplikasi  yang mencakup berbagai Data Source, Services , Third-Party API,
Business Logic, dan — yang terpenting — Team, yang menjembatani kompleksitas mereka 
dengan mulus ke dalam satu lapisan. <br/>

<br/>
Bagi mereka yang bertanggung jawab untuk memelihara Data Layer, <br/>
ini berarti Anda sekarang memiliki satu Holistic API untuk dikelola,  <br/>
bukan beberapa sumber data dan koneksi yang berbeda.<br/>
 Ini memungkinkan Anda untuk membuat CI/CD Pipelines, <br/>
memantau kinerja menggunakan industry-standard Observability tools, <br/>
dan mengelola Access Control dengan cara yang lebih efisien. <br/>

<br/>
Bagi konsumen Anda, ini berarti mereka memiliki Single Endpoint (satu endpoint)untuk mengakses semua data yang mereka butuhkan, <br/>
sehingga mengurangi kompleksitas aplikasi mereka. <br/>
Ini juga memungkinkan mereka untuk fokus membangun User Experience sebaik mungkin, <br/>
daripada bertikai (wrangling) dengan Data Layer yang mendasarinya.


## 1. Understanding Supergraph for GraphQL in General
>> Penjelasan ini diluar Dokumentasi

- Pada GraphQL, Supergraph merupakan "Single & Unified Schema" yang menggabungkan beberapa Subgraph menjadi Satu API. <br/>
  
- Istilahnya, Supergraph sebagai 'Sebuah Payung Besar' yang menutupi 'Beberapa Payung Kecil', yang mana Payung Kecil tersebut adalah "Subgraph".

### 1.1) What is a Supergraph ?

- Supergraph mengandung Subgraph dan Gateway. <br/>
Dengan kata lain, Subgraph & Gateway merupakan bagian dari Supergraph. <br/>

- Supergraph berinteraksi dengan Client. <br/>
Supergraph menggabungkan beberapa Subgraph menjadi "Satu Schema yang lebih besar". <br/>
Dengan ini, Supergraph menyediakan "Satu API" ke Client, walaupun Supergraph menarik Data dari beberapa Sumber (Source). <br/>

### 1.2) Why use a Supergraph ? <br/>

- Tanpa Supergraph, menggabungkan Data dari Domain yang berbeda akan menjadi tantangan karena setiap Team perlu mengkoordinasikan setiap perubahan kecil di seluruh API. <br/>

- Supergraph memungkinkan kita untuk : <br/>

(1) Unify API from Different Services : <br/>
menyatukan API dari berbagai Service (Layanan), sehingga Client tidak perlu tahu dari mana Data berasal. <br/>

(2)  Scale API Development : <br/>
Mengskalakan API Development di berbagai Team atau Services. <br/>

(3) Ensure API Flexibility : <br/>
Memastikkan Fleksibilitas API dengan memungkinkan Team untuk menambah Services baru atau meng-update Schema tanpa mempengaruhi keseluruhan API. <br/>

### 1.3) How The Supergraph Works with Subgraph and a Gateway ?  <br/>
(Bagaimana Supergraph bekerja dengan Subgraph dan Gateway)  <br/>
 <br/>
Berikut ini cara kerja "Supergraph" pada "GraphQL Federated System" :  <br/>

(1) Subgraph :   <br/>
Setiap Team mengelola sebuah Subgraph.  <br/>
yang mana Setiap Subgraph mengelola satu area tertentu.  <br/>

(2) Gateway :  <br/>
Gateway merupakan Komponen yang menggabungkan Semua Subgraph menjadi Supergraph.  <br/>
yang mana Gateway mengelola Routing (memberi Rute / memberi arah) dan mengelola Data Retrieval dari berbagai Subgraph dan menyediakan Skema 'Unified Supergraph' ke Client.  <br/>

(3) Supergraph Schema :  <br/>
Supergraph merupakan Schema yang terbuat dari Semua Subgraph.  <br/>

## 2. Understanding Supergraph for GraphQL in Hasura <br/>

- Pada Hasura, Supergraph merupakan "Unified GraphQL API" yang menggabungkan Data dari berbagai Sumber (seperti Database, Remote GraphQL Services, REST API, dan sebagainya) menjadi Satu API yang komprehensif yang Client dapat berinteraksi dengan lancar. <br/>
yang mana konsep ini berguna untuk Aplikasi Besar yang berbagai bagian data dikelola secara terpisah (seperti berbagai Database atau Service dikelola secara terpisah). <br/>

### 2.1) How Hasura Builds a Supergraph ?

- Hasura membangun Supergraph dengan menggunakan Features seperti "Remote Schemas" & "Actions".
Berikut ini Penjelasannya :

#### [1] Remote Schemas :
Kita dapat menghubungkan External GraphQL Services (layanan GraphQL Eksternal) ke Hasura sebagai Remote Schemas.
Setiap Remote Schema mewakili Area tertentu (misalnya, User Information, Payment Data) yang ingin kita tambahkan pada Skema Utama Hasura (Hasura's Main Schema).

>> ^For your information^ <br/>
>> ### {1} **Remote Schemas** <br/>
>>  - Pada GraphQL, "Remote Schemas" memungkinkan kita untuk menggabungkan "Beberapa GraphQL API" menjadi "Satu Unified API". <br/>
>> ini berarti bahwa meskipun Data & Service kita tersebar di berbagai Server atau Database yang berbeda, kita dapat menghubungkannya Dibawah "Satu GraphQL Endpoint", <br/>
>> Sehingga dapat memudahkan Client untuk mengakses semua data yang dibutuhkan tanpa perlu mengelola Multiple Endpoints (tanpa perlu mengelola Lebih dari Satu Endpoint). <br/>
>> (Dengan Remote Schemas, kita dapat menggunakan 'Satu Endpoint' untuk 'Multiple Services', sehingga Client tidak perlu tahu Data datang dari Service yang mana.)
>>  - Remote Schema adalah 'External GraphQL API' yang berada di luar ' Server GraphQL utama' kita. <br/>
>> (ini maksudnya "External GraphQL API" di-hosting pada Server yang berbeda dengan 'Server Utama GraphQL' kita) <br/>
>>
>> - Remote Schema adalah "GraphQL API" yang berada di luar "GraphQL Server atau Service Utama Kita", <br/>
>> contohnya :  <br/>
>>  [-] sebuah "User Service" mengelola Data User dengan 'GraphQL API nya' sendiri. <br/>
>>  [-] sebuah "Product Service" mengelola Data Product dengan 'GraphQL API nya' sendiri. <br/>
>>  [-] sebuah "Order Service"  mengelola Data Order dengan 'GraphQL API nya' sendiri. <br/>
>> <br/>
>> Karena Service untuk User, Product, dan Order memiliki GraphQL API yang berada di Luar GraphQL API Utama kita,  <br/>
>> maka jika kita ingin meng-akses Data untuk User, Product, Order dari 'Satu GraphQL Endpoint', kita bisa menggunakan "Remote Schemas" untuk menggabungkan banyak API ini. <br/> <br/> <br/>
>>
>> ### 1.1) Cara Kerja "Remote Schemas" pada GraphQL Federation :  <br/>
>> 
>> - Pada 'GraphQL Federation', Remote Schemas memugkinkan kita untuk menambah beberapa 'GraphQL API yang terpisah' ke sebuah 'GraphQL Server Utama'. <br/>
>> GraphQL Server Utama' ini menggabungkan beberapa Skema berbeda menjadi 'Satu Unified Schemas', <br/>
>> sehingga Client dapat meng-Query Data antar Service (layanan) dengan lancar. <br/>
>>
>> Misalnya : <br/>
>> [-] "User Service" & "Product Service" merupakan 'External GraphQL API', <br/>
>> sehingga saat Client meminta 'User Data' & 'Product Data' dalam sebuah Query yang sama, <br/>
>> 'Main GraphQL Server' (GraphQL Server Utama) meneruskan masing-masing bagian Query ke Service yang terkait <br/>
>> (Query yang meminta Data User dikrimkan ke 'User Service', dan Query yang meminta Data Product dikrimkan ke 'Product Service'), <br/>
>> kemudian Main GraphQL Server menggabungkan Result dari masing-masing Service.  <br/>
>> <br/>
>>
>> [-] Client menerima 'Satu Response' seolah-olah mereka meminta dari 'Satu GraphQL API', padahal Data bersumber dari Sumber yang berbeda. <br/>  <br/>
>>
>> ### 1.2) How Remote Schemas are used in Hasura ?  <br/>
>> ### (Bagaimana Remote Schemas digunakan di Hasura)  <br/>
>> - Remote Schemas memungkinkan kita untuk mengintegrasikan "External Service" dengan Hasura.  <br/>  <br/>
>>
>> ### 1.3) How Remote Schemas Compare to REST API ?  <br/>
>> ### (Bagaimana "Remote Schemas" dibandingkan dengan "REST API")   <br/>
>> 
>> - Dengan "REST API", kita perlu membuat 'Request Terpisah' untuk Endpoint yang berbeda untuk bisa mendapatkan Data User & Data Product,  <br/>
>> kemudian menggabungkan Result pada Cient Side.  <br/>
>> 
>> - Sedangkan dengan "Remote Schema" di GraphQL, kita hanya perlu melakukan Satu Request (dalam sebuah query yang sama) untuk bisa mendapatkan Data User & Data Product.  <br/>
>> 
>> (yang dimaksud dengan "Data Product" & "Data User" pada contoh ini, yaitu "User Service" & "User Product" merupakan 'External Service', yang merupakan Service yang berada di luar Hasura).  <br/>
>>
>> 
>> ----
>> <br/>
>>
>> ### {2} **REST API** : <br/>
>> ### (REST API in general)** <br/>
>>
>>  #### 2.1) Dengan "REST API", kita perlu membuat 'Request Terpisah' untuk Endpoint yang berbeda untuk bisa mendapatkan Data. <br/> 
>> #### ( Hal ini berbeda dengan Remote Schemas ) <br/>
>>
>> - Dengan REST API, setiap jenis data biasanya memiliki 'Endpoint nya sendiri'.  <br/>
>> misalnya, kita ingin mengambil Data mengenai "User" dan "Product"  <br/>
>> (seperti Data User, dan Data Product yang dibeli oleh User tersebut).  <br/>
>>  <br/>
>> Pada kasus ini, Data mengenai User & Product, berasal "bukan dari External Service."  <br/> 
>> <br/>
>> Jika kita ingin meminta Data untuk User & Product, kita harus membuat Dua "Request yang terpisah" ke Dua Endpoint yang berbeda, yaitu Endpoint User & Endpoint Product. <br/>
>> (jika kita ingin meminta Tiga jenis data berbeda, misalnya Data User, Product, dan Order, maka kita perlu membuat Tiga Request yang terpisah ke Tiga Endpoint yang berbeda, yaitu 'Endpoint User', 'Endpoint Product', dan 'Endpoint Order'). <br/>  
>>  <br/>
>> Berikut ini contohnya :  <br/> 
>> 
>> (1) untuk mengambil "Data User" :  <br/>
>> 	```
>> 	GET/users/{userId}
>> 	```
>> -> "/users" merupakan Endpoint untuk User <br/>
>> -> {userId} merupakan Id yang menunjukkan User mana yang ingin kita ambil datanya  <br/>  <br/>
>> 
>> (2) untuk mengambil "Data Product" (seperti Product yang dibeli oleh User) :   <br/>
>> 	
>> 		GET/users/{userId}/products
>>  
>>   
>> -> "/products" merupakan Endpoint untuk Product  <br/>
>> -> "/user/{userId}" menunjukkan User mana yang Data Product nya ingin kita ambil <br/>
>> <br/>
>> -> Cara kerja Request diatas - Step by Step :  <br/>
>> (1) Client membuat Request ke Endpoint berbeda : <br/>
>> [-] Pertama-tama, Client mengrimkan Request ke "User Endpoint" untuk mendapatkan "Informasi User", seperti User Name, User Email, dan User Address. <br/>
>> [-] Kemudian, Client mengirimkan Request kedua ke "Products Endpoint" untuk mendapatkan informasi Products yang berhubungan dengan User, seperti Product apa saja yang dibeli User. <br/>
>> <br/>
>> (2) Client menunggu setiap Response : <br/>
>> [-] untuk setiap Request, Client harus menunggu Server untuk memberikan Response berupa Data. <br/>
>> [-] Pada Slow Network (jaringan yang lambat), Pengiriman Response dari Server ini bisa memakan waktu, terutama jika melibatkan banyak Endpoint. <br/>
>>
>>  >> ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ <br/>
>>  >> ^^For your information^^ <br/>
>>  >> <1> **Bagaimana Cara Server & Endpoint bekerja sama pada REST API** <br/>
>>  >> 	<br/>
>>  >> -> REST API merupakan cara berbagai Software atau System yang berbeda untuk berkomunikasi melalui internet <br/>
>>  >> dengan menggunakan Metode 'Standard HTTP Methods' (seperti GET, POST, PUT, DELETE). <br/>
>>  >> <br/>
>>  >> -> Server merupakan sebuah Device atau System yang menyediakan Resources, Data, atau Services ke Systema atau Computer lain (seperti Client) melalui Network (jaringan).<br/>
>>  >> Pada konteks REST API, Server meng-hosting API dan Server memproses Request dari Clients. <br/>
>>  >> ("Hosts" atau "meng-hosting" berarti menyediakan Resources untuk Sytem lainnya)<br/>
>>  >> (Pada kalimat diatas "Server meng-hosting API" artinya API disimpan didalam Server (API is Stored inside the Server))<br/>
>>  >> <br/>
>>  >> -> Endpoint merupakan sebuah Spesifik URL (Uniform Resource Locator) di Server yang mewakili Resource tertentu. <br/>
>>  >> masing-masing Endpoint sesuai dengan Function atau Bagian Data tertentu pada API. <br/>  <br/>  <br/>
>>  >>
>>  >> -> Pada REST API, Endpoint merupakan Spesifik URL yang menentukan dimana Client dapat meng-akses Resources tertentu. <br/>
>>  >> contoh Spesifik URL adalah "/users" <br/> <br/>
>>  >>
>>  >> -> Cara kerja bagaimana "Endpoint" & "Server" berkerja sama :  <br/>
>>  >>  <br/>
>>  >> (1) Client membuat Request :  <br/>
>>  >> Saat Kita menggunakan 'Web Page' atau Aplikasi, "hal tersebut membutuhkan Informasi dari Server."  <br/>
>>  >> Misalnya jika kita ingin melihat informasi daftar User (berarti kita ingin melihat Data User), maka Client mengirim sebuah Request ke sebuat Spesifik Endpoint.  <br/>
>>  >> (seperti  `https://api.example.com/users`  <br/>
>>  >> , yang mana Endpoint tersebut adalah "/users")  <br/>
>>  >> (Pada REST API, dalam sebuah Request hanya bisa berisi permintaan ke Satu Endpoint.  <br/>
>>  >> yang mana ini berarti jika Client ingin mengirim permintaan ke Dua Endpoint, maka Client perlu membuat 'Dua Request terpisah' (two separate requests)).  <br/>
>>  >> <br/>
>>  >> 
>>  >> (2) Server menerima & memproses Request : <br/>
>>  >> Server mengecek Request apa yang diminta. <br/>
>>  >> Dan Server mungkin perlu berinteraksi dengan Database. <br/>
>>  >> Untuk sebuah Request GET ke Endpoint '/users', Endpoint tersebut bertindak sebagai "Entry Point" untuk Request ini. <br/>
>>  >> <br/>
>>  >> Saat Server menerima Request, Server memutuskan cara me-respond Request yang masuk berdasarkan URL(Endpoint) yang ditentukan dalam Request tersebut. <br/>
>>  >> Jika Request nya adalah "GET/users" berarti URL(Endpoint) pada Request tersebut adalah "/users" yang berarti Server mengarahkan (memberi Rute atau Routing) pengambilan datanya ke "Endpoint Users". <br/>
>>  >> <br/>
>>  >> Server menangani Request yang masuk dengan mengarahkan Request tersebut ke "Endpoint Handler" yang tepat, <br/>
>>  >> kemudian "Endpoint Handler" yang berinteraksi dengan Database untuk mengambil Data. <br/>
>>  >> ("Endpoint Handler" merupakan Function atau bagiah Code yang bertanggung jawab untuk memproses Request ke Endpoint tertentu dalam Web Apllication atau API). <br/>
>>  >> 
>>  >> 		 	just info,
>>  >> 			Contoh Routing Logic pada Javascript : 
>>  >> 			
>>  >> 			app.get('/users', getUsers);
>>  >> 			[-] GET request ke Endpoint "/users", memicu (trigger) untuk menjalankan "getUsers" function.
>>  >> 			
>>  >> 			app.post('/users', createUsers);
>>  >> 			[-] POST request ke Endpoint "/users" memicu (trigger) untuk menjalankan "createUsers" function.
>>  >> 	
>>  >> 
>>  >> (3) Server mengirim Response : <br/>
>>  >> Server mengirim Data ke Client beserta dengan Status Code (seperti 200 untuk OK, 404 untuk Not Found, dan sebagainya). <br/><br/>
>>  >> 
>>  >> (4) Client menerima Response : <br/>
>>  >> Client menerima Response dan dapat menampilkan Data. <br/>
>>  >> 
>>  >> ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ ^^ <br/>
>> <br/>
>> (3) Client Combines Data: <br/>
>> (Client menggabungkan Data) <br/>
>> [-] Setelah menerima beberapa Response (berupa Data) dari kedua Endpoint, <br/>
>> Client menggabungkan Data dari berbagai Response menjadi satu. <br/> <br/> <br/>
>> 
>> 
>>  #### 2.2) The Inefficiency in REST API. <br/>
>> #### (Ketidakefisienan pada REST API) <br/> <br/>
>> [1] Multiple Request : <br/>
>> -> Maksud dari "Multiple Request" : <br/>
>> [-] Pada REST API, setiap jenis data biasanya diakses dari Endpoint (URL) yang berbeda. <br/>
>> Misalnya jika kita ingin request "Data User", "Data Orders", dan "Data Wishlist". <br/>
>> karena kita meminta 3 jenis data berbeda yaitu data User, Order, dan Whistlist, <br/>
>> maka kita perlu mengakses ke Tiga Endpoint berbeda, yaitu : <br/>
>> (1) Endpoint "/user" <br/>
>> (2) Endpoint "/orders" <br/>
>> (3) Endpoint "/whishlist" <br/>
>> Pada REST API, satu Request hanya bisa meng-akses ke Satu Endpoint, <br/>
>> yang berarti Satu Request hanya bisa meminta Satu Jenis Data. <br/>
>> Sehingga jika kita ingin meminta lebih dari satu jenis data, berarti kita harus Membuat "Lebih dari satu Request". <br/>
>> <br/>
>> [-] Sedangkan pada GraphQLAPI menggunakan "Single Endpoint" yaitu "/graphql" untuk semua jenis data. <br/>  <br/>
>> 
>> -> Pada REST API, Client harus membuat lebih dari satu Request (Multiple Request) untuk mendapatkan semua data yang dibutuhkan.  <br/>
>> Setelah setiap request, Client harus menunggu Server untuk me-respond request yang pertama, sebelum Client dapat menerima Respond untuk Request yang setelahnya.  <br/>
>> yang mana proses ini menambah Waktu dan Kompleksitas, sehingga dapat menyebabkan aplikasi terasa lebih lambat karena memproses Request secara berurutan.  <br/>
>>  <br/>
>>  <br/>
>> [2] Network Latency :  <br/>
>> -> Setiap kali Client membuat Request ke Server, ada waktu yang dibutuhkan untuk memproses Request tersebut,  <br/>
>> yang mana hal ini disebut Network Latency.  <br/>
>> Jika Client harus melakukan Multiple Request untuk mendapatkan data yang dibutuhkan, hal ini dapat menambah Network Latency.  <br/>
>> Sehingga dengan banyaknya Request dapat memperlambat aplikasi, apalagi jika terdapat Koneksi internet yang lambat  <br/>
>> atau Aplikasi membutuhkan Data dari berbagai sumber (Multiple Sources).  <br/>
>>  <br/>
>> Aplikasi membutuhkan data dari berbagai sumber, dapat meningkatkan Network Latency, bukan hanya di REST API, tetapi juga di GraphQL,  <br/>
>> karena terdapat "Round Trip Time" (RTT) yaitu waktu yang dibutuhkan Request untuk melakukan perjalanan dari Client ke Server dan kembali lagi ke Client.  <br/>
>> Pada GraphQL, walaupun hanya membutuhkan Satu Request, tetapi Request tersebut butuh menarik data dari berbagai Data Source, sehingga menambah waktu perjalanan data >> >> (Round Trip Time).  <br/>
>> Pada REST API, dibutuhkan Multiple Request untuk mengambil data dari berbagai sumber data (Multiple Data Sources), sehingga hal ini dapat menambah Waktu Perjalanan Data >> (Round Trip Time) serta menambah Waktu tunggu untuk memproses Multiple Request secara berurutan.  <br/>
>>  <br/>
>> <br/>
>> [3] Data Overfetching :  <br/>
>> (Pengambilan Data Berlebih)  <br/>
>> -> Pada REST API, setaip Endpoint menngrimkan Response berupa "Fixed of Data" (Data yang sudah tetap),  <br/>
>> Misalnya kita Request data mengenai User, tetapi hanya ingin melihat informasi 'Nama User' & 'Email User',  <br/>
>> tetapi Data yang diterima Client adalah semua Informasi mengenai User, yaitu Nama, umur, alamat, email, dan Nomor Telfon.  <br/>
>> inilah yang dimaksud dengan "Fixed Data" yaitu data yang dikirimkan adalah keseluruhan informasi, walaupun Kita hanya membutuhkan sebagian informasi.  >> <br/>
>>  <br/>
>> Karena Data yang dikirimkan berlebih daripada yang dibutuhkan, sehingga Ukuran Data menjadi berlebih,  <br/>
>> yang mana hal ini dapat membuat Resource Bandwith terbuang secara mubazir.  <br/>
>> (Bandwith merupakan Kapasitas maksimum jaringan untuk mentrasmisikan data).  <br/>  <br/>
>>  <br/>
>>  <br/>
>>  <br/>
>> #### 2.2) Architecture of REST API <br/>  <br/>
>> 
>> #### A) REST API Workflow Overview :  <br/>
>> #### (Gambaran Alur Kerja REST API)  <br/>   <br/>
>> 
>> (1} Client :  <br/>
>> Client itu merupakan Front-End Application yang membuat Request.  <br/>
>> (Client itu seperti Orang yang meminta informasi)  <br/>
>> Contoh Client itu seperti Web Browser yang dipakai oleh User untuk membuat Request.  <br/>
>>  <br/>
>> [2] Server :  <br/>
>> Server merupakan tempat penyimpanan Data & Resources.  <br/>
>> Saat Client meminta Data, Server lah yang mengambil data dari Database dan mengirim Data tersebut ke Client.  <br/>
>>   <br/>
>> [3] Endpoints :  <br/>
>> -> Endpoint merupakan Spesifik Address (URL) yang menentukkan dimana Data tertentu dapat diakses pada Server.  <br/>
>>  <br/>
>> -> Setiap Endpoint berhubungan dengan Data yang berbeda,  <br/>
>> mirip seperti bagian-bagian dalam perpustakaan yang menyimpan kategori buku yang berbeda,  <br/>
>> begitu juga dengan Endpoint, masing-masing Endpoint berhubungan dengan kategori data yang berbeda,  <br/>
>> misalnya suatu Endpoint memiliki kategori data User, dan Endpoint yang satunya memiliki kategori data Order.  <br/>
>>  <br/>
>> -> Contoh Endpoint dengan analogi Library (Perpustakaan) :  <br/>
>> Bayangkan sebuah Library yang kita bisa menemukan berbagai macam kategori buku,  <br/>
>> seperti contoh berikut ini :  <br/>
>>  <br/>
>> [-] Fiction Section :  <br/>
>> Pada Library, Section ini berisi buku dengan "Kategori Fiction", seperti Novel & buku cerita lainnya.  <br/>
>>  <br/>
>> Pada konteks REST API, Section ini merupakan Endpoint dengan kategori Fiction,  <br/>
>> yang mana menujukkan Spesifik Address dimana Data Buku dengan Kategori Fiction dapat kita temukan.  <br/>
>>  <br/>
>> Contoh Endpoint untuk kategori Fiction :  <br/>
>> ```
>> https://api.library.com/books/fiction
>> ```
>> yang mana Endpoint ini merupakan Spesific Address (Alamat Khusus) tempat kita dapat menemukan Data Buku dengan Kategori Fiction.  <br/>  
>> <br/>
>> [-] Non-Fiction Section :   <br/>
>> Pada Library, Section ini berisi buku dengan "Kategori Non-Fiction", seperti Buku Biografi, Buku Sejarah, dan Buku Self-improvement.  <br/>
>> <br/>
>> Pada konteks REST API, Section ini merupakan Endpoint dengan kategori Non-Fiction, <br/>
>> yang mana menujukkan Spesifik Address dimana Data Buku dengan Kategori Non-Fiction dapat kita temukan. <br/>
>> <br/>
>> Contoh Endpoint untuk kategori Non-Fiction : <br/>
>>  ```
>>  https://api.library.com/books/non-fiction
>>  ```
>> yang mana Endpoint ini merupakan Spesific Address (Alamat Khusus) tempat kita dapat menemukan Data Buku dengan Kategori Non-Fiction. <br/>
>>  <br/>
>> [4] HTTP Methods :  <br/>
>> -> REST API menggunakan "HTTP metods" seperti "GET", "POST", "PUT", dan "DELETE" untuk menentukkan tindakan yang perlu diambil pada setiap Endpoint. <br/>
>> Maksudnya "untuk menentukkan tindakan yang perlu diambil pada setiap Endpoint" adalah bahwa HTTP Methods ini menentukkan jenis operasi yang ingin 
>>  dilakukan Client pada Data Source. <br/>
>> <br/>
>> -> Berikut ini penjelasan "HTTP Methods" dan Jenis Operasi yang dilakukan : <br/>
>> (1) GET = untuk Mengambil Data <br/>
>> (tidak ada data yang  dimodifikasi karena hanya mengambil Data) <br/>
>> (2) POST : untuk membuat Data Baru. <br/>
>> (3) PUT = untuk meng-update Data <br/>
>> (4) DELETE = untuk menghapus Data <br/> <br/> <br/>
>>
>> #### B) High-Level Workflow of of REST API :  <br/> <br/>
>> #### (Langkah-langkah secara Ringkas Cara Kerja REST API)
>> [1] Client makes a Request : <br/>
>> (Client membuat Request) <br/>
>> -> Client mengirim sebuah "HTTP Request" ke Server. <br/>
>> <br/>
>> [2] Server Processes The Request : <br/>
>> (Server memproses Request) <br/>
>> -> Server menerima Request, <br/>
>> Dan Server mengecek tindakan apa yang perlu dilakukan (seperti Mengambil Data. Meng-update Data, atau Menghapus Data), <br/>
>> Kemudian Server melakukan tindakan sesuai yang diminta oleh Request tersebut (seperti Mengambil Data pada Database, atau meng-update Data pada Database,  <br/>atau Menghapus Data pada Database). <br/>
>> <br/>
>> [3] Server Sends a Response : <br/>
>> (Server mengirim Response) <br/>
>> -> Server mengirim Data yang di-Request oleh Client. <br/>
>> <br/>
>> [4] Client Receives Response : <br/>
>> (Client menerima Response) <br/>
>> -> Client menerima Response (berupa Data) <br/>
>>  <br/>  <br/>
>> 
>> #### C) Detailed Steps in REST API Workflow :   <br/>
>> #### (Langkah-langkah Detail Cara Kerja REST API )  <br/>  <br/>
>> 
>> 
>> Mari kita bahas Detail Langkah Cara Kerja REST API menggunakan Contoh Case saat Mobile App melakukan Request untuk mendapatkan Informasi.  <br/>
>>  <br/>
>> [1] Step 1 : Client Sends a Request :  <br/>
>> (Client mengirimkan Request)  <br/>
>> -> Misalnya Client membutuhkan Data, seperti "User Information" (berarti Client ingin mengambil Data User).  <br/>
>>  <br/>
>> -> Kemudian Client mengirimkan "HTTP Request" ke Spesifik Endpoint pada Server.  <br/>
>> karena Data yang ingin diambil adalah Data User, maka HTTP Request dikirimkan ke "Endpoint User".  <br/>
>> Misalnya Endpoint User adalah  `https://api.example.com/users/123`  <br/>
>> ( `https://api.example.com/users/123` merupakan spesifik address yang menunjukkan Dimana Data User Dapat diaskes pada Server)  <br/>
>>  <br/>
>> -> untuk Request, sebagai contoh kita gunakan HTTP Method "GET" untuk mengambil Data.  <br/>
>> Contoh Request dengan HTTP METHOD "GET" : 
>>	 ```
>>	 GET https://api.example.com/users/123
>>	 ```
>> 
>> -> Request dari Client ini juga mengandung "Headers" (seperti 'Authorization Tokens') dan "Parameters" (seperti Filtering atau Sorting).  <br/>
>>
>> >> ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^ <br/> 
>> >> ^For your information^  <br/>
>> >> ### {1} URL vs HTTP Request : Identify the difference and how to Read them.  <br/>
>> >> ### (URL vs HTTP Request : Kenali Perbedaannya dan Pahami Cara Membacanya)  <br/>    <br/>
>> >>
>> >> #### [1] URL : <br/>
>> >> **`https://api.example.com/users/123`** 
>> >> <br/>
>> >> ini merupakan URL yang memberikkan Spesific Address untuk Lokasi Data pada Server. <br/>
>> >> <br/>
>> >> Misalnya :  <br/>
>> >> [-] **`https://api.example.com/users`** <br/>
>> >> URL tersebut menunjukkan Spesific Address atau Lokasi tempat Data User disimpan pada Server. <br/>
>> >> Karena pada URL tersebut terdapat Endpoint "/users" , sehingga URL tersebut menunjukkan Spesific Address untuk Data User. <br/>
>> >> <br/>
>> >> [-] **`https://api.example.com/users/123`** <br/>
>> >> "/123" merupakan ID yang ingin dicari. <br/>
>> >> Kalau pada konteks keseluruhan URL diadtas, berarti URL tersebut menujukkan Spesifik Address untuk Data User dengan ID 123. <br/>
>> >> <br/>
>> >> <br/>
>> >> -> URL Explanation : <br/>
>> >>(1) **`https://`** <br/>
>> >> [-] ini merupakan "Protocol" yang digunakan untuk meng-akses Data. <br/>
>> >> <br/>
>> >>  [-] Protocol merupakan seperangkat aturan (Set of Rules) yang memberi tahu Cara Data harus dikirim melalui Internet antara Device kita dan Server. >> >> <br/>
>> >> <br/>
>> >> [-] "https://" merupakan kepanjangan dari "HyperText Transfer Protocol Secure". <br/>
>> >> HTTPS itu mirip dengan HTTP, perbedaannya adalah HTTPS ditambahkan Security (HTTPS kepanjangan dari "HTTP Secure"). <br/>
>> >> yang mana Pada HTTPS, Data yang dkirimkan di-enkripsi menggunakan "SSL"(Secure Socket Layer) atau "TLS" (Transport Layer Security). <br/>
>> >> <br/>
>> >> "SSL" dan "TLS" keduanya merupakan Cryptographic Protocol yang digunakan untuk mengamankan Komunikasi pada Jaringan Komputer, <br/>
>> >> yang mana SSL dan TLS biasanya dgunakan untuk meng-Enkripsi Data yang dipertukarkan antara Client dan Server. <br/>
>> >> <br/>
>> >> Tanpa Enkripsi di HTTPS, Data yang dikrimkan berupa "Plain Text", yang berarti siapaun yang Menyadap Komunikasi (Intercept The Communication) dapat >> >> dengan mudah membaca dan memngubah (alter) informasi tersebut. <br/>
>> >> Penyadapan Komunikasi ini seperti "Man-in-The-Middle Attack". <br/>
>> >> Pada "Man-in-the-Middle Attack", Hacker menyadap komunikasi diantara Dua Pihak, yaitu Client (seperti Web Browser) dam Server, penyadapan ini tanpa >> >> diketahui Salah satu pihak. <br/>
>> >> Setelah Hacker mempunyai akses ke Komunikasi, Hacker tersebut dapat melakukan monitor & modifikasi pada Data yang sedang dikirimkan. <br/>
>> >> yang mana Hacker dapat Membaca Sensitive Information ( seperti Password & nomor kartu kredit ) <br/>
>> >> atau Hacker dapat mengubah Data (seperti mengubah Jumlah Transaksi pada E-Banking) <br/>
>> >> <br/>
>> >> <br/>
>> >> (2) `api.example.com`  <br/>
>> >> ini merupakan Domain (alamat) yang menunjukkan dimana Data disimpan  <br/>
>> >>  <br/>
>> >> (3)  `/users/123`  <br/>
>> >> merupakan Path ke Data tertentu.  <br/>
>> >> "/users" ini menunujukkan ke "Endpoint User", yang berarti Kita menginginkan Data User.  <br/>
>> >> "/123" ini menunjukkan Path ke Data User yang lebih spesifik , yang berarti Kita menginginkan Data User yang memiliki "ID 123"  <br/>  <br/> <br/>
>> >>  
>> >>  #### [2] HTTP Request : <br/>
>> >>  `GET https://api.example.com/users/123` <br/> 
>> >>
>> >> ini merupapakan HTTP Request. <br/>
>> >> HTTP Request diatas mengatakan "Saya ingin mengambil Data dari URL ini". <br/>
>> >> yang mana HTTP Request diatas berisi request "GET", yang berarti saya ingin mengambil data. <br/>
>> >> <br/>
>> >> [-] `GET` <br/>
>> >> GET merupakan HTTP Method yang digunakan untuk mengambil data dari sebuah server. <br/>
>> >> <br/>
>> >> [-] `https://api.example.com/users/123` <br/> 
>> >> ini merupakan URL yang menunjukkan Lokasi mengenai dimana Data yang mau kita ambil. <br/> <br/> <br/>
>> >> 
>> >> ### {2} Header & Parameter in HTTP Request :   <br/> <br/>
>> >> 
>> >> -> Pada HTTP Request, "Header" dan "Parameter" merupakan informasi tambahan yang dikirim bersama Request untuk membantu Server memahami cara >> >>  menangani Request. <br/> <br/>
>> >> 
>> >> ### A) HTTP Header <br/>
>> >> -> "HTTP Header" atau yang biasa disebut "Header". <br/>
>> >> -> "HTTP Header" merupakan bagian kecil dari Metadata atau Informasi yang dikirim bersama dengan "HTTP Request" atau "HTTP Response". <br/>
>> >> -> Header tidak selalu mandatory (diwajibkan) pada setiap Request, tetapi Header sangan sering dikirimkan bersama Request, bahkan keberadaan Header >> >> sangat penting pada Request. <br/> 
>> >> ("Metadata" disini berisi informasi yang memberi instruksi kepada Server atau Client mengenai cara memproses atau meng-handle Data) <br/> 
>> >> <br/>
>> >> -> Contoh HTTP Header :  <br/>
>> >>  (1) Authorization Header : <br/>
>> >> -> Authorization merupakan Header yang paling saat menangani dengan Private Data atau Secure Data. <br/>
>> >> <br/>
>> >> -> "Authorization Header" mengandung Token (seperti Special Code) yang sering diberikan saat kita LogIn, <br/>
>> >> yang mana Token memberitahu Server bahwa "User diperbolehkan untuk meng-akses data." <br/>
>> >> <br/>
>> >> -> Contoh "Authorization Header" : <br/>
>> >> 
>> >>   ```
>> >>      Authorization: Bearer abcdef12345
>> >>   ```
>> >> Pada contoh diatas, "Bearer abcdef12345" merupakan Token yang membantu Server meng-identifikasi apakah kita adalah Authorized User (User yang berwenang). <br/> <br/>
>> >> 
>> >> (2) Content-Type Header :  <br/>
>> >> -> ini memberi tahu Server mengenai Format Data yang dikirim oleh Request. <br/>
>> >> Format Data tersebut seperti JSON, XML, dan lain sebagainya. <br/>
>> >> <br/>
>> >> Contoh : 
>> >>   ```
>> >>      Content-Type: application/json
>> >>    ``` 
>> >> Code diatas memberitahu Server bahwa Client mengrim data dalam bentuk JSON dan Data tersebut perlu di-interpretasikan dalam bentuk JSON. <br/> <br/>
>> >> 
>> >> -> `Content-Type` memberitahu Server Format Data yang Client kirimkan. <br/>
>> >> `Content-Type` tidak memberitahu secara terang-terangan kalau Client menginginkan Server mengirimkan Response Data ke Client dalam format JSON, <br/>
>> >> tetapi Client memberitahu Server secara tersirat bahwa Client menginginkan Response data dikirimkan dalam bentuk JSON. <br/>
>> >> <br/>
>> >> -> Jika Client ingin secara terang-terangan memberitahu bahwa Client menginginkan untuk menerima Response Data dari Server dalam format JSON, <br/>
>> >> Client dapat menggunakan code 'Accept' . <br/>
>> >> contoh : <br/>
>> >> `Accept: application/json`
>> >> <br/>
>> >>  <br/>
>> >> (3) User-Agent Header : <br/>
>> >> -> ini memberitahu Server mengenai Browser atau Operating System yang meelakukan Request. <br/>
>> >> <br/>
>> >> -> Contoh : <br/>
>> >>  
>> >> ```
>> >>      User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)
>> >> ```
>> >> 
>> >> [-] `User-Agent` <br/>
>> >> merupakan identifikasi mengenai Identitas Client, yang mana biasanya mengandung infomasi mengenai Browser atau Operating System yang digunakan Client untuk membuat Request. <br/>
>> >> <br/>
>> >> [-] `Mozilla/5.0` <br/>
>> >> ini memberitahu bahwa Client menggunakan Browser "Mozilla" dengan versi "5.0" <br/>
>> >> <br/>
>> >> [-] `(Windows NT 10.0; Win64; x64)` <br/>
>> >> - "Windows NT 10.0" memiliki arti bahwa Client menggunakan Operating System Windows 10. <br/>
>> >> dan "NT" tersebut memiliki kepanjangan 'New Technology' <br/>
>> >> -"Win64" memiliki arti bahwa Operating System tersebut memiliki '64-bit version of Windows' (Windows Versi 64 bit). <br/>
>> >> - `x64` memiliki arti bahwa "Arsitektur CPU adalah 64-bit" (CPU Architecture is 64-bit)  <br/>
>> >> <br/>
>> >> <br/>
>> >>
>> >> ### B) HTTP Parameter <br/>
>> >> <br/>
>> >> -> Parameter itu seperti Extra Details yang ditambahkan ke URL untuk memberitahu Server secara lebih spesifik Data apa yang kita inginkan. <br/>
>> >> <br/>
>> >> -> Terdapat 2 jenis utama Parameter, yaitu "Query Parameters" & "Path Parameters" <br/> <br/> 
>> >> 
>> >> #### [1] Query Parameters : 
>> >> -> Query Parameter ditambahkan "pada akhir URL". <br/>
>> >> yang mana Query Parameter berada setelah "?" (tanda tanya), <br/>
>> >> kemudian menuliskan "Key Value Pair". <br/>
>> >> <br/>
>> >> -> Jika lebih dari satu Key Value Pair, kita perlu manuliskan "&" sebagai pemisah diantara masing-masing Key Value Pair. <br/>
>> >> Tetapi jika terdapat hanya satu Key Value Pair, kita tidak perlu memakai "&". <br/>
>> >> <br/>
>> >> [-] Format penulisan Query Parameter dengan "Single Key Value Pair" (Satu Key Value Pair) : <br/> 
>> >> 	
>> >>		 https://example.com/page?key=value
>> >> 
>> >> 
>> >> [-]  Format penulisan Query Parameter dengan "Multiple Key Value Pair" (Beberapa Key Value Pair) : 
>> >> ```
>> >> https://example.com/page?key1=value1&key2=value2
>> >> ```
>> >> 
>> >> [-] Contoh Request dengan Query Parameter :
>> >> 	```
>> >> 	GET https://api.example.com/products?category=shoes&sort=price
>> >> 	```
>> >> (1) Pada Request diatas, yang merupakan Query Parameter adalah : 
>> >> 	```
>> >> 	?category=shoes&sort=price
>> >>	 ```
>> >> 
>> >> (2) `category=shoes` <br/>
>> >> ini merupakan "Key Value Pair", yang mana : <br/>
>> >> - Key = `category` <br/>
>> >> - Value = `shoes` <br/>
>> >> Key Value Pair ini memiliki arti agar Server hanya mengirimkan "Data Shoes" (Data Sepatu) ke Client, <br/>
>> >> dan Server tidak perlu mengirim data lainnya yang bukan merupakan Data Sepatu. <br/>
>> >> <br/>
>> >> (3) `sort=price` <br/>
>> >> ini merupakan "Key Value Pair", yang mana :  <br/>
>> >>	 - Key : `sort` <br/>
>> >>	 - Value : `price` <br/>
>> >> Key Value Pair ini memiliki arti agar Server memberikan Data ke Client dalam keadaan yang sudah di-Sort berdasarkan Price (sudah diurutkan berdasarkan Harga). <br/>
>> >> Biasanya Sort ini dari harga terendah hingga harga tertinggi (ascending). <br/> <br/>
>> >> 
>> >> #### [2] Path Parameters : 
>> >> -> Path Parameter merupakan bagian dari URL tanpa menggunakan "?" (tanda tanya) dan tanpa menggunakan "&" (tanda 'dan'). <br/> 
>> >> <br/> 
>> >> -> Contoh Request dengan Path Parameters :  <br/> 
>> >> 		```
>> >> 		https://api.example.com/users/123
>> >> 		```
>> >> [-] Pada Request diatas, yang merupakan Path Parameters adalah : <br/> 
>> >>	 ```
>> >> 	/users/123
>> >> 	```
>> >> Path Parameter diatas memiliki arti yaitu : <br/> 
>> >> Request memberitahu Server agar hanya mengirim Data ke Client, yaitu Data User yang memiliki ID 123 <br/>  
>> >> (User yang memiliki User's ID = 123) <br/>  
>> >> Dan Server tidak perlu mengirimkan Data selain Data User yang memiliki User's ID = 123 <br/> 
>> >> <br/> 
>> >> [-] `/users` <br/> 
>> >> ini menunjukkan Endpoint yang ingin kita akses. <br/> 
>> >> Dalam Case ini, kita ingin meng-akses "Data Users" <br/> 
>> >> <br/> 
>> >> [-] `/123` <br/> 
>> >> ini menunjukkan "Unique Identifier" pada Data. <br/> 
>> >> ("Unique Identifier" merupakan Nilai yang bersifat unik dan dapat menjadi pembeda antara satu data dengan data lainnya). <br/> 
>> >> Dalam Case ini, kita hanya meminta Data User yang memiliki ID 123 . <br/> 
>> >> 
>> >> 
>> >> ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^ <br/> <br/>
>> 
>> [2] Step 2 : Server menerima Request dan menafsirkan Request tersebut <br/>
>> (Server receives Request and Server interpret that Request ) <br/>
>> <br/>
>> -> Server menafsirkan Request berikut ini : <br/>
>>	 ```
>>	 GET https://api.example.com/users/123
>>	 ```
>> [-] `GET` <br/>
>> ini berarti Client meminta untuk "Mengambil Data" (mengambil data User yang memiliki ID 123) <br/>
>> <br/>
>> [-] Kemudian Server mengecek apakah Client memiliki wewenang untuk meng-akses data, jika iya, berarti Request tersebut Valid, dan Server akan memverifikasi Request tersebut. <br/>
>> <br/>
>> <br/>
>> [3] Step 3 : Server Fetches Data from Database <br/>
>> <br/>
>> -> Setelah Request mendapat wewenang & ter-validasi (setelah Request ter-authorsasi & ter-validasi), <br/>
>> Kemudian Server berinteraksi dengan Database atau internal Services lainnya untuk mengambil User Data. <br/>
>> <br/>
>> (Setelah proses Authorisasi & validasi, kemudian server berinteraksi dengan Database dan internal Services lainnya untuk Retrieve Data (mengambil data)).
>> <br/>
>> -> Data yang diambil dari Datbase biasanya dalam bentuk "Raw Format", kemudian Data tersebut perlu dikonversikan (diubah) menjadi Format yang mudah dibaca, seperti JSON (Javascript Object Notation). <br/>
>> <br/>
>> -> Raw Data untuk setiap Database dapat berbeda-beda bentuknya, ada yang dalam Tabular Format (Format Tabel), CSV Format, ObjectId Format, XML Format, dan lain sebagainya. <br/>
>> <br/>
>> ->  Contoh JSON Format :  
>> 	```
>> 	{
>> 	  "user_id": 1,
>> 	  "first_name": "John",
>> 	  "last_name": "Doe",
>> 	  "email": "john@example.com"
>> 	}
>> 	
>> 	```
>>
>>  <br/>
>>  [4] Step 4 : Server Sends a Response to the Client   <br/>
>> (Server mengirim Response ke Client)  <br/>
>>  <br/>
>> -> Server mengirim HTTP Response yang berisi Data,   <br/>
>> yang mana Server mengirimkan HTTP Response tersebut ke Client.  <br/>
>>  <br/>
>> -> Server mengirim "Status Code" bersamaan dengan HTTP Response,  <br/> 
>> yang mana jika semuanya berjalan dengan baik, maka Status Code tersebut adalah "HTTP 200 OK"  <br/>
>>   <br/>
>> -> Contoh HTTP Response (yang juga berisi Status Code) :  <br/>
>> 			
>> 			Status: 200 OK
>> 			{
>> 			  "id": 123,
>> 			  "name": "John Doe",
>> 			  "email": "johndoe@example.com"
>> 			}
>> 			
>> 			
>> <br/>
>> [5] Step 5 : Client Receives and Processes The Data  <br/>
>> (Client menerima dan memproses Data) <br/>
>> <br/>
>> -> Client (seperti Mobile App) menerima "Response berupa JSON" (pada contoh ini, format data untuk Response adalah JSON) <br/>
>> dan kemudian Client memproses Response Data tersebut (seperti menampilkannya pada Layar). <br/>
>> (selain JSON, format data lainnya untuk Response dapat berupa HTML, XML, Plain Text, HTML, CSV, YAML, dan sebagainya) <br/>
>> <br/>
>> -> Jika terdapat error, "Error Message" juga dikirim di dalam Response Body. <br/>
>> "Error Message" merupakan informasi spesifik mengapa error bisa terjadi. <br/>  <br/> <br/>
>> 
>> 
>> 
>> 
>> #### D) Stateless in REST API <br/>
>> #### (REST API bersifat Stateless) <br/>
>> <br/> 
>> -> Definition :  <br/>
>> Dalam REST API, "Statelessness" berarti Server tidak menyimpan informasi apapun diantara Request satu dengan Request lainnya. <br/>
>> <br/>
>> -> Setiap Request dari Client ke Server harus mengandung semua informasi yang diperlukan untuk memproses Request tersebut, <br/>
>> Sehingga System tidak perlu untuk menyimpan Informasi dari Request sebelumnya. <br/>
>> <br/>
>>
>> -> "State" adalah informasi atau Context yang biasanya disimpan atau di-ingat oleh System. <br/>
>> <br/>
>> -> Pada System yang Stateless, <br/>
>>  setiap Request diperlakukan sebagai Independen dan tidak bergantung pada "State" yang  disimpan oleh Server dari Request sebelumnya. <br/>
>> <br/>
>> -> Pada Stateless System, Server tidak mengetahui apapun mengenai Request sebelumnya setelah Response dari Request tersebut terkirim. <br/>
>> <br/>
>> -> Setelah Request yang sebelumnya terpenuhi :  <br/>
>> Request yang baru tidak bergantung pada State apapun yang disimpan oleh Server, <br/>
>> sehingga Client harus menyertakan semua Informasi yang diperlukan untuk setiap Request. <br/>
>> <br/>
>> <br/>
>> -> "No Session Tracking" : <br/>
>> [-] tidak ada "Session Tracking", yang berarti REST API tidak perlu menyimpan Session atau Data User diantara satu Request dengan Request lainnya. <br/>
>> <br/>
>> [-] "Session Tracking" merupakan cara bagi Web Server untuk mengingat hal Detail tentang User pada antar berbagai Request. <br/>
>> yang mana Session Tracking memungkinkan kita untuk tetap Log In, dan menyimpan User Preference. <br/>
>> <br/>
>> <br/>
>>
>> -> Scalability :  <br/>
[-] Statelessness membantu menskalakan System karena setiap Request bersifat Independen sehingga Setiap Request bisa ditangani oleh Server manapun (tidak masalah Server mana yang menangani Request tersebut). <br/>
>> <br/>
>> [-] Statelessness mempermudah untuk menskalakan System (Statelessness makes it easier to Scale System). <br/>
>> Karena Request bersifat Independen, Kita dapat mendistribusikan Request ke banyak Server (Multiple Server) <br/>
>> tanpa harus khawatir Server mana yang menyimpan "State" untuk Interaksi sebelumnya yang berhubungan dengan Request yang saat ini diminta Client. <br/>
>> <br/>
>> [-] Pada Stateful System, Saat User membuat Multiple Requests,  <br/>
>> yang mana Multiple Requests berhubungan antara satu sama lain sehingga Server perlu berinteraksi dengan Aplikasi dari waktu ke waktu. <br/>
>> ini berarti setelah Request Pertama, Request berikutnya harus diarahkan ke Server yang sama  yang menyimpan State untuk Session tersebut, <br/>
>> yang mana ini disebut "Session Stickiness" atau "Session Affinity". <br/>
>> (Request Pertama & Request berikutnya merupakan Request yang saling berhubungan, sehingga Request-request tersebut perlu ditangani oleh Server yang sama, yakni Server yang menyimpan State untuk informasi mengenai Request sebelumnya, yang mana Request sebelumnya tersebut berhubungan dengan Request saat ini )
>> <br/>
>> >> ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
>> >>  ^For your information^ <br/>
>> >> #### {1} Session Stickiness & Session Affinity :  <br/>
>> >> "Session Stickiness" dan "Session Affinity" merupakan Dua Istilah yang dipakai pada Distributed System, Load Balancing, dan Web Application. <br/>
>> >> "Session Stickiness" dan "Session Affinity" merujuk pada praktik yang mengarahkan User's Request (Request dari User) ke Server yang sama selama <br/> Durasi Sesi tersebut (selama durasi sesi miliki Request-Request yang saling berkaitan tersebut) untuk mempertahankan Stateful Interactions. <br/>
>> >>  <br/>
>> >> {1} Session Stickiness :  <br/>
>> >> ->  merujuk pada perilaku yang mengarahkan User's Request (Request dari User) ke Backend Server yang sama yang menangani Request yang pertama. <br/>
>> >> -> hal ini diperlukan karena Server butuh untuk mengingat informasi tentang User atau Session mereka (seperti Login State, barang pada Shopping <br/> Cart, User Preference, dan sebagainya) <br/>
>> >> -> Cara Kerja "Session Stickiness" : <br/>
>> >>  Pada System Load-Balancing, Multiple Backend Server (beberapa Server) dapat tersedia untuk menangani banyak Request. <br/>
>> >> Namun, jika User's Session Data (Session Data milik User) disimpan pada sebuah Server tertentu, maka System butuh memastikkan semua Request <br/> berikutnya yang dibuat oleh User yang sama, Request tersebut akan diarahkan ke Server yang sama untuk menjaga kontinuitas (maintain continuity). <br/>
>> >> yang mana, Mekanisme Routing ini disebut "Session Stickiness." <br/>
>> >> <br/>
>> >> {2} Session Affinity : <br/>
>> >> -> Session Affinity merupakan nama lain dari Session Stickiness, <br/>
>> >> yang mana Session Affinity mendeskripsikan mekanisme untuk menjaga keberlangsungan User's Session (to maintain User's Session Continuity). <br/>
>> >> -> Session Affinity merujuk pada mekanisme untuk menjaga User's Session selalu diarahkan ke Server yang sama selama Durasi untuk Session tersebut. <br/>
>> >> <br/>
>> >> -> Cara Kerja Session Affinity : <br/>
>> >> Session Affinity memastikkan bahwa Load Balancer secara konsisten memberi Rute untuk Request yang berasal dari User yang sama (atau Session yang sama), yang mana Rute tersebut mengarahkan ke Backend Server yang sama. <br/>
>> >> Hal ini bisa dilakukan dengan cara : <br/>
>> >> (1)  Cookies : <br/>
>> >> [-] Load Balancer dapat mengatur "Session Cookie" yang secara unik mengidentifikasi Server yang menangani User's Session, <br/>
>> >> yang mana Request selanjutnya akan membawa Cookie ini untuk memastikkan Request diberikan Rute ke Server yang tepat (Request selanjutnya merupakan milik User yang sama dengan Request yang sebelumnya). <br/>
>> >> <br/>
>> >> [-] Load Balancer dapat mengatur sebuah "Session Cookie" yang berisi informasi unik (seperti "Session ID") yang mengidentifikasi Server yang menangani User's Session (Sesi Pengguna). <br/>
>> >> Dengan cara ini, Request selanjutnya dari User yang sama akan membawa Cookie tersebut, sehingga Load Balancer dapat memutuskan untuk mengarahkan Request tersebut ke "Server yang sama" yang menangani Sesi Pengguna sebelumnya (User's Session sebelumnya). <br/>
>> >> Berikut ini Rincian Cara Kerjanya : <br/>
>> >> <1> Pertama kali User Mengunjungi Aplikasi : <br/>
>> >>  - User akan mengirimkan Request ke Server. 
>> >>  - "Load Balancer" memilih Server untuk menangani Request ini, misalnya "Server A". 
>> >>  - "Server A" akan memproses Request dan menetapkan "Session Cookie" di Browser Pengguna. <br/>
>> >> Cookie ini berisi informasi unik, yang biasanya berupa "Session ID" (misalnya session_id=abd123 ), <br/>
>> >> yang mana 'Session ID' tersebut digunakan untuk mengidentifikasi Sesi milik Pengguna (User's Session) tersebut. <br/>
>> >>  <br/>
>> >> <2> Request Selanjutnya : <br/>
>> >> 	- Ketika User mengirimkan "Request Selanjutnya", Browser akan secara otomatis mengirimkan Session Cookie yang berisi "Session ID" yang sama (seperti Session ID yang sama dengan Request sebelumnya, yaitu session_id=abc123). <br/>
>> >> (Setiap kali User melakukan Request Baru, "Session Cookie" tersebut akan dikirimkan bersama dengan Request baru tersebut) <br/>
>> >> 	- "Load Balancer" menerima Request ini dan membaca Session ID dari Cookie.  <br/>
>> >> 	- Berdasarkan "Session ID" yang ada di Cookie, "Load Balancer" mengetahui bahwa Request ini berasal dari User yang sama dan harus diarahkan ke "Server A" (Server yang menangani Session Pertama, yakni pada Session tersebut 'Request Pertama' diproses) 
>> >> <br/>   <br/> 
>> >> <3> Menjaga Konsistensi Session : <br/>
>> >>  	- Dengan cara ini, "Load Balancer" memastikkan seluruh Sesi Pengguna (User's Session) diproses oleh "Server yang sama" sepanjang sesi tersebut berlangsung.  <br/>
>> >> 	 - Hal ini menjaga Konsistensi Data Sesi Pengguna, yakni memastikkan bahwa Data terkait Pengguna (User) tetap tersedia selama User berinteraksi dengan Aplikasi atau Website (seperti memastikkan informasi User's Login, User's Preference, dan Informasi Shopping Cart tetap tersedia).   <br/>
>> >>
>> >> [-] "Session Cookie" merupakan bagian kecil data yang disimpan Web Server pada User's Browser. <br/>
>> >> Cookie ini umumnya mengandung Unique Identifier (biasanya berupa "Session ID") yang membantu Server mengenali User pada Request setelahnya (Subsequent Request). <br/>
>> >>  <br/>
>> >> [-] "Session ID" pada Cookies merupakan sebuah Unique Identifier yang digunakan untuk tracking (melacak) & manage (mengelola) Sesi milik User (User's Session) pada Website. <br/>
>> >> "Session ID" memiliki nilai yang Unik untuk setiap Session. <br/>
>> >> Tujuan dari "Session ID" adalah untuk membedakan Session (to differentiate Sessions). <br/>
>> >> "Session" merupakan Periode Interaksi antara User dan Web Aplikasi. <br/>
>> >> <br/>
>> >> [-] Load Balancer mengarahkan Request yang baru ke Server tertentu berdasarkan Session yang sama yang terjadi pada periode antara 'Request yang baru' dan 'Request yang sebelumnya'. <br/>
>> >> ("Load Balancer directs the new Request to a certain Server based on The Same Session that happen during The New Request and the Previous Request.") <br/>
>> >> <br/>
>> >> [-] Load Balancer menggunakan Session ID ini untuk memverifikasi bahwa request baru berasal dari sesi yang sama dengan Request sebelumnya.  <br/>
>> >> Session ID ini adalah kunci yang memungkinkan Load Balancer mengetahui bahwa Request baru adalah bagian dari sesi yang sedang berlangsung, dan bukan hanya Request dari pengguna yang sama secara umum. <br/>
>> >>
>> >> <br/>
>> >> [-] "System Affinity" memastikkan Request selalu diarahkan ke Server yang sama <br/>
>> >>  ("System Affininity" ensures Requests always be directed to the same System Resource, in this case, "System Resource" is Server) <br/>
>> >> <br/>
>> >>  [-] "IP Hashing" merupakan Metode yang digunakan untuk mencapai "System Affinity". <br/>
>> >>  yang mana "IP Hashing" berkerja sama dengan "Session Cookies" untuk mencapai "System Affinity". <br/>
>>  >>  <br/>
>> >>  [-] "IP Hashing" merupakan Techhnique yang digunakan untuk menentukkan bagaimana Incoming Request (Request yang akan datang) akan di-distribusikan ke Berbagai Server berdasarkan "IP Address" milik Client yang membuat Request. <br/>
>> >>  ini merupakan bentuk dari "Load Balancing" dimana Load Balancer menggunakan "IP Address" milik Client untuk memastikkan Server mana yang seharusnya menangani Request. <br/>
>> >> <br/>
>>  >> 
>>  >>  [-] Cara Kerja "IP Hashing" : <br/>
>> >>  Saat "Request masuk", Load Balancer melihat "IP Address" milik User, kemudian Load Balancer mengaplikasikan "Hashing Algorithm", <br/>
>> >>  ini menghasilkan "Hash Value" yang selalu menunjuk ke "Server yang sama" setiap kali "IP Address yang sama" membuat Request. <br/>
>>  >> Sebagai Contoh : <br/>
>>  >> - Jika "User A" ('User A' memiliki IP Address 192.168.1.5 ) mengunjungi Website hari ini, "User A" akan diarahkan ke "Server 1". <br/>
>> >>  - Jika "User A" mengunjungi Website lagi pada besok hari, "User A" masih diarahkan ke "Server 1", karena "Hash Value" (Nilai Hash) dari IP Address dari "User A" akan selalu dipetakan ke "Server 1" <br/>
>> >>  - Sementara itu, "User B" ('User B' memiliki IP Address 192.168.1.6 ) akan diarahkan ke "Server 2",  dan seterusnya. <br/>
>>  >> ("User B" diarahkan ke Server yang berbeda dengan "User A" karena "User A" dan "User B" masing-masing memiliki IP Address yang berbeda). <br/>
>> >>  Hal ini memastikkan "Session Stickiness" untuk User, yang berarti Request-Request milik User yang sama akan selalu diarahkan ke Server yang sama. <br/>
>> >>  yang mana hal ini sangat bermanfaat untuk "Stateful Systems" dimana melakukan Maintain User Data antar Request sangatlah penting (seperti untuk mengingat User's Preference, dan menjaga agar User tetap Login). <br/>
>> >>  Dan juga hal ini menghindari dimana Request milik User diarahkan ke Server berbeda yang tidak mempunyai Data State miliik User tersebut. <br/>
>>  >> <br/>
>> >>  [-] Contoh Penerapan "IP Hashing" Pada Shopping Cart : <br/>
>> >>  Misalnya kita mempunyai Online Store dengan Multiple Server dan kita ingin memastikkan saat User menambahkan Item ke Keranjang Belanja (Shopping Cart) , Keranjang tersebut selalu Konsisten untuk Inteksi selanjutnya. <br/>
>> >>  Seperti Contoh berikut ini : <br/>
>>  >>  Misalnya kita mempunyai "Load Balancer", "Shopping Cart", dan "3 Web Server" (Server 1, Server 2, Server 3). <br/> <br/>
>>  >>  
>> >>  - Tanpa "IP Hashing" (Random Load Balancing) : <br/>
>>  >> Pada Case ini, Load Balancer tidak menggunakan "IP Hashing" untuk mengarahkan Traffic, <br/>
>> >>  yang mana Load Balancer dapat menggunakan "Round-Robin" atau "Random Distribution" Method, <br/>
>> >>  yang berarti User's Request dapat diarahkan ke Server mana saja. <br/>
>> >>  <br/>
>> >>  Berikut ini Step-by-Step Process tanpa "IP Hashing" : <br/>
>> >>  <1> User A (dari IP Address 192.168.1.5 ) mengunjungi Website untuk pertama kali : <br/>
>> >>    => Load Balancer secara Random mengarahkan (memberi Rute / Route) Request milik User A ke Server 1 <br/>
>> >> => "User A" menambahkan sebuah Product ke Shopping Cart, dan "Server 1" menyimpan Data Shopping Cart. <br/>
>> >>  <br/>
>> >> <2> "User A" kembali mengunjungi Website beberapa menit dikemudian ("User A" masih dari IP Address 192.168.1.5 ) : <br/>
>> >> => Load Balancer "secara acak" (randomly) memilih Server lainnya, misalnya "Server 2". <br/>
>> >> => "Server 2" tidak mempunyai Data Shopping Cart milik "User A" (karena data ata Shopping Cart milik "User A" disimpan di "Server 1"), Sehingga Shopping Cart nya kosong. <br/>
>> >> Misalnya sebelumnya "User A" sudah memasukkan Produk "Apel" ke Shopping Cart, kemudian "User A" ingin menambahkan Produk "Keju" ke Shopping Cart, <br/>
>> >> yang mana saat "User A" menambahkan Product "Keju" ke Shopping Cart, namun Prduct "Apel" tidak ada di Shopping Cart. <br/>
>> >> yang mana hal ini bisa menyebabkan "Poor User Experience" dan Frustasi bagi Customer. <br/> <br/>
>> >>
>> >> 
>> >> - Dengan IP Hashing : <br/>
>> >> Pada Case ini, Load Balancer menggunakan "IP Hashing" untuk memastikkan bahwa "Request yang berasal dari IP Address yang sama" selalu menuju Server yang sama, <br/>
>> >> yang mana ini disebut "Session Stickiness". <br/>
>> >> <br/>
>> >> Step-by-Step Process dengan "IP Hashing" :  <br/>
>> >> <1> "User A" (dari IP Address 192.168.1.5 ) mengunjungi Website untuk pertama kali : <br/>
>> >> => Load Balancer menerapkan "IP Hashing" Algorithm ke IP Address 192.168.1.5 dan menghintung Server mana yang harus menangani Request. <br/>
>> >> => Misalnya hasil Hash dari 192.168.1.5 selalu memetakan ke "Server 1". <br/>
>> >> => "Server 1" menyimpan Data Shopping Cart, yang mana "User A" menambahkan Product ke Shopping Cart (Misalnya "User A" menambahkan Product "Apel" ke Shopping Cart). <br/>
>> >>  <br/>
>> >> <2> "User A" mengunjungi Website lagi di lain waktu ("User A" masih dengan IP Address yang sama, yaitu 192.168.1.5 ) : <br/>
>> >>  => Load Balancer melakukan Hash pada IP 192.168.1.5  dan melakukan Request dari IP tersebut ke "Server 1" (Karena nilai Hash untuk IP selalu sama) <br/>
>> >>  => "Server 1" sudah mempunyai Data Shopping Cart yang sebelumnya untuk "User A", Sehingga "User A" dapat melihat Product yang sebelumnya ia tambahkan ke Shopping Cart, yaitu "Apel". <br/>
>> >>  <br/>
>> >> <3> "User A" menambahkan lebih banyak Product ke Shopping Cart <br/>
>> >>  => Karena Nilai Hash untuk IP Address milik "User A" selalu menunjuk ke "Server 1", maka Shopping Cart selalu utuh Saat User mengunjungi Website berkali-kali. <br/>
>> >> <br/>
>> >>  <br/>
>> >>  (Note : Kekurangan dari IP Hashing adalah IP Address milik User dapat berubah jika User mengubah Network (Jaringan), misalnya dari Jaringan Wifi ke Jaringan Data Seluler)
>> ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
>>
>> Even though REST APIs are stateless, they still need a way to authenticate users. This is done by passing a token (like a JWT — >> JSON Web Token) in each request, which contains all the information the server needs to know about the user. The server does not store session data but validates the token with each request to authenticate the user.`
contoh dengan JWT : 
>> 
>>	 ```
>>	GET /user/profile
>>	Authorization: Bearer <JWT_TOKEN>
>>	```
>>
>> ---------
>>  ### {3} **REST API in GraphQL** <br/>
>>
>> 
>> ------
>> ### {4} **External GraphQL Services** <br/>
>> ----
>> 

#### [2] Actions : 
Actions memungkinkan kita untuk memperluas Hasura Schema dengan mendefinisikan 'Custom Business Logic' dan menghubungkan ke REST API.
Dengan Actions, kita dapat mendefinisikan Custom GraphQL Query atau Mutations yang yang menghungkan REST Endpoints ke Supergraph.

>> ^For your information^ <br/>
>> {1} **Actions** <br/>
>>
>> ----
>> {2} **Custom Business Logic** <br/>
>> <br/>

