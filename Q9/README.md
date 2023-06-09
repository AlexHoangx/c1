# Q9: Please describe your experience in unit test, functional test, integration test, end to end test, regression test, penetration test, and load test that you have automated and developed. Please describe the business logic involved, what language, framework and tools you used.

## Topology
---
![High level diagram](img/q9-1.svg)
</br>

## Business logic
---
The test team expected a pipeline that could help them setup NFT(Non Functional Test) and extendable to benchmark our website. They wanted to virtualize thousand of user access and use features of our page at the same time, verify that all of the features work well and test the durability of the system til it reaches limit. After that, report of test case needed to be published on our Confluence to track the performance of our system. When all of the test had been done, all resources initialized for the test needed to be teardown to reduce unnecessary costs.
![Logic flow](img/q9-2.svg)
</br>

### Platform/Tools/Framework: GKE, Java, JMeter, Redis, InfluxDB, Prometheus, Confluence, Jira