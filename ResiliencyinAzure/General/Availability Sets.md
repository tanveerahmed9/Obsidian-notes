Availability sets is one of the way we can achived resiliency in Azure , to understand more on AS we need to understand Fault Domain and Update domain.


**Fault Domain**

Fault domain is a logical grouping of hardware that share a common power supply, if the power source goes down than all the resource within that group is compromised. It can be thought of as a rack in an on-prem datacenter which shares a common power supply.

![[Fault Domain.excalidraw]]

**Update Domain**

Update domain is a logical grouping of servers that undergo same maintainance cycles (update, patch etc) within the datacenter. 

![[Update domain.png]]

As you see in the above diagram the update domain will generally be in distributed in different racks , and in a single instance microsoft makes sure that only one updated domain is patched or updated and rebooted if required .

**Availability Set**

Availability set is a resiliency concept in azure which helps in deploying multiple copies of a resource over multiple fault domains and  update domains to avoid the complete downtime of the resource.


**Steps to create an Availability Set**

1. Login to Azure Console and Search for Availability Set .
2. Once you are in the availability set click on create availability set and fill the fields as below
   
     ![[As pg1.png]]
	 
  As you can see I have provided Fault domain as 2 and update domain as 5 , you can set the values as per your requirement. (maximum  3 for FD and 20 for UD)
  
  3. Go to review and create tab and click on create. 
  
**  Steps to assign VM to an Availibility sets during Creation**

1. Search for Virtual Machine in Azure
3. Click Create--> virtual machine
4. Fill the fields as per below
![[Vm creation.png]]

Note: - 
 The the Resource Group selection should be same where the Availability set was created. 
 In the availability options value "Availability set should be selected" and then in the Availability set field the Availability set you created earlier should be selected.
 
 4. Click on next and let there be default values for all other field click on create .
 5. Once the Vm deployment is completed you can actually see the VM in the Availability set in the virtual machine section .
   
   ![[VM in AS.png]]
   
   To summarise below is the pictorial representation of how the a VM deployed in AS would look like.
   
   ![[Availability sets demonstration.png]]
   
   
   