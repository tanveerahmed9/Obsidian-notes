Hello Everyone , Today we are going to look into the resiliency options in Azure which helps in distributing traffic generated from a client the app . If an application is used throughout the globe , deploying the app in just a single location can lead to performance degradation as the user (cleint requests) can be initiated from anywhere around the world , if the distance between the app location and the user is too far it affects the performance of the application with respect to latency. There are other several factors to be looked upon when we startegies the deployment of an application which we will talk about in this post. 


**Azure Traffic Manager**

It is a DNS based tarffic load balancer which helps to disttribute traffic across regions .
It uses tarrfic routing (more on this ahead) to direct requests to the appropriate service endpoints.

There are several benefits of Azure traffic mamnager as it helps in applications availability , increase performance of the application by directing traffic to the nearest endpoint or endpoint with lowest latency.

Even for complex deployment you can use Nested traffic manager profiles (more on this later).

**Steps to create traffic manager profile:-**

below is the pictorial representaion of how the traffic manager in our demo would look like.






























BiblioGraphy:-

John Savill Video,
Microsoft documents