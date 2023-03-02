# Testing Methods

There are different types of testing, such as [Load Testing](LoadTesting.md) or  [Stress Testing](StressTesting.md). Here will explain how to execute those tests more practically and point out different methods for different examples.



### API load testing 

API load testing is often used to test smaller components of an application that uses APIs or a self hosted API itself. The base idea is to write smaller scripts that generate a high traeffic and therefore simulate a high usage by potential visitors of said website. [2] [1]

It is usually best to start testing smaller isolated components first by doing alot of requests that would be sent to the server when for example a certain button on the website is pressed [1].

End-to-end tests are always possible afterwards but will not be part of this scientific work since it would be to extensive.

In the context of a Kubernetes environment we have different components, that communicate with each other using API-Requests, therefore API load testing is always a good and cheap options to test Kubernetes clusters.

The goal here is to test the API responsiveness and the Network traeffic.



### API stress testing

Basically the same thing that applied to API load testing also applies to API stress testing. Just the goal is different, with stress testing we really want to find out when our cluster breaks. [3]

The goal here is to find hwo much a system can handle and how it behaves during recovery











## Sources:

[1] https://k6.io/docs/testing-guides/api-load-testing/

[2] https://www.flood.io/blog/what-is-api-load-testing

[3] https://k6.io/docs/test-types/stress-testing/
