Hello Everyone , Today we are going to look into the resiliency options in Azure , In this post we are looking into Azure Traffic Manager which helps in distributing traffic generated from a client to the service (Endpoint) . 

If an application is used throughout the globe , deploying the app in just a single location can lead to performance degradation as the user (cleint requests) can be initiated from anywhere around the world , if the distance between the app location and the user is too far it affects the performance of the application with respect to latency. There are other several factors to be looked upon when we startegies the deployment of an application which we will talk about in this post. 


**Azure Traffic Manager**

It is a DNS based tarffic load balancer which helps to disttribute traffic from a client to a rule based identified endpoint .
It uses tarrfic routing (more on this ahead) to direct requests to the appropriate service endpoints.

There are several benefits of Azure traffic manager which includes applications availability , increase performance of the application , Geo-Fencing etc.

Even for complex deployment you can use Nested traffic manager profiles (more on this later).

**Steps to create traffic manager profile:-**

Below is the pictorial representaion of how the traffic manager in our demo would look like.

[[Azure Traffic Manager]]

For our demo we would be using a web app which will be deployed in two regions , one will server as a primary region and the second will be deployed to a failover region.

Follow below link to deploy web app.

LINK HERE PLEASE


Once we have deployed our web app we need to create the traffic manager profile:-

1. Click on Create a resource -> Traffic Manager Profile and then click create
2. Fill the fields as per following image 
    	![[traffic manager profile.png]]
   Note:- we have selected routing method as Priority , following options are available in case of roting method:-
   
   
        Priority
        Performance
		Weighted
		Geographic
		Multivalue
		Subnet
        

We will discuss about Performance,Weighted and Geographic routing method in more details in a little bit , however lets demonstrate how can one create a traffic manager profile in Azure by selecting priority based routing.

Once we have the traffic manager policy we can now add endpoints to which the client requests will be directed based on priority (since we selected priority as our routing method) .

To add the endpoints follow the below steps:-

1. Open the traffic manager profile you had created in the previous step.
2. Go to Endpoints tab
3. Click on create , fill the fields as per below:-
   ![[Add endpoint.png]]
    
Note:- We have selected the first deployment which we performed at East US region , the priority selected is 1 which means all the traffic will be redirected to this deployment , unless we have a failure in the region. In case of failure the traffic will be sent to the priority 2 region and when priority 2 region does down the traffic is then redirected to the priority 3 region and so on.

To add the endpoint for priority 2 region we add the endpoint from step 1-3 with values for priority resource to be 2 and webappaatWestUS2 respectively.


To see this is action , browse to the DNS name of the traffic manager profile , and you will notice that it takes us to the default website we created, Now disable the East US region endpointt in the traffic manager profile (the priority 1 endpoint) and then again browse to the DNS name of your traffic manager profile you will see that you are still able to browse to the website , although this time the traffic was redirected to the secondary region but an an end user you would not be able to see that. 

We can add more no of priorities based on the number of regions the app is deployed to.

**I will also cover this on how we can create the same infratsruture through terraform in CI/CD for folks who have basic hands on in terraform  ** 

























BiblioGraphy:-

John Savill Video,
Microsoft documents