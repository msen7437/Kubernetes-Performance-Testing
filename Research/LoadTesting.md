# Load Testing



Load Testing in Kubernetes context describes a process where the applications hosted in a kubernetes cluster are experiencing a lot of sudden requests wich are generated by the testing persons, to figure out how the cluster would behave in similar scenarios. [2]

It is crucial to determine the performance and load capacity of the applications run in that cluster. [1]

The testing process depends on the applications run on that cluster and on the cluster structure itself. For database applications the optimal way to load test would be to run alot of scripts at the same time and therefore making alot of requests to the hosted datebase server, for web applications the best way to increase the number of requests is by generating alot of requests on the HTTP or HTTPS ports of that application.

To generate alot of requests on those two examples, there are actually alot of different [Methods to test applications on a cluster](TestingMethods.md).



## Sources

[1] https://speedscale.com/kubernetes-load-testing/ 

[2] https://www.techtarget.com/searchitoperations/tutorial/Kubernetes-performance-testing-tutorial-Load-test-a-cluster