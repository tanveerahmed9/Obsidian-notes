Pods are ephermeral.
when pods are deleted or shutdown the data associated witn the pods also dies, to make sure the data is intact and the next pod which is created can use up the data we create a persistent volume (PV) in Kubernetes.

below diagram represents how PV in kubernetes is configured ans used. 

[[persistent storage demonstration]]

Storage Class?
When we create a storage class resource we do not think about the persistent volume infra, rather we can specify the resource (Azure files, Azure Disk, vsphere, AWS EBS etc) and the volume will be created and allocated automatically.

https://kubernetes.io/docs/concepts/storage/storage-classes/ for more infor refer the link here

In case of storage class resource , we do not have to worry about the storage infrastructure the cloud provider is going to create the required storage for us.



