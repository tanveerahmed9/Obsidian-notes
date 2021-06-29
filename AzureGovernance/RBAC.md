RBAC or role based access controls the way  users or groups has access over a resource 

Access can be provided in both management plane as well as data plane.

Most common example of allowing RBAC at data plane is when we are dealing with storage accounts.

understanding  roles defined at data plane vs roles defined at management plane

**Properties of role definition**

1. name - name of the role
2. Id - Id of the role
3. IsCustom - whether builtin or custom
4. Description - Description of the role defined by the creator
5. Actions[] - array of management actions allowed for this role
6. NotActions[] - array of management actions not allowed for this role
7. DataActions[] - array of data actions allowed for this role
8. notdataactions[] - array of data actions not allowed for this role
9. AssignableScope[] - scope at which the role is assigned to (subscription , MGs, RG etc)


	DataActions -
	
	DataActions are the list of role attributes which specify the permission at the data layer , for example reading the message of queue , reading the blob container etc . 
	
	Below examples are some of the DataActions that are used while defining the dataactions (or notdataactions).
	
	
	 "Microsoft.Storage/storageAccounts/blobServices/containers/blobs/read"
	 
	 In the above action the access is provided to read the blobs storage which is a data layer .
	 
	 Actions (Management):-
	 
	Actions[] represnets set of roles which allows or denies access to a resource at management layer , below are the examples of management layer actions.
	
	 `Microsoft.Storage/storageAccounts/blobServices/containers/read`
	  `Microsoft.Storage/storageAccounts/blobServices/containers/write`
	  
	  if you look into the path of the action it gives access to read or write the to the containers which is a management layer as there are no data associated with it directly .
	  
	   Note:-To Understand more on Azure storage and the data and management layer concept refer Link.
	  
	  So to sum up net role can be thought of as the substraction of roles in action (or dataaction ) with the notaction (ornotdataaction)
	  
	  
	  
	  
	  
	  
	  
	  
	  
	  
	  
	  
	  
	  
	
	
	
	
	
	
	
	Bibliography
	
	1.  https://docs.microsoft.com/en-us/azure/role-based-access-control/role-definitions for reference
	2.  John Savill Youtube
	3.  my own experiment with free account
	 
	 

