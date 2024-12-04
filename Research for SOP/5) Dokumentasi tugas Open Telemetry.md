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
maka kita jalankan Command berikut : <br/>
