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


