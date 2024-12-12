# Analyze Log in Elastic APM 

---
---
# A) Buka Hasura Console di Rancher, dan Ubah Endpoint pada "Open Telemetry Exporter"

1. Buka Rancher
   ![WhatsApp Image 2024-12-10 at 23 23 13_37f50fea](https://github.com/user-attachments/assets/f93ccf71-af46-4872-a369-2246feb0bea3)

2. Pilih Namespace "sheila"  <br/>
   (Namespace milik kita) <br/>
![WhatsApp Image 2024-12-10 at 23 23 35_118e6581](https://github.com/user-attachments/assets/96e81bb5-37a8-4139-a980-911cd792fdcf)


3. Pilih "Service Discovery"  <br/>
![WhatsApp Image 2024-12-10 at 23 27 38_0b472612](https://github.com/user-attachments/assets/62ff10ce-31b4-45da-9733-9f955883435b)


4. Pilih "Services" <br/>
![WhatsApp Image 2024-12-10 at 23 28 01_8e7a56d5](https://github.com/user-attachments/assets/71c79d6c-a465-4be6-8996-ac0337deaeff)


5. Click Value pada bagian "Target" . <br/>
   
kemudian ini akan mengarahkan kita ke "Hasura Console" <br/>
![WhatsApp Image 2024-12-10 at 23 33 17_8042e43d](https://github.com/user-attachments/assets/86daab14-2d70-416f-b8bb-205227eb188e)
<br/>
![WhatsApp Image 2024-12-10 at 23 28 34_8f9fbd87](https://github.com/user-attachments/assets/5e7910fe-d915-493b-9a23-e36e4eebf478)


6. Berikut ini Tampilan "Hasura Console"  <br/>
![WhatsApp Image 2024-12-10 at 23 34 03_63277967](https://github.com/user-attachments/assets/f5aeeb9c-f9bb-4312-a96d-1846d062facf)

7. Pilih "Settings" pada bagian kanan atas <br/>
![WhatsApp Image 2024-12-10 at 23 35 50_ae0acf18](https://github.com/user-attachments/assets/59e45dc8-af47-47ec-8fe1-b12387b57890)


8. Pilih "Open Telemetry Exporter" <br/>
![WhatsApp Image 2024-12-10 at 23 37 30_2f3ee44a](https://github.com/user-attachments/assets/1702537f-7dac-41b5-a886-b851fe8b5917)

![WhatsApp Image 2024-12-10 at 23 36 29_8328416b](https://github.com/user-attachments/assets/bbf0d142-36f4-4218-a319-cc07a4d45c96)


9. kita ganti dengan Endpoint 10.100.13.24  
<br/>
yakni menjadi seperti ini :  <br/>

- Traces Endpoint : 
http://10.100.13.24:4318/v1/traces

- Metrics Endpoint :
http://10.100.13.24:4318/v1/metrics

- Logs Endpoint :
http://10.100.13.24:4318/v1/logs

![WhatsApp Image 2024-12-10 at 23 46 15_82d7c292](https://github.com/user-attachments/assets/18f1ea74-0f0c-4ceb-8619-f53c4af9c766)


10. Pilih "Update"  <br/>
![WhatsApp Image 2024-12-10 at 23 47 19_2be3c0d5](https://github.com/user-attachments/assets/a9a7f72d-c602-4c8e-b1d1-818c9aa51244)
![WhatsApp Image 2024-12-10 at 23 47 19_e70fd47e](https://github.com/user-attachments/assets/56e767c2-f79b-46b2-94a7-2b4cd4c09791)


-----
-----
# B) Tutorial Setting di Hasura Rancher & Hit di Postman 500 kali


1. Buka Postman <br/>
![WhatsApp Image 2024-12-10 at 22 14 59_83468103](https://github.com/user-attachments/assets/666f343b-8ca3-438d-bb5b-15941c63d6f2)

2. Pilih Post <br/>
![WhatsApp Image 2024-12-10 at 22 29 35_95579548](https://github.com/user-attachments/assets/d58540b5-72b8-4bd4-8acd-e1ed735ebde7)
![WhatsApp Image 2024-12-10 at 22 27 45_db879c99](https://github.com/user-attachments/assets/60be369e-ebe9-4a06-8498-79a573e171e3)


3. bagian Endpoint pada Postman, kita copy dari Endpoint paling atas pada Hasura Console (Hasura yang ada di Rancher)  <br/>
![WhatsApp Image 2024-12-10 at 22 33 14_f921d3b7](https://github.com/user-attachments/assets/40d0cebf-7af6-4901-82e7-ab876463a9ab)


4. pada bagian "Headers" di Postman, kita tambahkan Password Hasura  <br/>
![WhatsApp Image 2024-12-10 at 22 36 09_fc635dd9](https://github.com/user-attachments/assets/3d6f2122-7227-4095-a9a1-17bd958c4d81)

dengan menambahkan 
- pada "Key" : x-hasura-admin-secret
- pada "Value" : rahasia123

(rahasia123 merupakan Password untuk masuk ke Hasura)  <br/>

![WhatsApp Image 2024-12-10 at 22 38 05_2c4c99a3](https://github.com/user-attachments/assets/4ae242ba-afa8-4497-98aa-86b74b48ac83)


5. Kemudian pada bagian "Body" di Postman, kita masukkan Query darI Hasura Console  <br/>
(masukkan Query nya dengan cara Copy & Paste)  <br/>
(Hasura Console = Hasura yang ada di Rancher)  <br/>

![WhatsApp Image 2024-12-10 at 22 42 46_8f372fc7](https://github.com/user-attachments/assets/c373b703-c999-4e89-b4f2-130920e8541a)

- Berikut ini adalah tampilan  "Body" pada Postman yang sudah diberikan Query :
![WhatsApp Image 2024-12-10 at 22 45 03_7e936b17](https://github.com/user-attachments/assets/5fd8ac46-9c1f-43cf-ab70-e761ebc33504)

- sebelummya, kita perlu Copy Query ini dari Hasura Console, kemudian Paste ke Postman pada bagian "Body"
![WhatsApp Image 2024-12-10 at 22 52 08_491a7221](https://github.com/user-attachments/assets/a928a113-5f39-4016-929d-30d6569e0b61)
![WhatsApp Image 2024-12-10 at 22 52 08_01ded351](https://github.com/user-attachments/assets/2aef9a55-33dc-4cfc-89b3-789d9e2ef06f)


6. Pada Postman, kita Pilih Send untuk Hit 1 kali <br/>
![WhatsApp Image 2024-12-10 at 22 52 37_3530732e](https://github.com/user-attachments/assets/b1fe9cf9-f99f-47c6-9fd8-4a8b3fbf35c5)


7. Pada Postman, kita Pilih "Save" pada bagian atas  <br/>
![WhatsApp Image 2024-12-10 at 22 53 57_9e395c6f](https://github.com/user-attachments/assets/db9b2e8e-d591-4fec-9d16-705111477c59)

![WhatsApp Image 2024-12-10 at 22 53 58_36e9fb16](https://github.com/user-attachments/assets/d3e4bc80-6c79-456f-a582-403b968e9b4f)


8. Pada Postman, Pilih "titik tiga " (pada sebelah kiri)   <br/>
![WhatsApp Image 2024-12-10 at 22 56 31_3afe6f3d](https://github.com/user-attachments/assets/7c2bc229-dda0-4d5b-97f3-5ab8003667ab)

![WhatsApp Image 2024-12-10 at 22 56 31_46d3f346](https://github.com/user-attachments/assets/69eb4ece-eacb-4eaf-ac7b-c449b9280946)


9. Pilih "Run Collection"  <br/>
![WhatsApp Image 2024-12-10 at 23 01 33_dd628278](https://github.com/user-attachments/assets/2c1a6fde-474e-4c4c-9876-85c6520777b5)

![WhatsApp Image 2024-12-10 at 22 58 56_856874c6](https://github.com/user-attachments/assets/15a9c368-4906-4ac5-a46d-7ddc10c0a0b0)


10. Pada bagian "Iteration" masukkan angka sesuai jumlah berapa banyak kita ingin lakukan "Hit". <br/>
Misalnya: <br/>
kita masukkan 500 untuk Hit sebanyak 500 kali  <br/>
![WhatsApp Image 2024-12-10 at 23 03 42_7262a10d](https://github.com/user-attachments/assets/2b3115da-49cd-4856-abc8-415faf681ea0)

![WhatsApp Image 2024-12-10 at 23 02 01_54bf8cae](https://github.com/user-attachments/assets/eb765daf-fbec-4f91-beb8-ff9291b0df96)

![WhatsApp Image 2024-12-10 at 23 04 02_adddecf3](https://github.com/user-attachments/assets/113c5017-52a2-4284-8d5b-c16d62b1c2a0)


11. kemudian Pilih "Tombol Orange" untuk menjalankan Hit    <br/>
(ada di Pojok kanan bagian bawah)


12. Kemudian akan muncul Tampilan seperti ini  <br/>
![WhatsApp Image 2024-12-10 at 23 06 14_5d77c8c8](https://github.com/user-attachments/assets/e1786756-61e6-42dd-bf78-efbbcc1ab76c)

Berikut ini Tampilan jika kita sudah berhasil Hit di Postman :  <br/>
![WhatsApp Image 2024-12-10 at 23 08 23_aedf43eb](https://github.com/user-attachments/assets/b875bfa8-75f3-47df-9bec-f901bc28035e)

dapat kita lihat pada bagian kanan, status nya "200 OK" yang berarti semuanya berjalan dengan baik :  <br/>
![WhatsApp Image 2024-12-10 at 23 09 23_d252f919](https://github.com/user-attachments/assets/7e6a75b3-8866-4f82-be01-2b4eac562342)


12. kemudian kita Connect ke VPN, dan kita buka URL Elastic APM pada Browser.
Berikut ini URL nya :
http://10.100.13.25:5601/app/apm/services

untuk masuk halaman Elastic APM, kita  masukkan Username & Password untuk Elastic APM

![WhatsApp Image 2024-12-10 at 23 17 21_87ecf99a](https://github.com/user-attachments/assets/388f64f7-c091-4f63-a06e-8f35a49ba063)

-------
-------

# C) Analisa Log pada Web "Elastic APM"

1. Tampilan APM saat kita membuka menggunakan URL Berikut ini :  <br/>
http://10.100.13.25:5601/app/apm/services

![WhatsApp Image 2024-12-10 at 20 56 00_ebd32a27](https://github.com/user-attachments/assets/44dc24ea-ea9a-4738-8445-992fb88529ea)

2. Kemudian pilih ini : <br/>
![WhatsApp Image 2024-12-10 at 20 56 57_6ede799d](https://github.com/user-attachments/assets/a11cc6f1-4e4d-4751-b617-b8b5c330d721)

![WhatsApp Image 2024-12-10 at 20 56 58_23b7375f](https://github.com/user-attachments/assets/95af26a3-043b-4901-8528-17162ada58de)

3. Kemudian Berikut ini tampilannya : <br/>
![WhatsApp Image 2024-12-10 at 20 58 43_472b7157](https://github.com/user-attachments/assets/355ccec1-9ef2-496f-9a6f-89d7971622d8)


kemudian kita scroll kebawah

4. Latency & Throughput <br/>
![WhatsApp Image 2024-12-10 at 21 00 52_bdadfef9](https://github.com/user-attachments/assets/e15c1dce-153c-4f20-b5ac-5d270a3460af)

<...lakukan analisa>

5. Failed Transaction Rate  <br/>
![WhatsApp Image 2024-12-10 at 21 01 41_6e22c6c9](https://github.com/user-attachments/assets/74e3ab39-aa09-40cd-aac9-0e80cf2415eb)

<...lakukan analisa>

6. Trace Samples  <br/>
![WhatsApp Image 2024-12-10 at 21 03 39_69c45b17](https://github.com/user-attachments/assets/8c4afa1d-8a36-44e2-8283-e3ec414a6fa4)

Versi Zooom :   <br/>
![WhatsApp Image 2024-12-10 at 21 03 39_e1903e11](https://github.com/user-attachments/assets/18aaa347-650b-4c26-a5ef-3cb240a499e9)

<...lakukan analisa>

7. Pilih Tab yang ada di Sebelahnya, yaitu Tab Metadata  <br/>
![WhatsApp Image 2024-12-10 at 21 09 01_f3607140](https://github.com/user-attachments/assets/edb494bb-aac0-4dbf-8a6a-b33c02e050b8)
![WhatsApp Image 2024-12-10 at 21 09 01_ccb440f4](https://github.com/user-attachments/assets/7ea0d156-e37f-43ff-8647-0394e88a73d5)

![WhatsApp Image 2024-12-10 at 21 09 02_498631da](https://github.com/user-attachments/assets/fdf066db-eb5e-4a23-804d-f7d8a2b9b6b4)

![WhatsApp Image 2024-12-10 at 21 09 03_f942f897](https://github.com/user-attachments/assets/420f3845-4447-4161-8af9-1af6b898920a)
![WhatsApp Image 2024-12-10 at 21 09 03_3dc195b4](https://github.com/user-attachments/assets/0d151c32-89f3-4977-8ab1-1406bc2df5a1)

<...lakukan analisa>


8. Pilih Investigate  <br/>

![WhatsApp Image 2024-12-10 at 21 16 58_b723d7a5](https://github.com/user-attachments/assets/88df7da3-10f4-485f-a2a7-0be876bff305)
![WhatsApp Image 2024-12-10 at 21 16 58_c69d3ea1](https://github.com/user-attachments/assets/738219b2-8241-4b75-9774-1e341f3b96a3)


9. kemudian Pilih "View Transactions in Discover"   <br/>
![image](https://github.com/user-attachments/assets/46a99b63-1991-4449-b668-70eb0a936e7b)

Setelah itu, tampilannya seperti berikut ini : <br/>
![WhatsApp Image 2024-12-10 at 21 48 53_a2c5711a](https://github.com/user-attachments/assets/d27faf1c-8b03-490b-984f-9cc258c1d017)

10. Kemudian Perbesar bagian ini :  <br/>
![WhatsApp Image 2024-12-10 at 21 50 44_3b6dffcf](https://github.com/user-attachments/assets/667ef829-5884-47d9-9175-231874e11afa)
![WhatsApp Image 2024-12-10 at 21 50 44_b7bdb8a2](https://github.com/user-attachments/assets/368170aa-7f07-4295-b1ce-d432c3b56164)

11. Kemudian akan muncul Log seperti ini, <br/>
Lalu kita click "Copy Value"  <br/>
![WhatsApp Image 2024-12-10 at 21 52 13_9392190f](https://github.com/user-attachments/assets/8d6c7eca-8395-4cc8-8100-aaaf8c030f51)

