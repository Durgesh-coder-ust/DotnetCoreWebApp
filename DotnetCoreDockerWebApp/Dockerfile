FROM microsoft/dotnet:2.2-aspnetcore-runtime AS base
WORKDIR /app
EXPOSE 80

FROM microsoft/dotnet:2.2-sdk AS build
WORKDIR /src
COPY 'DotnetCoreDockerWebApp\DotnetCoreDockerWebApp.csproj' ./
RUN dotnet restore 
COPY . /
RUN dotnet publish "DotnetCoreDockerWebApp.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "DotnetCoreDockerWebApp.dll"]
