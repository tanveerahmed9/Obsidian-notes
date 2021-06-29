use  

livenessProbe in the spec to add monitoring to the pods

https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/

Creating effective liveness probe:-

use \health in the path 

readiness probe :-

Lets say a pod crashed due to some reason (internal or external)  and a new pod comes up . It might take some time for the pod to be ready to accept requests, however load balancer (or Ingress) would not know if the pod is ready to accept request yet or not . To make sure the pod only recieves request when it is ready we use Readynessprobe property .

Type of Readiness probes:-

Exec
Http
tcp 

Explanation for them similar to Liveness probe





