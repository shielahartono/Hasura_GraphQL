# Connect SQL Server to Hasura V3

Kita ingin menghubungkan "SQL Server" yang ada di VM Mas Muji ke Hasura V3.  <br/> <br/>

Untuk Bisa menambahkan "SQL Server" ke Hasura V3, kita perlu terlebih dahulu meng-install Hasura V3 dengan PostgreSQL. <br/><br/>

Berikut ini adalah Link Dokumentasi yang kita gunakan untuk "install Hasura V3 dengan PostgreSQL" dan juga "Menghubungkan SQL Server dengan Hasura V3" <br/>
https://hasura.io/docs/3.0/quickstart/

 ( Dan juga pastikkan pada Powershel WSL sudah terinstall Docker, jika belum kita bisa ikuti link dokumentasi ini : https://docs.docker.com/engine/install/ubuntu/ ) 

## A. Install Hasura V3 dengan PostgreSQL

### 1) Buka Powershell

### 2) Ketik `wsl` kemudian tekan Enter
`wsl`
![image](https://github.com/user-attachments/assets/17f28ec6-75cb-46e3-a167-113e1253f457)   <br/>

Note :  <br/>
`wsl` harus sudah  di-install pada Powershell

### 3) jalankan Command untuk "Install DDN CLI"
```
curl -L https://graphql-engine-cdn.hasura.io/ddn/cli/v4/get.sh | bash
```

### 4) Jalankan Command `ddn doctor`
```
ddn doctor
```
![image](https://github.com/user-attachments/assets/3049fbc5-b6e5-4665-b64d-661c1639caad)

`ddn doctor` untuk memeriksa apakah dependensi (Docker dan Docker Compose) DDN CLI telah diinstal, apakah versinya diperlukan, dan apakah sedang berjalan.

### 5) Jalankan Command `ddn auth login`
```
ddn auth login
```
![image](https://github.com/user-attachments/assets/10d781fb-c977-4f18-b584-9f1ca1449740)

- `ddn auth login` merupakan authentikasi untuk login ke ddn cli

Nanti akan muncul Browser yang meminta kita untuk Login, setelah itu, akan muncul tampilan pada Browser seperti ini :  <br/>
![image](https://github.com/user-attachments/assets/e7a8f7d4-9e43-461a-87bf-c3b188cc4144)

ddn auth login 

Perintah **ddn auth login** biasanya digunakan dalam konteks command-line interface (CLI) untuk mengotentikasi pengguna ke dalam layanan atau platform tertentu yang menggunakan DDN (Dynamic Data Network) atau sistem penyimpanan terdistribusi. Fungsi utamanya adalah:

1. *Mengotentikasi Pengguna*: 
   - Perintah ini memungkinkan pengguna untuk masuk ke sistem menggunakan kredensial mereka (seperti username, password, atau token API). 

2. *Mengakses Fitur atau Data yang Dilindungi*:
   - Setelah berhasil login, pengguna biasanya mendapatkan akses ke fitur atau data yang memerlukan otorisasi.

3. *Menyimpan Token Otentikasi*:
   - Dalam banyak kasus, perintah ini akan menghasilkan token otentikasi yang dapat digunakan untuk melakukan operasi selanjutnya tanpa harus login ulang.

4. *Integrasi dengan Sistem DDN*:
   - Jika perintah ini digunakan dalam konteks penyimpanan data terdistribusi seperti DDN, maka tujuannya adalah untuk memungkinkan akses ke resource yang dikelola oleh DDN, seperti penyimpanan file, analisis data, atau layanan lainnya.

Jika memiliki konteks spesifik (misalnya, platform atau sistem tertentu di mana perintah ini digunakan), saya dapat memberikan penjelasan lebih rinci. Apakah Anda mengacu pada layanan atau aplikasi tertentu?

### 6) Jalankan Command `ddn supergraph init mysupergraph` dan `cd mysupergraph`
```
ddn supergraph init mysupergraph
cd mysupergraph
```
Lalu nanti pilih "PostgreSQL"
![image](https://github.com/user-attachments/assets/947e7ef6-2a1e-4600-b433-f7b4bf3351d6)


**Inisialisasi Supergraph Baru**
Langkah pertama adalah membuat sebuah proyek Supergraph baru menggunakan perintah ddn supergraph init. Proyek ini akan menjadi kerangka awal untuk aplikasi Supergraph Anda.

Langkah-langkah:
Jalankan perintah berikut untuk menginisialisasi supergraph:

```
ddn supergraph init mysupergraph
```
Perintah ini akan membuat direktori baru bernama mysupergraph yang berisi file dan folder yang diperlukan untuk proyek Supergraph.

Pindah ke direktori yang baru dibuat:

```
cd mysupergraph
```
Setelah masuk ke direktori ini, Anda dapat menjalankan perintah berikut untuk melihat isi direktori:

```
ls
```
Anda akan melihat file dan folder yang sudah disiapkan untuk Anda, seperti file konfigurasi dan template proyek.

### 7) Jalankan Command `ddn connector init my_connector -i`
```
ddn connector init my_connector -i
```

**Menghubungkan ke Data**
Langkah berikutnya adalah menghubungkan Supergraph ke sumber data menggunakan data connector. Dalam contoh ini, kita akan menggunakan konektor Hasura/Postgres untuk terhubung ke database PostgreSQL.

Langkah-langkah:
Pilih konektor data Hasura/Postgres dari dropdown (jika menggunakan antarmuka interaktif). Anda juga bisa langsung menggunakan perintah untuk menginisialisasi konektor.

Jalankan perintah berikut untuk menginisialisasi konektor:

```
ddn connector init my_connector -i
```
Perintah ini akan memulai proses inisialisasi konektor dengan mode interaktif (-i).

Saat diminta memasukkan URL koneksi database, gunakan URL berikut:

```
postgresql://read_only_user:readonlyuser@35.236.11.122:5432/v3-docs-sample-app
```

URL ini mengarahkan konektor ke database PostgreSQL sampel milik Hasura.

Setelah konektor berhasil diatur, konfigurasi akan otomatis disimpan dalam proyek Supergraph Anda.

### 8) Jalankan Command `ddn connector introspect my_connector`
```
ddn connector introspect my_connector
```
![image](https://github.com/user-attachments/assets/469f92c4-7cb8-4939-873f-f00cf3343faa)

`ddn connector introspect my_connector` dalam konteks Hasura Data Delivery Network (DDN) digunakan untuk memeriksa atau mengintrospeksi connector tertentu yang sudah diatur. Proses ini memungkinkan Anda untuk memahami skema, tabel, atau sumber data yang terkait dengan konektor tersebut.

### 9) Jalankan Command untuk "Add Resources"
```
ddn model add my_connector '*'
ddn command add my_connector '*'
ddn relationship add my_connector '*'
```
![image](https://github.com/user-attachments/assets/e6a747c6-c199-4502-bc8e-eceaa8cab989)
![image](https://github.com/user-attachments/assets/25f97416-f681-4ded-97d1-c2278a7eb0d6)
![image](https://github.com/user-attachments/assets/a3686f12-842b-4610-92eb-0eef3a5864be)

Command tersebut untuk menambahkan resources Model, Command, dan Relationship.  <br/><br/>

connector_sql adalah fitur yang membuat DDN bisa terhubung ke database SQL. <br/>
Dengan connector_sql , DDN bisa membaca, menulis, atau mengambil data dari database SQL. <br/><br/>


1) ddn model add connector_sql '*'  		<br/>
-> menambahkan Model bernama connector_sql <br/>
-> command ini penting untuk memberitahu DDN bahwa ia harus bisa terhubung ke database SQL.  <br/>
Tanpa perintah ini, DDN tidak akan tahu cara membaca data dari database SQL. <br/> <br/>


2) ddn command add connector_sql '*'		 <br/>
-> menambahkan Command yang berkaitan dengan connector_sql <br/>
-> Command ini digunakan untuk menambahkan semua perintah yang diperlukan oleh model connector_sql.  <br/>
yang mana, ini memberikan kemampuan kepada connector_sql untuk menjalankan berbagai tugas atau operasi di database SQL. <br/>
-> Tanpa command "ddn command add connector_sql '*'"  ,  Model hanya bisa "melihat" database, tapi tidak bisa membaca atau mengubah isinya. <br/><br/>

-> Contoh :<br/>
Dengan command ini, Model bisa membaca data, menambah data baru, atau menghapus data lama. <br/><br/>

3) ddn relationship add connector_sql '*'		  <br/>
-> menambahkan Relationship untuk connector_sql <br/>
-> Command ini digunakan untuk menambahkan semua hubungan (relationship) yang diperlukan oleh model connector_sql agar bisa berinteraksi dengan model lain dalam sistem DDN.  <br/>
-> Command ini membuat connector_sql bisa berbagi data atau berkomunikasi dengan model-model lain di dalam DDN. <br/>
-> Tanpa Relationship ini, connector_sql hanya bisa bekerja sendiri. Misalnya, dia bisa mengambil data dari database SQL, tapi tidak bisa memberikan data itu ke model lain yang membutuhkannya. <br/>
-> Relationship ini penting agar data yang diambil dari database SQL bisa diproses, digunakan, atau disebarkan ke seluruh sistem.  <br/>
Tanpa Realtionship ini, data tidak akan  berguna untuk model lain. <br/><br/>

### 10) Jalankan command `ddn supergraph build local`
```
ddn supergraph build local
```
![image](https://github.com/user-attachments/assets/07048c2b-2857-42b5-8e63-9640a1f4282d)

**ddn supergraph build local** digunakan untuk membangun supergraph secara lokal dalam ekosistem Hasura Data Delivery Network (DDN).

### 11) Jalankan Command `ddn run docker-start`
```
ddn run docker-start
```
Note : jika command ini tidak berhenti dalam waktu yang cukup lama, maka kita buka Terminal Powershell baru untuk menjalankan Command berikutnya

![image](https://github.com/user-attachments/assets/35db4ba6-99b8-429f-a351-10963664c669)

Langkah 1: Menjalankan Supergraph
Supergraph mengelola query GraphQL dan interaksi antara layanan. Jalankan engine, connector, dan layanan lain (seperti observability) dengan memverifikasi container aktif menggunakan docker ps.

Langkah 2: Perintah ddn run docker-start
Perintah ini memulai semua container yang diperlukan (engine, connector, database) secara otomatis menggunakan Docker Compose. Setelah dijalankan, periksa status dengan docker ps, dan supergraph siap digunakan.


### 11) Jalankan Command `ddn console --local`
```
ddn console --local
```
![image](https://github.com/user-attachments/assets/7c673c7e-3447-410f-9e13-0daa3d31256a)

Kemudian nanti akan terbuka "Hasura Console" (untuk versi V3)
![WhatsApp Image 2024-12-23 at 09 47 38_2f61f491](https://github.com/user-attachments/assets/01a992e6-5689-424f-b2a3-2eebbce7d5b2)

![WhatsApp Image 2024-12-23 at 09 47 39_8ccf83c7](https://github.com/user-attachments/assets/de072af1-0b55-4935-a8fc-773f931e2fe8)

------
## B. Connect "SQL Server" ke Hasura V3

### 1) Buka Powershell

### 2) Ketik `wsl` kemudian tekan Enter
`wsl`
![image](https://github.com/user-attachments/assets/17f28ec6-75cb-46e3-a167-113e1253f457)   <br/>

Note :  <br/>
`wsl` harus sudah  di-install pada Powershell

### 3) jalankan Command untuk "Install DDN CLI"
```
curl -L https://graphql-engine-cdn.hasura.io/ddn/cli/v4/get.sh | bash
```

### 4) Jalankan Command `ddn doctor`
```
ddn doctor
```
![image](https://github.com/user-attachments/assets/3049fbc5-b6e5-4665-b64d-661c1639caad)



### 5) Jalankan Command `ddn auth login`
```
ddn auth login
```
![image](https://github.com/user-attachments/assets/10d781fb-c977-4f18-b584-9f1ca1449740)

- `ddn auth login` merupakan authentikasi untuk login ke ddn cli

Nanti akan muncul Browser yang meminta kita untuk Login, setelah itu, akan muncul tampilan pada Browser seperti ini :  <br/>
![image](https://github.com/user-attachments/assets/e7a8f7d4-9e43-461a-87bf-c3b188cc4144)


### 6) Jalankan Command `ddn supergraph init mysupergraph` dan `cd mysupergraph`
```
ddn supergraph init mysupergraph
cd mysupergraph
```
Lalu nanti pilih "PostgreSQL"
![image](https://github.com/user-attachments/assets/947e7ef6-2a1e-4600-b433-f7b4bf3351d6)



### 7) Jalankan Command `ddn connector init my_connector -i`
```
ddn connector init my_connector -i
```



### 8) Jalankan Command `ddn connector introspect my_connector`
```
ddn connector introspect my_connector
```
![image](https://github.com/user-attachments/assets/469f92c4-7cb8-4939-873f-f00cf3343faa)

Nanti akan diminta untuk kita masukkan "Database URI" untuk SQL Server,  <br/>
berikut ini Database URI nya : <br/>
```
Server=10.100.13.167;Database=sql_admin_db;User Id=sql_admin;Password=password;TrustServerCertificate=true;
```
note : Password diatas tidak menggunakan Password asli yang kita gunakan 



### 9) Jalankan Command untuk "Add Resources"
```
ddn model add my_connector '*'
ddn command add my_connector '*'
ddn relationship add my_connector '*'
```
![image](https://github.com/user-attachments/assets/e6a747c6-c199-4502-bc8e-eceaa8cab989)
![image](https://github.com/user-attachments/assets/25f97416-f681-4ded-97d1-c2278a7eb0d6)
![image](https://github.com/user-attachments/assets/a3686f12-842b-4610-92eb-0eef3a5864be)


### 10) Jalankan command `ddn supergraph build local`
```
ddn supergraph build local
```
![image](https://github.com/user-attachments/assets/07048c2b-2857-42b5-8e63-9640a1f4282d)



### 11) Jalankan Command `ddn run docker-start`
```
ddn run docker-start
```
Note : jika command ini tidak berhenti dalam waktu yang cukup lama, maka kita buka Terminal Powershell baru untuk menjalankan Command berikutnya

![image](https://github.com/user-attachments/assets/35db4ba6-99b8-429f-a351-10963664c669)




### 11) Jalankan Command `ddn console --local`
```
ddn console --local
```
![image](https://github.com/user-attachments/assets/7c673c7e-3447-410f-9e13-0daa3d31256a)

Kemudian nanti akan terbuka "Hasura Console" (untuk versi V3)
![WhatsApp Image 2024-12-23 at 09 47 38_2f61f491](https://github.com/user-attachments/assets/01a992e6-5689-424f-b2a3-2eebbce7d5b2)

![WhatsApp Image 2024-12-23 at 09 47 39_8ccf83c7](https://github.com/user-attachments/assets/de072af1-0b55-4935-a8fc-773f931e2fe8)


------------------
------------------
# Catatan Kaki
## ini adalah Catatan Error apa saja yang tadi kita hadapi
