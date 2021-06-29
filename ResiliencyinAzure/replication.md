
Asynchronous vs synchronous replication:-

![[Async vs sync replication.png]]

**Async**
If you look at the above diagram , in case of synchronous 
(workflow marked in green) the once the client sends a request for data change , the change takes place immediately and then the data is replicated to a secondary location (generally in different region) . 

1. No impact in performance as the acknowledgement is sent back to the client immediately before doing replication.
2. Risk of Data loss in case of unplanned outage


**Sync**
In case of synchronous replication the data is first replicated to a different database (generally in the same location to avoid latency) and then the acknowledgemnt is sent back to the client as demonstrtaed with red workflow.

  1. Can imoact performance
  2. No risk of data loss even in unplanned outage to one location

The diagram Async vs Sync Replication represents the correct way.