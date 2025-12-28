## Docker Case
### Proje
Basit bir Node.js uygulamasının Docker ile containerize edilmesi

### Kullanılan Teknolojiler
-Docker
-Node.js
-Express

#Kurulum ve Çalıştırma


### 1) Dockerfile Yazıldı
![Dockerfile](https://github.com/user-attachments/assets/14be7f7f-b4f0-4946-8a19-e020235f6bc6)

### 2) Image build edildi
![Imagebuild](https://github.com/user-attachments/assets/c55adac8-7f95-44e6-981c-781ae7249196)
sudo docker build -t devops-test .

### 3) Container host'tan 3000 portu üzerinden erişilebilir hale getirildi
![port3000](https://github.com/user-attachments/assets/c2145e0a-b0cb-4800-8bc5-fd1212674f8c)
sudo docker run -d -p 3000:3000 --name myCase devops-test
### 4) Tarayıcıdan Hello Deevops çıktısı gösterildi
![hellodevops](https://github.com/user-attachments/assets/64585a93-c162-4f5d-b9b4-68baadbffd84)

```bash
docker build -t devops-test .
docker run -d -p 3000:3000 --name myCase devops-test
```
