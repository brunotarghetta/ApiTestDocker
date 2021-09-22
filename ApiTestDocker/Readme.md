BUILD
------
docker build -t apitestdocker:dev -f ./apitestdocker/Dockerfile .

RUN
-----
docker run -it --rm -p 8080:80 --name myapp apitestdocker:dev


Example: http://localhost:8080/weatherforecast


Set Develpment Env
--------------------
docker run -it --rm -p 8080:80 -e "ASPNETCORE_ENVIRONMENT=Development" --name myapp apitestdocker:dev
http://localhost:8080/swagger/index.html



Push to Docker Hub
---------------------
docker login
docker tag apitestdocker:dev brunotarghetta/apitestdocker:dev
docker push brunotarghetta/apitestdocker:dev