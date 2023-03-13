# docker-api-dockerizing

docker api test proje
docker-compose up
docker build -t docker-api-image .
docker run -p 80:80 --name docker-dotnet-web-api-container docker-api-image
