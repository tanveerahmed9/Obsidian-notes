Traffic routing methods are ways defined in tarffic manager profiler to direct the incoming client request to the deployed application , below are some of the traffic routing methods defined in Azure .

1. **Priority**:-

In case of priority endpoint a primary endpoint is defined in the traffic manager profiler where all the requests are redirected (priority is set to 1 while adding the end-point) , you can add one or more endpoint with different priorities (2,3,4 etc) , if the service is not available at priority 1 the client sreqyest is then redirected to the subsequent priority endpoint and if the subsequent priority endpoint is also not available the request will be redirected to the next available priority endpoint and so on .

Below Diagram represents how priority based tarffic manager profile looks like.

![[Priority Based routing.png]]

2. **Weighted**
    
	In case of weighted traffic routing the traffic redirection happens based on the weight of the endpoints. Lets say we have 5 endpoints , weighted 20,80,30,10,70. The one with the weight set at 70 will have highest chance of receving the traffic and one with weight set to 10 will have the lowest chance of receiving the traffic.
	
	This case is mostly used in case you want to gradually upgrade tarffic to an endpoint after the deployment is done. Lets say you deployed the service to a location and you want to make sure it is working as expected and only expose the service to very few users , to achieve this we set the value to the lowest among all endpoints (10 in the mentioned example) and once you observe that you are good to expose the service to more number of users you can gradually increase the weightage (this can be done through portal , PowerShell, PowerCLI etc).
	
	Below Diagram depicts how the weigted traffic routing method works:-
	
	![[Weight based traffic routing.png]]


3. **Performance**
  
     Performance based routing uses the latency table (which it maintains) to decide where the traffic needs to be redirected . When a traffic is recieved to the traffic controller it redirects the traffic to the endpoint with lowest latency (which is generally but not necessarily the nearest location from the IP address of the source ) 
	 
	 below picture depicts the working of performance based routing method.
	 
	 
	![[Performance based Routing.png]]
	
	If you look at the latency table in the diagram , for each IP range there is a latency in ms (millisecond) recorded, traffic manager will look at the IP source and check which IP range it is on , based on the IP range it determines which Endpoint has the lowest latency and directs the traffic to the identified endpoint. 
	
	This method is very useful when you have users around several geographical regions and is performance critical .
	
	
	4. **Geographic traffic-routing method**
	
          This method of routing is useful in case of data soveigreinty rules, localisation of content (for a example a paid up video streaming service will have different set of contents for US users and different for India users). 
		  
		  In Case of Geographic traffic-routing method the redirection of traffic happens based on the source IP's geographic location . The grouping can be done on basis of Regional Grouping (Like Africa, APAC etc) , Country, states etc. 
		  
		  It is commonly seen that geographic traffic-routing method is used in a nested format (we will see this in a bit) . below example diagram shows one of the use case in nested tarffic routing geographic method is a parent routing method to the priority based traffic routing method.
		  
		  ![[Geographic based routing.png]]
		  
	     You might have observed that there seems to be similarity between performance based and geographic routing , however with gerographic routing you have custom options to create your own rule to redirect the traffic. 
		 
		 Using Geographic-Routing can be very useful if combined with performance rotuing, for example lets say we have application deployed in US , India (North South , East, West) , Brazil ,Japan, Australia. If the source is from North of India, at first layer the traffic is first filtered to India Region (Geographically routed) and in the latency table it is observed that the lowest latency is observerd from North India Deployment hence the Traffic is finally routed to the North India Deployment.
		 
		 Below diagram depicts the above scenario.
		 
		![[Nested Traffic Controller (Geographic + performance based).png]]
		
		
		 
		 