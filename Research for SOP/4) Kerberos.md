# Kerberos

## A) What is Kerberos ?

-> Kerberos merupakan "Network Authentication Protocol" (Protocol Autentikasi Jaringan) yang memungkinkan "Secure Authentication" (Autentikasi Aman) bagi User dan Service melalui Jaringan yang tidak aman, seperti Internet.
"Network Authentication Protocol" ini dirancang untuk memberikan Keamanan yang kuat (Strong Security) dengan menggunakan "Cryptographic Key" dan "Tickets" untuk mengautentiikasi User tanpa mengirimkan Password melalui Jaringan.
<br/><br/>

-> Kerberos merupakan Sistem yang digunakan untuk memverifikasi Identitas secara aman melalui Jaringan (seperti internet), <br/>
tanpa mengirimkan Password secara langsung. <br/>
Sistem ini sangat penting pada Environment yang mengutamakan Keamanan, seperti Corporate Networks atau Cloud Services. <br/><br/>

->  Kerberos membantu mencegah Hacker mencuri Password atau Sensitive Information saat User mencoba mengakses Service atau Resources pada Jaringan.
Biasanya, jika User mengirim Password mereka melalui Internet, Hacker dapat melakukan Penyadapan terhadap Password tersebut (The Password could be Intercepted by Hacker).
Sebaliknya, Kerberos menggunakan "Cryptographic Key" dan "Tickets" untuk mengautentiikasi User tanpa mengirimkan Password melalui Jaringan.
<br/>
<br/>

## B) "Cryptographic Key" dan "Tickets" in Kerberos

-> Pada Konteks Kerberos, "Cryptographic Key" and "Tickets" merupakan konsep penting yang membantu memastikkan Autentikasi dan Komunikasi yang aman. <br/> <br/>

### 1. Cryptographic Keys
-> "Cryptographic Keys" (kunci Kriptografi) merupakan bagian informasi rahasia yang digunakan dalam Proses Enkripsi & Dekripsi untuk melindungi Data. <br/><br/>

-> "Encryption" : <br/>
adalah saat Data di-enkripsi. <br/>
Pada saat Data di-enkripsi, Data diacak ke dalam Format yang tidak bisa dibaca. <br/>
Dan Data tersebut hanya bisa dibaca oleh orang yang mempunyai "Secret Key". <br/>
<br/>
-> "Decryption" : <br/>
Decryption merupakan cara untuk membaca Data yang di-Enkripsikan. <br/>
Data yang di-Enkripsikan tersebut diterjemahkan menggunakan "Secret Key", <br/>
agar Data tersebut bisa di-terjemahkan kedalam format yang bisa dibaca. <br/><br/>


-> Pada case Kerberos : <br/>
[-] Client dan 'Authentication Server' (AS) masing-masing memiliki "Shared Secret Key", <br/>
yang mana "Shared Secret Key" ini tidak pernah di-transmisikan melalui jaringan. <br/>
<br/>
[-] "Ticket Granting Server" (TGS) dan Client juga memiliki "Shared Secret Key" yang sama  <br/>
<br/>
>> ^For your Information^ <br/>
>> "Ticket Granting Server" merupakan salah satu Komponen pada "Key Distribution Center" (KDC). <br/>
>> "Ticket Granting Server" berperan dalam Mengeluarkan Ticket kepada User untuk meng-akses Services lain. <br/>
<br/>


### 2. Tickets 
-> Pada Kerberos, "Ticket" merupakan 'jenis bukti khusus' yang membuktikkan Identitas Pengguna ke suatu Service tanpa mengungkapkan Password milik User. <br/>
(Ticket membuktikkan Identitas milik User tanpa mengungkapkan Password milik User) <br/><br/>

-> secara analogi, Ticket itu seperti 'Temporary Pass' (izin Akses ke Service atau System untuk Periode waktu tertentu) yang User dapatkan setelah berhasil membuktikkan Identitas User tersebut ke System. <br/>
Setelah User berhasil ter-autentikasi, User tersebut dapat menggunakan Ticket ini untuk meng-akses berbagai Service tanpa harus memasukkan kembali Password mereka. <br/><br/><br/>


## C) Key Components in Kerberos
## (Komponen Utama pada Kerberos) 

### [1] Client :
Client merupakan User atau Machine yang mencoba meng-akses sebuah Service. <br/> <br/>

### [2] Server : 
Server merupakan System yang menyediakan Service yang ingin diakses oleh Client <br/><br/>

### [3] Key Distribution Center (KDC) :
merupakan Autoritas Pusat (Central Authority) yang mengelola Autentikasi pada Kerberos. <br/><br/>

"Key Distribution Center" mempunyai Dua Komponen utama, yaitu : <br/>
#### [-] Authentication Server (AS) :
Bertugas memverifikasi Identitas User. <br/><br/>

#### [-] Ticket Granting Server (TGS) :
bertugas Mengeluarkan "Service Ticket" kepada User untuk meng-akses Services lain, <br/>
yang mana hal ini dilakukan setelah User ter-autentikasi oleh AS (Authenticated Server). <br/><br/>



### [4] Tickets :

-> "Tickets" adalah bagian data yang Secure dan ter-Enkripsi yang digunakan untuk meng-autentikasi identitas User dan memfasilitasi Komunikasi yang aman antara Client dan Service yang coba di-akses. <br/><br/>

-> Pada Kerberos, "Ticket" merupakan 'jenis bukti khusus' yang membuktikkan Identitas Pengguna ke suatu Service tanpa mengungkapkan Password milik User. <br/>
(Ticket membuktikkan Identitas milik User tanpa mengungkapkan Password milik User) <br/><br/>

-> secara analogi, Ticket itu seperti 'Temporary Pass' (izin Akses ke Service atau System untuk Periode waktu tertentu) yang User dapatkan setelah berhasil membuktikkan Identitas User tersebut ke System. <br/>
Setelah User berhasil ter-autentikasi, User tersebut dapat menggunakan Ticket ini untuk meng-akses berbagai Service tanpa harus memasukkan kembali Password mereka. <br/><br/> <br/>

-> "Tickets" mempunyai Dua Komponen, yaitu : <br/>
#### [-] Ticket Granting Ticket (TGT) :
merupakan Special Ticket yang membuktikkan bahwa Client telah terautentikasi oleh KDC (Key Distribution Center). <br/><br/>

#### [-] Service Ticket :
merupakan Ticket yang dikeluarkan oleh TGS (Ticket Granting Server) yang memungkinkan akses ke Service tertentu. <br/><br/>


>> ^For your Information^ <br/>
>> -> "Service Ticket" diterbitkan oleh TGS (Ticket Granting Server)  <br/><br/>
>>
>> -> "Ticket Granting Ticket" (TGT) diterbitkan oleh AS (Authentication Server) <br/><br/>


## D) Kerberos Authentication Process (Step-by-Step)
## (Proses Autentikasi Kerberos) <br/><br/>

### 1. Initial Login Request (AS Request)
("AS" adalah kepanjangan dari "Authentication Server") <br/><br/>

-> Client mengirim Request ke  "Authentication Server" (AS) <br/> <br/>

Saat Client LogIn ke System (seperti Memasukkan "Username" dan "Password"), <br/>
pada saat itu, User perlu di-autentikasi, <br/>
berikut ini hal yang terjadi : <br/><br/>

#### (a) Apa yang dilakukukan Client :
[-] Client's Action : <br/>
Client memasukkan Username & Password mereka ke dalam System. <br/><br/>

[-] Password tidak dikirim secara langsung melalui Jaringan,  <br/>
tetapi Password digunakan untuk membuat Permintaan Autentikasi ke Authentication Server (AS). <br/><br/>
 
>> ^For your Information^ <br/>
>> Password digunakan untuk membuat "Hash" atau "Secret Key" yang meng-enkripsi Permintaan Autentikasi (Authentication Request). <br/>
>> (Password milik masing-masing User, diolah menjadi "Secret Key" untuk meng-enkripsi data) <br/> <br/>

#### (b) What Happens in the "Authentication Server" (AS) Request : <br/>
[-] Client mengirim "Authentication Request" (Permintaan Authentikasi) kepada "Authentication Server" (AS) <br/>
(yang mana "Authentication Server" (AS) merupakan bagian dari "Key Distribution Center" (KDC) ) <br/> <br/>
<br/>
[-] "Authentication Request" biasanya mengandung hal berikut ini : <br/>
=> Client's Username (Username milik Client) :
- contohnya : "Alice" <br/><br/>

=> Timestamp :
- Timestamp ini bersifat Opsional.
- Timestamp dapat membantu untuk mencegah "Replay Attacks" dan memastikkan Request tersebut dalam keadaan Fresh <br/>
(Timestamp is helpful to prevent replay attacks and ensure the request is fresh)

>> ^For your Information^ <br/>
>> {1} **Timestamp dapat membantu untuk mencegah "Replay Attacks" dan memastikkan Request tersebut dalam keadaan Fresh**  <br/>
>> -> "Replay Attack" terjadi saat Hacker Menyadap Pesan (seperti "Authentication Request"), <br/>
>> lalu melakukan "Replay" atau mengirimkan Pesan yang sama tersebut ke Server di kemudian waktu, hal ini dilakukan untuk "Menipu Server" agar seolah-olah Request/Pesan tersebut merupakan saat ini. <br/> <br/>
>>
>> -> Untuk mencegah hal tersebut terjadi, Kerberos menggunakan Timestamp untuk hal berikut ini : <br/>
>> [-] Freshness : <br/>
>> Timestamp memastikkan Request yang dikirim ke Server merupakan Request saat ini. <br/>
>> Jika "Authentication Server" (AS) melihat "umur Timestamp terlalu tua" yang berarti Request dibuat terlalu lama dimasa lalu. <br/>
>> , maka "Authentication Server" (AS) dapat menolak Request tersebut <br/>
>> (karena bisa jadi Request tersebut merupakan Pengulangan atau Replay) <br/><br/>
>>
>> [-] Time Window (Jendela Waktu) : <br/>
>> Kerberos biasanya memberikkan "Time Window" yang singkat (misalnya 5 menit) agar Timestamp tersebut Valid <br/>
>> Jika Timestamp pada Request tersebut berada pada Time Window ini (Request dibuat tidak lebih lama dari 5 menit yang lalu), maka Server mengetahui bahwa Request tersebut Baru dan Sah. <br/>
>> dan Jika Timestamp pada Request tersebut berada diluar "Time Window", maka Server akan menolak Request tersebut. <br/>

<br/>

#### c) Why is The Password Not Sent in the Request ?

- Pada Kerberos Protocol, Password tidak pernah dikirimkan secara langsung melalui Network (Jaringan), tetapi Client menggunakan Password untuk menghasilkan "Cryptographic Request" (atau Hash) yang dikirim ke "Authentication Server" (AS).

- Password digunakan untuk membuat "Hash" atau "Secret Key" yang meng-enkripsi Permintaan Autentikasi (Authentication Request).
(Password milik masing-masing User, diolah menjadi "Secret Key" untuk meng-enkripsi data)



### 2. Authentication Server (AS) Response
### ("Authentication Server" (AS) memberikan Response)

[-] "Authentication Server" (AS) mengecek Identitas milik Client : <br/>
AS mengecek Client's Username pada Database dan mengambil Data Password (yang disimpan dalam bentuk Hash) <br/><br/>

[-]  "Authentication Server" (AS) membandingkan Hashed Value milik Password yang diambil dari Database dengan Hashed Value milik Password yang ada di dalam Request. <br/>
Jika kedua Hashed Value tersebut cocok, maka Authentication Server" (AS) tahu bahwa Client tersebut Authentic (asli). <br/><br/>

Jika Client tersebut Authentic (asli), maka kemudian "Authentication Server" (AS)  menerbitkan "Ticket Granting Ticket" (TGT) 
<br/><br/>

[-] Bersama dengan TGT (Ticket Granting Ticket), "Authentication Server" (AS) mengirim kembali "Session Key" yang di-enkripsikan menggunakan TGT.
"Session Key" akan digunakan untuk komunikasi lebih lanjut antara Client dan "Ticket Granting Server" (TGS).
<br/><br/>


### 3. Requesting Access to a Service (TGS Request)
### ("Ticket Granting Server" (TGS) melakukan Request )

[-] "Ticket Granting Ticket (TGT)" merupakan "Encrypted Ticket" (Ticket yang ter-enkripsi) yang membuktikkan Client sudah ter-autentikasi oleh KDC (Key Distribution Center) <br/> <br/>

[-] "Ticket Granting Ticket (TGT)" berisi informasi penting seperti : <br/>
- "Identitas Client" (seperti Username)
- "Timestamp" saat Ticket diterbitkan 
- "Expiration Time" of the Ticket (Waktu Kadaluawarsa Ticket)

<br/><br/>

[-] Karena Sekarang Client sudah mempunyai TGT yang valid, maka Client dapat menggunakan TGT tersebut untuk meng-akses Services pada Network. <br/><br/>

[-] Client mengirim TGT ke "Ticket Granting Server" (TGS) bersama dengan Request (Permintaan) untuk sebuah "Service Ticket", <br/>
yang mana "Service Ticket" tersebut untuk meminta izin akses ke Service tertentu (seperti File Server atau Database Server). <br/> <br/>

Dan juga Request tersebut juga mengandung Timestamp (untuk mencegah "Replay Attack"). <br/>
Request dan Timestamp di-enkripsi menggunakan "Session Key" dari TGT <br/>
<br/>

### 4. Ticket Granting Server (TGS) Response
### ("Ticket Granting Server" (TGS) memberikan Response)
<br/>
[-] TGS mengecek "Ticket Granting Ticket" (TGT) untuk meng-konfirmasi Identitas milik Client, dan Pastikkan Client mempunyai Autorisasi untuk meng-akses Service yang di-Request. <br/><br/>

[-] Jika semuanya Valid, maka TGS akan menerbitkan "Service Ticket" untuk Service yang di-request (contohnya Web Server atau File Server). <br/>
"Service Ticket" di-enkripsi menggunakan "Secret Key" milik Service (sehingga hanya Service yang bisa melakukan Dekripsi)<br/><br/>

[-] "Service Ticket" juga mengandung "Session Key" yang akan digunakan untuk mengamankan komunikasi antara Client dan Service.<br/><br/>


### 5. Accessing the Service (Service Request)

[-] Sekarang Client mengirimkan "Service Ticket" ke "Target Service" (Service yang Client ingin Akses, seperti Web Server). <br/>
Client juga mengirim sebuah Timestamps untuk membutikkan bahwa itu bukanlah "Replay Attack". <br/>
(Timestamp dikirimkan didalam "Service Ticket") <br/><br/>

[-] Service melakukan Dekripsi pada "Service Ticket" menggunakan "Secret Key" milik Service itu sendiri.  <br/>
Jika Service Ticket nya Valid  dan Session Key nya benar, maka Service memberikan akses ke Client. <br/><br/>


### 6. Session Communication 

[-] Setelah Proses Authetikasi yang berhasil, Client dan Service dapat dengan aman berkomunikasi menggunakan "Session Key" yang disediakan pada "Service Ticket"  <br/><br/>

[-] Session Key digunakan untuk meng-enkripsi komunikasi antara Client dan Service, <br/>
memastikkan Confidentiality (kerahasiaan) dan Integritas.  <br/><br/>

## E) Thick Client vs Thin Client

### 1. Thick Client (Fat Client)

-> Thick Client adalah Computer atau Device yang memiliki sebagian besar Resources dan Software yang dibutuhkannya terpasang secara lokal (pada Device itu sendiri). <br/>
ini berarti Thick Client dapat menjalankan aplikasi dan memproses Data tanpa perlu melakukan Komunikasi dengan Server secara terus menerus (Karena Thick Client sudah bisa melakukan Pemrosesan dengan Device nya sendiri, sehingga tidak membutuhkan banyak bantuan Server untuk Pemrosesan) <br/><br/>

-> Cara Kerjanya : <br/>
[-] Thick Client memiliki "Processinhg Power", "Memory", dan "Storage" sendiri
(di dalam Device milik Thick Client sudah terdapat "Processinhg Power", "Memory", dan "Storage" sendiri)  <br/>
yang mana ini memungkinkan Thick Client untuk menjalankan Program, Menyimpan File, dan Mengerjakan Tasks tanpa perlu bergantung pada "Remote Server". <br/>
Namun, terkadang Thick Client masih perlu meng-akses Server untuk Service tertentu, seperti Updates, Backups, dan meng-akses Database Besar (Large Database). <br/>
<br/><br/>

-> Contoh Thick Client : <br/>
[-] Komputer atau Laptop yang menjalankan 'Microsoft Word' atau 'Adobe Photoshop',
program-program ini terpasang langsung pada Device, sehingga anda dapat menggunakan Program tersebut bahkan tanpa Koneksi Internet atau Akses ke Server. <br/><br/>

[-] Video Games yang ter-install langsung pada Console tanpa harus terhubung ke Server untuk memainkan Video Game tersebut. <br/><br/>

### 2. Thin Client :
-> Thin Client merupakan Computer atau Device yang bergantung pada Server untuk melakukan sebagian besar Pekerjaannya. <br/>
(Sebagian Pemrosesan terjadi pada Server, bukan pada Device milik Thin Client) <br/><br/>

-> Device milik Thin Client hanya memiliki Sedikit "Computing Power" dan biasanya Device ini hanya menangani task untuk 'Displaying Information & input from User' (menampilkan Informasi & input dari User), <br/>
yang mana Sebagian Pemrosesan terjadi pada Server. <br/><br/>

-> Cara Kerja : <br/>
Thin Client tidak memiliki banyak 'Memory' atau 'Processing Power'. <br/>
Melainkan, Thin Client terhubung ke sebuah "Central Server" (Server Pusat), yang mana "Central Server" merupakan tempat semua Pemrosesan terjadi, dan juga "Central Server" juga dapat mmenjadi tempat Aplikasi dan Data berada. <br/><br/>

Device milik "Thin Client" hanya mengirimkan Input ke Server (seperti Input yang dimasukkan oleh User) <br/>
, dan Device milik "Thin Client" menunjukkan Hasil Pemrosesan Server kepada User
(Pemrosesan terjadi di Server, kemudian hasilnya ditampilkan ke User) <br/><br/>
<br/>

-> Contoh Thin Client : <br/>
[-] Web Browser : <br/>
"Web Browser" merupakan contoh umum Thin Client. <br/>
"Web Browser" hanya menampilkan 'Halaman Web', sementara Data di-fetch (diambil) dan diproses oleh 'Web Server' <br/>
(Data Diproses di Server) <br/><br/>

[-] Remote Desktop System : <br/>
Pada "Remote Desktop System", aplikasi atau Software sebenarnya berjalan di "Server yang kuat", dan User hanya berinteraksi dengan melalui Device yang Resources-nya tidak terlalu besar. <br/>
"Remote Desktop System" memilik contoh seperti 'Citirix' atau 'Windows Remote Desktop'. <br/><br/>

## F) Advantages & Disadvantages of "Thick Client"

### 1. Advantages of Thick Client : <br/>
<br/>
(1) Performance & Speed : <br/>
[-] Faster Response Time : <br/>
Karena Thick Client melakukan Sebagian Besar Pemrosesan-nya secara Lokal, maka "Thick Client" cenderung lebih cepat, <br/>
karena tidak perlu menunggu Data dikirim ke Server, dan tidak perlu menunggu Response dari Server. <br/><br/>

[-] Can Handle Complex Application (Dapat menangani Aplikasi yang Kompleks) : <br/>
Device milik "Thick Client" dapat menangani Aplikasi yang kompleks tanpa memerlukan Koneksi ke Server secara terus-menerus. <br/>
Hal ini karena "Thick Client" mempunyai lebih banyak 'Processing Power' dan 'Storage', <br/>
sehingga Device milik Thick Client dapat menjalankan 'Resource-heavy Applications'  <br/>(Aplikasi yang membutuhkan Resource Berat), seperti Video Editing Software, 3D Games, atau Large Database. <br/><br/>


(2) Offline Capabilities (Dapat bekerja Offline tanpa Internet) : <br/>
Device milik "Thick Clients" dapat bekerja tanpa Internet. <br/>
Misalnya, kita dapat menggunakan Aplikasi Excel tanpa perlu terhubung ke Internet. <br/><br/>


(3) Customization and Flexibility : <br/>
[-] More Control : <br/>
Pada Device milik "Thick Client", Users atau Organisasi dapat meng-install Software mereka sendiri, Customize Settings, dan Melakukan Konfigurasi berdasarkan kebutuhan tertentu. <br/><br/>


(4) Reduced Dependency on Network : <br/>
"Thick Client" tidak bergantung pada Network atau Server untuk menjalankan Tasks mereka, karena Device milik "Thick Client" mempunyai Software dan Data yang diperlukan. <br/>
Sehinhgga jika Network nya sedang 'down', User tetap bisa menjalankan Tasks mereka. <br/><br/>


### 2. Disadvantages of Thick Client :

(1) Higher Maintenance Cost : <br/>
(Biaya Perawatan yang lebih mahal) <br/><br/>

[-] Software Updates : <br/>
Setiap "Thick Client" membutuhkan Update secara individu (Secara masing-masing untuk setiap Device). <br/>
Jika ada Issue pada Software, kita perlu memperbaikinya pada setiap Komputer atau Device.
<br/><br/>

[-] Hardware Maintenance : <br/>
Karana setiap Device memiliki Hardware nya masing-masing, sehingga semakin mahal untuk Maintenance, <br/>
karena Setiap Device atau Komputer membutuhkan Upgrade atau Repairs (Perbaikkan) pada Hardware seiring berjalannya waktu. <br/>

(2) Security Risks : <br/>
[-] More Vulnerable to attacks : <br/>
(lebih rentan terkena Serangan) <br/>
Karena Data disimpan secara Local, maka terdapat Risiko yang lebih besar untuk Pencurian Data (Data Theft) atau Kehilangan Data (Data Loss). <br/>
Misalnya jika Komputer dicuri, kemudian Sensitive Information ter-ekspos. <br/>
atau Misalnya User secara tidak sengaja meng-install aplikasi yang terdapat Malware atau tidak sengaja terhubung ke Network yang tidak aman, <br/>
sehingga Attackers mendapatkan Akses ke File, Password, dan Sensitive Information lainnya.
<br/><br/>

(3) Higher Initial Cost : <br/>
[-] More Expensive Hardware : <br/>
Thick Client memerlukkan Computer yang Powerful, yang mana ini dapat lebih mahal dibandingkan 'Thin Client' <br/><br/>


(4) Difficlut to Scale : <br/>
[-] Limited Scalability : <br/>
Jika kita mau menambahkan lebih banyak User atau Devices, kita perlu membeli lebih banyak Hardware untuk setiap Komputer, <br/>
yang mana hal ini dapat menyebabkan Inefficient (ketidakefisienan) dan Biaya yang lebih mahal. <br/><br/>

## G) Advantages & Disadvantages of "Thin Client"

### 1. Advantages of "Thin Client" : <br/>
<br/>
{1) Lower Cost : <br/>
[-] Cheaper Hardware : <br/>
Komputer untuk "Thin Client" itu lebih murah karena tidak memerlukkan 'Powerful Processor' atau 'Big Storage' . <br/><br/>

(2) Easier to Maintain : <br/>
(lebih mudah untuk dirawat) <br/>
Karena semuanya diproses pada Central Server, kita tidak perlu, sehingga Maintenance hanya perlu pada Server.   <br/><br/>

(3) Better Security : <br/>
Semua Data disimpan pada Server, sehingga mengurangi Risiko 'Data Theft' (Pencurian Data). <br/><br/>

(4) Scalable : <br/>
melakukan 'Scale-up' hanya perlu pada Server, dan tidak perlu pada masing-masing Komputer, sehingga tidak ribet. <br/><br/>

### 2. Disadvantages of Thin Client :

(1) Depends on Network : <br/>
"Thin Clients" membutuhkan 'Network Connection' yang bagus dan Dapat diandalkan. <br/><br/>

(2) Cannot Work Offline: <br/>
Jika Server atau Internet nya 'down', kita tidak bisa menggunakan Thin Client sama sekali, karena kita tidak bisa meng-akses Server tanpa Internet. <br/>
Sehingga "thin client" bukan merupakan pilihan terbaik jika kita berada di daerah yang Konenksi Internet nya tidak memadai.
 <br/><br/>
 
(3) Limited Customization : <br/>
(Kustomisasi terbatas untuk Individual) <br/>
Karena semuanya dikelola pada "Central Server" (Server Pusat), <br/>
sehingga kita tidak bisa melakukan Personalized Setting untuk tiap Individual. <br/>
<br/>

(4) Ketergantungan Pada Server : <br/>
Jika Server mengalami "down", maka "Thin Client" akan terkena dampaknya. <br/>
dan juga jika semua User terhubung pada Server di waktu yang sama, hal ini akan memperlambat Server.<br/><br/>



## H) "Session Key" vs "Shared Secret Key" in Kerberos


