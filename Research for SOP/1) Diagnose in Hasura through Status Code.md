# Diagnose in Hasura Through Status Code

-> Memahami HTTP Status Code pada Hasura merupakan hal yang penting untuk melakukan Diagnosa Issue pada API Request. <br/>
-> Status Code ini dapat membantu kita untuk menentukkan apakah masalah disebabkan oleh Sisi Client (Client-Side Errors) seperti Incorrect Requests, <br/>
atau masalah disebebkan oleh oleh Sisi Server (Server-Side Issue) seperti Server Overload atau masalah pada Database Connectivity. <br/>

## A. Understanding Status Code in Hasura <br/>

### 1) Statues Code : 200 OK <br/>

-> Status Code ini berarti "Successful" atau Request diproses secara Success, dan Server me-respond dengan data yang diharapkan. <br/>

### 2) Status Code : 400 Bad Request  <br/>
-> Status Code ini mengindikasikan bahwa terdapat masalah pada Request dari Client, <br/>
(masalahnya ada pada Sisi Client) <br/>
sehingga Server tidak bisa memproses Request tersebut. <br/>

-> Common Cause (Penyebab Umum) : <br/>
[-] Syntax Errors : <br/>
GraphQL Syntax yang salah pada Query (seperti Missing Brackets (lupa tutup kurung)). <br/>

[-] Invalid Field Names : <br/>
ini berarti 'Field Names' (nama field) yang kita refrensikan tidak cocok dengan Nama Field yang ada di System. <br/>
yang mana, Error "Invalid Field Names" ini biasanya karena Client melakukan Request atau melakukan Mutasi untuk "Field" yang tidak ada di Schema. <br/>

[-] Missing Required Fields : <br/>
ini berarti "Field" yang dibutuhkan tidak dicantumkan pada Request. <br/>

-> How to Diagnose (Cara melakukan Diagnosa) : <br/>
[-] Check Error Message : <br/>
Hasura biasanya menyediakan "Error Message" secara detail pada Response untuk membantu melakukan Diagnosa pada Issue. <br/>

[-] Test in Hasura Console : <br/>
"Hasura Console" merupakan User Interface atau Dashboard yang memungkinkan Developer untuk berinteraksi dengan Hasura. <br/>
"API Explorer" pada Hasura Console, memungkinkan kita untuk menemukan masalah Syntax (Syntax Issue) atau menemukan Missing Fields <br/>
, dan memungkinkan kita untuk Menjalankan (Run) & Troubleshoot Query secara langsung. <br/> <br/>


-> Contoh Error "400 Bad Request" : <br/>
Jika kita Request Field dengan menulis "usernames" padahal nama field yang benar adalah "username", <br/>
maka kita akan mendapat 400 Status Code dengan error message "Unknown field 'usernames' " <br/> <br/>


### 3) Status Code : 401 Unauthorized  <br/>
-> Status Code ini berarti Request memerlukan "User Authentication", dan Client tidak menyediakan "User Authentication" tersebut. <br/>
-> ini berarti Request nya ditolak karena kurangnya "Authentication Credentials" yang layak, seperti Token. <br/>
<br/>
-> Common Causes (Penyebab Umum) : <br/>
[-] Missing Authorization Token : <br/>
ini biasanya terjadi karena System mengharapkan agar "Authorization Token" disediakan <br/>
("Authorization Token" tersebut seperti "API Key", "JWT", atau "OAuth Token"), <br/>
yang mana Request tersebut tidak mengandung "Authorization Token" atau Key. <br/>
<br/>
[-] Invalid or Expired Token : <br/>
ini berarti "Authorization Token" yang digunakan "Invalid" atau "Expired". <br/>
"Invalid" berarti Token tersebut Salah. <br/>
"Expired" berarti Token yang disediakan telah melebihi batas waktu kadaluwarsa nya (has passed its expiration time). <br/>
yang berarti Token tersebut tidak lagi Valid untuk Autentikasi atau Autorisasi. <br/>
<br/>
<br/> 
-> How to Diagnose (Cara melakukan Diagnosa) :  <br/> 
[-] Verify Token : <br/> 
mengecek Token pada 'Request Header' dan memastikkan Token tersebut Valid. <br/> 
<br/> 
[-] Check Hasura Permissions : <br/> 
Pada Hasura Console, kita arahkan ke Tab "Permissions" untuk memastikkan "User Role" (User Role yang diasosiasikan dengan Token tersebut) sudah mempunyai Akses ke Resource atau Data yang kita Request. <br/> 


### 4) Status Code : 403 Forbidden  <br/> 

-> Status Code ini memiliki arti walaupun Request dikenali, tetapi Server memblokir Request tersebut karena tidak User tidak memiliki Permissions (izin) yang memadai. <br/> 

-> Common Cause (Penyebab Umum) : <br/> 
[-] Role Restrictions : <br/> 
Role yang berkaitan dengan Token tidak punya Permission (izin) untuk menjalankan Operasi yang diminta. <br/> 

[-] Row-Level Permissions : <br/> 
"Row-Level Permissions" merupakan Pembatasan akses pada "Row Level",  <br/> 
ini berarti User memiliki larangan untuk mengakses atau melakukan Operasi pada Row (baris) tertentu. <br/> 
<br/> 
-> How to Diagnose (cara melakukan Diagnosa) :   <br/> 
[-] Check Role Permissions : <br/> 
Pilih Tab "Permissions" di 'Hasura Console' untuk memastikkan Role diizinkan untuk melakukan suatu tindakan. <br/> 
<br/> 
[-] Verify Row-Level Permissions : <br/> 
Kita perlu melakukan Review pada "Row-Level Permissions" yang ditetapkan pada Table untuk memastikkan Role yang diminta memenuhi ketentuan Akses. <br/> 
<br/>  <br/> 
-> Contoh Error "403 Forbidden" :  <br/> 
Contoh Budi memiliki Role hanya sebagai "Viewer", tetapi Budi mencoba untuk menghapus Data, <br/> 
namun hanya "Admin" yang diperbolehkan untuk menghapus data, <br/> 
sehingga mengirimkan Respons "403 Error" <br/> <br/> 


### 5) Status Code : 404 Not Found  <br/> 

-> Status Code ini meingdikasikan bahwa Server tidak dapat menemukan Resource atau Data yang diminta pada Request, <br/> 
Mungkin karena Data hilang (Missing) atau Endpoint yang salah (incorrect Endpoint). <br/> 
<br/> 
-> Common Cause (Penyebab Umum) : <br/> 
[-] Invalid Endpoint : <br/> 
(Endpoint yang salah) <br/> 
ini berarti terdapat kesalahan pada Endpoint (pada URL Path di Request)  <br/> 
<br/> 
[-] Nonexistent Resource : <br/> 
User mencoba untuk mengakses Table, Field, atau Endpoint yang tidak ada di Hasura. <br/> 
<br/> 

-> How to Diagnose (Cara melakukan Diagnosa ) : <br/> 
[-] Verify Endpoint URL : <br/> 
Kita pastikkan "Endpoint URL" sudah benar <br/> 
<br/> 
[-] Check Resource Availability : <br/> 
Pada Hasura Console, kita dapat mengecek bahwa Table & Fields itu Ada dan dapat diakses <br/> 
(Table & Fields exist and are accessible) <br/>  <br/> 


### 6) Status Code : 500 Internal Server Error <br/>

-> Status Code ini memilik arti "Server-Side Error", yang berarti Issue nya ada di Sisi Hasura (atau koneksi Hasura ke Database), <br/>
dan issue nya bukan karena Request dari Client. <br/>
<br/>
-> Common Cause (Penyebab Umum) : <br/>
[-] Database Connectivity Issues: <br/>
Hasura tidak bisa Connect ke Database <br/>
<br/>
[-] Resource Limitations :  <br/>
Kemungkinan Server mengalami "Out of Memory" atau Server mengalami "High CPU Load." <br/>
<br/>
"Out of Memory"(OOM) merupakan kondisi pada Server dimana Operating System (OS) kehabisan ketersediaan RAM (Random Access Memory) yang bisa dialokasikan untuk menjalankan proses. <br/>
yang mana "Out of Memory" dapat menyebabkan penurunan performa yang serius atau System Crash karena Operating System tidak dapat menyediakan Memory yang cukup untuk menjalankan Proses yang baru atau Proses yang sudah ada. <br/>
Saat System sudah mencapai kondisi dimana System tidak bisa menyediakan Memory untuk menjalankan Proses, System dapat mengambil tindakan seperti "Killing Process" (Menghentikan Poses) untuk 'Free-Up Memory' (membebaskan Memory), yang mana tindakan ini terkadang dapat terjadi tanpa User Intervention (tanpa campur tangan pengguna), <br/>
yang mana umumnya hal ini disebut sebagai mekanisme "OOM Killer" pada Linux. <br/>
<br/>
"High CPU Load" merupakan Situasi dimana Processor (CPU) dari sebuah Server sedang dalam Heavy Usage (sedang digunakan secara berat), 
artinya CPU tersebut memproses Task yang mendekati Full Capacity (kapasitas penuh dari CPU). <br/>
yang mana, hal ini dapat diakibatkan oleh hal seperti Menjalankan terlalu banyak Proses secara bersamaan, Inefficient Code (Code yang tidak efisien), atau menangani terlalu banyak Request melebihi yang System bisa. <br/>
("Inefficient Code" merupakan Code yang tidak menggunakan System Resources secara efisien, seperti terdapat Infinite Loop, Unoptimized Algorithm (Algorithm yang tidak teroptimisasi dengan baik), dan lain sebagainya) <br/>
<br/> 
[-] Timeouts :  <br/>
Timeouts berarti Request memakan waktu terlalu lama untuk diproses, seringkali ini terjadi karena Query yang Complex atau tidak efsien (Ineffiecient Query). <br/>
("Inefficient Query" merupakan Query yang memakan lebih banyak waktu atau Resources daripada yang dibutuhkan. <br/>
yang mana Query tersebut biasanya kurang memakai Index (lack of index), melakukan pengambilan data lebih dari yang diperlukkan (seperti memakai `select *` padahal hanya membutuhkan sedikit data), dan lain sebagainya ). <br/>  <br/>
<br/>
-> How to Diagnose (cara melakukan Diagnosa) : <br/>
[-] Check Logs :  <br/>
Hasura Logs seringkali menyediakan Detail mengenai Error, terutama yang berkaitan dengan Connectivity (konektifitas) atau Timeout Issues. <br/>
<br/>
[-] Monitor Server Resources : <br/>
Check penggunaan Memory dan CPU pada Server. <br/>
Jika penggunaan secara konsisten terus-menerus tinggi, pertimbangkan untuk meng-optimisasi Query (Optimizing Query).  <br/>
<br/>
[-] Simplify Queries : <br/>
lakukan Test dengan Query yang lebih sederhana untuk melihat apakah Hasura dapat menangani Query tersebut tanpa terjadi Issue. <br/>
<br/>
-> Contoh Error "500 Internal Server Error" : <br/>
Query yang mencoba melakukan Join pada beberapa Table tanpa Indexing yang bagus, dapat mengakibatkan Timeout, sehingga terjadi Error dengan Status Code "500" <br/>
<br/>

### 7) Status Code : 502 Bad Gateway / 504 Gateway Timeout <br/>

-> Status Code "502 Bad Gateway" & "504 Gateway Timeout" mengindikasikan "Server-Side Issues" (Issue yang terjadi di Server). <br/>
<br/>
-> Status Code "502 Bad Gateway" & "504 Gateway Timeout" <br/>
mengindikasikan adanya "Communication Issues" (masalah Komunikasi) dengan "Upstream Services", <br/>
yang mana seringkali issue ini terjadi antara Hasura dan Database (atau dengan Services lainnya yang terhubung yang bertindak sebagai Upstream Services (Penyedia Data)). <br/>
<br/>
>> ^For your information^ <br/>
>> ### 1) Upstream Service : <br/>
>> -> "Upstream Services" merupakan Component atau Services yang menyediakan Data (atau yang menyediakan functionality yang dibutuhkan oleh 'Downstream Services'). <br/>
>> <br/>
>> -> "Downstream" : <br/>
>> merupakan Service yang membuat Request  <br/>
>> <br/>
>>
>> -> "Upstream" : <br/>
>> merupakan Service atau Component yang me-respond terhadap Request. <br/>
> yang mana, "Upstream Services" merupakan Services yang berinteraksi atau dimintai Data oleh Downstream Services. <br/>
>>  <br/>
>> -> Istilah untuk memberi Contoh :  <br/>
>> Contoh nya pada Restaurant, mari kita buat analogy : <br/>
>> [-] Downstream Servive : <br/>
>> Customer merupakan "Downstream Service". <br/>
>> "Downstream Service" merupakan yang meminta Data. <br/>
>> Contoh pada implementasinya, "Downstream Service" ini merupakan "Web Application" <br/>
>> "Web Application" merupakan "Downstream Service" karena "Web Application" meminta Data <br/>
>>  <br/>
>> [-] Intermediate Service : <br/>
>> Waiter (Pelayan) merupakan "Intermediate Service". <br/>
>> "Intermediate Service" merupakan yang mengantarkan Data <br/>
>> Contoh pada implementasinya, "Intermediate Service" merupakan "Backend Server" <br/>
>> "Backend Server" merupakan "Intermediate Service" karena "Backend Server" menangani Request dan Response antara 'Web Application' dan Database. <br/>
>> yang mana "Backend Server" menangani Request & Response dengan "Mengantarkan Data" antara 'Web App' dan Database. <br/>
>>  <br/>
>> 
>> [-] Upstream Service : <br/>
>> Kitchen (dapur) merupakan "Upstream Service". <br/>
>> "Upstream Service" merupakan yang Menyediakan Data. <br/>
>> Contoh pada implementasinya, "Upstream Service" merupakan "Database". <br/>
>> "Database" merupakan "Upstream Service" karena Database menyediakan Data ke "Backend Server" (Intermediate Service) <br/>
>> <br/>
>> -> Contoh Alur Kerja "Upstream Services", "Intermediate Services", dan "Backend Server" pada konteks Web Services : <br/>
>> (1) User menggunakan "Web Application"  <br/>
>> (2) "Web Application" mengirim Request ke "Backend Server", yang mana Request tersebut berisi informasi untuk Mengambil Data (Fetch Data) <br/>
>> (3) "Backend Server" meminta ke Database mengenai Data yang diminta pada Request <br/>
>> (4) Database mengirim data yang diminta ke "Backend Server", <br/>
>> yang mana kemudian "Backend Server" mengirim Data ke "Web Application" <br/>
>> <br/>
>>





-----
to do list :
1) Understanding Error Messages & Analyze Log for Troubleshooting in Hasura  -> Untuk Troubleshoot ini, langsung cari tahu cara pengerjaannya  menggunakan Linux, Docker, dan Kubernetes.    <br/>
(Pahami Konsep cara Solve Issue nya, kemudian Langsung cari tahu cara Solve Issue tersebut menggunakan Linux, Docker, dan Kubernetes)<br/>  <br/>
2) How to see Status Code in Hasura
<br/>  <br/>
3) The Difference between  502 Bad Gateway vs 504 Gateway Timeout
   <br/> (explain the Detail)
<br/>  <br/>
2) Understanding Linux, Docker, and Kubernetes for Troubleshooting in Hasura <br/>
3) Understanding Linux, Docker, and Kubernetes for Scaling in Hasura <br/>
4) Understanding Linux, Docker, and Kubernetes for Horizontal Scale & Vertical Scale in Hasura <br/>
5) API Explorer in Hasura Console for Troubleshooting Issue (Missing Required Fields, and hopefully other issue)
