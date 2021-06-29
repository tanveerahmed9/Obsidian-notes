Azure Governance - The azure governance is a set of azure functionalities that helps in making  set of rules for maintating the way azure environment is handled.

For example - The Azure operator can make a policy on how a virtual machines are deployed (rules around locations, SKU's etc), or an RBAC rule which defines which set of groups has access to what set of resources and on what levels.

There are several services available at Azure's disposal to take of governance :-

1. Policies
2. RBAC
3. Budget tools
4. Blueprints
5. ARM


Management Group --> Management groups is used to oraganise the subscriptions of an organisation , lets say that we have 5 subscriptions of an organisation namely Dev , Networking , Staging , prod and external, with MGs we can group them together with parent child relationships (not more than 6 layers deep) and  apply policies at root or immediate parent or any other parent for that matter which will enforce the applied policy to all the subsequent child enitity be in MG or Subscription. 


         obsidian://open?vault=AzureGovernance&file=Untitled~9F1BC7BF-327D-4E61-8CBB-225D5733B293.animatedoc%2FThumbnail.png


