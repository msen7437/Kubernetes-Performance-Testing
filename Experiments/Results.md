# Results

Here are the results from the [tests](LoadTesting.md) documented. 



### Capacity:

- The hosted API is able to receive about 200 requests per second before generating the first failures
- 250 requests per second is the breaking point of our cluster - every request is an error



### Latency:

- Until the API reached its breaking point the latency kept rising
- After reaching its breaking point the latency dropped, because sending out failures is faster than sending out database values.



### Resources:

- The API and the Database took one entire CPU core during the test
- RAM Usage and network traffic was low therefore the Pod was not OOMkilled



### Reasons:

- The API did not use the entire CPU power of a node
  - The Applications on the cluster are not scheduled in a balanced manner
  - A lot of Pods were running on the same node



### Solutions:

- Setting proper scheduling rules
- Scaling up (creating replicas in free nodes)