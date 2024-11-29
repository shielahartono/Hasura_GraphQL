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
<br/>
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
