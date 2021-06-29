How Conatiners Isolate themselves even though they are using same VM resource?

1. Linux Namespaces - It makes sure that each process sees its own view of the system resource (files, process, network etc)
2. Linux Control Groups - Limiting resource consumption


Following Kind of Namespaces exists:-

 Mount (mnt)  Process ID (pid)  Network (net)  Inter-process communication (ipc)  UTS  User ID (user)


Kubernetes Architcture

![[General Architecture Kubernetes.jpeg]]

/Users/tanveerahmed/Library/Containers/com.docker.docker/Data/vms/0/data

