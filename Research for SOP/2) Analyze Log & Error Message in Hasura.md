# Analyze Log & Error Message in Hasura

-> Where do you See Error Messages ? <br/>
(dimana kita bisa melihat Error Messages) <br/>
<br/>
[-] Hasura Console :  <br/>
Pada Hasura Console, kita dapat melihat Error Messages, salah satunya kita dapat melihat di "API Explorer" <br/>
<br/>
[-] API Response : <br/>
Error Messages dapat kita lihat Pada "Response Body" <br/>
<br/>
[-] Server Logs :  <br/>
Saat kita menjalankan Hasura pada Server atau Container, <br/>
yakni seperti Docker atau Kuberntes, <br/>
Logs dapat kita lihat melalui "Terminal" <br/>
<br/>

-> Menganalisis Log (Analyze Log) merupakan Langkah penting untuk Debugging Issue, yakni untuk Mengidentifikasi, Meng-Diagnosa, dan Memperbaiki Masalah. <br/>


## A. Why "Linux", "Docker", and "Kubernetes" are important for Troubleshooting ? <br/>
## (Mengapa Linux, Docker, dan Kubernetes penting untuk Troubleshooting) <br/>


### 1) Linux : 
Linux merupakan Operating System yag berjalan pada Server kita. <br/>
Linux membantu kita untuk Mengakses "Server-Level Logs", "System Resources", dan"Configurations". <br/>
<br/>
[-] Server-Level Logs :  <br/>
Linux menyediakan akses ke "System Logs" untuk menangkap informasi detail mengenai apa yang terjadi di dalam System. <br/>
<br/>
[-] System Resources : <br/>
Linux menyediakan akses ke "System Resources" untuk memonitor penggunaan Resources (Sumber Daya) seperti 'CPU Usage' , 'Memory' , dan 'Disk Space' untuk mengidentifikasi kendala pada Sumber Daya yang dapat mempengaruhi Aplikasi (seperti Hasura). <br/>
<br/>
[-] Configuration Files : <br/>
Linux menyediakan akses ke "Configuration Files", <br/>
yang mana kita dapat meng-akses dan memodifikasi Configuration Files untuk memastikkan System telah diatur dengan benar. <br/>
"Configuration Files" mengontrol perilaku System (System Behavior). <br/>
<br/>

### 2) Docker :  <br/>
-> Docker memungkinkan kita untuk Troubleshoot Container tertentu (Specific Container) tanpa mempengaruhi bagian lainnya pada System.
(Troubleshoot The Specific Container)  <br/>

-> Docker menyediakan "Consistent Environment" dan "Isolates Problems" dalam Container.  <br/>

-> "Consistent Environment" memiliki arti bahwa Aplikasi akan Berjalan dengan cara yang sama, tidak masalah pada Environment manapun Aplikasi tersebut di-Deploy. <br/>
(Application will run in the same way, regardless of where the application is deployed), <br/>
Misalnya Aplikasi di-deploy pada Local Machine, pada Test Server, atau pada Production Environment di Cloud, <br/>
Consistency akan tetap terjaga melalui penggunaan "Container" pada Docker. <br/>
<br/>
-> "Isolates Problem" ini berarti Masalah pada sebuah Container tidak akan mempengaruhi Container lainnya. <br/>
"Isolaltion" sendiri berarti Setiap Container berjalan secara independen dengan Environment, Resources, dan Dependencies nya sendiri. <br/>
yang mana, "Isolation" membantu mencegah Problem yang terjadi pada satu Container agar tidak mempengaruhi Container lainnya, dan juga tidak mempengaruhi Host System. <br/>

-> Troubleshooting dengan Docker melibatkan pengecekkan "Container Log", "Resource Usage", dan "Network Configuration". <br/>
Docker memastikkan Environment tempat Hasura berjalan terisolasi (isolated) dan dapat direproduksi (Reproducible). <br/>
"Reproducible" atau "Reproducibility" artinya kita bisa membuat ulang (re-create) Environment yang berjalan pada Development, Testing, Staging, atau Production. <br/> <br/>

### 3) Kubernetes : <br/>
-> Kubernetes memungkinkan kita untuk Manage, Scale, dan Monitor Hasura pada 'Distributed Containerized Environment'. <br/>
<br/>
("Distributed Containerized Environment" merupakan System tempat beberapa Container dijalankan dan dikelola di seluruh rangkaian Machines atau Node yang terdistribusi, <br/>
yang seringkali mencakup beberapa Server, Data Center, atau Cloud Regions) <br/> <br/>


## B. Where to Find "Hasura Log" ?
## (Dimana menemukan "Hasura Log")
-> "Error Message" berada di dalam "Hasura Log", tetapi adalah Dua Hal yang berbeda untuk dianalisa. <br/>

-> Disini kita akan membahas cara menemukan "Hasura Log",  <br/>
yang mana didalam "Hasura Log" tersebut juga terdapat "Error Message" <br/> <br/>

### 1. Hasura Console (Self-Hosted)
-> "Self-Hosted" berarti kita meng-install Hasura di Laptop atau Machine kita sendiri (menggunakan Docker atau Kubernetes), <br/>
maka kita bisa mengecek "Hasura Console".  <br/>
<br/>
-> Cara melihat Log pada "Hasura Console" : <br/>
(1) Buka "Hasura Console" pada Browser <br/>
(2) Pilih Tab "Monitoring" <br/>
(3) Dibawah "Logs" atau "Request Logs", kita bisa menemukan Detail Logs milik GraphQL Requests. <br/>
(4) Kita dapat melakukan Filter dengan "Timestamps" atau dengan "requestID" untuk menemukkan "exact error" (untuk menemukkan letak Error yang pasti). <br/>
Contoh Timestamp : <br/>
(`2024-11-14T12:05:00Z`) <br/>
<br/>
>> ^For your information^ <br/>
>> ### {1} Cara baca Timestamp : 
>> `2024-11-14T12:05:00Z` <br/>
>>  <br/>
>> -> Format Jam ini menunjukkan Format "ISO 8601" <br/>
>>  ```
>>  YYYY-MM-DDTHH:MM:SSZ
>>  ```
>>  [-] `T` : adalah huruf yang memisahkan antara "Date" dan "Time" <br/>
>> <br/>
>> <br/>
>>  -> Date : `2024-11-14` <br/>
>>  [-] `2024` : The Year (Tahun) <br/>
>>  [-] `11` : The Month (Bulan) , yaitu November (Bulan ke-11) <br/>
>>  [-] `14`: The Day (Tanggal) , yaitu Tanggal 14 atau Hari ke-14 pada Bulan tersebut <br/>
>>  <br/>
>>  Jadi "Date" tersebut adalah November 14, 2024 <br/>
>>  <br/>
>> -> Time : `12:05:00` <br/>
>> [-] `12` : The Hour (Jam), jam tersebut dalam 24-hour Format, yang berarti jam tersebut >>  adalah Pukul 12 Siang atau 12 PM <br/>
>> [-] `05` : The Minutes (Menit) <br/>
>> [-] `00` : The Seconds (Detik) <br/>
>> <br/>
>> Jadi "Time" tersebut adalah 12:05:00 PM  (Dengan Format 24-hour) <br/>
>>  <br/>
>>  -> Timezone :  `Z`  <br/>
>>  [-] huruf `Z` diakhir merupakan kepanjangan dari "Zulu Time".  <br/>
>>  yang mana "Zulu Time" sama dengan "UTC" (Coordinated Universal Time) <br/>
>>  <br/>
>> [-] Timezone untuk Indonesia bagian Barat (WIB), seperti Jakarta adalah **UTC+7**   <br/>
>> , yang mana jika kita ingin Konversikan (ubah) jam UTC ke jam UTC+7 , kita hanya perlu >> menambah 7 jam. <br/>
>> yaitu Pukul 19:05:00 PM waktu Indonesia bagian Barat (UTC+7) <br/>
>>  <br/>
>> Jadi "Timezone" yang dipakai adalah **UTC** (Coordinated Universal Time) <br/> <br/>
>> 

## 2. Docker or Kubernetes Logs

-> Jika Hasura kita berjalan di dalam "Docker Container" atau pada "Kubernetes Cluster",
maka Logs dapat diakses melalui Command pada "Terminal" <br/>
<br/>

### 2.1) Cara mengecek Logs pada Docker melalui Terminal : <br/>

#### (1) Menampilkan Log untuk Spesifik Container : <br/>
#### (Menampilkan Log utnuk Container tertentu)  <br/>
Jalankan Command ini pada Terminal :
```
docker logs <container_name>
```

contoh : <br/>
Nama Container adalah : my-app-container  <br/>
, maka Contoh Command pada Terminal adalah : <br/>

```
docker logs my-app-container
```

#### (2) Menampilkan Log dengan Timestamp untuk Spesifik Container :
Jalankan Command ini pada Terminal :
```
docker logs --timestamps <container_name>
```
contoh : <br/>
Nama Container adalah : my-app-container  <br/>
, maka Contoh Command pada Terminal adalah : <br/>

```
docker logs --timestamps my-app-container
```

#### (3) Menampilkan Log secara Real-Time untuk Spesifik Container :
```
docker logs -f <container_name>
```
contoh : <br/>
Nama Container adalah : my-app-container  <br/>
, maka Contoh Command pada Terminal adalah : <br/>
```
docker logs -f my-app-container
```
[-] `-f` = memberitahu Docker untuk mengikuti Logs secara Real-Time   <br/>


#### (4) Menampilkan Log mulai dari Jangka Waktu tertentu untuk Spesifik Container :
#### (View Logs "Since" Specific Time Range for Spesific Container)
-> Kita bisa menggunakan `--since` untuk menampilkan Logs mulai dari Periode waktu tertentu  <br/> 
<br/>
-> Misalnya, Kita ingin menampilkan Logs yang terbentuk semenjak 10 Menit terakhir :
```
docker logs --since 10m my-app-container
```
[-] `10m` = 10 menit terakhir (Berarti kita ingin menampilkan Log yang terbentuk selama 10 menit terakhir) <br/>
[-] `my-app-container` =  merupakan nama Container yang ingin kita lihat Log nya <br/>

<br/> <br/>
`10m` merupakan format Waktu yang berarti "menit", yang mana Format tersebut dapat kita ganti ke "hour"(jam) atau "day"(hari), <br/>
contoh seperti ini : <br/>
[-] `10m` = 10 menit terakhir (untuk melihat Log yang terbentuk selama 10 hari terakhir) <br/>
[-] `2h` = 2 hours terakhir atau 2 jam terakhir (untuk melihat Log yang terbentuk selama 2 jam terakhir) <br/>
[-] `1d` = 1 day terakhir atau 1 hari terakhir (untuk melihat Log yang terbentuk selama 1 hari terakhir) <br/>

<br/>

-> Misalnya, Kita ingin menampilkan Logs yang terbentuk semenjak Timestamp tertentu : <br/>
(kita ingin menampilkan Logs yang terbentuk semenjak Waktu & tanggal sepesifik tertentu) 
```
docker logs --since "2024-11-15T14:00:00" my-app-container
```
[-] `"2024-11-15T14:00:00"` = merupakan Timestamp (Berarti kita ingin menampilkan Log yang terbentuk semenjak Timestamp ini) <br/>
[-] `my-app-container` =  merupakan nama Container yang ingin kita lihat Log nya <br/>

<br/>
<br/>
-> Menampilkan Logs dengan "Time Range" menggunakan `--since` dam `--until` <br/>
- Kita dapat mengkombinasikan `--since` dengan `--until` untuk memperinci waktu "Start" dan waktu "End" untuk Logs. <br/>

- Contoh :
```
docker logs --since "2024-11-15T14:00:00" --until "2024-11-15T16:00:00" my-app-container
```
[-] `--since "2024-11-15T14:00:00"` = berarti kita menampilkan Logs yang terbentuk semenjak 15 November 2024, pada Jam 14.00  <br/>
[-] `--until "2024-11-15T16:00:00"` = berarti kita menampilkan Logs yang terbentuk sampai 15 November 2024, pada Jam 16.00   <br/>
[-] `my-app-container` =  merupakan nama Container yang ingin kita lihat Log nya <br/>
<br/>
Jadi Command diatas meminta untuk menunjukkan Logs mulai dari jam 14.00 sampai 16.00 UTC pada 15 November, 2024.  <br/> <br/>

#### (5) Menampilkan Daftar Log dengan jumlah tertentu <br/>
-> Misalnya kita ingin melihat 50 baris Log terakhir yang terbentuk, maka kita bisa gunakan `--tail`
Contoh :
```
docker logs --tail 50 my-app-container
```
[-] `--tail 50` =  50 baris Log terakhir yang terbentuk. <br/>
Jumlah baris Log nya tidak harus 50, kalau misalnya kita ingin melihat 100 baris Log terakhir yang terbentuk, maka kita bisa menggunakan `--tail 100` pada Command. <br/>
[-] `my-app-container` =  merupakan nama Container yang ingin kita lihat Log nya <br/>
<br/>
<br/>

#### (6) Menampilkan Logs dengan beberapa Kombinasi Command diatas :
- Misalnya kita ingin melihat Logs secara "Real-Time", kita ingin pada Logs tersebut terdapat "Timestamp", <br/> dan kita hanya ingin melihat "100 baris Logs terakhir" yang terbentuk. <br/>
Contoh :
```
docker logs -f --timestamps --tail 100 my-app-container
```
[-] `-f` = untuk menunjukkan Logs secara "Real-Time"  <br/>
[-] `--timestamps` = untuk meampilkan "Timestamps" pada Logs  <br/>
[-] `--tail 100` = untuk menampilkan 100 Baris Terakhir Logs yang terbentuk  <br/>


### 2.2) Cara mengecek Logs pada Kubernetes melalui Terminal :

-> Kubernetes merupakan sebuah System yang membantu kita Mengelola Aplikasi (manage applications) yang berjalan pada Containers (seperti Docker, yang mana Docker merupakan 'Container Technology'). <br/>
<br/>
-> Saat kita menerapkan Hasura di Kubernetes,  <br/>
maka Hasura berjalan di Pod. <br/>
yang mana "Pod mengandung Satu atau Lebih Containers".  <br/> <br/> 

<br/>

#### (1) Menampilkan Logs dari Pod tertentu : <br/>
#### (View Logs dari Pod tertentu)

```
kubectl logs <pod_name>
```
kemudian ganti `<pod_name>` dengan "Nama Pod" yang ingin kita lihat Log nya.  <br/>
Contoh : <br/>
```
kubectl logs hasura-abc123
```
[-] `hasura-abc123` = merupakan "Nama Pod" <br/>
<br/>

#### (2) Menampilkan Logs dari Container tertentu (Jika terdapat Multiple Container dalam satu Pod) <br/>

-> Misalnya Suatu Pod mempunyai Multiple Containers (lebih dari Satu Container), <br/>
maka kita dapat menggunakan Command berikut untuk mengecek Logs : <br/>
```
kubectl logs <pod_name> -c <container_name>
```
Contoh :
```
kubectl logs hasura-abc123 -c hasura
```
[-] `-c` = merupakan kepanjangan dari "Container",  <br/>
yang mana `-c` memungkinkan kita untuk menetukkan Container yang mana yang ingin kita tampilkan Log nya,   <br/>
(yang mana Container tersebut berada di dalam Pod)   <br/>

[-] `hasura-abc123` = merupakan "Nama Pod"   <br/>
[-] `hasura`	= merupakan "Nama Container"   <br/>

Jadi kita ingin melihat Container yang bernama "hasura",    <br/>
yang mana Container tersebut berada di dalam Pod "hasura-abc123"   <br/>

#### (3) Menampilkan Logs untuk Semua Container yang ada di dalam Pod : 

-> Sebuah Pod berisi banyak Container, <br/>
dan kita ingin menampilkan Logs untuk semua Container yang berada di dalam Pod tersebut.

```
kubectl logs <pod_name> --all-containers=true
```
contoh :
```
kubectl logs hasura-abc123 --all-containers=true
```
[-] `hasura-abc123` = merupakan "Nama Pod"  <br/>
<br/> 
Jadi kita ingin Menampilkan Logs untuk semua Container yang ada di Pod "hasura-abc123"  <br/>  <br/> 

>> ^For your Information^ <br/>
>> ### Pengecekkan Logs jika Pod mengandung Multiple Containers :
>> <br/>
>> Misalnya kita mempunyai Sebuah Pod yang berisi Multiple Containers, <br/>
>> jika kita lihat penjelasan beberapa Jenis Command diatas, maka kita berfikir kita bisa memakai Banyak Jenis Command. <br/>
>> Mari kita bahas Jenis Command jika kita gunakan untuk mengecek Logs untuk Pod yang mengandung Multiple Containers : <br/>
>>
>> #### (1) `kubectl logs <pod_name>`
>> -> Jika kita menggunakan Command diatas, maka akan muncul error seperti ini :
>>   ```
>>	error: a container name must be specified for pod <pod_name>, because there are multiple containers in the pod
>>   ```
>>  [-] `a container name must be specified for pod` = Error itu menyuruh kita memberitahu secara Spesifik Nama Container  <br/>
>>  [-] Error tersebut terjadi karena Kubernetes tidak mengetahui Container mana yang ingin ditampilkan Logs nya  <br/>
>> <br/>
>> -> yang mana Command ini lebih cocok untuk Menampilkan Logs untuk Pod yang hanya mengandung Satu Container. <br/> <br/>
>>
>>
>> #### (2) `kubectl logs <pod_name> -c <container_name>` 
>> -> Pada Command diatas, kita perlu memberitahu secara Spesifik Nama Container yang ingin kita tampilkan Logs nya. <br/>
>> yang mana, dengan Command diatas kita hanya bisa menampilkan Logs untuk Salah Satu Container yang ada pada Pod. <br/>
>> -> Seharusnya tidak ada error saat kita menggunakan Command tersebut, jika kita sudah mendeskripsikan secara Spesifik nama Container nya. <br/>
>>
>> -> Seharusnya Command ini cocok untuk menampilkan Logs untuk Pod yang memiliki Multiple Containers, dengan catatan kita harus menuliskan secara Spesifik salah satu Container yang ingin kita tampilkan Logs nya. <br/> <br/>
>>
>> #### (3) `kubectl logs <pod_name> --all-containers=true`
>> -> Pada Command diatas, kita dapat Menampilkan Logs untuk semua Contaginers yang ada di dalam Pod.  <br/>
>> -> Seharusnya Command ini cocok untuk menampilkan Logs untuk Pod yang memiliki Multiple Containers.  <br/>
>>
>>

#### (3) Menampilkan Logs untuk Container yang "Crashed" atau yang "ter-Restart" 

-> Jika Container (yang ada di dalam Pod) mengalami Crash atau Restart. <br/>
maka kita dapat melihat Log untuk Container tersebut dengan cara :

```
kubectl logs <pod_name> -c <container_name> --previous
```
contoh :
```
kubectl logs hasura-abc123 -c hasura --previous
``` 
[-] `--previous`  = memberitahu Kubernetes untuk menampilkan Log dari "Previous instance of Container" (keadaan Container sebelum Container tersebut ter-Restart atau mengalami Crash ) <br/>
[-] `hasura-abc123` = merupakan "Nama Pod"  <br/>
[-] `hasura`  = merupakan "Nama Container"   <br/>
<br/>
Jadi Command diatas ingin menampilkan Log untuk Container yang bernama "hasura". dimana Logs yang ditampilkan pada keadaan sebelum Container tersebut mengalami Crashed atau ter-Restart. <br/>

#### (4) Menampilkan Logs secara Real-Time : 

-> untuk menampilkan Logs secara Real-Time, kita dapat mengunakan `-f` .  <br/>

{1} Command untuk menampilkan Logs secara Real-Time untuk Pod tertentu :   
```
kubectl logs -f <pod_name>
```
`-f` artinya "Follow", yang mana memungkinkan kita untuk melihat Logs secara Real-time atau langsung (let us Stream Logs in Real-Time)
<br/>
contoh :
```
kubectl logs -f hasura-abc123
```
[-] `hasura-abc123`  = merupakan "Nama Pod" yang ingin kita tampilkan Logs nya  <br/>

Jadi kita ingin melihat Logs untuk Pod yang bernama "hasura-abc123" secara Real-Time   <br/> <br/>


{2} Command untuk menampilkan Logs secara Real-Time untuk Container tertentu :  <br/>
(yang mana Container tersebut berada di dalam Pod)  <br/>
(For your information, Setiap Container memang harus berada di dalam Pod)  <br/>

```
kubectl logs -f <pod_name> -c <container_name>
```
contoh :
```
kubectl logs -f hasura-abc123 -c hasura
```
[-] `-f`  = artinya "Follow", yang mana memungkinkan kita untuk melihat Logs secara Real-time atau langsung (let us Stream Logs in Real-Time)  <br/>
[-] `hasura-abc123`  = merupakan "Nama Pod"   <br/>
[-] -c = merupakan kepanjangan dari "Container",   <br/>
yang mana -c memungkinkan kita untuk menetukkan Container yang mana yang ingin kita tampilkan Log nya,   <br/>
(yang mana Container tersebut berada di dalam Pod)   <br/>
[-] `hasura`  = merupakan "Nama Container"   <br/>
<br/>
Jadi kita ingin melihat Logs untuk Container yang bernama "hasura" secara Real-Time  <br/> <br/>


#### (5) Menampilkan Logs dari semua Pods (yang mengandung Label yang sama)

-> Label merupakan informasi tambahan yang kita bisa tambahkan di Resource Kubernetes.  <br/>
 <br/>
-> Jika kita mempunyai Multiple Pods , maka kita bisa menampilkan Logs pada banyak Pods,   <br/>
yang mana kita hanya menampilkan Logs untuk Pod yang mempunyai Nilai pada Label yang sama.  <br/>  <br/>

-> Command :
```
kubectl logs -l <label> --all-containers=true
```

Contoh :
```
kubectl logs -l app=hasura --all-containers=true
```
[-] `-l app=hasura`  = ini memberitahu Kubernetes untuk menampilkan semua Pods yang mempunyai Label `app=hasura`.   <br/>
(yang mana maksudnya Label tersebut dimiliki oleh Pods, bukan Container)   <br/>
(for your information, Pod mempunyai Label, tetapi Container tidak mempunyai Label )   <br/>
 <br/>
[-] `--all-containers=true`  = ini memberitahu Kubernetes untuk mengambil Logs dari Semua Container yang ada di Pod yang mengandung nilai Label ``app=hasura``    <br/>
(ini akan menampilkan semua Pods yang mengandung Label `app=hasura`)   <br/>
 <br/>
  <br/>

#### (6) Menampilkan Logs dengan Keyword menggunakan `grep`
#### (seperti menampilkan Logs yang mempunyai keyword "error" atau "failed")
<br/>
-> Kita bisa mem-filter Logs menggunakan Keyword, misalnya kita ingin filter untuk hanya menampilkan Log yang mengandung kata "error" atau "failed". <br/>
yang mana kita bisa menggunakan `grep` pada Command.

```
kubectl logs <pod_name> | grep "error"
```
[-] `| grep "error"`  = artinya kita ingin menampilkan Logs yang mengandung kata "error" <br/>

<br/>
Contoh :

```
kubectl logs hasura-abc123 | grep "failed"
```
Pada Command diatas, kita ingin menampilkan Logs yang mengandung kata "Failed", <br/>
yang mana Logs tersebut berada pada Pod yang bernama "hasura-abc123". <br/>

[-] `hasura-abc123`  = merupakan "Nama Pod"  <br/>
[-] `| grep "failed"` =  artinya kita ingin menampilkan Logs yang mengandung kata "failed"  <br/> <br/>


>> ^For your information^  <br/>
>> ### `grep`  <br/>
>> ### Understanding `grep` untuk mem-Filter Log  <br/>
>>  <br/>
>> -> `grep` merupakan command-line tool yang memungkinkan kita untuk "Mencari melalui Teks" untuk baris yang berisi Kata tertentu.
>>  <br/> <br/>
>> -> Dengan `grep` kita bisa mem-Filter, yakni hanya menampilkan Log yang hanya mengandung Kata tertentu. <br/>
>> Misalnya kita mem-Filter dengan kata "error",  <br/>
>> berarti kita hanya menampilkan Log yang mengandung kata "error".  <br/> <br/>
>> 
>> #### (1) `grep` dengan penggunaan yang Simple :
>> 
>> Jika kita ingin mem-Filter Logs dengan hanya menampilkan Logs yang mengandung kata "error",  <br/>
>> maka kita bisa menggunakan Command berikut ini :  
>>   ```
>>   kubectl logs <pod_name> | grep "error"
>>   ```
>> maka ini akan menampilkan hanya Logs yang mengandung kata "error"  <br/>
>>  <br/>
>> -> Contoh : <br/>
>> Jika kita mempunyai Daftar Logs seperti ini :
>>   ```
>>   2024-11-19 10:00:00 - error: database connection failed
>>   2024-11-19 10:05:00 - info: starting process
>>   2024-11-19 10:10:00 - error: timeout occurred
>>   ```
>>  
>> maka dengan Command diatas, <br/>
>> output yang tampil adalah : 
>>    ```
>>    2024-11-19 10:00:00 - error: database connection failed
>>    2024-11-19 10:10:00 - error: timeout occurred
>>    ```
>>
>> #### (2) Searching for Multiple Keywords (menggunakan `-e` ) :  
>> Misalnya kita ingin mem-Filter dengan Keywords "error" dan "failed",  <br/>
>> maka kita bisa gunakan Command berikut ini : 
>>    
>>      kubectl logs <pod_name> | grep -e "error" -e "failed"
>>     
>> [-] `-e`  = memungkinkan kita untuk mem-filter menggunakan beberapa Kata  <br/>
>> [-] '-e "error"'  = untuk mem-filter dengan menggunakan Kata "error", sehingga hanya menampilkan Logs yang mengandung kata "error". <br/>
>> [-] `-e "failed"`  = untuk mem-filter dengan menggunakan Kata "failed", sehingga hanya menampilkan Logs yang mengandung kata "failed". <br/>
>> <br/>
>> 
>> -> Contoh :  <br/>
>> Jika kita mempunyai Daftar Logs seperti ini :
>>     
>>      2024-11-19 10:00:00 - error: database connection failed
>>      2024-11-19 10:05:00 - info: starting process
>>      2024-11-19 10:10:00 - error: timeout occurred
>>      
>> maka dengan Command diatas,
>> <br/>
>> output yang tampil adalah :
>>     
>>     2024-11-19 10:00:00 - error: database connection failed
>>     2024-11-19 10:10:00 - error: timeout occurred
>>     
>> #### (3) Case-Insensitive Search (menggunakan `-i`)
>> -> Secara default, `grep` merupakan "Case-Sensitive" yang berarti secara Default, `grep` mem-filter menggunakan persis "huruf Kapital" atau "huruf kecil" yang kita ketik di Command. <br/>
>>  <br/>
>> -> Jika kita ingin `grep` mem-filter menggunakan "Case-Insensitive",  <br/>
>>  maka kita perlu menggunakan `-i`.   <br/>
>> <br/>
>> -> Misalnya pada Command kita mengetik "error", <br/>
>> maka dengan menggunakan `-i` , Logs yang kita tampilkan adalah  yang mengandung kata : <br/>
>> "ERROR"    <br/>
>> "Error"    <br/>
>> "error"     <br/>
>> <br/>
>> -> tetapi misalnya kita tidak menggunakan `i`, maka `grep` kembali lagi ke Default menjadi "Case-Sensitive". <br/>
>> Contoh pada Command kita mengetik "error",  <br/>
>> maka Logs yang kita tampilkan adalah  yang mengandung kata : <br/>
>> "error"  <br/>
>>  <br/>
>> Dan System tidak akan menampilkan Logs yang mengandung kata :  <br/>
>> "ERROR"  <br/>
>> "Error"  <br/>
>>  <br/>
>> -> Contoh Command dengan menggunakan `-i` : 
>>    ```
>>    kubectl logs <pod_name> | grep -i "error"
>>    ```
>> [-] `-i`  = ini membuat search menjadi "Case-Insensitive", sehingga tidak masalah huruf nya "Uppercase" atau "Lowercase".  <br/>
>> <br/>
>> -> Contoh :  <br/>
>> Jika kita mempunyai Daftar Logs seperti ini :  
>>    
>>      2024-11-19 10:00:00 - Error: database connection failed
>>      2024-11-19 10:10:00 - error: timeout occurred
>>     
>> maka dengan Command diatas,
>> <br/>
>> output yang tampil adalah :
>>         
>>         2024-11-19 10:00:00 - Error: database connection failed
>>         2024-11-19 10:10:00 - error: timeout occurred
>>         
>> Dapat kita lihat diatas. walaupun pada Command kita ketik "error",   <br/>
>> tetapi dengan `-i` , `grep` dapat mem-Filter dan menampilkan Logs yang mengandung kata "Error" dan "error".  <br/>
>> 
>> #### (4) `grep` untuk mencari Phrase (beberapa Kata) 
>> -> Misalnya kita ingin mem-Filter menggunakan "beberapa Kata",  <br/>
>> maka kita bisa menggunakan contoh Command berikut ini : 
>>   ```
>>   kubectl logs <pod_name> | grep "database connection failed"
>>   ```
>> [-] `grep "database connection failed"` =  ini berarti mem-Filter Logs untuk hanya menampilkan Logs yang mengandung Phrase "database connection failed". <br/>
>>  <br/>
>> -> Contoh : <br/>
>> Jika kita mempunyai Daftar Logs seperti ini :
>> ```
>> 2024-11-19 10:00:00 - database connection failed
>> 2024-11-19 10:05:00 - error occurred
>> 2024-11-19 10:07:00 - error occurred database connection failed
>> ```
>> maka dengan Command diatas,
>> <br/>
>> output yang tampil adalah :
>> ```
>> 2024-11-19 10:00:00 - database connection failed
>> 2024-11-19 10:07:00 - error occurred database connection failed
>> ```
>>
>> ##### (5) Menggunakan "Regular Expression" (menggunakan `-E`)
>>  <br/>
>> -> Contoh Command :
  ```
   kubectl logs <pod_name> | grep -E "error|failure"
  ```
>> [-] `-E "error|failure"` =  ini artinya kita ingin hanya menampilkan Logs yang mengandung kata "error" atau "failure"  <br/>
>>  <br/>
>> -> Contoh :  <br/>
>> Jika kita mempunyai Daftar Logs seperti ini :
```
  2024-11-19 10:00:00 - error: database connection failed
  2024-11-19 10:05:00 - failure: timeout occurred
  2024-11-19 10:10:00 - info: process started
```
>>  
>> 
>> maka dengan Command diatas,
>> <br/>
>> output yang tampil adalah :
```
  2024-11-19 10:00:00 - error: database connection failed
  2024-11-19 10:05:00 - failure: timeout occurred
```
>> 
>> 
>> #### (6) Excluding Specific Keywords (menggunakan `-v`) :
>> #### (Mengecualikan Keywords tertentu - menggunakan `-v`)
>> 
>> Jika kita ingin mengecualikan Logs, yaitu kita tidak ingin menampilkan Logs yang mengandung kata tertentu,
>> kita dapat menggunakan `-v`.
>> 
>> -> Contoh Command :
>> ```
>> kubectl logs <pod_name> | grep -v "info"
>> ```
>> [-] `-v "info"`  = ini artinya kita ingin mengecualikan Logs yang mengandung kata "info"
>> (Kita tidak ingin menampilkan Logs yang mengandung kata "info")
>> 
>> 
>> -> Contoh :
>> Jika kita mempunyai Daftar Logs seperti ini :
>> ```
>> 2024-11-19 10:00:00 - info: starting process
>> 2024-11-19 10:10:00 - error: timeout occurred
>> ```
>> maka dengan Command diatas,
>> output yang tampil adalah :
>> ```
>> 2024-11-19 10:10:00 - error: timeout occurred
>> ```
>>
>> #### (7) Show "Line Numbers" (menggunakan `-n`)
>> 
>> -> dengan menggunakan `-n` , kita dapat melihat di baris keberapa Logs yang mengandung Keyword berada.  <br/>
>>  <br/>
>> -> Contoh Command :
>> ```
>> kubectl logs <pod_name> | grep -n "error"
>> ```
>> [-] `-n "error"` =  ini menujukkan di baris keberapa Logs yang mengandung Keyword "error" berada.  <br/>
>> 
>> -> Contoh :  <br/>
>>  Jika kita mempunyai Daftar Logs seperti ini :
>> ```
>> 2024-11-19 10:00:00 - error: database connection failed
>> 2024-11-19 10:05:00 - info: starting process
>> 2024-11-19 10:10:00 - error: timeout occurred
>> ```
>> maka dengan Command diatas, output yang tampil adalah :
>> ```
>> 1:2024-11-19 10:00:00 - error: database connection failed
>> 3:2024-11-19 10:10:00 - error: timeout occurred
>> ```
>> [-] Angka `1` dan `3` merupakan "Baris Keberapa" Logs yang mengandung kata "error" berada.  <br/>
>> (Logs yang mengandung kata "error" berada pada baris `1` dan `3`)  <br/>
>> <br/>
>> 


## C. Hasura Log vs Error Message 
## (Konsep Perbedaan "Hasura Log" dan "Error Message")


-> "Logs" merupakan Catatan terperinci yang ter-generate secara otomatis. <br/>
yang mana Catatan Terperinci tersebut berisi Peristiwa & Aktifitas yang terjadi di dalam Sistem. <br/>
<br/>
-> "Error Messages" merupakan bagian Spesifik pada Logs yang menyediakan Informasi Detail mengenai Issue, yang mana hal ini sangat penting untuk mengidentifikasi penyebab Failure atau kegagalan. <br/>
("Error Messages" berada di dalam Logs) <br/>
<br/>
-> "Logs" & "Error Messages" berguna untuk Monitoring, Debugging, dan Auditing operasi yang berlangsung di Hasura. <br/>
<br/>
-> "Debugging" merupakan Proses untuk melakukan Identifikasi, Diagnosa, dan Memperbaiki Problem atau Error. <br/>
<br/>
-> "Auditing" merupakan Proses untuk menyimpan Catatan semua Aktifitas & Peristiwa yang terjadi pada System untuk tujuan Tracking (Pelacakan) & Review (evaluasi). <br/>
<br/>

### [1] Contoh Logs :
### (Real-World Example of Logs)

-> Misalnya kita memakai Hasura, dan kita mencoba menambahkan sebuah User baru dengan Email john@example.com    <br/>
, tetapi email tersebut sudah ada di Database, sehingga Hasura mengirimkan Response Error,   <br/>
yang mana Log nya akan terihat seperti contoh berikut ini :  <br/>


```
{
  "timestamp": "2024-11-14T12:00:00Z",
  "level": "error",
  "message": "query failed",
  "query": "mutation { insert_users_one(object: { name: \"John\", email: \"john@example.com\" }) { id } }",
  "error": {
    "message": "duplicate key value violates unique constraint \"users_email_key\"",
    "details": "Key (email)=(john@example.com) already exists."
  },
  "request_id": "abc123",
  "session_variables": {
    "x-hasura-user-id": "123",
    "x-hasura-role": "admin"
  }
}
```


## D. Example of "Hasura Log" vs "Error Message"
## (Contoh Real Example "Hasura Log", dan Identifilkasi "Error Message" di dalam "Hasura Log" tersebut )


