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


### A. Why "Linux", "Docker", and "Kubernetes" are important for Troubleshooting ? <br/>
### (Mengapa Linux, Docker, dan Kubernetes penting untuk Troubleshooting) <br/>


#### 1) Linux : 
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
