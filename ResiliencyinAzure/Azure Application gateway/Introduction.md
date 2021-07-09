Hello everyone ! 
Today we will be continuing the series on resilency options available in Azure.

In part 1 of the series we discussed on Azure traffic Manager  Click here for Part 1.
In the post we will be looking  into **Application gateway** service available in Azure. Application gateway is a web traffic load balancer  in Azure which helps to manage traffic of  the application and helps the application in autoscaling , Rediection, SSL/TLS termination , connection draining etc (We will cover some of these). 

The Application gateway works at Application layer of the application (Layer 7) which means it can also accept query information in the URL as well like example.com/**Images/ **, example.com/**videos */* and rediect based on those specific parameters, this is an example of one of the features in Application Gateway called URL-based routing. 


![[App gateway overview.png]]

If you look into the image you can see that the request with query as /imges/* goes to a different deployment (VM's or VMSS or Azure app service) and the request with query as /videos/* goes to a different one.

**Difference between VM's VMSS and Azure app service** (Put this in a yellow box)
VM-> When we create a virtual machine in Azure and deploy our code manually there we have to manage everything like maintenance , scaling (horizontal and vertical) , upgrade etc on our own. This is useful when you want to have a greater control of you code as well the infrastructure deployed.

VMSS-> VMSS or virtual machine scale set is a feature in Azure where we can define the OS we need and the scale options . Whenever the scale conditions are met(like 90% CPU  or 80% of the memory consumed  or any other parameter as per your requirement) the VMSS creates a number of VM's automatically (scaling out) and whenever the threshold for lower limit is reached the number of VM's gets reduced (scaling in).

Azure App service is PAAS service by Azure where the entire infratsructure management (scaling,maintenance,upgrade etc) is managed by Azure . As a user you just have to create the App service and specify the infrastructure requirement like cores, cpu and also specify the technology stack (Like .Net Core, Java, Python etc) and the rest will be taken care by Azure. This scenario is useful in case where you just want to focus on your code and it deployment and not care about how the infrastructure is being handled.


**Components of Application Gateway**

Below diagram depicts the components for Application Gateway

![[Application Gateway Components.png]]

Lets Understand each component .

1. **Application Gateway Frontend :- **
     
	 Frontend is the Public facing component (Generally with a static Public IP) which is exposed to the client to recieve the traffic.
	 
2. **Backends**
    
	 Backends or Backend Pool is a collection of rersouces (VM's , VMSS , Externalnally deployed application , Azure App service and FQDN) where the traffic needs to be routed. 

3. Routing Rules:-
     
	 Routing Rules are the set of rules defined on how and where the trffic should be sent based on the type and content of the request. A routing rule consists of a listener and atleast one Backend target (VMs, VMSS , App service etc).
	 
	 In the routing rules we define parameters like Protocol (HTTP, HTTPS) , Port , Certs (in case of HTTPS) , listener type (Basic and Multisite- We will cover this in the feature section) and the backend targets.
	 
	 
