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


# Menghubungkan Hasura ke Postman

### 1. Unduh Postman
Langkah pertama adalah mengunduh Postman Desktop melalui tautan berikut ini: [https://www.postman.com/downloads/](https://www.postman.com/downloads/). Mengapa perlu menggunakan Postman Desktop? Walaupun Postman Web dapat digunakan, ia memerlukan *Postman Agent* untuk menghubungkan Hasura yang diprivate. Oleh karena itu, saya menggunakan Postman Desktop untuk mempermudah prosesnya.

### 2. Install dan Login
Setelah berhasil diunduh, lakukan instalasi Postman Desktop. Setelah itu, buat akun Postman terlebih dahulu dan login ke Postman Desktop. Setelah masuk, Anda akan melihat tampilan awal Postman seperti berikut.

![Screenshot (192)](https://github.com/user-attachments/assets/e47e04d2-7189-4454-903a-7f5d155a4b74)

  
### 3. Membuat API Request Baru
Untuk membuat *API Request* baru, klik tombol **New Request** pada pojok kanan atas. Anda akan diarahkan ke tampilan untuk membuat permintaan baru. Atau, Anda juga dapat mengklik tombol **New** pada *workspace* yang Anda gunakan, lalu pilih tipe permintaan seperti **HTTP Request**.

![Screenshot (194)](https://github.com/user-attachments/assets/867a522e-485b-4019-b1ad-3067c0ff4aa8)

Setelah itu kalian akan diarahkan kepada tampilan seperti berikut.

![Screenshot (193)](https://github.com/user-attachments/assets/505d323d-40e1-48a9-833d-be7bf1578428)
  

### 4. Ubah Request dari GET ke POST
Setelah masuk ke halaman *request*, ubah metode *request* dari **GET** menjadi **POST** seperti tampilan berikut.

![Screenshot (195)](https://github.com/user-attachments/assets/beb70a90-6adb-4fa3-b51d-f1d3bc8696d7)

  
### 5. Masukkan URL GraphQL Hasura
Selanjutnya, masukkan URL GraphQL Hasura yang ingin Anda koneksikan ke Postman. Jika Anda menggunakan *admin secret* (x-hasura-admin-secret) untuk mengakses Hasura, Anda bisa memasukkannya ke bagian **Headers** seperti contoh berikut. *Admin secret* ini dapat ditemukan di menu **API** di Hasura Anda.

![Screenshot (196)](https://github.com/user-attachments/assets/b52bf82f-9a72-4131-addc-f26503e2164b)

  
### 6. Menjalankan Query GraphQL
Masukkan *query* GraphQL yang tersedia dan yang ingin Anda jalankan pada kolom **Body**. Pastikan Anda memilih tipe **GraphQL** sebagai format *body*. Anda dapat merujuk pada gambar di bawah ini untuk lebih jelasnya.  

![Screenshot (197)](https://github.com/user-attachments/assets/4e675b99-aa77-4535-ba2a-764f03ef5c98)
  

### 7. Contoh Query
Di sini saya mencoba memasukkan *query* untuk menampilkan seluruh data pada tabel *todos* yang di-*join* dengan tabel *user*. 

#### Contoh Query:
```graphql
query MyQuery {
  todosGraphql {
    todos {
      done
      id
      text
      user {
        id
        name
      }
    }
  }
}
```

Hasil dari query akan muncul di bagian bawah seperti pada gambar berikut.  
  
![Screenshot (200)](https://github.com/user-attachments/assets/b11805c1-db6e-42fb-aad4-7b613e25e8c4)

# Menghubungkan Hasura ke Postman Menggunakan GraphQL

Selain menggunakan metode HTTP, Anda juga dapat menghubungkan Hasura ke Postman dengan memanfaatkan fitur bawaan Postman untuk GraphQL. Berikut langkah-langkahnya:

### 1. Memilih Mode GraphQL pada Postman

- Buka Postman dan buat request baru.
- Alih-alih memilih metode `HTTP`, pilihlah `GraphQL` seperti gambar di bawah ini.

![Screenshot (238)](https://github.com/user-attachments/assets/d2a6893b-a7c9-4fa7-99c6-82a248bfd2e3)


### 2. Konfigurasi URL dan Header

Setelah memilih mode `GraphQL`, Anda akan diarahkan ke halaman konfigurasi request GraphQL seperti berikut.

![Screenshot (239)](https://github.com/user-attachments/assets/4b2ff14a-d865-4531-bfe5-9d3977ea4ce1)

    
- Masukkan URL Hasura Anda pada kolom URL.
- Tambahkan header `x-hasura-admin-secret` dan isi dengan value yang sesuai.

## 3. Menampilkan Query yang Tersedia

Pada halaman query, klik tombol `Use GraphQL Introspection` untuk melihat query yang tersedia pada Hasura. Dengan fitur ini, Anda dapat mengeksplorasi skema GraphQL dan query yang dapat dijalankan.

![Screenshot (240)](https://github.com/user-attachments/assets/419c2303-d5f6-4d22-8ad5-349183c13ebf)


## 4. Mengeksplorasi Query GraphQL

Setelah melakukan introspection, Postman akan menampilkan query explorer yang memungkinkan Anda melihat skema GraphQL yang tersedia pada Hasura.

- Pilih query yang ingin dijalankan, kemudian salin query tersebut ke kolom query editor.

![Screenshot (241)](https://github.com/user-attachments/assets/d40cd684-d4d9-42f2-854b-eb4080e66d02)


## 5. Menjalankan Query

Setelah memasukkan query pada editor, klik tombol `Query` untuk menjalankan query. Hasil dari query yang dijalankan akan ditampilkan pada panel `Response` di Postman.

![Screenshot (242)](https://github.com/user-attachments/assets/342e444f-d471-4a90-8a6e-578a62f19925)


Dengan langkah-langkah di atas, Anda dapat dengan mudah menghubungkan Hasura ke Postman dan menjalankan query GraphQL secara langsung tanpa menggunakan metode HTTP.

----
----


# Menambahkan Remote Schema di Hasura

Langkah pertama untuk menambahkan *Remote Schema* pada Hasura adalah dengan masuk ke menu **Remote Schema**. Kemudian, klik tombol **Add** pada bagian kiri navigasi untuk menambahkan remote schema. Setelah itu, Anda akan diarahkan ke tampilan seperti berikut:

![image](https://github.com/user-attachments/assets/e92a9af5-7175-4680-8a18-3b56ae909410)

    
## Mengisi Remote Schema
1. Pada kolom **Remote Schema Name**, masukkan nama yang sesuai atau yang Anda inginkan untuk menandai schema.
2. Pada kolom **GraphQL Service URL**, masukkan URL Service yang mengarahkan ke GraphQL yang ingin Anda *remote* dari Hasura. Misalnya, Anda dapat memasukkan nama dan URL seperti berikut ini.

## Kustomisasi Root Field
Selanjutnya, gulir ke bagian bawah untuk **Customization GraphQL** dan tambahkan **Customization Root Field Namespace**. Hal ini bertujuan agar tabel pada schema disimpan dalam satu namespace sehingga tidak bercampur atau berantakan dengan schema lainnya. Kalian dapat merujuk pada gambar berikut.

![image](https://github.com/user-attachments/assets/ec499c25-d1bd-4806-af29-d3a11614fa02)

Jika pengaturan sudah selesai, klik **Save** untuk mengimplementasikan. 
  
## Menguji Remote Schema dengan Query
Setelah selesai menambahkan remote schema, cobalah untuk melakukan *query* GraphQL pada schema tersebut. Anda bisa masuk ke menu **API** dan menuliskan langsung *Query GraphQL* yang tersedia untuk dijalankan.

### Contoh Query:
```graphql
query MyQuery {
  todosGraphql {
    todos {
      done
      id
      text
      user {
        id
        name
      }
    }
  }
}
```

Hasil dari query akan muncul di bagian bawah seperti pada gambar berikut.

![image](https://github.com/user-attachments/assets/6a5e4fc3-d36c-4c5d-a17e-006ce0864c7f)
