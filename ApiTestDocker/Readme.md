DOC
-------------
https://www.youtube.com/watch?v=wQSuZFd01tY
https://www.youtube.com/watch?v=CV_Uf3Dq-EU&t=944s
https://code.visualstudio.com/docs/containers/quickstart-aspnet-core


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


Change AppSetting.json
-----------------------
docker run -it --rm -p 8080:80 -e "ASPNETCORE_ENVIRONMENT=Development" -e "MyConnectionSettings:Host=TestHost" -e "MyConnectionSettings:Port=90" -e "MyConnectionSettings:User=testUser" --name myapp apitestdocker:dev