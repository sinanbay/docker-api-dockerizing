FROM mcr.microsoft.com/dotnet/aspnet:6.0-alpine3.16 AS base
WORKDIR /app
FROM mcr.microsoft.com/dotnet/sdk:6.0-alpine3.16 AS build
WORKDIR /src
COPY . .
RUN dotnet restore
COPY . .
RUN dotnet publish -c Release -o publish
FROM base AS runtime
COPY --from=build /src/publish .
ENTRYPOINT ["dotnet","DockerApi.dll"]
