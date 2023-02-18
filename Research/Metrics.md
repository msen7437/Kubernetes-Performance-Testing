# Metrics

Here are a couple important Kubernetes metrics listed. They help us to determine the health and performance of a Kubernetes cluster.



### Node Level:

Node-Level-Metrics are used to check the health of Nodes	

1. #### Node Memory Pressure:

   - Metric that lets us determine the memory consumption of a Node [2]

   - It lets us prevent unnecessary evictions in case of a high memory usage

     

2. #### Node CPU Utilization:

   - This metric allows us to determine the CPU usage of a Node [2]

   - It is important if we have sensitive applications/pods running on a node with high CPU utilization

     

3. #### Node Disk Pressure:

   - Monitors disk space on Hard Drives, to avoid potential issues [2]



4. #### Network In and Out:

   - Helps us determine the current state of our clusters network traffic [2]
   - A lack of traffic or too much traffic may indicate  that our application is not running the way it should



### Deployment Level:

Deployment-Level-Metrics are used to check the health of Deployments.

1. #### Pod creation rate:

   - Helps us to determine how quickly Deployments are able to scale up [2]

   - Helps us identify scaling issues

     

2. #### Pod deletion rate:

   - Helps us to determine how quickly Deployments are able to scale down [2]
   - Helps us identify scaling issues

   

### Pod Level:

Pod-Level-Metrics are used to check the health of Pod.

1. #### OOMkilled Pods

   - Number of Pods that got killed because of exceeding its memory limits [2]

     

2. #### Pod States

   - There are different states of pods:

     - Running

     - CrashLoopBackOff

     - Pending

     - ...

       

3. #### API-Responsiveness

   - A metric  that defines one of Kubernetes performance goals [3]
   - A lot of Kubernetes pods and services communicate using API requests, therefore the Responsiveness of those APIs is also an indicator for Cluster performance



4. #### Pod startup time

   - If a pod takes along amount of time to start it may indicate performance issues [3]

     

​			2.1.3.1 OOM-killed Pods

​			2.1.3.2 Pod States

​			2.1.3.3 API-Responsiveness

​			2.1.3.4 Pod startup time

​			2.1.3.5 Pod Creation Latency

## Sources:

[1]  https://www.datadoghq.com/blog/monitoring-kubernetes-performance-metrics/

[2] https://medium.com/@bregman.arie/18-kubernetes-metrics-to-monitor-for-optimal-cluster-performance-ca9458869e52

[3] https://kubernetes.io/blog/2015/09/kubernetes-performance-measurements-and/