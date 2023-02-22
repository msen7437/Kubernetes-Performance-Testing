# Stress Testing



"Stress Testing is a type of load testing used to determine the limits of the system. The purpose of this test is to verify the stability and reliability of the system under **extreme conditions**." [1]



- Helps us to determine the maximum user or rthroughput capacity of the cluster
- Lets us identify the breaking point of the system and shows us the behavior of the system after a failure 
- After the system failure we can simulate the behavior of the systems recovery and identify other issues during the recovery and also determine Disaster Recovery Measurements such as Mean Time To Recovery (MTTR) [2]



The difference between [Load Testing](LoadTesting.md) and Stress Testing, is that Load testing wants to identify problems that come up after a sudden increase in requests while stress testing wants to identify the breaking point of a cluster. [3] [1]



## Sources:

[1] https://k6.io/docs/test-types/stress-testing/

[2] https://www.comptia.org/blog/disaster-recovery-measurements

[3] https://www.techtarget.com/searchitoperations/tutorial/Kubernetes-performance-testing-tutorial-Load-test-a-cluster