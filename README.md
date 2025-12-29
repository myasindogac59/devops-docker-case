# Docker Case

### Görev 1
Basit bir Node.js uygulamasının Docker ile containerize edilmesi

### Kullanılan Teknolojiler
-Docker
-Node.js
-Express


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
docker ps -a
```
### 4) Port Eşleşmesi(Uygulama tarafı)
Container içindeki uygulama, tanımlanan  portu dinliyor mu kontrol edilir
`
app.listen(3000, () =>
  {
    console.log("App running on port 3000")
  }
)
`
## Görev 3
### Container içerisindeki uygulama loglarına nasıl bakılır?

### 1) docker logs

Bu komut kullanılarak bir Docker containerinin logları alınabilir.
```
docker logs <container-name>
```
### 2) docker logs -f devops-container
Container loglarını canlı izlemek için kullanılabilir

```
 docker logs <container-name> -f
```
### Host makinede disk doluluğunu kontrol etmek için

```
df -h
```
Disklerin doluluk oranı % olarak bu komut sayesinde görüntülenebilir

## Görev 4

### Aşağıdaki pipeline sırasını doğru buluyor musun? Doğru değilse neden?
Deploy -> Build -> Test
*Doğru depil çünkü build edilmemiş birşey deploy edilemez ayrıca test edilmemiş bir uygulamanın production a alınması hatalı bir kodun canlı ortama gitmesi açısından risklidir.

Doğru pipeline sıralaması;

* Build -> Test -> Deploy

Build de uygulama derlenir ve docker image oluşturulur, test de uygulamanın doğru çalışıp çalışmadığı test edilir, deploy da ise testleri geçen uygulama production a alınır.

## Görev 5 (Güvenlik)

### Bu uygulamayı root user olarak çalıştırmak neden risklidir ve ne yapılabilir?

* Uygulamada güvenlik açığı varsa saldırgan container içerisinde root yetkisini alabilir
* Yanlış oluşturulmuş bir container host kaynaklarına erişebilir
Ne yapılabilir?

* Root kullanıcı ile sadece paket kurulumları yapılabilir ve uygulama çalışırken root olmayan kullanıcı ile çalıştırılabilir. Bu sayede daha güvenli bir ortam oluşmuş olur

Görev 6 (Bonus)
## Bu uygulamayı prodction a alacak olsak ne eklerdin?
Port ve  ortam bilgilerini kod içerisine değil .env ye koyardım.
