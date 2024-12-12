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

