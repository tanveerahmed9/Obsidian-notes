Topic:-

Alternative to application gateway


Trafeik with NGINX  vs App gateway vs F5 load balancer


Topic
---
Ingress
Service vs Ingress
Ingress controllers
Types of controllers
host vs path Ingress
SSL termination


Projects
---
 Using an Ingress controller and resource to access two different app on kubernetes using Ingress and TLS
 
 Secure your app using Ingress and TLS
 
 Using Cert-Manager to issue and renew certificates for your app in kubernetes
 
 
 
 
 Ingress:
 ---
 
 Route http/https traffic outside the cluster , into a service using rules defined in the manifest
 
  Path based routing -> backend path to the service
  
  
  . Single external URL
  . Include SSL
  . layer 7 load balancer built - in
  . Uses existing K8s resource types
  
  
  
  Ingress Controller - if you dont create ingress controller at all , ingress wont work.
  
   Nginx most popular as Ingress controller
   
   
   TrarfiK also used as an ingress controller
   
   
   . Contains configMap , Service Account and Roles
   
   . Deployed as a deployment and service
   
   
   SSL termination:-
   ---
   
   HTTP to HTTPS
   
   
   
   Secret -> Cert and private Key (buy the certificate from a trusted provider)
   
   TLS vs SSL ?
   
   
   
   NGINX can be used in place of Application Gateway as well
   
   Trafeik can also be used
   
   
   https://kubernetes.github.io/ingress-nginx/examples/tls-termination/
   
   
   Only solution that I can think of is using NGINX instead of App gateway (If we do not want to use app gateway for any reason whatsoever)
   
   
   Surajit - actual deployment
   ITSOM - support infra
   Architect - Some time
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
  
  
  
  
  
  
  
  
  
  
  
 
 
 
 
 





