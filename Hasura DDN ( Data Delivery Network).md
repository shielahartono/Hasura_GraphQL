# Hasura DDN ( Data Delivery Network)

## 1. Understanding DDN (Data Delivery Network)

- Data Delivery Network (DDN) juga dikenal sebagai Content Delivery Network (CDN).
DDN adalah system yang dirancang untuk meningkatkan pengiriman Digital Content melalui internet.
System ini mengurangi Latency (waktu yang dibutuhkan untuk mengirimkan Data), mempercepat Loading Times (waktu pemuatan), dan meningkatkan User Experience untuk aplikasi/website, terutama yang melayani Large Volume of Data (Volume Data yang besar).

### A. Fungsi Utama DDN (atau CDN) : 
#### (1) Caching Content at Edge Servers :

-> DDN menggunakan Distributed Server Network yang terletak di berbagai Geographical Locations, server dinamakan "Edge Server".
Edge Server menyimpan sementara Salinan Content (seperti Image, Videos, dan Web Page).

"Edge Server" merupakan tempat penyimpanan sementara (temporary storage), tetapi Perannya lebih dari sekedar tempat penyimpanan sementara.

Saat User melakukan "Request Content", DDN menyajikan "Request Content" tersebut dari "Edge Server" terdekat, untuk mengurangi jarak yang harus ditempuh untuk pengiriman Data, yang mana hal ini bertujuan untuk mengurangi Latency (waktu yang dibutuhkan untuk mengirimkan Data).

(yang dilakukan Edge Server ini merupakan Caching Strategy)


-> "Edge Server" berfungsi sebagai "Temporary Storage" (tempat penyimpanan sementara),
tetapi peran dari "Edge Server" lebih dari sekedar tempat penyimpanan sementara.
Fungsi utama "Edge Server" adalah menyimpan Data yang sering diakses agar Data tersebut dekat ke pengguna akhir untuk mengurangi Latency & meningkatkan performance.
(Data yang sering diakses tersebut seperti Web Pages, images, Videos, atau Content lainnya)

