# Dokumentasi Tugas Open Telemetry


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
docker run -v $(pwd)/otel-collector-config.yaml:/root/OTEL/otel-collector-config.yaml otel/opentelemetry-collector-contrib:0.114.0
```

<br/> <br/>

-> Command tersebut, Original nya sebelum dimodifikasi, kita ambil dari File Dokumentasi,
yaitu pada Link berikut ini : <br/>
https://opentelemetry.io/docs/collector/installation/

```
docker run -v $(pwd)/config.yaml:/etc/otelcol-contrib/config.yaml otel/opentelemetry-collector-contrib:0.114.0
```

<img width="542" alt="image" src="https://github.com/user-attachments/assets/1f70a260-704a-465a-9dde-a200b2a4619d">




