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




## >>> For your Information :  <<<

#### 1.  External Authentication Services in Hasura :

#### 2. External Authorization Services in Hasura :

#### 3. JWT Token for Authentication in Hasura :

#### 4. JWT Token for Authorization in Hasura :
================

To do :

1. Give Detail Explanation (Give in this article) : DDoS Protection in Hasura, SSL/TLS Encryption in Hasura, Web Application Firewall in Hasura
