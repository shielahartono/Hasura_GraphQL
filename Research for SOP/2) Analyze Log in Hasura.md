# Analyze Log in Hasura

-> Where do you See Error Messges ? <br/>
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
