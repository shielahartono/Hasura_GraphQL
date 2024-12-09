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
