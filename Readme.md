Пример, демонстрирующий односторонний self hosted tls

1 - install tls certificate to dotnet core store

install tool
dotnet tool install --global dotnet-certificate-tool

install certificate
certificate-tool add --file ./iis_2020.pfx  --password 1 --thumbprint 61a5818f40baed9207a92ad79a885c5d5f8f9e82

2 - install tls certificate to cp store
/opt/cprocsp/bin/amd64/certmgr -install  -pfx -file ./iis_2020.pfx -store My -pin 1


3 - restore build and run
dotnet restore
dotnet build
dotnet run

4 - visit https://0.0.0.0:5000/weatherforecast, skip certificate error, seems working

5 - uncomment csproj making build target our framework, fix versions and paths

6 - restore build and run
dotnet clean
dotnet restore
dotnet build
dotnet run

7  - visit https://0.0.0.0:5000/weatherforecast, see Secure Connection Failed

