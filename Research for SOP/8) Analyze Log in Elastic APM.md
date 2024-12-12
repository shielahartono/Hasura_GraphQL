# Analyze Log in Elastic APM 

---
---
# A) Buka Hasura Console di Rancher, dan Ubah Endpoint pada "Open Telemetry Exporter"

1. Buka Rancher
   ![WhatsApp Image 2024-12-10 at 23 23 13_37f50fea](https://github.com/user-attachments/assets/f93ccf71-af46-4872-a369-2246feb0bea3)

2. Pilih Namespace "sheila"  <br/>
   (Namespace milik kita) <br/>
![WhatsApp Image 2024-12-10 at 23 23 35_118e6581](https://github.com/user-attachments/assets/96e81bb5-37a8-4139-a980-911cd792fdcf)


3. Pilih "Service Discovery"  <br/>
![WhatsApp Image 2024-12-10 at 23 27 38_0b472612](https://github.com/user-attachments/assets/62ff10ce-31b4-45da-9733-9f955883435b)


4. Pilih "Services" <br/>
![WhatsApp Image 2024-12-10 at 23 28 01_8e7a56d5](https://github.com/user-attachments/assets/71c79d6c-a465-4be6-8996-ac0337deaeff)


5. Click Value pada bagian "Target" . <br/>
   
kemudian ini akan mengarahkan kita ke "Hasura Console" <br/>
![WhatsApp Image 2024-12-10 at 23 33 17_8042e43d](https://github.com/user-attachments/assets/86daab14-2d70-416f-b8bb-205227eb188e)
<br/>
![WhatsApp Image 2024-12-10 at 23 28 34_8f9fbd87](https://github.com/user-attachments/assets/5e7910fe-d915-493b-9a23-e36e4eebf478)


6. Berikut ini Tampilan "Hasura Console"  <br/>
![WhatsApp Image 2024-12-10 at 23 34 03_63277967](https://github.com/user-attachments/assets/f5aeeb9c-f9bb-4312-a96d-1846d062facf)

7. Pilih "Settings" pada bagian kanan atas <br/>
![WhatsApp Image 2024-12-10 at 23 35 50_ae0acf18](https://github.com/user-attachments/assets/59e45dc8-af47-47ec-8fe1-b12387b57890)


8. Pilih "Open Telemetry Exporter" <br/>
![WhatsApp Image 2024-12-10 at 23 37 30_2f3ee44a](https://github.com/user-attachments/assets/1702537f-7dac-41b5-a886-b851fe8b5917)

![WhatsApp Image 2024-12-10 at 23 36 29_8328416b](https://github.com/user-attachments/assets/bbf0d142-36f4-4218-a319-cc07a4d45c96)


9. kita ganti dengan Endpoint 10.100.13.24  
<br/>
yakni menjadi seperti ini :  <br/>

- Traces Endpoint : 
http://10.100.13.24:4318/v1/traces

- Metrics Endpoint :
http://10.100.13.24:4318/v1/metrics

- Logs Endpoint :
http://10.100.13.24:4318/v1/logs

![WhatsApp Image 2024-12-10 at 23 46 15_82d7c292](https://github.com/user-attachments/assets/18f1ea74-0f0c-4ceb-8619-f53c4af9c766)


10. Pilih "Update"  <br/>
![WhatsApp Image 2024-12-10 at 23 47 19_2be3c0d5](https://github.com/user-attachments/assets/a9a7f72d-c602-4c8e-b1d1-818c9aa51244)
![WhatsApp Image 2024-12-10 at 23 47 19_e70fd47e](https://github.com/user-attachments/assets/56e767c2-f79b-46b2-94a7-2b4cd4c09791)


-----
-----
# B) Tutorial Setting di Hasura Rancher & Hit di Postman 500 kali


1. Buka Postman <br/>
![WhatsApp Image 2024-12-10 at 22 14 59_83468103](https://github.com/user-attachments/assets/666f343b-8ca3-438d-bb5b-15941c63d6f2)

2. Pilih Post <br/>
![WhatsApp Image 2024-12-10 at 22 29 35_95579548](https://github.com/user-attachments/assets/d58540b5-72b8-4bd4-8acd-e1ed735ebde7)
![WhatsApp Image 2024-12-10 at 22 27 45_db879c99](https://github.com/user-attachments/assets/60be369e-ebe9-4a06-8498-79a573e171e3)


3. bagian Endpoint pada Postman, kita copy dari Endpoint paling atas pada Hasura Console (Hasura yang ada di Rancher)  <br/>
![WhatsApp Image 2024-12-10 at 22 33 14_f921d3b7](https://github.com/user-attachments/assets/40d0cebf-7af6-4901-82e7-ab876463a9ab)


4. pada bagian "Headers" di Postman, kita tambahkan Password Hasura  <br/>
![WhatsApp Image 2024-12-10 at 22 36 09_fc635dd9](https://github.com/user-attachments/assets/3d6f2122-7227-4095-a9a1-17bd958c4d81)

dengan menambahkan 
- pada "Key" : x-hasura-admin-secret
- pada "Value" : rahasia123

(rahasia123 merupakan Password untuk masuk ke Hasura)  <br/>

![WhatsApp Image 2024-12-10 at 22 38 05_2c4c99a3](https://github.com/user-attachments/assets/4ae242ba-afa8-4497-98aa-86b74b48ac83)


5. Kemudian pada bagian "Body" di Postman, kita masukkan Query darI Hasura Console  <br/>
(masukkan Query nya dengan cara Copy & Paste)  <br/>
(Hasura Console = Hasura yang ada di Rancher)  <br/>

![WhatsApp Image 2024-12-10 at 22 42 46_8f372fc7](https://github.com/user-attachments/assets/c373b703-c999-4e89-b4f2-130920e8541a)

- Berikut ini adalah tampilan  "Body" pada Postman yang sudah diberikan Query :
![WhatsApp Image 2024-12-10 at 22 45 03_7e936b17](https://github.com/user-attachments/assets/5fd8ac46-9c1f-43cf-ab70-e761ebc33504)

- sebelummya, kita perlu Copy Query ini dari Hasura Console, kemudian Paste ke Postman pada bagian "Body"
![WhatsApp Image 2024-12-10 at 22 52 08_491a7221](https://github.com/user-attachments/assets/a928a113-5f39-4016-929d-30d6569e0b61)
![WhatsApp Image 2024-12-10 at 22 52 08_01ded351](https://github.com/user-attachments/assets/2aef9a55-33dc-4cfc-89b3-789d9e2ef06f)


6. Pada Postman, kita Pilih Send untuk Hit 1 kali <br/>
![WhatsApp Image 2024-12-10 at 22 52 37_3530732e](https://github.com/user-attachments/assets/b1fe9cf9-f99f-47c6-9fd8-4a8b3fbf35c5)


7. Pada Postman, kita Pilih "Save" pada bagian atas  <br/>
![WhatsApp Image 2024-12-10 at 22 53 57_9e395c6f](https://github.com/user-attachments/assets/db9b2e8e-d591-4fec-9d16-705111477c59)

![WhatsApp Image 2024-12-10 at 22 53 58_36e9fb16](https://github.com/user-attachments/assets/d3e4bc80-6c79-456f-a582-403b968e9b4f)


8. Pada Postman, Pilih "titik tiga " (pada sebelah kiri)   <br/>
![WhatsApp Image 2024-12-10 at 22 56 31_3afe6f3d](https://github.com/user-attachments/assets/7c2bc229-dda0-4d5b-97f3-5ab8003667ab)

![WhatsApp Image 2024-12-10 at 22 56 31_46d3f346](https://github.com/user-attachments/assets/69eb4ece-eacb-4eaf-ac7b-c449b9280946)


9. Pilih "Run Collection"  <br/>
![WhatsApp Image 2024-12-10 at 23 01 33_dd628278](https://github.com/user-attachments/assets/2c1a6fde-474e-4c4c-9876-85c6520777b5)

![WhatsApp Image 2024-12-10 at 22 58 56_856874c6](https://github.com/user-attachments/assets/15a9c368-4906-4ac5-a46d-7ddc10c0a0b0)


10. Pada bagian "Iteration" masukkan angka sesuai jumlah berapa banyak kita ingin lakukan "Hit". <br/>
Misalnya: <br/>
kita masukkan 500 untuk Hit sebanyak 500 kali  <br/>
![WhatsApp Image 2024-12-10 at 23 03 42_7262a10d](https://github.com/user-attachments/assets/2b3115da-49cd-4856-abc8-415faf681ea0)

![WhatsApp Image 2024-12-10 at 23 02 01_54bf8cae](https://github.com/user-attachments/assets/eb765daf-fbec-4f91-beb8-ff9291b0df96)

![WhatsApp Image 2024-12-10 at 23 04 02_adddecf3](https://github.com/user-attachments/assets/113c5017-52a2-4284-8d5b-c16d62b1c2a0)


11. kemudian Pilih "Tombol Orange" untuk menjalankan Hit    <br/>
(ada di Pojok kanan bagian bawah)


12. Kemudian akan muncul Tampilan seperti ini  <br/>
![WhatsApp Image 2024-12-10 at 23 06 14_5d77c8c8](https://github.com/user-attachments/assets/e1786756-61e6-42dd-bf78-efbbcc1ab76c)

Berikut ini Tampilan jika kita sudah berhasil Hit di Postman :  <br/>
![WhatsApp Image 2024-12-10 at 23 08 23_aedf43eb](https://github.com/user-attachments/assets/b875bfa8-75f3-47df-9bec-f901bc28035e)

dapat kita lihat pada bagian kanan, status nya "200 OK" yang berarti semuanya berjalan dengan baik :  <br/>
![WhatsApp Image 2024-12-10 at 23 09 23_d252f919](https://github.com/user-attachments/assets/7e6a75b3-8866-4f82-be01-2b4eac562342)


12. kemudian kita Connect ke VPN, dan kita buka URL Elastic APM pada Browser.
Berikut ini URL nya :
http://10.100.13.25:5601/app/apm/services

untuk masuk halaman Elastic APM, kita  masukkan Username & Password untuk Elastic APM

![WhatsApp Image 2024-12-10 at 23 17 21_87ecf99a](https://github.com/user-attachments/assets/388f64f7-c091-4f63-a06e-8f35a49ba063)

-------
-------

# C) Analisa Log pada Web "Elastic APM"
(APM = Application Performance Monitoring) <br/>

1. Tampilan APM saat kita membuka menggunakan URL Berikut ini :  <br/>
http://10.100.13.25:5601/app/apm/services

![WhatsApp Image 2024-12-10 at 20 56 00_ebd32a27](https://github.com/user-attachments/assets/44dc24ea-ea9a-4738-8445-992fb88529ea)

2. Kemudian pilih ini : <br/>
![WhatsApp Image 2024-12-10 at 20 56 57_6ede799d](https://github.com/user-attachments/assets/a11cc6f1-4e4d-4751-b617-b8b5c330d721)

![WhatsApp Image 2024-12-10 at 20 56 58_23b7375f](https://github.com/user-attachments/assets/95af26a3-043b-4901-8528-17162ada58de)

3. Kemudian Berikut ini tampilannya : <br/>
![WhatsApp Image 2024-12-10 at 20 58 43_472b7157](https://github.com/user-attachments/assets/355ccec1-9ef2-496f-9a6f-89d7971622d8)


kemudian kita scroll kebawah

4. Latency & Throughput <br/>
![WhatsApp Image 2024-12-10 at 21 00 52_bdadfef9](https://github.com/user-attachments/assets/e15c1dce-153c-4f20-b5ac-5d270a3460af)



## (1) Chart "Throughput" pada Elastic APM (App):
![image](https://github.com/user-attachments/assets/9663f807-6896-487a-a962-0e863e640746)

Throughput mengukur jumlah transaksi atau Request yang diproses oleh aplikasi dalam jangka waktu tertentu (Pada case ini adalah menit).  <br/>
satuan untuk Throughput adalah "tpm", yaitu transaksi per menit. <br/>
<br/>
Grafik membantu memahami intensitas Request yang diterima. <br/>



### **Cara Membaca Grafik**
1. **Sumbu X (Horizontal):**  
   Menunjukkan waktu (jam dan menit). Dalam grafik ini, datanya mencakup rentang waktu singkat sekitar pukul **20:40 hingga 20:50**.

2. **Sumbu Y (Vertikal):**  
   Menunjukkan jumlah transaksi per menit (**tpm**). Nilainya berkisar dari **0 hingga 400 tpm**.

3. **Garis Hijau Tua (Throughput):**  
   Mewakili jumlah transaksi per menit yang diproses pada waktu tertentu.  
   - Grafik ini menunjukkan adanya puncak throughput sekitar pukul **20:50**, yang berarti aplikasi memproses **hampir 400 transaksi per menit** pada waktu itu.

4. **Garis Hijau Muda (Day Before):**  
   Mewakili throughput pada waktu yang sama **hari sebelumnya** (jika ada data pembanding untuk hari sebelumnya).  <br/>
Pada grafik ini, garis tersebut tidak terlihat jelas, kemungkinan karena throughput hari sebelumnya sangat kecil atau tidak ada data pembanding.



### **Pola yang Ditunjukkan**
- Ada lonjakan tajam throughput di sekitar pukul **20:50**, yang kemudian cepat turun kembali mendekati **0 tpm**.
- Hal ini menunjukkan bahwa aplikasi memproses transaksi dalam jumlah besar pada satu waktu tertentu, kemudian aktivitas menurun drastis.



### Grafik ini digunakan untuk:

   
1. **Menganalisis Pola Penggunaan:**  
   Memahami kapan lonjakan aktivitas terjadi (misalnya, pada waktu tertentu atau selama event khusus).

2. **Mengidentifikasi Anomali:**  
   Jika throughput tiba-tiba melonjak tinggi atau terlalu rendah dibandingkan biasanya, bisa jadi tanda adanya masalah atau perubahan pola penggunaan.


- **Jika terjadi Lonjakan Tidak Normal:**  
  - Cek apakah ada kejadian yang menyebabkan Load (beban) tidak terduga 
  - Optimalkan aplikasi untuk menangani lonjakan throughput.


## (2) Chart "Latency" pada Elastic APM (App):
![image](https://github.com/user-attachments/assets/d930bbbc-f408-4542-bc90-1c18c630e693)



### **Apa itu Latency?**
Latency adalah waktu rata-rata yang diperlukan untuk menyelesaikan satu transaksi atau permintaan, biasanya diukur dalam **milidetik (ms)**. Latensi rendah menunjukkan bahwa aplikasi memproses permintaan dengan cepat, sedangkan latensi tinggi bisa menjadi tanda adanya bottleneck atau masalah performa. <br/>
(semakin kecil Latency, maka semakin baik) <br/>



### **Cara Membaca Grafik**
1. **Sumbu X (Horizontal):**
   Menunjukkan waktu, yaitu dari pukul **20:45 hingga 20:55**.

2. **Sumbu Y (Vertikal):**
   Menunjukkan latensi rata-rata dalam milidetik (**ms**) pada waktu tertentu, dengan skala dari **0 ms hingga 1.0 ms**.

3. **Garis Biru Tua**
nilai Latency pada gambar di atas ditunjukkan oleh garis biru tua. Garis tersebut merepresentasikan latensi rata-rata (Average Latency) pada waktu tertentu dalam rentang yang ditampilkan di sumbu X (horizontal).

Garis biru tua ini menunjukkan bahwa latensi rata-rata aplikasi berada di sekitar 1.0 ms selama rentang waktu yang diukur (sekitar pukul 20:50). Karena garisnya datar dan stabil, ini mengindikasikan bahwa latensi rata-rata tidak mengalami fluktuasi signifikan selama periode tersebut. <br/>
![image](https://github.com/user-attachments/assets/08b66afe-8d8e-494b-b5de-de481b066b9f)

4. **Warna Abu-abu**
- Rentang Waktu dengan Data Belum Final (Partial Data): <br/>
Area abu-abu sering menunjukkan bahwa data untuk waktu tersebut belum sepenuhnya terkumpul atau diproses, sehingga belum tersedia metrik final untuk latensi. Ini terjadi jika data dikumpulkan dalam interval tertentu dan waktu akhir grafik mencakup periode yang sedang berlangsung. <br/>
![image](https://github.com/user-attachments/assets/d43490e5-e3c8-4029-8a24-dd311ec95cfc)


### **Pola yang Ditunjukkan**
- **Latensi Stabil:** Grafik menunjukkan bahwa rata-rata latensi tetap stabil di sekitar **1.0 ms** selama waktu yang ditampilkan.
- **Data Terbatas:** Grafik hanya mencakup beberapa titik waktu (mungkin karena pengambilan data diatur per interval tertentu atau aktivitas rendah).



### Grafik latensi digunakan untuk:
1. **Monitoring Kinerja Aplikasi:**  
   Memastikan aplikasi memproses permintaan dengan cepat.
   
2. **Identifikasi Masalah:**  
   Jika latensi tiba-tiba meningkat, itu bisa menunjukkan adanya bottleneck, overload, atau kegagalan sistem tertentu.

3. **Analisis Tren:**  
   Membandingkan performa hari ini dengan hari sebelumnya untuk mendeteksi degradasi atau peningkatan kinerja.



### **Apa yang Bisa Dilakukan?**
- **Jika Latensi Stabil:**  
  Artinya aplikasi bekerja dengan baik. Pastikan untuk terus memantau agar tidak ada perubahan signifikan.

- **Jika Latensi Naik:**  
  - Lakukan analisis mendalam untuk mencari tahu penyebab lonjakan, seperti query lambat, beban tinggi, atau masalah infrastruktur.
  - Optimalkan database, aplikasi, atau layanan terkait.



5. Failed Transaction Rate  <br/>
![WhatsApp Image 2024-12-10 at 21 01 41_6e22c6c9](https://github.com/user-attachments/assets/74e3ab39-aa09-40cd-aac9-0e80cf2415eb)


Chart **Failed Transaction Rate** digunakan untuk memonitor persentase transaksi yang gagal dalam sistem kita.

### Penjelasan Elemen Chart:
1. **Failed Transaction Rate (Avg.)**: 
   - Garis (atau bar) berwarna **oranye** mewakili rata-rata persentase transaksi yang gagal pada waktu tertentu.

2. **Day Before**:
   - Garis tambahan (jika ada) menunjukkan data pembanding, yaitu persentase transaksi gagal **pada hari sebelumnya**.

3. **Sumbu Vertikal (0% - 100%)**:
   - Menunjukkan tingkat kegagalan transaksi dalam persentase. 
   - 0% berarti tidak ada transaksi yang gagal, sedangkan 100% berarti semua transaksi dalam periode tersebut gagal.

4. **Sumbu Horizontal (Waktu)**:
   - Menampilkan waktu dalam interval menit, memperlihatkan kapan transaksi gagal terjadi.

5. **Garis Orange** :
Garis Orange merupakan Representasi persentase transaksi gagal dalam waktu yang ditampilkan. <br/>
Berdasarkan grafik di atas, Failed Transaction Rate terlihat sangat kecil, mendekati 0%.   <br/> <br/>

Hal ini terlihat dari garis oranye yang hampir tidak naik dari sumbu 0% pada skala vertikal. Karena tidak ada angka spesifik yang tertulis pada grafik, kita hanya bisa mengasumsikan bahwa tingkat kegagalan ini sangat rendah, mungkin di bawah 1%.  <br/> <br/>

Pada grafik, garis oranye muncul diantara waktu 20:50:00 dan 20:51:00, artinya kegagalan transaksi hanya terjadi pada waktu tersebut.  <br/>
Tidak ada garis oranye di waktu lain, yang menunjukkan tidak ada transaksi gagal di luar waktu tersebut.  <br/> <br/>

6. Area Abu-abu**:
 **Area Abu-abu** artinya Data untuk waktu tersebut belum tersedia atau sedang menunggu pembaruan.

 **Area abu-abu di bagian kanan grafik** menunjukkan:
   - Data pada waktu tersebut (setelah 20:56:00) **tidak tersedia** atau **belum terkumpul**.
   - Ini mungkin disebabkan karena:
     - Grafik diambil sebelum data terbaru diproses.
     - Waktu akhir grafik belum sampai pada waktu tersebut.


### Cara Membaca Chart:
1. **Lihat Waktu Terjadinya Kegagalan**:
   - Dari chart ini, kegagalan hanya tercatat pada **20:50:00**.
   - Setelah itu, tidak ada laporan kegagalan hingga 20:56:00 (area kosong).

2. **Evaluasi Skala Kegagalan**:
   - Persentase kegagalan (Failed Transaction Rate) pada 20:50:00 terlihat sangat rendah, mendekati **0%** (hampir tidak signifikan).
   - Tidak ada kegagalan besar atau lonjakan berarti pada periode lainnya.

3. **Bandingkan dengan Hari Sebelumnya**:
   - Karena tidak terlihat garis pembanding untuk **Day Before**, artinya data ini hanya berlaku untuk hari ini.



### Interpretasi Data:
- **Sistem Anda Stabil**:
   - Hampir seluruh transaksi berjalan dengan lancar. Hanya ada kegagalan kecil pada 20:50:00.
- **Tidak Ada Masalah Besar**:
   - Grafik ini menunjukkan performa sistem cukup baik, dengan tingkat kegagalan mendekati nol sepanjang waktu yang ditampilkan.




6. Latency Distribution :   <br/>
![WhatsApp Image 2024-12-10 at 21 03 39_69c45b17](https://github.com/user-attachments/assets/8c4afa1d-8a36-44e2-8283-e3ec414a6fa4)

Versi Zooom :   <br/>
![WhatsApp Image 2024-12-10 at 21 03 39_e1903e11](https://github.com/user-attachments/assets/18aaa347-650b-4c26-a5ef-3cb240a499e9)

## (1) Chart untuk "Latency Distribution"
Chart tersebut menampilkan **Latency Distribution** dari 500 transaksi dalam sistem. Berikut penjelasannya: <br/> <br/>

Latency adalah waktu rata-rata yang diperlukan untuk menyelesaikan satu transaksi atau Request. <br/><br/>

1. **Latency Distribution**:
   - Grafik ini menunjukkan distribusi latensi atau waktu yang diperlukan untuk menyelesaikan transaksi.
   - **Sumbu X (Latency)**:
     - Menampilkan latensi dalam mikrodetik (µs) hingga milidetik (ms), dari nilai terkecil hingga terbesar.
   - **Sumbu Y (Transactions)**:
     - Menunjukkan jumlah transaksi pada setiap rentang latensi.
   - **Titik Puncak Histogram**:
     - Menunjukkan nilai latensi yang paling sering terjadi .
   - **Garis Abu-abu "95p"**:
     - Ini adalah persentil ke-95, yang berarti 95% transaksi memiliki latensi **lebih rendah** dari nilai ini. 
     - Dengan kata lain, hanya 5% transaksi yang memiliki latensi **lebih tinggi** dari nilai ini.

2. **Trace Sample**:
   - Informasi tambahan mengenai salah satu transaksi dari total 500 transaksi:
     - **8 minutes ago**: Waktu transaksi terakhir yang diproses (8 menit yang lalu).
     - **1.2 ms**: Durasi atau latensi transaksi yang sedang ditampilkan.
     - **100% of trace**: Persentase cakupan trace yang telah tercatat untuk transaksi tersebut.


### Cara Membaca Chart:
1. **Identifikasi Distribusi Latensi**:
   Pada Grafik diatas, dapat kita ketahui, bahwa :
   - Sebagian besar transaksi berada di bagian awal grafik, di sekitar **1 ms hingga 2 ms**, yang mana ini menunjukkan sistem memproses transaksi dengan cepat.
   - Hanya sedikit transaksi yang memiliki latensi tinggi (di atas 6 ms), seperti terlihat pada histogram yang menurun tajam di sisi kanan.

3. **Perhatikan Garis "95p" (Garis warna abu-abu)**:
   - Garis abu-abu menunjukkan batas **95%** transaksi, yang berarti hanya 5% transaksi yang lebih lambat dari latensi ini.
   - Anda dapat menggunakan nilai ini untuk menetapkan ambang batas performa sistem.


### Kesimpulan:
- Grafik ini menunjukkan bahwa mayoritas transaksi memiliki latensi rendah dan performa sistem umumnya baik.
- Transaksi dengan latensi tinggi (lebih dari 6 ms) sangat jarang.
- Untuk memastikan kinerja optimal, Anda dapat fokus pada analisis transaksi dengan latensi di atas garis **95p**.
  (Maksudnya kita perlu fokus pada transaksi dengan latensi yang lebih tinggi dari garis 95p (persentil ke-95).)
<br/><br/><br/>

7. Pilih Tab yang ada di Sebelahnya, yaitu Tab Metadata  <br/>
![WhatsApp Image 2024-12-10 at 21 09 01_f3607140](https://github.com/user-attachments/assets/edb494bb-aac0-4dbf-8a6a-b33c02e050b8)
![WhatsApp Image 2024-12-10 at 21 09 01_ccb440f4](https://github.com/user-attachments/assets/7ea0d156-e37f-43ff-8647-0394e88a73d5)

![WhatsApp Image 2024-12-10 at 21 09 02_498631da](https://github.com/user-attachments/assets/fdf066db-eb5e-4a23-804d-f7d8a2b9b6b4)

![WhatsApp Image 2024-12-10 at 21 09 03_f942f897](https://github.com/user-attachments/assets/420f3845-4447-4161-8af9-1af6b898920a)
![WhatsApp Image 2024-12-10 at 21 09 03_3dc195b4](https://github.com/user-attachments/assets/0d151c32-89f3-4977-8ab1-1406bc2df5a1)




8. Pilih Investigate  <br/>

![WhatsApp Image 2024-12-10 at 21 16 58_b723d7a5](https://github.com/user-attachments/assets/88df7da3-10f4-485f-a2a7-0be876bff305)
![WhatsApp Image 2024-12-10 at 21 16 58_c69d3ea1](https://github.com/user-attachments/assets/738219b2-8241-4b75-9774-1e341f3b96a3)


9. kemudian Pilih "View Transactions in Discover"   <br/>
![image](https://github.com/user-attachments/assets/46a99b63-1991-4449-b668-70eb0a936e7b)

Setelah itu, tampilannya seperti berikut ini : <br/>
![WhatsApp Image 2024-12-10 at 21 48 53_a2c5711a](https://github.com/user-attachments/assets/d27faf1c-8b03-490b-984f-9cc258c1d017)

10. Kemudian Perbesar bagian ini :  <br/>
![WhatsApp Image 2024-12-10 at 21 50 44_3b6dffcf](https://github.com/user-attachments/assets/667ef829-5884-47d9-9175-231874e11afa)
![WhatsApp Image 2024-12-10 at 21 50 44_b7bdb8a2](https://github.com/user-attachments/assets/368170aa-7f07-4295-b1ce-d432c3b56164)

11. Kemudian akan muncul Log seperti ini, <br/>
Lalu kita click "Copy Value"  <br/>
![WhatsApp Image 2024-12-10 at 21 52 13_9392190f](https://github.com/user-attachments/assets/8d6c7eca-8395-4cc8-8100-aaaf8c030f51)


12. Kemudian kita analisa Log yang sudah kita lakukan "Copy Value" tadi. <br/>
ini merupakan Log dari "Elastic APM" :

```
{
  "@timestamp": [
    "2024-12-10T14:27:41.541Z"
  ],
  "agent.name": [
    "otlp"
  ],
  "agent.version": [
    "unknown"
  ],
  "ecs.version": [
    "1.12.0"
  ],
  "event.ingested": [
    "2024-12-10T14:32:36.808Z"
  ],
  "event.outcome": [
    "success"
  ],
  "labels.enduser_role": [
    "admin"
  ],
  "labels.graphql_operation_name": [
    "MyQuery"
  ],
  "labels.http_response_content_length": [
    "24"
  ],
  "labels.request_id": [
    "d0eab577-5388-4436-9edb-8695ebb2c970"
  ],
  "labels.session_variables": [
    "{\"x-hasura-role\":\"admin\"}"
  ],
  "observer.ephemeral_id": [
    "f1168f81-ff63-485a-a3de-7bad197ee4f4"
  ],
  "observer.hostname": [
    "worker1.k8s.alldataint.com"
  ],
  "observer.id": [
    "4fa9447e-2492-4e9b-af43-0977fa67cb28"
  ],
  "observer.type": [
    "apm-server"
  ],
  "observer.version": [
    "7.17.18"
  ],
  "observer.version_major": [
    7
  ],
  "processor.event": [
    "transaction"
  ],
  "processor.name": [
    "transaction"
  ],
  "service.framework.name": [
    "hasura"
  ],
  "service.framework.version": [
    "v2.42.0"
  ],
  "service.language.name": [
    "unknown"
  ],
  "service.name": [
    "hasura"
  ],
  "timestamp.us": [
    1733840861541105
  ],
  "trace.id": [
    "27148b955db232089406bbf2a8ce0196"
  ],
  "transaction.duration.us": [
    1073
  ],
  "transaction.id": [
    "d38652ae50be0b52"
  ],
  "transaction.name": [
    "/v1/graphql"
  ],
  "transaction.name.text": [
    "/v1/graphql"
  ],
  "transaction.result": [
    "Success"
  ],
  "transaction.sampled": [
    true
  ],
  "transaction.type": [
    "custom"
  ],
  "_id": "d3L8sJMB2LTZdF1KegbI",
  "_index": "apm-7.17.18-transaction-000001",
  "_score": null
}
```

Data diatas adalah log transaksi dari **Elastic APM** yang berisi berbagai informasi mengenai transaksi yang terjadi dalam sistem.  <br/>
Berikut penjelasan detail dari setiap elemen yang ada dalam data tersebut:   <br/>  <br/>




### 1. **@timestamp**  
   - **"2024-12-10T14:27:41.541Z"**  
     **Penjelasan**: Ini adalah waktu **UTC** saat transaksi ini terjadi. Waktu ini merekam kapan transaksi berlangsung dalam sistem. Dalam hal ini, transaksi terjadi pada tanggal **10 Desember 2024**, pukul **14:27:41 dan 541 milidetik**.

### 2. **agent.name** & **agent.version**  
   - **"otlp"**:  
     **Penjelasan**: Agen yang digunakan untuk mengirim data ke Elastic APM adalah **OTLP** (OpenTelemetry Protocol). OTLP adalah protokol standar yang digunakan untuk mengirimkan data observasi (seperti transaksi dan metrik) dari aplikasi ke sistem monitoring.
   - **"unknown"**:  
     **Penjelasan**: Versi agen ini tidak dapat diketahui atau tidak ditentukan.

### 3. **ecs.version**  
   - **"1.12.0"**:  
     **Penjelasan**: Ini adalah versi dari **Elastic Common Schema (ECS)** yang digunakan. ECS adalah format standar yang dipakai oleh Elastic untuk menyimpan dan mengatur data log, sehingga data dapat lebih mudah dianalisis.

### 4. **event.ingested**  
   - **"2024-12-10T14:32:36.808Z"**:  
     **Penjelasan**:waktu event.ingested menunjukkan kapan data tersebut diterima dan diproses oleh server APM. Waktu ini sedikit berbeda dengan **@timestamp**, karena mencatat waktu data diproses di server APM.

     Waktu event.ingested yang tercatat dalam log, seperti "2024-12-10T14:32:36.808Z", adalah waktu ketika data transaksi diproses atau dimasukkan ke dalam server APM (Application Performance Monitoring) oleh sistem Elastic APM.

Pencatatan waktu ini dilakukan oleh APM Server, yang merupakan komponen yang mengumpulkan, memproses, dan menyimpan data dari aplikasi yang dipantau. APM Server berfungsi untuk menerima data dari agen yang terpasang pada aplikasi (seperti agen OTLP yang disebutkan dalam log ), memproses data tersebut, dan mengirimkannya ke penyimpanan backend (seperti ElasticSearch).

Jadi, APM Server yang bertanggung jawab untuk mencatat waktu saat data transaksi dimasukkan ke dalam sistem Elastic APM, tepatnya pada elemen event.ingested.

### 5. **event.outcome**  
   - **"success"**:  
     **Penjelasan**: Ini menunjukkan bahwa transaksi ini berhasil diselesaikan tanpa error. Hasil dari transaksi tersebut adalah **sukses**.

### 6. **labels.enduser_role**  
   - **"admin"**:  
     **Penjelasan**: Pengguna yang melakukan transaksi ini memiliki peran **admin** dalam sistem. Artinya, pengguna ini memiliki hak akses penuh untuk melakukan berbagai tindakan dalam aplikasi.

### 7. **labels.graphql_operation_name**  
   - **"MyQuery"**:  
     **Penjelasan**: Nama dari operasi **GraphQL** yang dijalankan dalam transaksi ini. **GraphQL** adalah query language untuk API, dan **MyQuery** adalah nama operasi yang dijalankan di backend.

### 8. **labels.http_response_content_length**  
   - **"24"**:  
     **Penjelasan**: Ini adalah ukuran **konten respons HTTP** yang dikembalikan setelah transaksi selesai. Dalam hal ini, respons yang dikembalikan berukuran **24 byte**.

### 9. **labels.request_id**  
   - **"d0eab577-5388-4436-9edb-8695ebb2c970"**:  
     **Penjelasan**: Ini adalah ID unik yang digunakan untuk melacak permintaan (request) ini di seluruh sistem. Setiap request yang dikirim akan memiliki ID unik untuk memudahkan pencarian atau pemantauan.

### 10. **labels.session_variables**  
   - **"{\"x-hasura-role\":\"admin\"}"**:  
     **Penjelasan**: Ini adalah variabel sesi yang berisi informasi tambahan tentang transaksi. Dalam hal ini, variabel **x-hasura-role** menunjukkan bahwa peran pengguna di sistem adalah **admin**.

### 11. **observer.ephemeral_id**  
   - **"f1168f81-ff63-485a-a3de-7bad197ee4f4"**:  
     **Penjelasan**: Ini adalah ID sementara yang digunakan untuk mengidentifikasi **observer** yang mencatat transaksi ini. Observer ini mengawasi dan mencatat data transaksi.

### 12. **observer.hostname**  
   - **"worker1.k8s.alldataint.com"**:  
     **Penjelasan**: Nama host dari **worker** (server) yang menjalankan aplikasi ini dalam lingkungan **Kubernetes**. Host ini bertanggung jawab atas pemrosesan transaksi.

### 13. **observer.id**  
   - **"4fa9447e-2492-4e9b-af43-0977fa67cb28"**:  
     **Penjelasan**: ID unik yang digunakan untuk mengidentifikasi observer ini dalam sistem.

### 14. **observer.type** & **observer.version**  
   - **"apm-server"** & **"7.17.18"**:  
     **Penjelasan**: Jenis observer ini adalah **APM Server** yang memproses data transaksi aplikasi. Versi APM Server yang digunakan adalah **7.17.18**.

### 15. **processor.event** & **processor.name**  
   - **"transaction"**:  
     **Penjelasan**: Ini menandakan bahwa data yang tercatat adalah tentang **transaksi** (bukan error atau jenis event lain).
  
### 16. **service.framework.name** & **service.framework.version**  
   - **"hasura"** & **"v2.42.0"**:  
     **Penjelasan**: Framework yang digunakan oleh aplikasi ini adalah **Hasura** (platform untuk membangun aplikasi GraphQL secara real-time), dengan versi **v2.42.0**.

### 17. **service.language.name**  
   - **"unknown"**:  
     **Penjelasan**: Bahasa pemrograman yang digunakan dalam aplikasi ini tidak diketahui atau tidak teridentifikasi dalam log ini.

### 18. **service.name**  
   - **"hasura"**:  
     **Penjelasan**: Nama layanan yang tercatat adalah **Hasura**, platform backend untuk API GraphQL.

### 19. **timestamp.us**  
   - **1733840861541105**:  
     **Penjelasan**: Timestamp dalam **mikrodetik** yang menunjukkan waktu pasti dari transaksi ini.

### 20. **trace.id**  
   - **"27148b955db232089406bbf2a8ce0196"**:  
     **Penjelasan**: ID unik untuk melacak **trace** ini di seluruh sistem. Trace ini berfungsi untuk menghubungkan berbagai transaksi yang saling terkait dalam alur kerja yang lebih besar.

### 21. **transaction.duration.us**  
   - **1073**:  
     **Penjelasan**: Durasi transaksi ini adalah **1073 mikrodetik** (atau sekitar 1.073 milidetik). Artinya, transaksi ini selesai dalam waktu yang sangat singkat.

### 22. **transaction.id**  
   - **"d38652ae50be0b52"**:  
     **Penjelasan**: ID unik untuk transaksi ini, digunakan untuk melacak transaksi tersebut dalam sistem.

### 23. **transaction.name** & **transaction.name.text**  
   - **"/v1/graphql"**:  
     **Penjelasan**: Nama endpoint yang dijalankan dalam transaksi ini. Endpoint yang dipanggil adalah **/v1/graphql**, yang menunjukkan bahwa transaksi ini adalah operasi GraphQL.

### 24. **transaction.result**  
   - **"Success"**:  
     **Penjelasan**: Hasil transaksi ini adalah **berhasil**, yang berarti tidak ada error yang terjadi saat transaksi berlangsung.

### 25. **transaction.sampled**  
   - **true**:  
     **Penjelasan**: Data ini disample untuk dianalisis lebih lanjut. Artinya, data transaksi ini dimonitor untuk analisis lebih dalam mengenai kinerja aplikasi.

### 26. **transaction.type**  
   - **"custom"**:  
     **Penjelasan**: Jenis transaksi ini adalah **custom**, artinya ini adalah transaksi yang dikategorikan khusus oleh sistem, mungkin transaksi yang tidak standar atau unik bagi aplikasi.

### 27. **_id** & **_index**  
   - **"d3L8sJMB2LTZdF1KegbI"** & **"apm-7.17.18-transaction-000001"**:  
     **Penjelasan**: Ini adalah **ID dokumen** dan **indeks** tempat data transaksi disimpan dalam **ElasticSearch**, tempat Elastic APM menyimpan semua data observasi.



### **Kesimpulan:**
Transaksi ini merekam operasi GraphQL yang terjadi pada aplikasi **Hasura**, yang berlangsung dengan durasi  **1.073 milidetik**. Transaksi ini berhasil tanpa error dan melibatkan pengguna dengan peran **admin**.

>> ^For your Information^
>> "transaction.duration.us": [1073]     -> artinya : Durasi Transaksi selama 1.073 milidetik   <br/> <br/>
>> 
>> "labels.enduser_role": ["admin"]	 -> artinya : Transaksi ini melibatkan User dengan Role "admin"

