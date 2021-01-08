#Report for laboratory 6: Microservices
**Author: Sergio Martínez Martín**\
**NIP: 719974**

#1. Setting up one instance of each service
##1.1 Running the services
* RegistrationServer
![RegistrationServerInit](screenshots/RegistrationServerInit.PNG)

* AccountsServer
![AccountsServerInit2222](screenshots/AccountsServerInit2222.PNG)

* WebServer
![WebServerInit](screenshots/WebServerInit.PNG)

##1.2 Checking the services
You can see in _localhost:1111_ that the _Accounts_ and _Web_ services are running.
![EurekaInit](screenshots/EurekaInit.PNG)

##1.3 Running a second _accounts_ service
You must change the port in which is running from '2222' to '4444' in the file ```accounts/src/main/resources/application.yml```.\
![ChangePort](screenshots/ChangePort.PNG)

After doing this, you can now run a second instance of the _accounts_ service and check that it's running in _localhost:1111_.\
![AccountsServerInit4444](screenshots/AccountsServerInit4444.PNG)
![EurekaSecond](screenshots/EurekaSecond.PNG)

#2. What happens when you kill the microservice accounts (2222) and do requests to web? Can the web service provide information about the accounts again? Why?
After killing the _AccountsServer_ service running in port 2222, as the alert was claiming, the service is reported as running when it is not running.
This causes that when you access to ``http://localhost:3333/accounts/123456789``, sometimes it will work correctly as the request is handled by _AccountsServer:4444_.\
![ServiceWorking](screenshots/ServiceWorking.PNG)

But it may also end in an error because it tries to make it work with the service in port 2222.\
![ServiceNotWorking](screenshots/ServiceNotWorking.PNG)