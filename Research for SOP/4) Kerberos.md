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
