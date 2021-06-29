a way to expose a cluster to the external traffic.
------------------
Types:- 
ClusterIP - Default
Nodeport 
Load Balancers
Ingress

1. Cluster IP - Can be accessed only when combined with proxy
   Format:- 
   
   http://localhost:8080/api/v1/proxy/namespaces/default/services/my-internal-service:http/
   
   . Use Case - Only in case when you want to debug your services, generally not used for external traffic except on POC
   
  . Allowing Internal traffic for dasboard creation etc
  
  
  2. Nodeport : - opens up a port for all the nodes (30000-32768)
       all traffic sent to the node is rediected to the service 
	   
	   Downside - not cost sensitive as well as you need to manage when node IP changes

 3. Load balancer :-
     
	 an external load balancer is placed , which has a public IP external client should reach to this IP for any type if requests.
	 
	 (HTTP , UDP, TCP etc)

The big downside is that each service you expose with a LoadBalancer will get its own IP address, and you have to pay for a LoadBalancer per exposed service, which can get expensive!

pecularities of external client
-----------------------------
Network hop is required to reach the pod in case the node that receives request does not conatin the randomly chosen pod. to avoid this we can use the policy :-
	externalTrafficPolicy: Local
	
the above problem also solves the issue of client ip not reaching the service (pod).



3. Ingress:-
    Ingress is not actually a sevice it is a resource in front of a service.
	
	Ingress in a layman term can be described as a resource that distributes traffic to the service based on the request ( host and path).
	Diagram below for illustration:-

	![[30C72C4C-E2E0-40C3-B51E-2EBAA068105C_1_105_c.jpeg]]
	
	
4. Headless service:-
    When the client wanst to connect directly to the pods ip we create a healdess service (where IP is not provided)
	
	