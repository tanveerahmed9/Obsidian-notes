Policies are set of rules defined to allow or deny a certain attribute to a resource. 

lets take an example, suppose at the leadership meeting it is decided that due to cost constraints the linux VM's built will only be on a pre approved SKU's or with a certain amount of cores , to make sure no one builds any linux VM's with the standard defined we make a policy and deny any other deployments. 

**definitions:-**
The actual json is the defination of the policies that we defining.


below is the snippet for one of the built in policy definition (Azure backp should be enabled )


![[Screenshot 2021-06-21 at 3.16.43 PM.png]]

In the above json you can see that it specifies condition on what type of resource this policy will be applied to.

explaining the conditions:-
allof - it means all the subsequents conditions should be satisfied (similar to "and" in any programming langaue)

anyof - It means any of the conditions should match (similar to or in programming terms)

As per above json snippet only those resouces are in scope of this policy which are of type Microsoft.Compute/virtualMachines and not in resource groups "databricks-rg-"

once we have the definition of the policy completed we can assign the same to any scope (subscription , MG , RG  etc).


**Initiatives:-**

An Azure initiative is a collection of policies which are grouped for a bigger goal to be achived. It generally used to coordinate a set of policies to achive a common solution.

(In programming pedagogy world it can be though of as a class (initiative) with a list of methods (policies))






