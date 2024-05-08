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
--filter : ile containerlar için arama yapabiliriz. şunları getir falan filan gibi <br/>
docker info => Mevcut işletim sisteminde genel bilgiler veriliyor. cpu ram vb. build versionu. running durumda olan. pause durumda olan. log dosyasının json olduğunu. operating sistemi, işletim sistemini, docker dosyalarının tutulduğu dizinde görülür <br/>
docker container exec -it con_id => ile var olan containerın içerisine bağlanabiliriz. <br/>
docker container logs --tail 10 con_id => çalışsan container üzerindeki son 10 tane logu gösterir. <br/>
docker container logs -f con_id => container loglarını canlı canlı gösterir. Anlık ne oluyor ise görürsün. control + c ile çıkarsak sorun yok container kapanmaz. attach de öyle değil. <br/>
docker container inspect con_id => container detaylarını göerüyoruz. Config kısmı, volum, içerisindeki versionlar, yapılandırma ayarları falan gözüküyor. <br/>
docker container rm con_id => con çalışmıyor ise siler. <br/>
docker-compose --version <br/>
docker-compose up <br/> <br/>


docker network create --driver bridge my_bridge => network oluşturur. farklı networkler birbirine direk erişemez. <br/>
--network=my_bridge => ile de oluşturulan containerları bu networklerın içerisine atabiliyoruz. <br/>
docker network inspect bridge => network detayları <br/> <br/>

docker system prune => sistemde çalışmayan kullanılmayan containerları ve imajları siler temizler ortamı. <br/>
docker container prune => sistemde çalışmayan kullanılmayan containerları siler temizler ortamı. <br/>
docker container prune --filter 'label=apple'. => filter ile ilgililer prune de edebiliriz. <br/> <br/>


Volum Listesi : docker volume ls <br/>
Volume Silme : docker volume rm <volume_name> <br/>
Volume Ekleme: docker volume create my-volume <br/>
docker run -v /docker-volume/mysql:/var/lib/mysql mysql-depo <br/> <br/>

docker api test proje <br/>
docker-compose up <br/>
docker build -t docker-api-image . <br/>
docker run -p 5000:80 --name docker-dotnet-web-api-container docker-api-image <br/> <br/>

my core api rabbit image <br/>
docker run -d --hostname my-rabbit --name myrabbit -e RABBITMQ_DEFAULT_USER=admin -e RABBITMQ_DEFAULT_PASS=123456 -p 5672:5672 -p 15672:15672 rabbitmq:3-management <br/>
docker build -t my-core-api-rabbit-image:1.0 . <br/>
docker run --name my-core-rabbitmq_api -d -p 8080:80 --link myrabbit:my-rabit-alians -e host=myrabbit my-core-api-rabbit-image:1.0 <br/> <br/>

docker run --name my-web-server -v my-volume:/usr/share/nginx/html -d -p 8080:80 nginx <br/>
docker run --name some-nginx -v /var/my-docker-mapping:/usr/share/nginx/html:ro -d -p 800:80 nginx <br/>
docker run --name my-web-server -v D:/DockerVolume/ngx:/usr/share/nginx/html -d -p 8080:80 nginx <br/> <br/>

docker run -v /docker-volume/mysql:/var/lib/mysql --name my-mysql-server -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123test -d mysql <br/>
docker run --name phpmyadmin -d --link my-mysql-server:db -p 5100:80 phpmyadmin <br/> <br/>

alpine içerisindeki data klasörünü volum ile ana pc ile eşitliyoruz. <br/>
docker run -it -v var/my-docker-mapping:/data alpine sh <br/> <br/>

Local Repo için registry kullan ve kendi imajlarını locale yükle <br/>
docker run -d -p 5000:5000 --restart always --name registry registry:2 <br/>
5000 portunun sonuna /v2/_catalog yazarak içerideki imajları görebiliriz. <br/>
docker pull ubuntu <br/>
docker tag ubuntu localhost:5000/ubuntu <br/>
docker push localhost:5000/ubuntu <br/> <br/>

portainer => görsel üzeriden kullanılacak ve yönetimi yapabiliriz. contrainer durumlarını falan gösteriyor. <br/> <br/>

Yararlı Sayfalar <br/> <br/>

https://container.training <br/>
