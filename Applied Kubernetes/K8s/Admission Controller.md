. It is done after the authetication and authorisation process
. This stage is bypassed in case of Read operation (since authentication and authorisation takes care of that)
. Refer Chapter 16 of admission controllers for advanced controlling


It is a component of the kubernetes which intecepts all calls to the kubernetes API server and makes sure that the desired rules are met before reaching the API server.

Majorly two components are useful controller which can be used because of their flexibility :- Mutating admission webhook , Validating admission webhook


In Chapter 16:-


Admission Controller diagram illustrated , now it is time to go through CNCF for more details.

Mutating admission controller :- Modifies the request before getting applied to the K8s.

Validating :- Validates the request and either accepts/rejects the call to the API server.

You can control what all default AC's to enabled or disabled while creating a cluster.


Default admission controllers

Some important ones are :-
1. NameSpaceLifecycle
2. LimitRanger
3. PersistentVolumeLabel
4. DefaultStorageClass
5. DefaultTolerationSeconds
6. ResourceQuota
7. Priority
8. **MutatingAdmissionWebhook**
9. **ValidatingAdmissionWebhook**




CertificateApproval, CertificateSigning, CertificateSubjectRestriction, DefaultIngressClass, DefaultStorageClass, DefaultTolerationSeconds, LimitRanger, MutatingAdmissionWebhook, NamespaceLifecycle, PersistentVolumeClaimResize, Priority, ResourceQuota, RuntimeClass, ServiceAccount, StorageObjectInUseProtection, TaintNodesByCondition, ValidatingAdmissionWebhook


Creating Custom admission controllers:-




Mutating Admission Webhooks- Adhere to policy and complicance using these webhooks


**Open Policy Agent:-**

CNCF hosted Sandbox project
General purpose policy engine
can be used across the stack
Declarative policy language (Rego)


NamespaceLifecycle AC -> For handling Namespace related policies, for example when a Namespace is being terminted and the request which comes to kubernetes API is trying to create a pod in that particular namespace , it blocks the requests and denied.
 
 
 
 Use cases for Mutating and validating webhooks:-
 
 Allow pulling images only from specific registries
 Replica count emforcement
 Lagel validation
 Inject Environment setting
 SideCar Injection
 Adding Resource Limits :- This could be helpful in maintaining the overall budget of the project. Make that use case available in the article
 
 
 Steps to create Admission Controllers:-
 
 1. Create a Kubernetes Cluster
 2. Create a TLS certs.
 3. Create Webhook Configuration


How Source Code would look Like:-
 
 1. DockerFile - 
    
	FROM golang:1.15-alpine as dev-env
	WORKDIR /app
	
2. 




 
 
 
 









