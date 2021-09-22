#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS base
WORKDIR /app
#EXPOSE 5000
#ENV ASPNETCORE_URLS=http://*:5000
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /src
COPY ["ApiTestDocker/ApiTestDocker.csproj", "ApiTestDocker/"]
RUN dotnet restore "ApiTestDocker/ApiTestDocker.csproj"
COPY . .
WORKDIR "/src/ApiTestDocker"
RUN dotnet build "ApiTestDocker.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "ApiTestDocker.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "ApiTestDocker.dll"]