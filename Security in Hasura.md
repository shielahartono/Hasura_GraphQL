# Security in Hasura

## A. Key Security Features in Hasura
(Fitur Keamanan utama pada Hasura )

### 1. Authentication :

- Authentication erat kaitannya dengan slogan "Who Are You ?",
yakni pertanyaan untuk memastikkan siapakah anda sebenarnya, untuk mem-verifikasi User Credential

-  Analogi nya seperti memasuki Gedung dan kita harus menunjukkan ID Card di pintu untuk membuktikkan Siapa kita.
Di dunia Digital, Authentication berarti "Log In" menggunakan Username & Password,
atau bentuk identifikasi lainnya untuk membuktikkan identitas.

- Bagaimana Authentication bekerja di Hasura ? 

Hasura tidak secara langsung menangani Authentication (seperti mengelola Username atau Password), tetapi Hasura berkerja sama dengan layanan lainnya, seperti JWT (JSON Web Token), dan juga Third Party Services, seperti Auth0, Firebase Auth, atau Okta.


- Langkah-langkah Proses Authentication :

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

### 2. Authorization :

-  Authorization memastikkan bahwa User hanya bisa "mengakses Data" & "melakukan Action" yang diizinkan.
-  Authorization merupakan Proses untuk menetukkan "apa yang boleh anda lakukan",
yang mana hal ini menjawab pertanyaan "Apa yang boleh kamu akses, setelah anda di-autentikasi ?"

- bayangkan saat kita memasuki Gedung, kita memiliki Akses untuk lantai yang berbeda-beda.
Misalnya Rudi hanya memiliki akses untuk ke lantai 10 & 7,
sementara Jane memiliki akses untuk ke lantai 12, 8, dan 5.

yang mana, di dunia Digital, Authorization mengontrol Data dan Feature apa yang bisa kita akses berdasarkan Role (Peran) atau Permission (izin) kita.

- Hasura menggunakan Authorization berupa "Role-Based Access Control" (RBAC).
RBAC menentukkan Data apa yang bisa kita akses dan Action apa yang bisa kita lakukan berdasarkan Role (peran) kita.

- Langkah-langkah dalam Authorization Process :

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


### 3. Row-Level Security (Fine-Grained Data Access)

- "Row-Level Security" juga dikenal sebagai "Fine-Grained Data Access" (Akses Data Terperinci), merupakan sebuah Fitur keamanan di Hasura yang mengontorol akses ke "Baris Data Tertentu" (Specific Rows of Data).

- "Row-Level Security" berarti mengontrol Akses di tingkat Baris pada Database
(Controlling Access at the Row Level in Database)

- Kita dapat menentukkan Aturan untuk setiap Tabel (Rules for each table) untuk membatasi Data berdasarkan kondisi tertentu.

Misalnya, kita dapat membuat aturan yang menyatakan :

-> Pada Table Orders, User hanya dapat melihat Baris (row) yang memiliki nilai user_id yang cocok dengan nilai user_id milik User tersebut,
yang mana tidak diperbolehkan melihat Baris (row) yang memiliki nilai user_id milik User lain.

yan mana pada Tabel Orders , "Row-Level Security" dapat memastikkan agar User hanya dapat melihat "Order milik mereka sendiri", dan tidak bisa melihat Order milik orang lain.

-> Dan juga, misalnya pada suatu Table terdapat baris tertentu yang merupakan Sensitive Data, maka "Row-Level Security" memastikkan hanya Orang tertentu yang dapat mengakses atau memodifikasi data tersebut. 

#### 3.1) Bagaimana "Row-Level Security" bekerja :

-> Hasura memungkinkan kita untuk membuat "Permission Rules" yang menentukkan Row mana yang User dapat Akses berdasarkan Role nya (seperti Role sebagai Admin, User, dan peran khusus lainnya)

 - Langkah-langkah "Row-Level Security" bekerja :

##### [1} Define Roles :
(Tentukan Peran)

-> Kita menentukkan Role di Hasura, seperti "Admin", "User", atau "Guest",
yang mana setiap Role dapat memiliki tingkat akses yang berbeda (Different levels of access)



## >>> For your Information :  <<<

### 1. Where does "Web Application Firewall" (WAF) fit in Hasura Security ?

### 2.  External Authentication Services in Hasura :

### 3. External Authorization Services in Hasura :

### 4. JWT Token for Authentication in Hasura :

### 5. JWT Token for Authorization in Hasura :
================

To do :

1. Give Detail Explanation (Give in this article) : DDoS Protection in Hasura, SSL/TLS Encryption in Hasura, Web Application Firewall in Hasura
