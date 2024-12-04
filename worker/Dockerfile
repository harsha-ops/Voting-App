FROM mcr.microsoft.com/dotnet/sdk:7.0

WORKDIR /app

COPY *.csproj ./

RUN dotnet restore

COPY . .

RUN dotnet publish -c release -o /out

WORKDIR /out

EXPOSE 80

ENTRYPOINT [ "dotnet", "Worker.d11" ]