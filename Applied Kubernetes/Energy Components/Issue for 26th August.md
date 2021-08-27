
Could not connect ACR from Kubernetes cluster


 
try this:-


az aks update -n handsonaks \
        -g rg-handsonaks --attach-acr <acrName>
	
	
	https://docs.microsoft.com/en-us/azure/container-registry/container-registry-troubleshoot-login
	
	
	https://docs.microsoft.com/en-us/azure/container-registry/container-registry-health-error-reference
	
	https://docs.microsoft.com/en-us/azure/container-registry/container-registry-troubleshoot-login
	
	
	