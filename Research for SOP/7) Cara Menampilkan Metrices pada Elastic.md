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


----
----

# Menganalisa Metrics di Elasticsearch

## Panduan Penggunaan Elastic

Kita akan mengakses GUI Elastic menggunakan Kibana. 
  
### 1. Login ke Kibana
  
Terlebih dahulu login ke kibana untuk mengakses GUI Elastic. Masuk ke endpoint elasticsearch ganti port elastic 9200 (Port Default Elastic) menjadi 5601 (Port Default Kibana) dan lalu masukkan username dan password.
  
![screencapture-10-100-13-25-5601-login-2024-12-06-16_17_43](https://github.com/user-attachments/assets/e7f739b8-690c-47ce-ad4d-2a5a15e68568)

  
### 2. Masuk ke Discover

Setelah itu pergi ke Discover dengan cara klik `Discover` pada sidebar menu. Lebih jelasnya perhatikan gambar berikut.

![Screenshot (5) (1)](https://github.com/user-attachments/assets/38c6ca93-7e31-4113-8093-3f014b3cd54a)
  
### 3. Filter Data View
  
Kita dapat memfilter data yang ditampilkan dengan klik dropdown button di sebelah button `Data view` pada pojok kiri atas. 

![Screenshot (6)](https://github.com/user-attachments/assets/88a40089-da56-456c-b219-44528eac1644)

### 4. Munculkan Metrics
  
Setelah itu, pilih metrics untuk memfilter data yang dimunculkan hanya terkhusus pada metrics, metrics yang dimaksud adalah metrics dari sistem observasi atau monitoring aplikasi, khususnya terkait penggunaan dan performa layanan Hasura GraphQL Engine. Metrics seperti ini digunakan untuk memantau aktivitas, performa, dan status sistem yang berjalan. Perhatikan gambar berikut untuk lebih jelasnya.

![Screenshot (7)](https://github.com/user-attachments/assets/243118a8-cf76-4d37-9340-2045fd7f152b)

### 5. Fitur Filter Metrics

Kita dapat memfilter data Metrics dengan menggunakan KQL. KQL (Kibana Query Language) adalah bahasa kueri yang memungkinkan pengguna untuk membuat kueri secara cepat dan intuitif di Kibana, terutama untuk pencarian dan penyaringan data yang disimpan di Elasticsearch. Berikut panduan penggunaannya.
  
#### 1. Pilih kolom `Filter your data using KQL syntax`.
     
   ![Screenshot (7) (1)](https://github.com/user-attachments/assets/b63d3567-2253-4d55-8826-284dbe5db255)

#### 2. Ketikan field atau element yang ingin dicari atau difilter
  
Dalam hal ini kita menfilter metrics berdasarkan `host.name` atau `nama host` yang mengacu pada identitas atau nama dari server atau pod yang menangani permintaan.  

![Screenshot (8)](https://github.com/user-attachments/assets/24aeea6d-f23a-4cef-bf0d-731e035606be)

  
#### 3. Equals dan exist
  
Ketika selesai mengetikkan `field` atau `elemen` pada kolom filter, kolom filter akan memberikan `suggestion` antara `equals` dan `exist`.
  
![Screenshot (9)](https://github.com/user-attachments/assets/b9c51bff-9bb2-4338-b622-807cc2091c2c)


---
---
