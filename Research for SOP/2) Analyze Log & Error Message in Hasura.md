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

#### [1.a] Mari kita uraikan Logs tersebut :
<br/>
{1) Timestamp :  <br/>
` "timestamp": "2024-11-14T12:00:00Z" `   <br/>
Timetamp ini memberitahu "Kapan" Error terjadi.  <br/>
<br/>
(2) Level   :   <br/>
` "level": "error" `  <br/>
ini merupakan "Log Levels".   <br/>
yang mana disini menujukkan Level dari Log tersebut adalah "Error". <br/>
<br/>
"Log Levels" digunakan untuk meng-klasifikasikan tingkat Keparahan. <br/>
<br/>
=> Berikut ini Urutan Tingkatan Log Level (Mulai dari yang paling "Ringan" hingga yang "Paling Parah") :   <br/>
<1> Trace  <br/>
<2> Debug  <br/>
<3> Info  <br/>
<4> Warn  <br/>
<5> Error  <br/>
<6> Fatal  <br/>
 <br/>
"Trace" merupakan Kondi yang Paling Ringan.  <br/>
"Fatal" merupakan kondisi paling Parah, biasanya meng-indikasikan Applikasi tidak tetap berjalan.   <br/>
("Fatal" usually indicating that application cannot continue running)   <br/>

 <br/>
=> Berikut ini adalah Deskripsi mengenai tingkatan "Log Levels" : <br/>
<br/>
[1] ERROR :  <br/>
- ini meng-indikasikan 'Serious Issue' yang membutuhkan perhatian. <br/>
yang mana Aplikasi mengalami masalah yang mencegah aplikasi tersebut bekerja dengan benar. <br/>
- Contoh : <br/>
"Failure in Database Connection" <br/>
atau "Unhandled Exception" <br/>

>> ^For your information^ <br/>
>> {1} **Unhandled Exception**  :  <br/>
>> merupakan Error yang terjadi saat 'excecution of program', tetapi error tersebut tidak ditangani secara baik oleh mekanisme "Error Handling" pada Program.  <br/>
>> Mekanisme "Error Handling" itu seperti "Try and Catch" pada Kodingan.  <br/>
>> yang mana Pada Case Normal, jika terjadi error, seharusnya Exceptions tersebut dapat ditangani oleh Mekanisme "Error Handling".  <br/>
>> 
>> "Exceptions" merupakan kejadian tidak terduga yang mengganggu aliran eksekusi normal suatu program.  <br/>
>>  <br/>
>> Misalnya, kita mempunyai Program untuk "Divide two numbers" tetapi salah satu angka tersebut adalah 0 (Nol), yang mana angka Nol tersebut tidak bisa dibagi, yang mana ini dapat menyebabkan Error.  <br/>
>> Error tersebut yang kita sebut "Exception."  <br/>
>> Dan Exception seharusnya dapat tertangani dengan baik oleh Mekanisme "Error-Handling" ,  <br/>
>> yang mana jika Exception tidak tertangani dengan baik, maka hal ini dapat menyebabakn Error "Unhandled Exception".  <br/>
>>

[2] WARN (Warning) : <br/>
- Meng-indikasikan "Potential Problem" (Potensi Masalah) atau sesuatu yang tidak Ideal tetapi tidak menghambat jalannya Aplikasi. <br/>
yang mana ini bukan merupakan masalah yang Critical, tetapi tetap membutuhkan Perhatian. <br/>

- Contoh : <br/>
"Deprecated Featured being Used" <br/>
atau  <br/>
"Slow Database Queries"  <br/>
<br/>
"Deprecated Features being Used" merupakan Features, Functions, atau Method pada Software atau Library yang "tidak lagi direkomendasikan" atau "akan di-remove di masa yang akan datang". <br/>
yang mana Feature ini masih berfungsi dengan baik tetapi dianggap ketinggalan jaman.  <br/>
<br/>
"Slow Database Queries" merupakan Database Query yang memakan lebih banyak waktu saat diekseskusi, dibandingkan waktu perkiraan. <br/>

<br/>
<br/>

[3] INFO :  <br/>
- menyediakan informasi mengenai Application's Normal Operation (Operasi Normal Aplikasi) 

- INFO berarti suati aksi telah sukses dan tidak ada error saat itu.

- Pada waktu saat kita mendapatkan INFO, berarti tidak ada error. <br/>
tetapi Error masih dapat terjadi di kemudian waktu. <br/>

- Contoh : <br/>
"User Login Successful" <br/>
atau <br/>
"File Uploaded Successfully" <br/>
<br/>


[4] DEBUG :  <br/>
Log Levels tingkat DEBUG menyediakan informasi detail yang digunakan untuk Troubleshoot & Debug Issues pada Aplikasi.
Log untuk DEBUG berisi catatan mendalam mengenai cara kerja Internal Aplikasi (seperti Nilai Variable, Flow of Execution, atau langkah-langkah dalam Algoritme).  <br/>
Tingkat pencatatan Log tingkat DEBUG ini biasanya lebih bertele-tele dan mencakup informasi yang biasanya tidak diperlukan selama 'Normal Operation',  <br/>
tetapi Log DEBUG ini berguna untuk "Mengidentifikasi Masalah" atau "Memahami cara kerja secara Internal".  <br/>
<br/>
=> Apa saja isi "DEBUG Logs" :  <br/>
- Internal States : berisi informasi mengenai keadaan Variable, Objects, atau Data Structure.  <br/>
- Execution Flow : Informasi Detail mengenai apa yang program lakukan pada Setiap Step (Seperti "Entering atau Exiting Functions, Loop, atau Code Block tertentu")  <br/>
- Intermediate Data : Values yang diproses pada Aplikasi (seperti isi dari Arrays atau Objects saat Loop atau Calculations)  <br/>

<br/>
=> Contoh "DEBUG Log" : <br/>
<1> `Entering function calculateTotal()`   <br/>
ini menunjukkan Program memasuki Function Tertentu.  <br/>
yang mana, hal ini dapat membantu kita untuk Melacak Function atau Bagian Code mana yang di-eksekusi.  <br/>
(Jika terdapat Error, klta dapat melihat Function mana yang Error atau Bagian Code mana yang Error)  <br/>
<br/>
<2> `Value of counter in loop: 5`   <br/>
ini menunjukkan Nilai dari Variable "counter" pada sebuah Point Khusus, yaitu pada Loop.  <br/>
yang mana kita dapat memahami bagaimana Loop Berlangsung.  <br/>
<br/>
<3> `Querying database with parameters: {username: 'JohnDoe', age: 30}`  <br/>
ini menunjukkan Parameter Tertentu yang digunakan pada Database Query.  <br/>
<br/>
Berikut Detail Penjelasan Parameter :  <br/>
` username: 'JohnDoe' `   <br/>
- Parameter Name : `username`  <br/>
- Value : ` 'JohnDoe' `  <br/>
<br/>
`age: 30`  <br/>
- Parameter Name : `age`  <br/>
- Value : `30`  <br/>
<br/>

<4> `"Variable result after calculation: 256"`  : <br/>
ini menunjukkan Hasil Perhitungan,  <br/>
yang mana ini dapat juga kita gunakan untuk Memverifikasi apakah Logika nya benar.  <br/>
<br/>
<br/>

=> Kita tidak bisa selalu melihat "DEBUG Logs" kecuali jika "DEBUG Logs" di-Setting "Enable" pada "System Configuration".  <br/>
Secara Default, "DEBUG Logs" biasanya di-setting "Disabled" pada 'Production Environments' untuk menghindari hal berikut ini :   <br/>
<1> Performance Overhead :  <br/>
merupakan Konsumsi "Computational Resources" yang berlebihan (seperti Konsumsi Memory atau Processing Power yang berlebihan)  <br/>
 <br/>
<2> Excessive Log Data :  <br/>
merupakan situasi dimana System menghasilkan Jumlah Log yang lebih banyak daripada biasanya,  <br/>
yang mana ini dapat mencakup terlalu banyak detail, informasi yang tidak relevant, atau lebih banyak data dari yang diperlukan untuk Normal Operations.   <br/>
 <br/>
<3> Potential Exposure of Sensitive Information :   <br/>
Merupakan Risiko bahwa Data Rahasia atau Pribadi dapat diakses, di-ungkapkan, atau dikompromikan   <br/>
karena Vulnerabilities, Misconfigurations, Penanganan System yang tidak Proper.  <br/>
(ini bisa terjadi oleh berbagai cara seperti melalui Improper Logging, Insecure Data Storage, Inadequate Encryption, atau System Flaws yang memungkinkan Pihak yang tidak berwenang untuk mengakses Sensitive Data)  <br/>
 <br/>
=> Misalnya terjadi Issue saat kita membuat Settingan Disable untuk "DEBUG LOG", maka kita tidak bisa melihat "DEBUG Log" untuk kita mencoba Troubleshoot, bahkan jika setalah itu kita mengubah Settingan "DEBUG Log" menjadi "Enable",  <br/>
kita masih tetap tidak bisa melihat "DEBUG Log" untuk Issue tersebut karena Issue tersebut terjadi saat settingan masih "Disable", sehingga tidak "DEBUG Log" tidak terbentuk issue tersebut.  <br/>  <br/>
<br/>

[5] Fatal :
- Fatal merupakan Kondisi paling Parah (Most Severe Level)
- "Fatal" berarti System berada pada Kondisi Kritis (Critical State) dan System tidak bisa terus berjalan.
Biasanya issue yang terjadi menghentikkan aplikasi agar tidak berfungsi.
- Contoh : System mengalami "Out of Memory" kemudian Crash



[6] Trace : 
- Trace merupakan Log Level yang memiliki Tingkat pencatatan paling terperinci, <br/>
bahkan Trace lebih terperinci daripada DEBUG.
- Trace Log mencatat setiap Detail Kecil pad Alur Aplikasi, bahkan lebih terperinci daripada DEBUG. <br/>
Dan Trace Log biasanya digunakan saat Fase Development (Development Phase).
- Trace biasanya digunakan saat Fase Development untuk melacak Detail terkecil dari Eksekusi Program, <br/>
sehingga Trace Log dapat membantu kita melihat apa yang terjadi di dalam aplikasi. <br/>
yang mana, Trace Logs dapat membantu untuk Melacak Bugs atau Errors, dan memudahkan untuk menemukan dimana kesalahannya. <br/>

<br/>
<br/>

(ini kembali lagi ke Penjelasan Uraian Log) <br/>
(3) message : <br/>
` "message": "query failed" `
- "message" pada Log memberi Rangkuman Singkat mengenai masalah (Quick Summary of the problem).
- ""query failed" berarti Operasi atau Query yang kita coba lakukan telah gagal. <br/>
Pada case ini, kita coba menjalankan Query untuk memasukkan User baru ke Database, tetapi kita gagal untuk memasukkan User baru tersebut ke dalam Database. <br/>

<br/>

(4) query :

- "query" pada Log berarti menunjukkan Query yang dilakukan. <br/>
pada Case ini, Query tersebut adalah :
```
mutation { 
  insert_users_one(object: { name: "John", email: "john@example.com" }) { 
    id 
  } 
}

```
- Query diatas meminta untuk Insert User ke Database dan meminta System untuk Memberikan Response berupa User's ID yang di-insert tersebut. <br/>
yang mana pada Query diatas, User yang ingin di-insert diatas adalah "John" dengan email "john@example.com".

```
{ 
    id 
  } 
```
ini berarti Query meminta System untuk Memberikan Response berupa User's ID yang di-insert tersebut.
<br/>
<br/>

(5) error : (ini merupakan "Error Message" )
```
"error": {
    "message": "duplicate key value violates unique constraint \"users_email_key\"",
    "details": "Key (email)=(john@example.com) already exists."
  }
```
- Bagian pada Log ini merupakan "Error Message".
- yang mana, pada bagian "Error Message", terdapat "message" dan juga "details"
- Bagian "Error Message" menjelaskan apa yang bermasalah.

<5.a> Bagian "message" : `"message": "duplicate key value violates unique constraint \"users_email_key\""`
- `duplicate key value violates unique constraint` ini berarti Operasi gagal karena ada ada "Duplicate Key Violation".  <br/>
"Duplicate Key Violation" biasanya terjadi karena ada usaha untuk Insert atau Update Data ke Database, tetapi pada Database sudah ada Data dengan Value yang sama dengan yang mau di-insert atau di-update,  <br/>
sehingga muncul issue "Duplicate Key Violation".  
- Pada Contoh Case ini, User Baru yang ingin di-insert ke Database, ternyata sudah ada pada Database,  <br/>
sehingga muncul error "Duplicate Key Violation".  <br/> <br/>

<5.b> Bagian "details" : ` "details": "Key (email)=(john@example.com) already exists."`
- "details" merupakan tambahan detail informasi mengenai Error
- yang mana pada Case ini, "details" memberitahu bahwa penyebab issue adalah email "john@example.com" sudah ada di Database

<br/>
<br/>

(6) request_id :
`"request_id": "abc123" `
- "request_id" itu seperti 'tracking number' (nomor pelacakan) untuk Request tertentu. <br/>
yang mana "request_id" itu seperti tanda pengenal unik (Unique Identifier) untuk setiap Request,  <br/>
yang mana ini berguna untuk membedakan suatu Request dengan Request lainnya.

- "request_id" berguna untuk debugging, jika sesuatu issue terjadi dan kita ingin melihat Log, kita bisa mem-filter Log dengan request_id sehingga kita dapat hanya melihat Log milik suatu Request yang terjadi issue (sehingga tidak perlu melihat Log milik Request lainnya).  <br/>

<br/>
<br/>

(7) session_variables :
```
"session_variables": {
    "x-hasura-user-id": "123",
    "x-hasura-role": "admin"
  }
```
- "session_variables" mengandung informasi tambahan mengenai Session yang aktif saat Request dibuat.  <br/>
Informasi Tambahan itu seperti Data User Preference, Data Shopping Cart, dan sebagainya.  <br/>
Misalnya kita mengunjungi sebuah Website, kemudian kita Log-in,  <br/>
Website perlu mengingat detail tertentu tentang kita (ini yang dimaksud "informasi tambahan"),  <br/>
Detail tersebut seperti :  <br/>
=> Username  <br/>
=> Data Preferences (seperti Language, Theme)  <br/>
=> Data Shopping Cart Items   <br/>
=> Permission (seperti "admin" atau "user")   <br/> <br/>

- "Session Variables" itu seperti catatan sementara yang Website ingat saat User berinteraksi dengan Website.   <br/>
Catatan ini hanya disimpan saat Durasi Session.    <br/>
Catatan ini digunakan untuk melacak aktivitas kita saat kita Log-in.    <br/>
Saat Session berakhir, maka Session Data biasanya dihapus ('Session berakhir' itu seperti saat kita Log-out atau saat Session times out (Sesi berakhir))   <br/>

Catatan mengenai User ini biasanya tidak disimpan secara Permanent oleh Server,    <br/>
kecuali jika User membuat Account (create an account), melakukan pembelian (making a purchase),   <br/>
maka Data User akan disimpan di Database.   <br/>

- pada "session_variables" terdapat "x-hasura-user-id" dan "x-hasura-role"   <br/>

<7.a> ` "x-hasura-user-id": "123" `    <br/>
ini menunjukkan "User ID" milik User yang membuat Request.   <br/>
Pada case ini, "User ID" tersebut adalah 123    <br/>  <br/>

<7.b> ` "x-hasura-role": "admin" `  <br/>
ini menunjukkan Role milik User yang membuat Request.   <br/>
Pada case ini, Role tersebut adalah "admin",  <br/>
yang berarti User memiliki hak istimewa sebagai admin untuk melakukan tindakan pada System   <br/> <br/>


### [2] Types of Hasura Logs <br/>
### (Berbagai Jenis Log di Hasura)  <br/>

-> Berikut berbagai Jenis Logs pada Hasura : <br/>
(1) Request Logs : <br/>
"Request Logs" menunjukkan Detail mengenai Request yang masuk (incoming Request). <br/>
yang mana, "Request Log" berisi informasi apakah Request berhasil atau terdapat Issue.  <br/> <br/>

(2) Error Logs : <br/>
"Error Logs" mencatat Issue atau Error yang terjadi saat Request  <br/>
(Misalnya Invalid Queries atau Permission Issue)  <br/> <br/>

(3) Performance Logs : <br/>
"Performance Logs" ini menunjukkan berapa lama Query di-eksekusi. <br/>
yang mana "Performance Logs" membantu kita menemukkan 'Slow Request'.  <br/>

(4) System Logs :  <br/>
menrupakan Log Umum (General Logs) yang memberikkan informasi mengenai Kesehatan System Hasura secara keseluruhan   <br/><br/>

-> Mari kita lihat contoh Tipe Log berikut : <br/>
(1) Request Log :
```
{
  "timestamp": "2024-11-14T12:00:00Z",
  "level": "info",
  "message": "processed request",
  "query": "query { users { id name email } }",
  "response_time_ms": 120,
  "status_code": 200,
  "execution_time_ms": 50,
  "request_id": "abc123"
}
```

(Kita bahas component yang belum pernah dibahas diatas) <br/>
[-] response_time_ms : <br/>
Waktu yang dibutuhkan untuk mendapatkan Response. <br/>
Satuan dalam miliseconds. <br/> <br/>

[-] execution_time_ms : <br/>
Waktu yang dibutuhkan untuk mengeksekusi Query. <br/>
Satuan dalam miliseconds. <br/>
(time to execute Query) <br/> <br/>

[-] status_code : <br/>
merupakan HTTP Status Code dari Request  <br/>
(`200` untuk Success, `500` untuk Error, dan sebagainya) <br/> 

[-] request_id : <br/>
merupakan "Unique ID" untuk Request. <br/> <br/> <br/>


=> Apa yang coba dikatakan oleh "Request Log" :  <br/>
[-] Status Code : <br/>
jika "Status Code" nya 200 berarti semua berjalan dengan baik <br/> 

[-] response_time_ms : <br/>
jika `response_time_ms` nya tinggi, <br/>
berarti Request memakan waktu lebih banyak waktu untuk diproses, <br/>
yang mana ini bisa jadi meng-indikasikan 'Performance Issue' <br/> <br/>

[-] execution_time_ms  : <br/>
jika `execution_time_ms` nya tinggi,  <br/>
maka bisa jadi Query tersebut kompleks atau menangani banyak data. <br/> <br/>

<br/> <br/>

(2) Error Logs :
```
{
  "timestamp": "2024-11-14T12:05:00Z",
  "level": "error",
  "message": "query failed",
  "query": "mutation { insert_users_one(object: { name: \"John\", email: \"john@example.com\" }) { id } }",
  "error": {
    "message": "duplicate key value violates unique constraint \"users_email_key\"",
    "details": "Key (email)=(john@example.com) already exists."
  },
  "request_id": "abc124"
}

```
(Komponen di Log ini sudah pernahj diatas pada Catatan bagian atas)  <br/>
<br/>
=> Apa yang coba dikatakan oleh "Error Logs" :  <br/>
[-] bagian "Error Message" : <br/>
berikut ini bagian "Error Message"  
```
 "error": {
    "message": "duplicate key value violates unique constraint \"users_email_key\"",
    "details": "Key (email)=(john@example.com) already exists."
  }
```

untuk memahami masalahnya, kita bisa pahami bagian "Error Message" pada Error Logs. <br/>

pada bagian "message", terdapat kalimat ` "duplicate key value violates unique constraint" ` <br/> 
ini berarti Issue terjadi karena ada 'Duplicate Value'  <br/><br/>

Pada bagian "details", terdapat kalimat ` "Key (email)=(john@example.com) already exists"  `  <br/>
berarti Issue terjadi karena terdapat Duplikat Email, yakni karena email john@example.com sudah ada di Database.  <br/> <br/> <br/>



(3) Performance Logs : <br/>
-> Performance Logs digunakan untuk mennjukkan Waktu yang digunakan untuk ekseskusi Query, <br/>
yang mana ini membantu kita meng-identifikasi "Slow Queries". 

```
{
  "timestamp": "2024-11-14T12:10:00Z",
  "level": "info",
  "message": "query performance",
  "query": "query { users { id name email } }",
  "execution_time_ms": 180,
  "status_code": 200,
  "request_id": "abc125"
}

```
 
(Kita bahas component yang belum pernah dibahas diatas) <br/> <br/>

[-] execution_time_ms  : <br/>
ini menunjukkan Berapa lama waktu yang dibutuhkan untuk menjalankan Query di dalam Hasura. <br/>
<br/>

=> Apa yang coba dikatakan oleh "Performance Log" : <br/>
[-] jika `execution_time_ms` terlalu tinggi (misalnya melebihi Threshold. dan misalnya Threshold kita 100ms) maka artinya Query kita itu lambat (Slow Query). <br/>
yang mana, mungkin kita ingin meng-optimisasi dengan menambah Indexing ke Database atau dengan menyederhanakan Query  <br/>
<br/> <br/>


(4) System Logs :   <br/>
-> System Logs pada Hasura menyediakan Informasi Umum (General Information) mengenai System's Operation, Health, and Environment.
Systems Logs memberikkan informasi mengenai keadaan Hasura dan bagaimana Hasura berinteraksi dengan Komponen-komponennya (seperti berinteraksi dengan Database, Server, dan sebagainya).
System Logs biasanya mengandung informasi mengenai Service Startup, onfiguration Changes, System Error, dan sebagainya.  <br/>  <br/>

-> Contoh System Logs :
```
{
  "timestamp": "2024-11-14T12:30:00Z",
  "level": "info",
  "message": "Hasura instance started",
  "instance_id": "hasura-instance-001",
  "db_connection_status": "connected",
  "server_status": "running",
  "version": "v2.21.0",
  "uptime": "5 hours 20 minutes",
  "request_id": "sys-start-001"
}

```


[1] Timestamp :
```
 "timestamp": "2024-11-14T12:30:00Z"
```
- Timestamp memberitahu kita "kapan Log dibentuk"
Pada case ini, Log dibentuk pada 14 November 2024 pada jam 12:30 PM UTC

- Timestamp membantu kita untuk mengetahui waktu persis kejadian, yang mana ini berguna untuk Tracking (melacak) & Troubleshooting. <br/><br/>


[2] Level :
```
"level": "info"
```
- ini memberitahu kita tingkat keparahan suatu Issue
atau seberapa penting issue tersebut harus diprioritaskan.

- pada case ini, `info` berarti semua baik-baik saja dan Log ini hanya berupa informational message. <br/><br/>


[3] Message :
```
"message": "Hasura instance started"
```

- ini merupakan "Main Message" (Message utama) pada Log.
- Pada case ini, `Hasura instance started` memberitahu kita bahwa Hasura "has successfully started" (telah berhasil dimulai).
yang mana `Hasura instance started` merupakan Log message yang biasa kita temui saat System mulai berjalan. <br/><br/>


[4] Instace ID :
```
 "instance_id": "hasura-instance-001"
```
- Jika kita mempunyai Hasura Instances lebih dari satu (misalnya untuk Server yang berbeda atau Environment berbeda),
"Instance ID" membantu untuk meng-identifikasi dari Instance mana Log tersebut berasal.
Pada Case ini, Log berasal dari Instance `hasura-instance-001` <br/><br/>


[5] Database Connection Status :
```
"db_connection_status": "connected"
```
- "Database Conncection Status" memberitahu kita mengenai "Koneksi" antara Hasura dan Database.

- pada case ini, ` "connected" ` berarti Hasura telah berhasil terkoneksi ke Database.

- Jika terdapat masalah, maka biasanya kita akan melihat ` "disconnected" ` yang mana meng-indikasikan issue saat meng-koneksikan ke Database (mengkin dikarenakan Credential yang salah, atau Network Issue)  <br/><br/>


[6] Server Status :
```
"server_status": "running"
```
- "Server Status" menunjukkan  dari Hasura Server.
pada case ini, `running` berarti Server aktif dan berjalan tanpa masalah (Server is up & Running without Issues).

- Jika terjadi masalah (Misalnya Server Crashed) , maka biasanya pada Log akan tertulis "Not Running" atau "Crashed"
 <br/><br/>

[7] Version :
```
  "version": "v2.21.0"
```
- ini memberitahu kita Versi Hasura berapa yang Running.
Pada case ini, Versi Hasura nya adalah 2.21.0

- Version dapat membantu, karena terkadang features dan bug dapat spesfik untuk version tertentu.
<br/><br/>

[8] Uptime :
```
"uptime": "5 hours 20 minutes"
```
- "Uptime" menunjukkan berapa lama Hasura telah berjalan secara terus-menerus sejak terakhir kali di-restart (how long Hasura has been Running Continuously since it was last restarted).
- contohnya, pada case ini, `5 hours 20 minutes` System menyala selama 5 jam 20 menit.
- Jika "Uptime" nya Singkat, maka ini mungkin menunjukkan masalah seperti System yang sering mengalami "Restart",
yang mana dapat disebabkan oleh Crash atau 'Configuration Issues'
<br/><br/>

[9] Request ID :
```
 "request_id": "sys-start-001"
```
- "Request ID" merupakan "Unique Identifier" untuk "Log Entry" (untuk membedakan antara "Log Entry" satu dengan "Log Entry" lainnya ).
yang mana, "Log Entry" merupakan Message yang dibuat oleh System untuk menangkap Informasi mengenai suatu Event, Action, atau Status pada spesifik moment.

- "Request ID" dapat digunakan untuk melacak (tracking) event tertentu atau menghubungkannya dengan Log lain yang terkait dengan Event ini.
yang mana, jika kita sedang Troubleshooting, maka kita perlu refer ke "Request ID".
<br/><br/> <br/>

=> How to gain insight from System Logs : <br/>
Mendapatkan Insight (wawasan) dari Sytem Logs itu seperti membaca Report Card milik System. <br/>
yang mana, hal tersebut memberi tahu Apa yang bekerja dengan baik, apa yang perlu attention, dan bagaimana Performa dari waktu ke waktu. <br/>
<br/>
Cara untuk mendapatkan Insight dari System Logs : <br/>
<br/>
[1] **Monitor System Health** : <br/>
untuk Monitor System Health, kita dapat lihat dari aspek berikut ini pada Log : <br/>
<1.a> Server Status :  <br/>
apakah Server nya berjalan atau Server nya Down. <br/>
Logs akan memberitahu apakah Server berjalan lancar atau apakah ada Problem, Crash atau Downtime. <br/>
Contoh : <br/>
Jika pada Log tertulis `server_status": "running` maka artinya Server berjalan tanpa ada masalah yang mendesak. <br/>
<br/>
<1.b> Database Connection : <br/>
Logs bagian "Database Connection" menunjukkan bagaimana System telah sukses terkoneksikan ke Database. <br/>
Jika terdapat Issue, biasanya kita akan menemukan `disconnected` pada Log bagian "Database Connection" <br/>
Contoh : <br/>
jika pada Log terdapat ` "db_connection_status": "connected" ` maka artinya System mempunyai Healthy Connection ke Database.
<br/><br/>

[2] Detect Issues Early : <br/>
Untuk mendeteksi Issue secara early (lebih awal), <br/>
kita bisa melihat dari aspek berikut ini pada Log : <br/>
<2.a> Startup Errors : <br/>
Startup Error terjadi saat System gagal saat meng-inisialisasi atau menyelesaikan Startup Process. <br/>
Hal ini dapat terjadi karena beberapa alasan, seperti masalah Koneksi ke Database, Pengaturan yang salah dikonfigurasi, Missing Files, atau Network Problems. <br/>
Startup Error merupakan hal yang sangat Critical karena itu mencegah System berfungsi secara baik. <br/>
Kita dapat lihat dari aspek berikut ini pada Log : <br/>
[-] `db_connection_status` : menjelaskan bagaimana Koneksi ke Database <br/>

[-] `server_status` : menjelaskan apakan Server berjalan dengan baik <br/>

[-] `message` : message menjelaskan Status yang terjadi <br/>

[-] `error_detail` : memberikan Informasi tambahan mengenai Error <br/>

[-] `Level` : menjelaskan apakah terdapat error <br/><br/>


Contoh Startup Errors :
Jika terdapat Error pada Log bagian `database connection failed` , hal ini mengetahui kita untuk mengetahui bahwa ada yang salah dengan Koneksi Database saat Startup Process,
dan kita perlu memperbaikinya. <br/><br/>


<2.b> Error and Warnings : <br/>
Saat terjadi suatu masalah, System Logs biasanya berisi "Error Messages", <br/>
yang mana "Error Messages" memberitahu kita apa yang menyebabkan Masalah. <br/> <br/> 

Misalnya terdapat error terkait Database atau Network, artinya kita perlu investigasi masalah yang berkaitan dengan Database atau Network dan memperbaikinya. <br/> 

Untuk meng-assess Error & Warning, kita bisa melihat aspek berikut ini pada Log : <br/> 
[-] `level` : menjelaskan apakah terdapat error <br/>  <br/> 

[-] `message` : message menjelaskan Status yang terjadi <br/>  <br/> 

[-] Error Messages : menyediakan Informasi Detail mengenai Issue <br/> 
Contoh bagian pada Error Messages :
```
"error": {
    "message": "duplicate key value violates unique constraint \"users_email_key\"",
    "details": "Key (email)=(john@example.com) already exists."
  }
```

[-] Contextual Information : <br/> 
beberapa Logs mengandung Contextual Information <br/> 
(tidak semua Logs berisi 'Contextual Information') <br/> <br/> 

"Contextual Information" merupakan informasi detail tambahan pada Log. <br/> 
yang mana "Contextual Information" memberikan informasi Spesifik mengenai apa yang menjadi masalah, <br/> 
yang hal ini bermanfaat untuk mempersempit Ruang Lingkup masalah, dan membantu kita untuk Troubleshoot lebih cepat. <br/> <br/> 

^^Contoh 1 : User Information
```
{
  "timestamp": "2024-11-28T10:20:00Z",
  "level": "ERROR",
  "message": "authentication failed",
  "context": {
    "user_id": "john_doe",
    "ip_address": "192.168.0.2"
  }
}

```
yang merupakan "Contextual Information" pada Log diatas adalah :
```
"context": {
    "user_id": "john_doe",
    "ip_address": "192.168.0.2"
  }
```

Pada Log diatas, terdapat bagian ` "message": "authentication failed" ` yang berarti Error tersebut dikarenakan "gagal pada proses Autentikasi". <br/> 
Kemudian dengan melihat pada Log bagian Context, kita bisa mengetahui bahwa gagal authetikasi dilakukan oleh User yang memiliki user_id `john_doe` dan User tersebut memakai ip_address `192.168.0.2` <br/> <br/> 


^^Contoh 2 : System Component atau Service Involved <br/> 
Jika terdapat Issue pada Database atau Service, kita bisa melihat mengenai Nama Spesifik pada Database atau Service yang mengalami Issue.
```
{
  "timestamp": "2024-11-28T10:20:00Z",
  "level": "ERROR",
  "message": "unable to connect to database",
  "context": {
    "database_name": "user_db",
    "error_code": "ECONNREFUSED"
  }
}
```
yang merupakan "Contextual Information" pada Log diatas adalah :
```
"context": {
    "database_name": "user_db",
    "error_code": "ECONNREFUSED"
  }
```
Pada Log diatas, terdapat bagian `"message": "unable to connect to database"`, yang artinya error tersebut dikarenakan "tidak bisa Connect ke Database". <br/> 
Kemudian dengan melihat pada Log bagian Context, kita bisa mengetahui bahwa Error terjadi pada Database yang bernama "user_db", <br/> 
dan Error Code tersebut adalah "ECONNREFUSED". <br/> 
ECONNREFUSED merupakan kepanjangan dari "Connection Refused", yang mana ini biasanya terjadi ketika Upaya Koneksi Jaringan ditolak secara aktif (actively rejected) oleh Machine atau Service. <br/> <br/> 

^^Contoh 3 : Request or Process ID
Contoh Log :
```
{
  "timestamp": "2024-11-28T10:20:00Z",
  "level": "ERROR",
  "message": "request timed out",
  "context": {
    "request_id": "abc123",
    "process_id": "pid789"
  }
}

```
Pada Case dimana Banyak Proses atau Banyak Request ditangani, Logs yang berisi Contextual Information, ini dapat membantu untuk mengetahui secara Spesifik Request mana atau Process mana yang mengalami masalah. <br/>  <br/> 

yang merupakan "Contextual Information" pada Log diatas adalah :
```
 "context": {
    "request_id": "abc123",
    "process_id": "pid789"
  }
```
Pada Log diatas, terdapat bagian ` "message": "request timed out" ` yang artinya Penyebab Error tersebut adalah "Request Timed Out".
Kemudian dengan melihat pada Log bagian Context, kita bisa mengetahui bahwa Error terjadi pada Spesifik Request & Spesifik Process,
yaitu Request yang memiliki request_id `abc123` dan Proses yang memiliki process_id `pid789`  <br/> <br/> 


^^Contoh 4 : Location or Source of the Issue <br/> 
Misalnya terjadi masalah pada System atau Network Component (Komponen Jaringan), dengan Contextual Information kita dapat mengetahui secara Spesifik System atau Network Component mana yang mengalami masalah. <br/> <br/> 

Contoh Log :
```
{
  "timestamp": "2024-11-28T10:20:00Z",
  "level": "ERROR",
  "message": "failed to connect to remote server",
  "context": {
    "server": "app_server_01",
    "ip_address": "192.168.0.10"
  }
}
```
Pada Log diatas, terdapat bagian "message": "failed to connect to remote server" yang artinya Penyebab Error adalah "Failed to connect ti Remote Server" (Gagal untuk menghubungkan ke Remote Server).<br/> 
Kemudian dengan melihat pada Log bagian Context, kita bisa mengetahui bahwa Error terjadi pada Spesifik Server yaitu "app_server_01" dan Server tersebut memiliki ip_address `192.168.0.10` <br/> <br/> 


^^Contoh 5 : Environment or Configuration Information <br/> 
Logs dapat berisi Informasi Detail mengenai "Environment" diamana System berjalan <br/> 
(Environment tersebut seperti Development, Staging, atau Production). <br/> 

Contoh Logs :
```
{
  "timestamp": "2024-11-28T10:20:00Z",
  "level": "ERROR",
  "message": "configuration file missing",
  "context": {
    "environment": "production",
    "config_file": "/etc/config/app_config.json"
  }
}

```
yang merupakan "Contextual Information" pada Log diatas adalah :
```
 "context": {
    "environment": "production",
    "config_file": "/etc/config/app_config.json"
  }
```
Pada Log diatas, terdapat bagian ` "message": "configuration file missing" ` yang artinya Error diakibatkan oleh "Hilangnya Configuration File". <br/> 
Kemudian dengan melihat pada Log bagian Context, kita bisa mengetahui bahwa :  <br/> 
- Configuration File yang hilang, seharusnya berada pada Environment Production, <br/> 
dah seharusnya berada pada Path `/etc/config/` 
- Nama Configuration yang hilang adalah `app_config.json`

<br/> <br/> 

## D. Example of "Hasura Log" vs "Error Message"
## (Contoh Real Example "Hasura Log", dan Identifilkasi "Error Message" di dalam "Hasura Log" tersebut )

<br/>

## E. How to gain insight from Debug Log

<br/>

## F. How to gain insight from Trace Log
