# Q2: Please describe a service or front end application that you created and how you made it secure and/or performance

Normally every company must have at least one website where the customers are able to reach to understanding about that company. That's a part of business but also a challenge for engineer team, company's homepage is where people rate how professional and strong a company is (no big company has a bad homepage). With just 0.01s of latency could make big different experience for customer and they can easy imagine how our business related to the company website. 
<br/>

To prevent all of incident could happen to company website and the best experience for our customer, this is few note that we mind to have the best practice:

| No| Performance               | Durability        | Security      |   |
|---|---------------------------|-------------------|---------------|---|
| 1.| Optimize everything       | High Availability | Monitor       |   |
| 2.| Optimize database         | Fault Tolerance   | Alert         |   |
| 3.| Handle workload           | Disaster Recovery | Action        |   |

For example: about the homepage of 2 last companies. We use many different methods to have the highest SLA/SLO:
1. Performance:
- We optimize everything in our system (code, database, network, etc...)
- Always functional/ non functional test before release
- For any reason homepage must be able to handle high resources consumption. We use auto scaling in both way vertical(resources) and horizontal(instances)

2. Durability:
- We have at least 2 clusters for service in production environment just in case (only core components need to be in mirror cluster).
- Using load balancing to distribute traffic, also prevent downtime when incident happen with 1 cluster
- Automatically and manually react with incident: system needs to be back to normal state as fast as possible, auto restart service/instances whenever it down nor engineer aware of incident as soon as possible to react with it.

3. Security:
- We monitor site 24/7 with Datadog, every single metric that is meant for our durable website we will collect and set up alert for anomaly event
- Minimum attack surface: always scanning and patch any potential issue via scanning/patching tools (ex: Snyk for code scanning, ocs inventory for scanning/patching packages/os, etc...)
- Setup policy to prevent both external and internal security risk