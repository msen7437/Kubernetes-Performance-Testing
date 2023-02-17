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







## Sources:

[1]  https://www.datadoghq.com/blog/monitoring-kubernetes-performance-metrics/

[2] https://medium.com/@bregman.arie/18-kubernetes-metrics-to-monitor-for-optimal-cluster-performance-ca9458869e52