FROM microsoft/aspnetcore:2.1.0-preview1 AS base
WORKDIR /app
EXPOSE 80

FROM microsoft/aspnetcore-build:2.1.300-preview1 AS build
WORKDIR /src
COPY SomeApp.sln ./
COPY SomeApp/SomeApp.csproj SomeApp/
RUN dotnet restore -nowarn:msb3202,nu1503 /p:RestoreUseSkipNonexistentTargets="false"
COPY . .
WORKDIR /src/SomeApp
RUN dotnet build -c Release -o /app

FROM build AS publish
RUN dotnet publish -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "SomeApp.dll"]
