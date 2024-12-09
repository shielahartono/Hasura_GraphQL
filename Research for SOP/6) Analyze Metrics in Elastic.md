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
Menandakan bahwa data ini adalah Metrik yang bersifat "Generic" atau merupakan 'Metric Umum', yakni tidak spesifik ke satu jenis aplikasi tertentu.






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
