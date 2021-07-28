Hello everyone ! 
Today we will be continuing the series on resilency options available in Azure.

In part 1 of the series we discussed on Azure traffic Manager  Click here for Part 1.
In the post we will be looking  into **Application gateway** service available in Azure. Application gateway is a web traffic load balancer  in Azure which helps to manage traffic of  the application and helps the application in autoscaling , Rediection, SSL/TLS termination , connection draining etc (We will cover some of these). 

The Application gateway works at Application layer of the application (Layer 7) which means it can also accept query information in the URL as well like example.com/**Images/ **, example.com/**videos */* and rediect based on those specific parameters, this is an example of one of the features in Application Gateway called URL-based routing (one of the features of application gateway). 


![[App gateway overview.png]]

If you look into the image you can see that the request with query as /imges/* goes to a different deployment (VM's or VMSS or Azure app service) and the request with query as /videos/* goes to a different one.

**Difference between VM's VMSS and Azure app service** (Put this in a yellow box)
VM-> When we create a virtual machine in Azure and deploy our code manually  we nned to manage everything like maintenance , scaling (horizontal and vertical) , upgrade etc on our own. This is useful when you want to have a greater control of your code as well the infrastructure it is deployed due to company policy or security concerns.

VMSS-> VMSS or virtual machine scale set is a feature in Azure where we can define the OS we need and the scale options . Whenever the scale conditions are met(like 90% CPU  or 80% of the memory consumed  or any other parameter as per your requirement) the VMSS creates a number of VM's automatically (scaling out) and whenever the threshold for lower limit is reached the number of VM's gets reduced (scaling in).

Azure App service is PAAS service by Azure where the entire infratsructure management (scaling,maintenance,upgrade etc) is managed by Azure . As a user you just have to create the App service and specify the infrastructure requirement like cores, cpu and also specify the technology stack (Like .Net Core, Java, Python etc) and the rest will be taken care by Azure. This scenario is useful in case where you just want to focus on your code and its deployment and not care about how the infrastructure is being handled.


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
	 
	 **Steps to Create Application Gateway in Azure**
	 
	 1. Login to the portal , go to  Application gateways and click create.
	 2. Fill the basic tab as per below:-
	    
		![[Basic tab.png]]
	     
	    Note: Put this in yellow:- 
		
		The field that are underlined in yellow in above image (Tier, Firewall Status , Firewall Mode) will be explained in the Feature section of this article.
	 
	    You might have to create some resources while creating the application gateway (Like resource group , virtual network ,public IP). This can be either done before or while creatig application gateway.
		
		3. Click on next, in the frontends tab you can either create a public IP or you provide the Public IP from the dropdown (provided you have already created one).
		4. In the Backend tab click on Add a **backend pool** ,  provide the necessary values and select the type of (VM, VMSS, App service , FQDN) and select the resource from the dropdown.
		    
			Note: Whatever value you might have selected among the backend type please make sure you already have the resource created before hand so that you can select the same from the dropdown.
			
		5. Click on next , in the configuration tab click on **Add a routing rule** 
		6. In the listener tab let there be default values, in the backend targets tab in the HTTP setting field click on Add new and fill the values as per below.
		
	        ![[HTTP setting.png]]
		
	      Note:- Some fields like Cookie-based affinity and Connection draining might not be familiar to you now however we will cover those topics in feature section.
		  
		  7. Click on add -> next-> Create
	
	 **Features of Application Gateway**
	 
	Below are the List of features available in Application gateway :-
	
	
	SSL Termination
	**AutoScaling**
	**Zone Redundancy**
	Static VIP
	**Web Application Firewall**
	**Ingress controller for AKS**
	**URL-Based routing**
	**Multiple Site-hosting**
	Redirection
	**Session Affinity**
	Websocket and HTTP/2 Traffic
	**connection draining**
	custom error pages
	Rewrite HTTP headers and URL
	Sizing
	
   We will be discussing the bold topics in this article. 
   
   
   
   **AutoScaling**
   Auto-Scaling is one of the most important feature for any service specially when you are building in cloud. In Case of Application gateway while creating the service you can specify whether you want to Auto-scale or not , when autoscale is configured while creation based on traffic requirement the instances of the application gateway is Autoscaled up(Maximum scaling capacity is 125).  In the case when the traffic is low the service will be autoscaled down (this helps in avoiding unnecessary resource which in turn saves cost).
   
   We also have the option to manually scale it which we can chose while creating the service.  In case of manual scaling we need to specify the instance count (1 to 125). 
   Manual scaling is not the recommended approch for applications with large traffic or large user base as the performance is degraded when there is sudden spike in traffic.
   
   
   **Web Application Firewall (WAF):-**
   
   WAF is one the most imprtant feature for application gateway as it provides several benefits specailly with respect to vulnerabilities (Sql Injection and cross-site scripting are the most common ones), WAF can be thought of as a central point for protecting against exploits and vulnerabilities in your web application.
   
     Note:- OWASP in layman term can be thought of as a set of industry practice in the field of web application security. There are several methodolgies which are included as part of WAF and automatically upgraded within the configuration.
	 
   There are two types of WAF policy that can be associated with the Application Gateway:-
   1. Managed Rules:-
       These are rules already available in azure and can be used directly and associated to the Application gateway, below are the list of available category of rules currenly available that can be used.
	   ![[Managed WAF rules.png]]
	   
   2. Custom Rules:-
       Custom rules are something which we can define and associate with an Application gateway. This is generally used if you want to specifically allow or deny a set of IP addresess (for example allow only the IP address originating from employees of a company in case of in-house applications) , or allow a certain set of rules for one site and another set of rules for another sites , custom rules allow us to design the centralized security of or application based on our needs.
	   
WAF has two policy modes ,Prevention and Detection. 

As the name suggests when we chose Prevention as the policy mode , the traffic is blocked from reaching the application in case it does not comply with the rules. 

However , In case of Detection mode traffic is not blocked rather the threat (or traffic not complying to the rules) are logged and monitored (this can be viewed in the Diagnostic logs section), this log can also be integrated with Azure Monitor (This is a centralized monitoring service for Azure where you visualize the errors and other logs for resources available in Azure) which will helps in visualizing the threats .


**Ingress Controller for AKS**

Before we have a look on Ingress , lets get familiar with some basic terminologies related to it.

Containers:- Containers are basic building blocks for building a modern application , it is lighteweight virtualized system which can be used to  run microservice , processes etc. 

When a modern application is being developed with use of containers it becomes unmanageable when the complexity increases,to overcome this we use kubernetes.


Kubernetes is a container orchestration tool which helps in managing container runtime (creating , deleting , scaling , networking services etc). 

Lets get familiar with some of the basic terminologies of Kubernetes :- 

   Pod:- A pod is a basic deployable unit in kubernetes which has one or more containers associated with it.
	  
   ![[Pod Demonstration.png]]
	  
	  
   Node : Nodes are computational units (a virtual machine, a physical machine etc) which provides the necessary ram and cpu to deploy a pod.
   
   ![[Node.png]]
   
   
  Cluster:- Having a single node is ok when you are working with a small application with less number of pods , however in case of large applications we need large computational resource , in such a scenario a group of nodes is created which is termed as a cluster , when you deploy your pod in a cluster the pod is deployed inteliigently to a node within that cluster depending upon the available resource (There are several other factors which Kubernetes used to chose a node, the exaplanantion of which beyond the scope of this article) .
  
   ![[Cluster.excalidraw]]
   
   
Now that we are familiar with pods, nodes, cluster we are good till deployment of the servcies, now we need to take care of exposing the services to the external client . This is where Ingress comes into picture , an ingress is a component in kubernetes which helps in  rediecting the external requests among pods (actually among services but for simplicity and scope of the post lets assume it to be pods).

![[Ingress.png]]

The abobe image is a representation of traditional ingress controller .


Problem with Traditional Ingress controller :-

The WAF problem (WAF could not be created within the cluster hence we need to create it outside the cluster which will add unnecessary hop).




**AGIC (Azure gateway Ingress controller)**

  AGIC is an add-on in Kubernetes through which AKS uses it to expose the application external to the cluster . Below diagram depicts the working of AGIC.
  
  ![[AGIC.png]]
  
  Lets have a look at  each components.
  
   Azure resource manager - Azure resource manager is a tool which helps in creating , updating and deleting a resource within azure,. In this case whenever there is a requiremenet to update the configuration of the Application Gateway (the backend, rules etc) it will apply the same and the configuration is updated automatically.
   
   App gateway :- This is the same app gateway which we have discussed in our post , however in this case the backends and other configuration was updated automatucally based on the AKS cluster. 
   
   Pods:- Pods here are the actual service of the application to which app gateway has the backned configuration pointed to. 
   
   AGIC - AGIC here interacts with Kubernetes API and looks for any changes in the kubernetes resource , when it encounters any change it update the Azure resource manager , and azure resource manager will make the necessary changes.
   
   Kubernetes API- Kubernets API is the main component of the Kubernetes architecture where all the information about the cluster and other resource within the kubernetes resides, AGIC uses this information and applies to azure resource manager.
   
  
  
  In this post of the resilienct series we covered application gatewya , Ttough we have looked into various components and features of Application gateway there are several other features as well which makes it more a great layer 7 load balancer for your modern applications. In the next we will discuss about Azure Front Door.
  
  Have a great day!
  
  
  