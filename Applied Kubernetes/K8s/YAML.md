
**structure**:


**mandatory**:-
apiVersion:apps/v1,v2
Kind: Pods, Deployment, Service,Infress
spec:


example:-

apiversion:apps/v1
Kind: Deployment
metadata:
	labels:
		app: nginx
		name: nginx
spec:
replicas: 1 # count of the pod to be maintained
selector:
	matchLabels:
		app:nginx
template:
	metadata:
		labels:
			app:nginx
	spec:
		containers:
		- image: nginx
		  name: nginx
		  
		  
		



To create a deployment yaml or any basic yaml , you can use below strcuture of a command


kubectl create deploy nginx --image nginx  --dry-run=client -o yaml > deploy.yaml



