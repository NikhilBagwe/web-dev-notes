## Introduction :

- A basic .NET web api application will require .NET SDK, class libraries, system configuration to run it.

![image](https://github.com/NikhilBagwe/web-dev-notes/assets/67143015/54b47183-10ec-4f9b-bab1-970845da3a20)

- Once everything is in place, the application is executed and then we can see the endpoints in Swagger on Browser.
- Thus, we understand that the .NET api cannot run by itself. It requires multiple system configurations to work.
- So as of now, everything is running on local machine.
- Now when we want to deploy API to Server we will have to replicate the similar setup that we have on local onto Server.
- It will include the system and network configuration, installing correct SDK version, etc.

## Basics :

- Instead of trying to manually setup/configuring server, we can use Docker.
- Docker will essentially store all the information related to network configuration, permissions, software installed, etc. on local machine into a box (Docker Image). Then at the time of deployment, the box will pasted on the Server and same environment will ne recreated onto server.

## Containerize an .NET web api:

- Open the project in VSCode.
- Create a file with name "Dockerfile" at root of the project.
- So basically, we can create 2 boxes: One for Testing i.e "Base" (called as Staging) and second for Prod i.e Build.

```python
# base image
FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS Base
# Creating a folder
WORKDIR /app
# Exposing ports that will be utilize - http, https
EXPOSE 8080 
EXPOSE 8081

# building the application
FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
# When the app will be built, it wil be build for "release"
ARG BUILD_CONFIGURATION=Release
WORKDIR /src

# Add dependencies
COPY ["MongoAPI.csproj", "MongoAPI/"] 

RUN dotnet restore "MongoAPI.csproj"

# copy rest of the source code from local directory to Docker image
COPY  . .

WORKDIR "/src/MongoAPI"
RUN dotnet build "MongoAPI.csproj" -c $BUILD_CONFIGURATION -o /app/build

FROM build AS publish
ARG BUILD_CONFIGURATION=Release
RUN dotnet publish "MongoAPI.csproj" -c $BUILD_CONFIGURATION -o /app/publish

# final deployment
FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT [ "dotnet", "MongoAPI.dll" ]
```
- Then install docker on system and run the above docker image in terminal : docker build -t mongoAPI .
