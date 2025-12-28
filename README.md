### Docker Case
### Proje
### Görev 1
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
### 4) Tarayıcıdan Hello Devops çıktısı gösterildi
![hellodevops](https://github.com/user-attachments/assets/64585a93-c162-4f5d-b9b4-68baadbffd84)


## Görev 2
Container çalışıyor ama uygulamaya erişilemiyorsa;

### Nereler kontrol edilmeli?
### 1) Container logları
* Server ayağa kalkmış mı?
* Hata var mı?
* Port dinleniyor mu?
* 
```
docker logs myCase
```
### 2) Port Mapping(Docker)
Container ın doğru port ile dışarı açılıp açılmadığı kontrol edilir.
Aşağıdaki komut girildiğinde port kısmında 3000 -> 3000 eşleşmesi var mı bakılır.
```
docker ps
````
### 3) Container Durumu
Aşağıdaki komut girildiğinde up durumda mı yoksa exited durumda mı kontrol edilir
```
docker ps
```
### 4) Port Eşleşmesi(Uygulama tarafı)
Container içindeki uygulama, tanımlanan  portu dinliyor mu kontrol edilir
app.listen(3000, () =>
  {
    console.log("App runnig on port 3000")
  }
)

