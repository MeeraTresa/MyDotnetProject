FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build-env
WORKDIR /app
# copy the csproj
COPY *.csproj ./
RUN dotnet restore
# copy everything else
COPY . ./
RUN dotnet publish -c Release -o out
#build runtime image
FROM mcr.microsoft.com/dotnet/aspnet:7.0
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT [ "dotnet", "API.dll" ]
