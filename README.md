# docker-api-dockerizing

docker api test project => DockerApi => Basic Dockerfile and yml file </br>
docker-compose up </br>
docker build -t docker-api-image . </br>
docker run -p 5000:80 --name docker-dotnet-web-api-container docker-api-image </br>
 </br> </br>
http://localhost:5000/WeatherForecast/</br>
http://localhost:5000/api/Values/</br>
http://localhost:8080/swagger/index.html



name: Containerımıza vereceğimiz isimdir. <br/>
-p: Localimizden containera erişmek için verdiğimiz porttur. <br/>
-link: Başka bir container ile haberleşmesini sağlamak için kullanılır. <br/>
-e: Environment tanımlamak için kullanılır. <br/>
-d: Container’ın deamon modunda yani arka planda çalışmasını sağlar. <br/>
--filter : ile containerlar için arama yapabiliriz. şunları getir falan filan gibi
docker info => Mevcut işletim sisteminde genel bilgiler veriliyor. cpu ram vb. build versionu. running durumda olan. pause durumda olan. log dosyasının json olduğunu. operating sistemi, işletim sistemini, docker dosyalarının tutulduğu dizinde görülür
docker container exec -it con_id => ile var olan containerın içerisine bağlanabiliriz.
docker container logs --tail 10 con_id => çalışsan container üzerindeki son 10 tane logu gösterir.
docker container logs -f con_id => container loglarını canlı canlı gösterir. Anlık ne oluyor ise görürsün. control + c ile çıkarsak sorun yok container kapanmaz. attach de öyle değil.
docker container inspect con_id => container detaylarını göerüyoruz. Config kısmı, volum, içerisindeki versionlar, yapılandırma ayarları falan gözüküyor.
docker container rm con_id => con çalışmıyor ise siler.
docker-compose --version
docker-compose up


docker network create --driver bridge my_bridge => network oluşturur. farklı networkler birbirine direk erişemez.
--network=my_bridge => ile de oluşturulan containerları bu networklerın içerisine atabiliyoruz.
docker network inspect bridge => network detayları

docker system prune => sistemde çalışmayan kullanılmayan containerları ve imajları siler temizler ortamı.
docker container prune => sistemde çalışmayan kullanılmayan containerları siler temizler ortamı.
docker container prune --filter 'label=apple'. => filter ile ilgililer prune de edebiliriz.


Volum Listesi : docker volume ls
Volume Silme : docker volume rm <volume_name>
Volume Ekleme: docker volume create my-volume
docker run -v /docker-volume/mysql:/var/lib/mysql mysql-depo

docker api test proje
docker-compose up
docker build -t docker-api-image .
docker run -p 5000:80 --name docker-dotnet-web-api-container docker-api-image

my core api rabbit image
docker run -d --hostname my-rabbit --name myrabbit -e RABBITMQ_DEFAULT_USER=admin -e RABBITMQ_DEFAULT_PASS=123456 -p 5672:5672 -p 15672:15672 rabbitmq:3-management
docker build -t my-core-api-rabbit-image:1.0 .
docker run --name my-core-rabbitmq_api -d -p 8080:80 --link myrabbit:my-rabit-alians -e host=myrabbit my-core-api-rabbit-image:1.0

docker run --name my-web-server -v my-volume:/usr/share/nginx/html -d -p 8080:80 nginx
docker run --name some-nginx -v /var/my-docker-mapping:/usr/share/nginx/html:ro -d -p 800:80 nginx
docker run --name my-web-server -v D:/DockerVolume/ngx:/usr/share/nginx/html -d -p 8080:80 nginx

docker run -v /docker-volume/mysql:/var/lib/mysql --name my-mysql-server -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123test -d mysql
docker run --name phpmyadmin -d --link my-mysql-server:db -p 5100:80 phpmyadmin

alpine içerisindeki data klasörünü volum ile ana pc ile eşitliyoruz.
docker run -it -v var/my-docker-mapping:/data alpine sh

Local Repo için registry kullan ve kendi imajlarını locale yükle
docker run -d -p 5000:5000 --restart always --name registry registry:2
5000 portunun sonuna /v2/_catalog yazarak içerideki imajları görebiliriz.
docker pull ubuntu
docker tag ubuntu localhost:5000/ubuntu
docker push localhost:5000/ubuntu

portainer => görsel üzeriden kullanılacak ve yönetimi yapabiliriz. contrainer durumlarını falan gösteriyor.

Yararlı Sayfalar

https://container.training
