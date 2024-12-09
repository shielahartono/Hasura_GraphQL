# Cara Menampilkan Metrices pada Elastic

-> Endpoint Elastic : 10.100.13.25:9200
<br/>
-> Endpoint Hasura : http://10.100.14.16:8332/v1/graphql
<br/>
("Endpoint Hasura" diambil dari URL yang ada di bagian atas saat kita membuka Hasura di Rancher). <br/><br/>

Note : <br/>
[-] Pada Postman, Kita melakukan Hit pada "Endpoint Elastic" adalah untuk mengecek apakah "Elastic sudah berjalan atau belum".
Note :  <br/>
- Melakukan pengecekkan dengan Hit "Endpoint Elastic" adalah untuk melihat apakah "Elastic sudah berhasil berjalan", bukan untuk melihat apakah Elastic sudah terhubung ke 'Open Telemetry' atau belum. Karena penghubungan antara 'Open Telemetery' dan 'Elastic' dilakukan menggunakan Server Ubuntu Linux, sehingga untuk mengecek apakah 'Open Telemetery' sudah dihubungkan ke 'Elastic', Pengecekkan dilakukan menggunakan Server Ubuntu Linux.

[-] Pada Postman, Kita melakukan Hit pada "Endpoint Hasura" adalah untuk "Menampilkan Metrics" pada Elastic.  <br/>
saat kita melakukan "Hit" menggunakan Postman, di bagian Body pada Postman, kita masukkan Query apa saja dari Hasura kita yang ada di Rancher. <br/><br/>


----
----
Pada analisa kali ini, kita akan melakukan analisa pada hasil dari Elastic pada bagian Metrics


Sebelum itu kita melakukan Perintah Put dan juga Post dengan menggunakan Postman


1. Berikut untuk penggunaan perintah Put pada postman

   Lakukan hit dengan alamat 10.100.13.25:9200/nama-indexmu -> Klik Send
![image](https://github.com/user-attachments/assets/c294f538-8cee-4aba-9a9a-4376217ad3df)


3. Dan berikut untuk penggunaan perintah Post pada postman
![image](https://github.com/user-attachments/assets/705356cd-234d-4fc5-aaa4-21672f66562b)


4. Maka pada Elastic apabila sudah melakukan hit akan terbaca pada bagian Data -> Index Management, seperti ini 
![image](https://github.com/user-attachments/assets/3293430c-d780-4fcc-991b-50b203430fc6)



5. Selanjutnya kita akan melakukan hit pada metric elastic melalui hasura graphql dan juga postman
![image](https://github.com/user-attachments/assets/9a380c9f-ad76-4d9b-81d7-3567e0637b8b)


6. Berikut adalah contoh hasil pada bagian metrics elastic ketika dilakukan hit
![image](https://github.com/user-attachments/assets/d7159e6f-dc13-4acf-880a-8b7f75ede409)
