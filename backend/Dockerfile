FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build-env
WORKDIR /backend


COPY *.csproj ./
RUN dotnet restore


COPY . ./
# RUN dotnet publish -c Release -o out
EXPOSE 5000
EXPOSE 5001
ENV ASPNETCORE_URLS=http://*:5000
ENTRYPOINT ["dotnet", "watch", "run"]


# FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
# WORKDIR /backend
# COPY --from=build-env /app/out .
# EXPOSE 5000
# ENV ASPNETCORE_URLS=http://*:5000
# ENTRYPOINT ["dotnet", "backend.dll"]