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
- Docker will essentially store all the information related to network configuration, permissions, software installed, etc. on local machine into a box. Then at the time of deployment, the box will pasted on the Server and same environment will ne recreated onto server.
