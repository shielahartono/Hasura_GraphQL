# Analyze Metrics in Elastic

Metrics adalah gambaran besar kinerja sistem atau aplikasi, digunakan untuk monitoring dan alerting. 
<br/> <br/><br/>

# A) Metrics yang Success : 

Berikut ini Log Pada Elastic : 

```
{
  "_index": ".ds-metrics-generic-default-2024.12.06-000001",
  "_id": "MBIam5MBatu-e5CD0VNL",
  "_version": 1,
  "_source": {
    "@timestamp": "2024-12-06T08:29:13.561688326Z",
    "data_stream": {
      "dataset": "generic",
      "namespace": "default",
      "type": "metrics"
    },
    "hasura_graphql_requests_total": 9,
    "host": {
      "hostname": "hasura-sheila-688fb7b47c-bgdt8:8080",
      "name": "hasura-sheila-688fb7b47c-bgdt8:8080"
    },
    "operation_name": "MyQuery",
    "operation_type": "query",
    "parameterized_query_hash": "4ef3f375a154c4cf81d3f8f0d1743d568cd9be64",
    "response_status": "success",
    "service": {
      "name": "hasura"
    }
  },
  "fields": {
    "operation_name": [
      "MyQuery"
    ],
    "parameterized_query_hash": [
      "4ef3f375a154c4cf81d3f8f0d1743d568cd9be64"
    ],
    "@timestamp": [
      "2024-12-06T08:29:13.561Z"
    ],
    "operation_type": [
      "query"
    ],
    "response_status": [
      "success"
    ],
    "service.name": [
      "hasura"
    ],
    "data_stream.namespace": [
      "default"
    ],
    "data_stream.dataset": [
      "generic"
    ],
    "host.hostname": [
      "hasura-sheila-688fb7b47c-bgdt8:8080"
    ],
    "host.name": [
      "hasura-sheila-688fb7b47c-bgdt8:8080"
    ],
    "data_stream.type": [
      "metrics"
    ],
    "hasura_graphql_requests_total": [
      9
    ]
  }
}
```

## 1. Informasi Meta Elasticsearch

```
 "_index": ".ds-metrics-generic-default-2024.12.06-000001",
  "_id": "MBIam5MBatu-e5CD0VNL",
  "_version": 1
```

<br/> <br/>

### [1] Index :
Index merupakan "Nama Folder Besar" tempat dokumen ini disimpan di Elastic Search.
```
.ds-metrics-generic-default-2024.12.06-000001
```
-> Arti dari bagian-bagian ini : <br/>
[-] `.ds-metrics` : <br/>
- "ds" = berarti 'Data Stream' (Aliran Data)  <br/>
- "metrics" = ini menunjukkan Data tentang 'Metrik Kinerja System'  <br/>
<br/>
       
[-] `generic` : <br/>
Menandakan bahwa data ini adalah Metrik yang bersifat "Generic" atau merupakan 'Metric Umum', yakni tidak spesifik ke satu jenis aplikasi tertentu. <br/>
<br/> <br/>

[-] `default` :  <br/>
ini adalah "Namespace", <br/>
seperti Group atau Kategori dimana Data disimpan.  <br/>
Pada case ini, nama Namespace tersebut adalah "default"  <br/><br/>

[-] `2024.12.06` : <br/>
merupakan Tanggal data dibuat. <br/>
yang mana, pada case ini adalah "6 Desember 2024" <br/> <br/>

[-] `000001`  : <br/>
merupakan "Generasi Indeks". <br/>
pada case ini, "Generasi Indeks" adalah "000001". <br/>
"Generasi Indeks" digunakan untuk Mengorganisasi Data dalam jumlah besar, <br/>
yang mana hal ini bermanfaat agar Performa tetap baik, Penyimpanan data lebih terorganisir, dan Proses Pencarian Data lebih cepat.
<br/><br/> <br/>

### [2] _Id :
```
 "_id": "MBIam5MBatu-e5CD0VNL"
```
ini merupakan "ID unik dokumen" pada ElasticSearch.  <br/>
 <br/>
Setiap dokumen di Elasticsearch memiliki ID yang unik, seperti nomor identitas. Ini mempermudah Elasticsearch untuk mengambil dokumen tertentu.  <br/>
Dalam ElasticSearch, "ID Unik Dokumen" adalah "Pengidentifikasi Khusus" yang diberikan kepada setiap dokumen yang disimpan di Indeks.
 <br/>

### [3] _version :
```
"_version": 1
```
ini merupakan "Versi Dokumen" dalam Indeks.  <br/>
pada Case ini, Nilai "Versi Dokumen" adalah "1", yang berarti ini adalah "Versi Pertama Dokumen ini".  <br/>
Jika Dokumen diperbarui (misalnya jika data baru ditambahkan), maka "_version" akan meningkat  <br/> <br/>


## 2. Informasi Utama dalam _source
bagian ini merupakan "inti data yang diambil"
```
"_source": {
    "@timestamp": "2024-12-06T08:29:13.561688326Z",
    "data_stream": {
      "dataset": "generic",
      "namespace": "default",
      "type": "metrics"
    },
    "hasura_graphql_requests_total": 9,
    "host": {
      "hostname": "hasura-sheila-688fb7b47c-bgdt8:8080",
      "name": "hasura-sheila-688fb7b47c-bgdt8:8080"
    },
    "operation_name": "MyQuery",
    "operation_type": "query",
    "parameterized_query_hash": "4ef3f375a154c4cf81d3f8f0d1743d568cd9be64",
    "response_status": "success",
    "service": {
      "name": "hasura"
    }
```

### [1] @timestamp :
```
 "@timestamp": "2024-12-06T08:29:13.561688326Z"
```
- @timestamp merupakan "Waktu" dokumen ini dibuat.
- pada case ini, "GraphQL Request" terjadi pada 6 Desember 2024, pukul 08:29:13 UTC

### [2] Data Stream :
```
 "data_stream": {
      "dataset": "generic",
      "namespace": "default",
      "type": "metrics"
```
Elasticsearch menggunakan data stream untuk menangani data yang terus-menerus masuk, seperti log dan metrik <br/> 

"data_stream" ini merupakan informasi tentang Aliran Data. <br/>

[-] `dataset` :
```
 "dataset": "generic"
```
-> `generic` menunjukkan bahwa dataset ini adalah data umum atau tidak spesifik untuk aplikasi tertentu. <br/>
-> Data ini mungkin mencakup metrik dasar seperti penggunaan CPU, memori, atau metrik jaringan yang bisa digunakan oleh berbagai sistem. <br/>
<br/>
-> Contoh : <br/>
- Jika dataset-nya adalah `nginx`, berarti datanya spesifik untuk server NGINX.  <br/>
- Jika dataset-nya `hasura` , berarti data berasal dari aplikasi Hasura. <br/><br/>

[-] `namespace` : 
```
"namespace": "default"
```
->  Namespace adalah grup atau label untuk mengelompokkan data. <br/>
->  Pada case ini, nama "Namespace" tersebut adalah "default" <br/>
->  `default` adalah namespace bawaan, biasanya digunakan jika Anda tidak menentukan namespace khusus saat mengirim data. <br/>
<br/>
-> Tujuan Penamaan Namespace : <br/>
Membantu membedakan data berdasarkan sumber atau tujuan. <br/>
- `default` : Kita dapat mengeetahui bahwa Data tersebut merupakan "Data metrik umum". <br/>
- `application-logs` : Kita dapat mengeetahui bahwa Data tersebut merupakan  "Data log dari aplikasi tertentu". <br/>
- `infrastructure` : Kita dapat mengeetahui bahwa Data tersebut merupakan  "Data dari infrastruktur server". <br/>

<br/>

[-] `type` : <br/>
"type" memberitahukan "Jenis Data".
```
"type": "metrics"
```
-> Pada Case ini, jenis Data tersebut adalah "Metrics" , yang berarti data ini berisi informasi mengenai "Data Pengukuran Kinerja Sistem", seperti Waktu Response aplikasi, dan sebagainya. <br/>
-> Pentingnya "Type" yaitu memberitahukan Informasi apa yang diberitahukan oleh Jenis Data tersebut, <br/>
seperti : <br/>
- `logs` : jenis data ini memberikan informasi mengenai "Data log" (rekaman aktivitas sistem).
- `traces` : jenis data ini memberikan informasi mengenai "Data Trace yang melacak alur permintaan di dalam sistem"


### [3] hasura_graphql_requests_total
```
"hasura_graphql_requests_total": 9
```
-> `hasura_graphql_requests_total`: 
merupakan total "GraphQL Request" yang diterima oleh Hasura

-> `9` : 
artinya, sejauh ini, Hasura telah menerima 9 "GraphQL Request" 

### [4] Host :
```
 "host": {
      "hostname": "hasura-sheila-688fb7b47c-bgdt8:8080",
      "name": "hasura-sheila-688fb7b47c-bgdt8:8080"
    }
```
-> "Host" Informasi tentang server yang memproses permintaan  <br/>
-> `hasura-sheila-688fb7b47c-bgdt8:8080` merupakan Informasi mengenai Nama Host & Port tempat Server atau Aplikasi berjalan.   <br/>
coba kita breakdown :  <br/>
- Hostname : `hasura-sheila-688fb7b47c-bgdt8`
- Port : `8080`   <br/>
yaitu nomor port tempat Hasura GraphQL Engine menjalankan layanannya.  <br/> <br/>


### [5]  operation_name  : 
-> "operation_name" merupakan 'Nama operasi' GraphQL yang dijalankan.
```
  "operation_name": "MyQuery"
```
->  `MyQuery` : Operasi GraphQL yang dilakukan bernama "MyQuery"


### [6]  operation_type :
```
"operation_type": "query"
```
-> `operation_type` : merupakan 'Jenis operasi' pada GraphQL. <br/><br/>

-> `query` : artinya jenis operasi ini adalah "Query",  <br/>
yang  berarti Operasi ini adalah Permintaan Data (query), yang mana Permintaan Data tersebut bersifat "Read-Only" dan tidak mengubah data. <br/><br/>

-> Contoh "Operation Type" lainnya :
- `mutation` : digunakan untuk "mengubah data" di Server.
- `subscription` : digunakan untuk "berlangganan Update Real-Time" dari Server.


<br/><br/>

### [7] parameterized_query_hash :
```
 "parameterized_query_hash": "4ef3f375a154c4cf81d3f8f0d1743d568cd9be64"
```
"parameterized_query_hash" merupakan Hash unique untuk operasi GraphQL . <br/>
yang mana, Hash ini digunakan untuk mengidentifikasi operasi tertentu tanpa menyimpan detail seluruh query. <br/>
yang mana, Hash ini digunakan untuk mengidentifikasi operasi tertentu tanpa menyimpan detail seluruh query. <br/>


### [8]  response_status :
```
"response_status": "success"
```
-> `response_status` : merupakan Status balasan dari server (Status Response dari Server).  <br/>
-> `success` : artinya Operasi berhasil diproses oleh Hasura.  <br/>
 <br/> <br/>


### [9]  service : 
```
 "service": {
      "name": "hasura"
    }
```
-> `service` : merupakan Informasi tentang layanan atau Service yang memproses data ini.  <br/>
-> `hasura` : artinya nama Service adalah "hasura"  <br/>


## 3. Bagian Fields : 
Bagian ini menyusun ulang data dari _source untuk digunakan dalam pencarian atau analitik. 

### [1]  operation_name :
```
 "operation_name": [
      "MyQuery"
    ]
```
-> `MyQuery` : artinya "MyQuery" adalah 'Nama operasi GraphQL' yang dijalankan oleh klien


### [2] parameterized_query_hash :
```
 "parameterized_query_hash": [
      "4ef3f375a154c4cf81d3f8f0d1743d568cd9be64"
    ]
```
-> `parameterized_query_hash` merupakan Hash unik yang merepresentasikan isi query. <br/>
Ini digunakan untuk mengenali query serupa yang dikirimkan berulang kali oleh klien tanpa menyimpan detailnya. <br/>
Misalnya, Kita memiliki sebuah query (permintaan data) yang sama, tetapi dengan parameter yang berbeda-beda.  <br/><br/>

-> Daripada menyimpan setiap query yang berbeda dengan parameter yang berbeda, sistem hanya akan menyimpan "Unique Hash" dari struktur query itu sendiri. <br/>

-> Jadi, meskipun Parameter nya berbeda, karena struktur query-nya sama, hash-nya akan tetap sama. <br/> <br/>

-> Daripada menyimpan banyak query dengan Parameter yang berbeda-beda, sistem hanya menyimpan hash-nya saja. Ini menghemat banyak ruang penyimpanan. <br/><br/>

-> Sistem bisa memantau berapa sering query yang sama dipanggil. Ini berguna untuk mengetahui query mana yang lebih sering dipakai.
<br/><br/>




### [3] @timestamp :
```
"@timestamp": [
      "2024-12-06T08:29:13.561Z"
    ]
```

-> `@timestamp` merupakan Waktu ketika operasi ini terjadi, dalam format UTC. <br/><br/>
-> pada Case ini, Operasi ini terjadi pada 6 Desember 2024, pukul 08:29:13 UTC.
<br/><br/>


### [4]  operation_type :
```
 "operation_type": [
      "query"
    ]
```
-> `operation_type` merupakan 'Jenis operasi' GraphQL yang dilakukan <br/><br/>

-> `query` : artinya jenis operasinya adalah "Permintaan Data dari Server".
yang mana, jenis operasi "query" artinya hanya "read-only", dan tidak melakukan perubahan data seperti `mutation` dan tidak menerima Data Real-Time seperti `subscription`. <br/><br/>



### [5]  response_status :
```
"response_status": [
      "success"
    ]
```
-> `response_status` artinya Status respons dari server <br/>

-> `success` artinya Operasi berhasil tanpa error <br/>


### [6]  service.name :
```
 "service.name": [
      "hasura"
    ]
```
-> `service.name` artinya  Nama layanan atau aplikasi yang menghasilkan Metrices ini. <br/>
Pada case ini, Metrices berasal dari aplikasi Hasura. <br/><br/>



### [7] data_stream.namespace :
```
"data_stream.namespace": [
      "default"
    ]
```
-> `data_stream.namespace` adalah elemen yang digunakan  untuk mengelompokkan data berdasarkan kategori atau tujuan tertentu. <br/>
Dalam hal ini, "namespace" digunakan untuk memberi label atau kelompok untuk data yang dikumpulkan. <br/><br/>

-> Namespace adalah cara untuk mengelompokkan atau mengorganisir data observabilitas yang dikumpulkan. <br/><br/>

-> Data observabilitas seperti log, metrics, atau traces dapat dikelompokkan ke dalam namespace tertentu untuk membedakan satu set data dengan set lainnya. <br/><br/>

-> `default` : <br/>
pada Case ini, nilai namespace adalah "default". Ini menunjukkan bahwa data observabilitas ini tidak memiliki namespace khusus dan disimpan dalam namespace default. <br/><br/>

### [8]  data_stream.dataset  :
```
"data_stream.dataset": [
      "generic"
    ]
````
-> `data_stream.dataset`: adalah elemen yang digunakan untuk mengidentifikasi "jenis dataset" yang digunakan untuk mengelompokkan data observabilitas. <br/>
Dataset ini menggambarkan kategori data berdasarkan jenis atau sumber data yang dikumpulkan. <br/><br/>

-> `generic` : <br/>
Pada case ini, "Jenis Dataset" adalah `generic`. <br/>
ini berarti data tersebut adalah data umum atau generik yang tidak terikat pada dataset spesifik. Ini biasanya digunakan untuk data yang tidak terkait langsung dengan aplikasi atau proses tertentu. <br/><br/>

-> Contoh lain, jenis Dataset : <br/>
- `database` untuk data yang berkaitan dengan sistem basis data.
- `web` untuk data yang berkaitan dengan aplikasi web atau permintaan HTTP.
- `authentication` untuk data yang berkaitan dengan sistem autentikasi.

<br/><br/>

### [9] host.hostname
```
 "host.hostname": [
      "hasura-sheila-688fb7b47c-bgdt8:8080"
    ]
```
-> `hasura-sheila-688fb7b47c-bgdt8` = ini adalah "hostname". <br/>
yang mana, "hostname" adalah Nama server atau container tempat aplikasi berjalan. <br/><br/>

-> `8080` : ini adalah "Port". <br/>
yang mana ini merupakan "Port" tempat server menerima koneksi <br/><br/>

### [10]  data_stream.type  :
```
"data_stream.type": [
      "metrics"
```

-> `data_stream.type` : memberikan informasi mengenai tipe data yang dikumpulkan, yang membantu untuk mengelompokkan data sesuai dengan kategori atau fungsinya.  <br/><br/>

-> `metrics` :  <br/>
pada Case ini, kita memakai Tipe data "metrices". <br/>
Data ini berisi pengukuran dan statistik performa atau status sistem. <br/>

-> (contoh lain type) berikut ini adalah tiga kategori utama dalam Observabilitas :
- `metrics` : Data yang berisi pengukuran dan statistik performa atau status sistem. Contoh: penggunaan CPU, memori, latensi,  throughput, dll.
- `logs` : Data yang berisi informasi log tentang aktivitas dan kejadian dalam aplikasi atau sistem. Contoh: error logs, event logs, dll. 
- `traces` : Data yang berisi jejak atau riwayat eksekusi dari permintaan atau proses yang berjalan dalam aplikasi, untuk melacak alur eksekusi dan interaksi antara layanan. <br/>


### [11]  hasura_graphql_requests_total  :
```
"hasura_graphql_requests_total": [
      9
    ]
```
-> `hasura_graphql_requests_total` : ini merupakan Total permintaan GraphQL (GraphQL Request) yang telah diterima oleh server Hasura pada saat log ini dihasilkan.

-> `9` : artinya Server Hasura telah menerima 9 'GraphQL Request'.


--------
--------
# B) Metrics yang Failed : 

```
{
  "_index": ".ds-metrics-generic-default-2024.12.06-000001",
  "_id": "kRJGm5MBatu-e5CDTqZF",
  "_version": 1,
  "_source": {
    "@timestamp": "2024-12-06T09:16:43.968594654Z",
    "data_stream": {
      "dataset": "generic",
      "namespace": "default",
      "type": "metrics"
    },
    "hasura_cron_events_invocation_total": 0,
    "hasura_cron_events_processed_total": 0,
    "hasura_oneoff_events_invocation_total": 0,
    "hasura_oneoff_events_processed_total": 0,
    "host": {
      "hostname": "hasura-sheila-688fb7b47c-bgdt8:8080",
      "name": "hasura-sheila-688fb7b47c-bgdt8:8080"
    },
    "service": {
      "name": "hasura"
    },
    "status": "failed"
  },
  "fields": {
    "hasura_cron_events_processed_total": [
      0
    ],
    "@timestamp": [
      "2024-12-06T09:16:43.968Z"
    ],
    "service.name": [
      "hasura"
    ],
    "data_stream.namespace": [
      "default"
    ],
    "data_stream.dataset": [
      "generic"
    ],
    "hasura_cron_events_invocation_total": [
      0
    ],
    "hasura_oneoff_events_processed_total": [
      0
    ],
    "host.hostname": [
      "hasura-sheila-688fb7b47c-bgdt8:8080"
    ],
    "host.name": [
      "hasura-sheila-688fb7b47c-bgdt8:8080"
    ],
    "data_stream.type": [
      "metrics"
    ],
    "hasura_oneoff_events_invocation_total": [
      0
    ],
    "status": [
      "failed"
    ]
  }
}
```

## 1. Index :

### [1] Index :
Index merupakan "Nama Folder Besar" tempat dokumen ini disimpan di Elastic Search.
```
.ds-metrics-generic-default-2024.12.06-000001
```
-> Arti dari bagian-bagian ini : <br/>
[-] `.ds-metrics` : <br/>
- "ds" = berarti 'Data Stream' (Aliran Data)  <br/>
- "metrics" = ini menunjukkan Data tentang 'Metrik Kinerja System'  <br/>
<br/>
       
[-] `generic` : <br/>
Menandakan bahwa data ini adalah Metrik yang bersifat "Generic" atau merupakan 'Metric Umum', yakni tidak spesifik ke satu jenis aplikasi tertentu. <br/>
<br/> <br/>

[-] `default` :  <br/>
ini adalah "Namespace", <br/>
seperti Group atau Kategori dimana Data disimpan.  <br/>
Pada case ini, nama Namespace tersebut adalah "default"  <br/><br/>

[-] `2024.12.06` : <br/>
merupakan Tanggal data dibuat. <br/>
yang mana, pada case ini adalah "6 Desember 2024" <br/> <br/>

[-] `000001`  : <br/>
merupakan "Generasi Indeks". <br/>
pada case ini, "Generasi Indeks" adalah "000001". <br/>
"Generasi Indeks" digunakan untuk Mengorganisasi Data dalam jumlah besar, <br/>
yang mana hal ini bermanfaat agar Performa tetap baik, Penyimpanan data lebih terorganisir, dan Proses Pencarian Data lebih cepat.
<br/><br/> <br/>


## 2.  _Id :
```
 "_id": "kRJGm5MBatu-e5CDTqZF"
```
ini merupakan "ID unik dokumen" pada ElasticSearch.  <br/>
 <br/>
Setiap dokumen di Elasticsearch memiliki ID yang unik, seperti nomor identitas. Ini mempermudah Elasticsearch untuk mengambil dokumen tertentu.  <br/>
Dalam ElasticSearch, "ID Unik Dokumen" adalah "Pengidentifikasi Khusus" yang diberikan kepada setiap dokumen yang disimpan di Indeks.
 <br/>


## 3.  _version :
```
"_version": 1
```
ini merupakan "Versi Dokumen" dalam Indeks.  <br/>
pada Case ini, Nilai "Versi Dokumen" adalah "1", yang berarti ini adalah "Versi Pertama Dokumen ini".  <br/>
Jika Dokumen diperbarui (misalnya jika data baru ditambahkan), maka "_version" akan meningkat  <br/> <br/>


## 4. _source :

### [1] @timestamp :
```
 "@timestamp": "2024-12-06T08:29:13.561688326Z"
```
- @timestamp merupakan "Waktu" dokumen ini dibuat.
- pada case ini, "GraphQL Request" terjadi pada  6 Desember 2024, pukul 09:16:43 UTC


### [2] Data Stream :
```
 "data_stream": {
      "dataset": "generic",
      "namespace": "default",
      "type": "metrics"
```
Elasticsearch menggunakan data stream untuk menangani data yang terus-menerus masuk, seperti log dan metrik <br/> 

"data_stream" ini merupakan informasi tentang Aliran Data. <br/>

[-] `dataset` :
```
 "dataset": "generic"
```
-> `generic` menunjukkan bahwa dataset ini adalah data umum atau tidak spesifik untuk aplikasi tertentu. <br/>
-> Data ini mungkin mencakup metrik dasar seperti penggunaan CPU, memori, atau metrik jaringan yang bisa digunakan oleh berbagai sistem. <br/>
<br/>
-> Contoh : <br/>
- Jika dataset-nya adalah `nginx`, berarti datanya spesifik untuk server NGINX.  <br/>
- Jika dataset-nya `hasura` , berarti data berasal dari aplikasi Hasura. <br/><br/>

[-] `namespace` : 
```
"namespace": "default"
```
->  Namespace adalah grup atau label untuk mengelompokkan data. <br/>
->  Pada case ini, nama "Namespace" tersebut adalah "default" <br/>
->  `default` adalah namespace bawaan, biasanya digunakan jika Anda tidak menentukan namespace khusus saat mengirim data. <br/>
<br/>
-> Tujuan Penamaan Namespace : <br/>
Membantu membedakan data berdasarkan sumber atau tujuan. <br/>
- `default` : Kita dapat mengeetahui bahwa Data tersebut merupakan "Data metrik umum". <br/>
- `application-logs` : Kita dapat mengeetahui bahwa Data tersebut merupakan  "Data log dari aplikasi tertentu". <br/>
- `infrastructure` : Kita dapat mengeetahui bahwa Data tersebut merupakan  "Data dari infrastruktur server". <br/>

<br/>

[-] `type` : <br/>
"type" memberitahukan "Jenis Data".
```
"type": "metrics"
```
-> Pada Case ini, jenis Data tersebut adalah "Metrics" , yang berarti data ini berisi informasi mengenai "Data Pengukuran Kinerja Sistem", seperti Waktu Response aplikasi, dan sebagainya. <br/>
-> Pentingnya "Type" yaitu memberitahukan Informasi apa yang diberitahukan oleh Jenis Data tersebut, <br/>
seperti : <br/>
- `logs` : jenis data ini memberikan informasi mengenai "Data log" (rekaman aktivitas sistem).
- `traces` : jenis data ini memberikan informasi mengenai "Data Trace yang melacak alur permintaan di dalam sistem"


## 5. hasura_cron_events_invocation_total
```
hasura_cron_events_invocation_total": 0
```

-> `hasura_cron_events_invocation_total` : <br/>
Metrik ini menunjukkan jumlah total "cron events" yang telah 'dipanggil' oleh Hasura. <br/>
(Invocation = Pemanggilan) <br/>

-> "Cron events" adalah event yang dijadwalkan untuk dijalankan pada waktu tertentu, seperti tugas terjadwal. <br/>
<br/>
-> Contoh "Cron Event" : <br/>
Bayangkan Anda memiliki aplikasi e-commerce, dan Anda ingin: <br/>

- Mengirimkan email promosi setiap hari pukul 7 pagi.
- Mengirim pengingat email ke pengguna setiap hari pukul 9 pagi.
- Memproses laporan penjualan setiap akhir bulan.
- Memperbarui cache atau data tertentu setiap jam.
<br/>
Cron events memungkinkan Anda menjadwalkan tugas-tugas ini tanpa campur tangan manual. <br/> <br/>


-> `0` : <br/>
pada case ini, nilai "Cron Events" adalah 0. <br/>
ini berarti tidak ada cron event yang dipanggil sejauh ini. <br/><br/>




## 6. hasura_cron_events_processed_total 
```
"hasura_cron_events_processed_total": 0
```

-> `hasura_cron_events_processed_total` : <br/>
Metrik ini menunjukkan jumlah total "cron events" yang telah diproses oleh Hasura. <br/>
<br/>
-> Setelah cron event dipanggil, Hasura bertanggung jawab untuk menjalankan atau memproses event tersebut. <br/><br/>

-> `0` : <br/>
Nilai 0 berarti tidak ada cron event yang berhasil diproses. <br/><br/>

## 7. hasura_oneoff_events_invocation_total
```
"hasura_oneoff_events_invocation_total": 0
```

## 8. hasura_oneoff_events_processed_total
```
"hasura_oneoff_events_processed_total": 0
```
