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
-> 

## C. Hasura Log vs Error Message 
## (Konsep Perbedaan "Hasura Log" dan "Error Message")

<br/>
<br/>


## D. Example of "Hasura Log" vs "Error Message"
## (Contoh Real Example "Hasura Log", dan Identifilkasi "Error Message" di dalam "Hasura Log" tersebut )


