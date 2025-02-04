# Dokumentasi Open Telemetry - Task


## (A) Connect ke Server yang dipakai 
Kita Connect ke Server yang dipakai dengan cara : <br/>
(1) Buka "Windows Powershell"  <br/> <br/>

(2) ketik command berikut ini :  <br/>
ssh root@10.100.13.239
<br/> <br/>
(3) kemudian ketik Password  <br/><br/>

## (B) Install Docker pada Server yang dipakai
(link referensi Dokumentasi : https://docs.docker.com/engine/install/ubuntu/ )

### 1. Set up Docker's `apt` repository.

Pada Terminal Windows Powershell, kita jalankan Command berikut :

```
sudo apt-get update
```

```
sudo apt-get install ca-certificates curl
```

```
sudo install -m 0755 -d /etc/apt/keyrings
```

```
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
```

```
sudo chmod a+r /etc/apt/keyrings/docker.asc
```

```
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

### 2. Install the Docker packages.

```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

### 3. Verify that the installation is successful by running the `hello-world` image:

```
sudo docker run hello-world
```
## (C) Kita buat Folder & File

[1] Buat Folder OTEL :
```
mkdir OTEL
```

[2] Buat file otel-collector-config.yaml
```
touch otel-collector-config.yaml
```

## (D) Install "Open Telemetry" pada Server

Link Referensi Dokumentasi :  <br/>
https://opentelemetry.io/docs/collector/installation/          <br/>
https://opentelemetry.io/docs/collector/configuration/          <br/>

### 1. Masuk ke Folder OTEL :
```
cd OTEL
```

### 2. Jalankan Command berikut ini :
```
docker pull otel/opentelemetry-collector-contrib:0.114.0
```

```
docker run otel/opentelemetry-collector-contrib:0.114.0
```

### 3. Masukkan "File Configuration YAML" untuk "Open Telemetry"

[1] tampilkan Daftar File atau Direktori : 
```
ls -ll
```
![image](https://github.com/user-attachments/assets/d172dde1-03ad-4433-8564-5a93d35e0362)


[2] Kita arahkan ke Folder "OTEL"  <br/>
```
cd OTEL
```

[3] Kemudian tampilkan daftar file pada Folder OTEL <br/>
```
ls -ll
```
![image](https://github.com/user-attachments/assets/2c826014-fd9d-402d-bb6e-c4a88d6c6a13)

[4] Kemudian kita edit file "otel-collector-config.yaml" untuk memasukkan File Configurasi
```
nano otel-collector-config.yaml
```
![image](https://github.com/user-attachments/assets/5492195a-3238-4704-bf02-8433e05ea610)

<br/> <br/>
Kemudian kita masukkan File Configurasi berikut ini :
```
receivers:
  otlp:
    protocols:
      grpc:
        endpoint: 0.0.0.0:4317
      http:
        endpoint: 0.0.0.0:4318
processors:
  batch:

exporters:
  debug: {}
  verbosity: detailed

extensions:
  health_check:
  pprof:
    endpoint: 0.0.0.0:1777
  zpages:
    endpoint: 0.0.0.0:55679

service:
  pipelines:
    traces:
      receivers: [otlp]
      processors: [batch]
      exporters: [debug, otlp]
    metrics:
      receivers: [otlp]
      processors: [batch]
      exporters: [debug, otlp]
    logs:
      receivers: [otlp]
      processors: [batch]
      exporters: [debug, otlp]
```

![image](https://github.com/user-attachments/assets/e9350219-64bd-4626-a222-f62723292a9f)


<br/><br/>

[5] Kemudian kita ketik `ctrl + x` untuk Exit. <br/>
Kemudian kita pilih "yes" untuk Save

<br/><br/>


[6] Kemudian kita jalankan Command berikut ini :
```
docker run -d -v $(pwd)/otel-collector-config.yaml:/root/OTEL/otel-collector-config.yaml otel/opentelemetry-collector-contrib:0.114.0
```

### (E) Check apakah "OpenTelemetry Collector" (otelcol)  sudah ter-install :
```
sudo systemctl status otelcol

```
![image](https://github.com/user-attachments/assets/e245a478-3fd4-4011-8044-da33b81f1c38)
Setelah menjalankan ini, terdapat issue `Unit otelcol.service could not be found`

### (F) Install "OpenTelemetry Collector" (otelcol) pada Server

Kita cari error `Unit otelcol.service could not be found` pada ChatGPT, <br/>
yang mana, Error tersebut artinya kita perlu install "otelcol", <br/>

#### [1] maka kita jalankan Command berikut : <br/>

```
which otelcol
```

```
curl -sL https://github.com/open-telemetry/opentelemetry-collector-releases/releases/download/v0.81.0/otelcol_0.81.0_linux_amd64.deb -o otelcol.deb
```

```
sudo dpkg -i otelcol.deb

```

```
sudo nano /etc/systemd/system/otelcol.service
```

<br/> <br/>

#### [2] Kita masukkan "File Configurasi" untuk otelcol "OpenTelemetry Collector" :

```
[Unit]
Description=OpenTelemetry Collector
After=network.target

[Service]
Type=simple
ExecStart=/usr/local/bin/otelcol --config=/etc/otelcol-config.yaml
Restart=always
RestartSec=10
User=otel
Group=otel

[Install]
WantedBy=multi-user.target

```

#### [3] Untuk melihat Log, kita jalankan Command berikut ini :
```
journalctl -u otelcol -f
```

#### [4] Sambungkan Server kita dengan Hasura pada Rancher :
(Sambungkan Server yang ada di Powershell dengan Hasura pada Rancher ) :

(1) Buka Hasura pada Rancher  <br/> <br/>

(2) Pilih Setting : <br/>
![image](https://github.com/user-attachments/assets/06b482a8-ae7b-4df4-bce6-eaa36a1250c7)     <br/>
![image](https://github.com/user-attachments/assets/ee113a11-0b68-446c-b231-841b375ada26)

<br/><br/>
(2) Pilih "Open Telemetry Exporter" <br/>
![image](https://github.com/user-attachments/assets/8163f19c-0a65-41f0-8eaf-f1551906986d)    <br/>
![image](https://github.com/user-attachments/assets/3e9f610e-5ef8-4897-a27a-d871026d5798)    <br/><br/>

(3) masukkan Endpoint pada Hasura di Rancher : <br/>
-> disini kita masukkan Endpoint "4318". <br/>
yang mana "4318" merupakan Port http pada Configuration File <br/> <br/>

![image](https://github.com/user-attachments/assets/f0becc6c-669f-46bb-b45a-2cee508e7b13)    <br/>
![image](https://github.com/user-attachments/assets/cd1f9fca-5eec-4ea0-a92c-c5923c8cb870)      <br/>



#### [5] Kemudian lakukan "Hit" dengan menjalankan Query di Hasura

![image](https://github.com/user-attachments/assets/47d8e418-403c-42a8-a1ad-e83a5bef489f)

-> Query yang di-Hit tersebut mempunyai :
- nama Tabel "todo"
- dan salah satu Nama Kolom nya adalah "name" yang mempunyai nilai "ferdy"


### [6] Kemudian kita Filter Log, dengan hanya menampilkan Log yang memiliki keyword tertentu

(1) Kita ingin menampilkan Log yang memiliki Keyword "Nama Tabel", yaitu `todo`
```
journalctl -u otelcol --since "1 hour ago" | grep "todo"
```
![image](https://github.com/user-attachments/assets/1e4e5975-7d0d-4c5a-8c33-b68ff7d5a021)

Pada gambar diatas, dapat kita lihat, saat kita ingin menampilkan Log yang memiliki Keyword "Nama Tabel", 
"Log tersebut ada"

(2)  Kita ingin menampilkan Log yang memiliki Keyword "Nama Kolom", yaitu yang mempunyai nilai "ferdy" (ini value untuk kolom "name" )
```
journalctl -u otelcol --since "1 hour ago" | grep "ferdy"
```

![image](https://github.com/user-attachments/assets/6d07ff7f-0243-4a8c-ac59-308e93deafc5)

Pada gambar diatas, dapat kita lihat, saat kita ingin menampilkan Log yang memiliki Keyword "Nama Kolom", 
"Log tersebut tidak ada"


#### Kesimpulan : 

Pada gambar diatas, dapat kita lihat, saat kita ingin menampilkan Log yang memiliki Keyword "Nama Tabel",  <br/>
"Log tersebut ada".
<br/> <br/>
tetapi Pada gambar diatas, saat kita ingin menampilkan Log yang memiliki Keyword "Nama Kolom",  <br/>
"Log tersebut tidak ada" .
<br/><br/>


Dapat kita buat dugaan, bahwa Log tersebut tidak menampilkan Secara Detail, melainkan hanya menampilkan secara garis besar.
yaitu saat Kita ingin mem-filter Log dengan "Nama Tabel", Log tersebut muncul. <br/>
Tetapi jika ingin meanampilkan Log secara lebih detail lagi, yaitu dengan mem-filter Log dengan "Nama Kolom", Log tersebut tidak muncul. <br/><br/>


-----
# Catatan Kaki: <br/>
<br/>
-> Catatan Kaki ini berisi Catatan mengenai Error yang terjadi selama kita mengerjakkan tugas ini, dan bagaimana Proses kita dalam Solve Error tersebut.
<br/>
Berikut ini penjelasannya : 

##  1) Error Command :
### Solusi : kita perbaiki Path pada Command tersebut
-> Berikut ini adalah Command yang benar setelah diperbaiki :
```
docker run -d -v $(pwd)/otel-collector-config.yaml:/root/OTEL/otel-collector-config.yaml otel/opentelemetry-collector-contrib:0.114.0
```

<br/> <br/>

-> Command tersebut, Original nya sebelum dimodifikasi, kita ambil dari File Dokumentasi,
yaitu pada Link berikut ini : <br/>
https://opentelemetry.io/docs/collector/installation/

```
docker run -v $(pwd)/config.yaml:/etc/otelcol-contrib/config.yaml otel/opentelemetry-collector-contrib:0.114.0
```

<img width="542" alt="image" src="https://github.com/user-attachments/assets/1f70a260-704a-465a-9dde-a200b2a4619d">


Pada original Command tersebut, Path nya berbeda dengan Path milik File Configurasi yaml Open Telemetry kita.
<br/><br/>

Kita menggunakan Command berikut ini untuk menge-cek Lokasi Path milik File Configurasi kita :
```
ls $(pwd)/otel-collector-config.yaml
```
[-] Nama File Konfigurasi kita adalah : `otel-collector-config.yaml`   <br/>
[-] `ls $(pwd)/`  =  merupakan Command untuk menge-cek Path untuk Lokasi File kita   <br/> <br/>
Hasil dari menjalankan Command tersebut adalah `/root/OTEL/otel-collector-config.yaml`


-> Sehingga Command tersebut kita perbaiki menjadi :
```
docker run -d -v $(pwd)/otel-collector-config.yaml:/root/OTEL/otel-collector-config.yaml otel/opentelemetry-collector-contrib:0.114.0
```
Perubahan yang kita buat pada Command tersebut adalah : <br/>
[-] Nama File Konfigurasi : 
- Nama File Konfigurasi yang kita pakai adalah : `otel-collector-config.yaml`
- Sedangkan Nama File Konfigurasi pada Link Dokumentasi adalah : `config.yaml`

[-] Path untuk Lokasi File Konfigurasi :
- Path untuk Lokasi File Konfigurasi yang kita pakai adalah : `/root/OTEL/otel-collector-config.yaml`
- Sedangkan Path untuk Lokasi File Konfigurasi pada Link Dokumentasi adalah : `/etc/otelcol-contrib/config.yaml`

<br/><br/>


## 2) Error "File Configuration Yaml" untuk Open Telemetry :
### Solusi : Kita gunakan "File Configuration Yaml untuk Open Telemetry" yang ada di Server Mas Fahryan

Ada beberapa Fase dalam memperbaiki Error "File Configuration Yaml" untuk Open Telemetry, yaitu :

#### Fase 1) Mengambil File Configuration yaml dari "Link Dokumentasi" dan digabungkan dengan yang dari "PDF"

-> File Configuration yang ada pada Link Dokumentasi adalah :
(Link Dokumentasi : https://opentelemetry.io/docs/collector/configuration/ )
```
receivers:
  otlp:
    protocols:
      grpc:
        endpoint: 0.0.0.0:4317
      http:
        endpoint: 0.0.0.0:4318
processors:
  batch:

exporters:
  otlp:
    endpoint: otelcol:4317

extensions:
  health_check:
  pprof:
  zpages:

service:
  extensions: [health_check, pprof, zpages]
  pipelines:
    traces:
      receivers: [otlp]
      processors: [batch]
      exporters: [otlp]
    metrics:
      receivers: [otlp]
      processors: [batch]
      exporters: [otlp]
    logs:
      receivers: [otlp]
      processors: [batch]
      exporters: [otlp]

```

-> Pada PDF, hanya terdapat File Configuration untuk Service, yaitu :
```
service: 
 pipelines: 
 traces: 
 receivers: [otlp] 
 processors: [batch] 
 exporters: [debug, otlp/elastic] 
 metrics: 
 receivers: [otlp] 
 processors: [batch] 
 exporters: [debug, otlp/elastic] 
 logs: 
 receivers: [otlp] 
 processors: [batch] 
 exporters: [debug, otlp/elastic]
```

-> Kemudian kita gabungkan, File Configuration yaml dari Link Dokumentasi & PDF.  <br/>
yang dari PDF hanya untuk bagian Services, yang lainnya menggunakan File Configuration dari Link Dokumentasi. <br/>
Sehingga File Configuration kita adalah :
```
receivers:
  otlp:
    protocols:
      grpc:
        endpoint: 0.0.0.0:4317
      http:
        endpoint: 0.0.0.0:4318
processors:
  batch:

exporters:
  otlp:
    endpoint: otelcol:4317

extensions:
  health_check:
  pprof:
  zpages:

service:
  pipelines:
    traces:
      receivers: [otlp]
      processors: [batch]
      exporters: [debug, otlp/elastic]
    metrics:
      receivers: [otlp]
      processors: [batch]
      exporters: [debug, otlp/elastic]
    logs:
      receivers: [otlp]
      processors: [batch]
      exporters: [debug, otlp/elastic]
```

tetapi File Configuration tersebut masih error <br/><br/>


#### Fase 2) Mengganti Port 9200 pada Endpoint
#### (9200 merupakan Port Elastic Search )

Berdasarkan Error pada Fase 2, ChatGPT menyarankan menggunakan Port 9200 untuk Endpoint. <br/>
Port 9200 merupakan Port untuk 'Elastic Search' ) <br/><br/>

Sepertinya ChatGPT menyarankan kita untuk memakai Port ElasticSearch karena pada bagian Service di File Configuration PDF terdapat tulisan `otlp/elastic`.
<br/><br/>
Sehingga File Configuration kita menjadi :
```
receivers:
  otlp:
    protocols:
      grpc:
        endpoint: 0.0.0.0:4317
      http:
        endpoint: 0.0.0.0:4318
processors:
  batch:

exporters:
  debug: {}
  otlp:
    endpoint: "http://localhost:9200"

extensions:
  health_check:
  pprof:
  zpages:

service:
  pipelines:
    traces:
      receivers: [otlp]
      processors: [batch]
      exporters: [debug, otlp]
    metrics:
      receivers: [otlp]
      processors: [batch]
      exporters: [debug, otlp]
    logs:
receivers: [otlp]
      processors: [batch]
      exporters: [debug, otlp]
```

#### Fase 3) Port yang ada pada File Configuration, tidak ada yang aktif melakukan "LISTENING" pada Server
#### (Port 4317 , 4318 , 9200 tidak ada yang aktif melakukan "LISTENING" )
```
sudo netstat -tuln
```
kita Check menggunakan Command diatas untuk mengecek Port apa saja yang aktif melakukan "LISTENING" pada Server  <br/>
![image](https://github.com/user-attachments/assets/9f83b6f9-a9a3-4770-84b3-e14a328b313d)
![image](https://github.com/user-attachments/assets/b265819c-fc2c-45d6-b501-3bdaad65b6ee)


tetapi Port yang ada pada File Configuration, tidak ada yang aktif melakukan "LISTENING" pada Server, <br/>
yakni Port 4317 , 4318 , 9200 tidak ada yang aktif melakukan "LISTENING" pada Server, <br/>
yang mana artinya Server tidak melakukan Koneksi dengan Port 4317 , 4318 , 9200 . <br/>


<br/><br/>
Kemudian kita juga melakukan Pengecekkan Telnet, tetapi Connection Refused
![image](https://github.com/user-attachments/assets/4a54f56c-32ca-4e8b-8c0f-00645d6b16ae)


#### Fase 4) Kita menggunakan "File Configuration Open Telemetry" yang ada di Server milik Mas Fahryan

Kita Copy File Configuration yang ada di Server Mas Fahryan, kemudian kita melakukan Adjustment (Penyesuaian) sebelum kita taruh File Configuration tersebut di Server kita.

-> File Configuration milik Mas Fahryan - Versi Original (sebelum dimodifikasi) :
```
extensions:
  health_check:
  pprof:
    endpoint: 0.0.0.0:1777
  zpages:
    endpoint: 0.0.0.0:55679

receivers:
  otlp:
    protocols:
      grpc:
        endpoint: 0.0.0.0:4317
      http:
        endpoint: 0.0.0.0:4318

  opencensus:
    endpoint: 0.0.0.0:55678

  # Collect own metrics
  prometheus:
    config:
      scrape_configs:
      - job_name: 'otel-collector'
        scrape_interval: 10s
        static_configs:
        - targets: ['0.0.0.0:8888']

  jaeger:
    protocols:
      grpc:
        endpoint: 0.0.0.0:14250
      thrift_binary:
        endpoint: 0.0.0.0:6832
      thrift_compact:
        endpoint: 0.0.0.0:6831
      thrift_http:
        endpoint: 0.0.0.0:14268

  zipkin:
    endpoint: 0.0.0.0:9411

processors:
  batch:

exporters:
  debug:
    verbosity: detailed

service:

  pipelines:

    traces:
      receivers: [otlp, opencensus, jaeger, zipkin]
      processors: [batch]
      exporters: [debug]

    metrics:
      receivers: [otlp, opencensus, prometheus]
      processors: [batch]
      exporters: [debug]

    logs:
      receivers: [otlp]
      processors: [batch]
      exporters: [debug]

  extensions: [health_check, pprof, zpages]

```


-> Kemudian kita melakukan Adjustment pada File Configuration Mas Fahryan,
yakni dengan menghilangkan bagian yang tidak perlu, yaitu  opencensus ,  prometheus , jaeger , zipkin.
Berikut ini File Configuration setelah di-adjust :

```
receivers:
  otlp:
    protocols:
      grpc:
        endpoint: 0.0.0.0:4317
      http:
        endpoint: 0.0.0.0:4318
processors:
  batch:

exporters:
  debug: {}
  verbosity: detailed

extensions:
  health_check:
  pprof:
    endpoint: 0.0.0.0:1777
  zpages:
    endpoint: 0.0.0.0:55679

service:
  pipelines:
    traces:
      receivers: [otlp]
      processors: [batch]
      exporters: [debug, otlp]
    metrics:
      receivers: [otlp]
      processors: [batch]
      exporters: [debug, otlp]
 logs:
      receivers: [otlp]
      processors: [batch]
      exporters: [debug, otlp]
```


Setelah menambahkan File Configuration tersebut, kemudian kita jalankan Command Open Telemetry selanjutnya, yaitu :
```
docker run -d -v $(pwd)/otel-collector-config.yaml:/root/OTEL/otel-collector-config.yaml otel/opentelemetry-collector-contrib:0.114.0
```
Dan berhasil menjalankan Command tersebut


## 3) Error OTECOL (OpenTelemetry Collector) belum ter-install
### Solusi : Install OTECOL

(1) Kita ingin Check apakah OTEL (Open Telemetry) sudah ter-install pada Server,
yakni dengan menggunakan Command :
```
sudo systemctl status otelcol

```
tetapi terdapat Error yaitu :
![image](https://github.com/user-attachments/assets/54a4af89-e14e-46db-b00f-e79147b23180)
Error tersebut dikarenakan kita belum meng-install OTECOL pada Sever
<br/><br/>
Sehingga untuk Solve error tersebut, kita perlu Install OTECOL. <br/>
Langkah-langkah untuk meng-install OTECOL sudah dijelaskan pada Penjelasan sebelumnya.  <br/>
