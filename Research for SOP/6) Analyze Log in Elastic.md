# Analyze Metrics in Elastic

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
