K8s.

It is a container orchestration tool used to manage the lifecycle of the pods (including networking , deployment strategy etc).


Architecture:-

Control Plane (Master)
Worker Nodes (the compute node where pods are deployed)

Control Plane:-

![[Control Plane architecture.png]]

   **API server**
   
   API server :-
   Scheduler:-
   Control manager:-
   Etcd:-
   
  
   
**Main resources**
   
PODS:- Basic Deployable unit of K8s. It contains one or more containers which shares storage and networking.

Deployment:- Maintains the desired state of the Pods (number of pods , deployment nodes etc)

Services :- Helps in exposing the pods for outside clients



Service accounts 

Service Accounts are the accounts that is used for authentication. 

Roles:-
A Role is an entity which is provided permission to perform a list of activties (For Example a Reader, R/W , Admin etc).

Role binding :- It is the association of a role with a resource (for example associate reader roles with a Pod resource)

Cluster Roles:- Similar to roles, only that they are not limited to a Namespace



Certificates:-

https://kubernetes.io/docs/setup/best-practices/certificates/














