# Cara Menampilkan Metrices pada Elastic

-> Endpoint Elastic : 10.100.13.25:9200
<br/>
-> Endpoint Hasura : http://10.100.14.16:8332/v1/graphql
<br/>
("Endpoint Hasura" diambil dari URL yang ada di bagian atas saat kita membuka Hasura di Rancher). <br/><br/>

Note : <br/>
[-] Pada Postman, Kita melakukan Hit pada "Endpoint Elastic" adalah untuk mengecek apakah "Elastic sudah berjalan atau belum".
Note :  <br/>
- Melakukan pengecekkan dengan Hit "Endpoint Elastic" adalah untuk melihat apakah "Elastic sudah berhasil berjalan", bukan untuk melihat apakah Elastic sudah terhubung ke 'Open Telemetry' atau belum. Karena penghubungan antara 'Open Telemetery' dan 'Elastic' dilakukan menggunakan Server Ubuntu Linux, sehingga untuk mengecek apakah 'Open Telemetery' sudah dihubungkan ke 'Elastic', Pengecekkan dilakukan menggunakan Server Ubuntu Linux.


[-] Pada Postman, Kita melakukan Hit pada "Endpoint Hasura" adalah untuk "Menampilkan Metrics" pada Elastic.  <br/>
saat kita melakukan "Hit" menggunakan Postman, di bagian Body pada Postman, kita masukkan Query apa saja dari Hasura kita yang ada di Rancher. <br/><br/>
