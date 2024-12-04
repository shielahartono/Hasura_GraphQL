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


## (C) Install "Open Telemetry" pada Server

Link Referensi Dokumentasi :  <br/>
https://opentelemetry.io/docs/collector/installation/          <br/>
https://opentelemetry.io/docs/collector/configuration/          <br/>

### 1. Jalankan Command berikut ini :
```
docker pull otel/opentelemetry-collector-contrib:0.114.0
```

```
docker run otel/opentelemetry-collector-contrib:0.114.0
```

### 2. Masukkan "File Configuration YAML" untuk "Open Telemetry"


