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



## B. How to See Status Code in Hasura



-----
to do list :
1) Understanding Error Messages & Analyze Log for Troubleshooting in Hasura <br/>
2) Understanding Linux, Docker, and Kubernetes for Troubleshooting in Hasura <br/>
3) Understanding Linux, Docker, and Kubernetes for Scaling in Hasura <br/>
4) Understanding Linux, Docker, and Kubernetes for Horizontal Scale & Vertical Scale in Hasura <br/>
5) API Explorer in Hasura Console for Troubleshooting Issue Missing Required Fields:
