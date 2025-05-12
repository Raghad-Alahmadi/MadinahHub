FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /app

COPY . ./
RUN dotnet restore
RUN dotnet publish -c Release -o out

# Use .NET 9 ASP.NET runtime
FROM mcr.microsoft.com/dotnet/aspnet:9.0 AS runtime
WORKDIR /app

COPY --from=build /app/out ./
COPY Backend/MHBackend/MadinahHubDb.sqlite ./MadinahHubDb.sqlite

EXPOSE 80

ENTRYPOINT ["dotnet", "MHBackend.dll"]