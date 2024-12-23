# Connect SQL Server to Hasura V3

Kita ingin menghubungkan "SQL Server" yang ada di VM Mas Muji ke Hasura V3.  <br/> <br/>

Untuk Bisa menambahkan "SQL Server" ke Hasura V3, kita perlu terlebih dahulu meng-install Hasura V3 dengan PostgreSQL. <br/><br/>

Berikut ini adalah Link Dokumentasi yang kita gunakan untuk "install Hasura V3 dengan PostgreSQL" dan juga "Menghubungkan SQL Server dengan Hasura V3" <br/>
https://hasura.io/docs/3.0/quickstart/

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



------------------
------------------
# Catatan Kaki
## ini adalah Catatan Error apa saja yang tadi kita hadapi
