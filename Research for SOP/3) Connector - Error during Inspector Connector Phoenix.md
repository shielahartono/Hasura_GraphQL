# Analyze Real-Life Issue :
# Connector - Error during Inspector Connector Phoenix

<br/><br/>

## 1. Understanding Connector ini General :
## (Memahami Connector secara umum)

-> Connector merupakan komponen yang memungkinkan Hasura untuk meng-integrasikan dengan System atau Services lainnya,  <br/>
yang memungkinkan kita untuk menghubungkan Hasura dengan External Database, API, atau Service lainnya.  <br/>
Connector ini berfungsi sebagai jembatan yang memungkinkan Hasura untuk mengambil atau mengirim Data ke Sumber yang berbeda. <br/><br/>

-> Berikut ini adalah Berbagai Tipe Connector atau Berbagai "Integration Points" pada Connector : <br/>
1. Database Connector (Primary Connector)  <br/>
2. Remote Schema Connector  <br/>
3. Event Trigger Connector <br/>
4. Data Connector (for External Databases)  <br/>
5. Authentication/Authorization Connectors  <br/>
<br/>
("Integration Points" merupakan mekanisme Spesifik yang memungkinkan System atau Service yang berbeda untuk terhubung dan bertukar data)
<br/>
Berikut ini merupakan Penjelasan Detail nya : <br/><br/>

### (1) Database Connector (Primary Connector) :
