# Connect SQL Server to Hasura V2

Kita ingin menghubungkan "SQL Server" ke Hasura Version 2.  <br/>   <br/>

SQL Server yang kita pakai, adalah "SQL Server" yang sudah ter-install di VM Mas Muji.  <br/> <br/>

-> Akun VM Mas Muji :  <br/>
IP : 10.100.13.167        <br/>
Username : Administrator         <br/>
Password : *******************           <br/> <br/>

-> Akun "SQL Server" pada VM Mas Muji :      <br/>
Username : sa           <br/>
Password : *************           <br/> <br/>
Note : Pastikkan Akun ini memiliki izin akses untuk Membuat Database baru & Menambahkan Dataa

## A. Cara masuk ke VM Mas Muji
## (via Remote Desktop Connection )

### 1) Buka "Remote Desktop Connection"
![image](https://github.com/user-attachments/assets/5984062e-a916-4ff7-818a-d3e75f784ff0)

### 2) Masukkan IP milik VM Mas Muji
![image](https://github.com/user-attachments/assets/af4f7160-fad1-4d7a-b659-de5c3538d875)   <br/>
![image](https://github.com/user-attachments/assets/9c7ec34d-39a0-4391-89bd-ac7ce289c803)  

### 3) Masukkan Password milik VM Mas Muji
![image](https://github.com/user-attachments/assets/79160273-e828-4f68-b9b7-51563195b2db)


----------------
## B. "Create New Database" dan Tambahkan Data Baru

Buka Aplikasi "SQL Server" pada VM Mas Muji.

### 1) Pilih "New Database"
<img width="264" alt="image" src="https://github.com/user-attachments/assets/87900f4c-e0cf-4ff2-9873-2cd6d4c5b1f3" />

### 2) Ketik "Nama Database", kemudian pilih OK
<img width="537" alt="image" src="https://github.com/user-attachments/assets/8fd31fd3-da7a-4d1b-903f-485183dfffc5" />     <br/>
<img width="314" alt="image" src="https://github.com/user-attachments/assets/b3fb5424-dabb-466e-9a98-85cb5ef1eee2" />     <br/>
<img width="68" alt="image" src="https://github.com/user-attachments/assets/fdb09537-cc24-4e6a-b575-78e79bcf50b7" />    <br/>

### 3) "CREATE TABLE" (buat Table) pada Database yang sudah kita buat
![image](https://github.com/user-attachments/assets/840a5dbd-e682-4571-9fd8-8628ec1f9223)


### 4) "INSERT DATA" (Masukkan Data) ke Table yang tadi sudah kita buat 
![image](https://github.com/user-attachments/assets/d4de8bfb-0ede-4ac6-8bc8-75d67431741b)

--------
## C. Buka "Hasura Console" (untuk Hasura V2) Pada Rancher

Connect ke VPN, kemudian buka Rancher. <br/>
Setelah itu kita buka "Hasura Console" pada Rancheer <br/>

![image](https://github.com/user-attachments/assets/c2e41d9e-12a0-4e79-addd-38141f2d9351)

### 1) Pilih Tab "Data"
![image](https://github.com/user-attachments/assets/697202fd-17f7-4f64-a11b-aae0a49ca44a)  <br/>
![image](https://github.com/user-attachments/assets/89bf6d52-df2a-48a9-9855-5f1567323bfd)   <br/>

### 2) Pilih "Connect Database"
![image](https://github.com/user-attachments/assets/76be21e4-4ed4-43c7-bd48-0cddc01926e7)  <br/>
![image](https://github.com/user-attachments/assets/754559a9-887b-4730-a292-9637c447ab4a)


### 3) Pilih "MS SQL Server"
![image](https://github.com/user-attachments/assets/cf5420b6-1779-4a67-ab81-f48bba90c2a4)  <br/>
![image](https://github.com/user-attachments/assets/9b9d50ee-b0f1-4968-83cc-15234f20a7ff)


### 4) Pilih "Connect Existing Database"
![image](https://github.com/user-attachments/assets/9f8a48fc-8755-450e-9585-23722fd2eb72)


### 5) Masukkan "Database Name"
![image](https://github.com/user-attachments/assets/9c2f4b32-6625-4b88-8d85-3e618d1bac9b)
![image](https://github.com/user-attachments/assets/11815879-51f7-4c3c-b288-6de239d189f2)

### 6) Pilih "Database URL" pada bagian "Connect Database via"
![image](https://github.com/user-attachments/assets/4af6da3d-892b-443d-ab07-51c89e374134)

### 7) Masukkan "Database URL" untuk connect ke SQL Server padam VM Mas Muji (pada Server lain tempat "SQL Server" berada)
![image](https://github.com/user-attachments/assets/ee61569d-bd02-4ac8-9b43-9ad842ba9b56)
Berikut ini adalah "Database URL" yang kita masukkan 
```
Driver={ODBC Driver 18 for SQL Server};Server=10.100.13.167,1433;Database=tempdb;Uid=sql_admin;Pwd=password;Encrypt=optional
```
Note :
bagian "pwd" (untuk Password) diatas, tidak kami tuliskan Password asli yang digunakan. <br/>
Password asli tidak bisa kami tuliskan disini berhubung ini adalah Github untuk Public. <br/>
bagian "pwd" dapat kita tuliskan dengan Password yang kita gunakan untuk Login "SQL Server" di VM Mas Muji (atau di Server lainnya tempat "SQL Server" berada) <br/>


### 8) Pilih "Connect Database"
Pilih "Connect Database" pada bagian bawah  <br/>
![image](https://github.com/user-attachments/assets/f0fa1b78-1167-4ea3-8be0-9fcd58d3827d)









