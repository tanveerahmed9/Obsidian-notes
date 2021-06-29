Labels are key value pairs assigned to a pod for organising large number of pods .

Lets say in a Microservices architecture we have frontend, backend and web API, all these will have there own replicas (generally Dabase has more replicas , more on that)

While Creating a pod through Yaml we specify one more labels to it . example below

	 

apiVersion: v1
kind: Pod
metadata: 
name: kubia-manual-v2
labels:
    creation_method: manual
    env: prod 
spec:
  containers:
  	- image: luksa/kubia 
  name: kubia
 ports:
    - containerPort: 8080 
protocol: TCP


