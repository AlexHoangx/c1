# Q2: Please describe a service or front end application that you created and how you made it secure and/or performance

Normally every company must have at least one website where the customers able to reach to understand about that company. That's apart of business but also a challenge for engineer team, company's homepage is where people rating how professional and strong of a company (no big company have a bad homepage). With just 0.01s of latency could make big different experience for customer and they can easy imagine if how our business related to the company website. 
<br/>

To prevent all of incident could happen to company website and the best experience for our customer, this is few noted stuff that we can mind about to have the best practice:

| No| Performance               | Durability        | Security      |   |
|---|---------------------------|-------------------|---------------|---|
| 1 | Optimize everything       | High Availability | Monitor       |   |
| 2 | Optimize database         | Fault Tolerance   | Alert         |   |
| 3 | Handle workload           | Disaster Recovery | Action        |   |

For example for the homepage of 2 last company. We use many different method to have the highest SLA/SLO:
1. Performance:
- We optimize everything in our system (code, database, network, etc...)
- Always functional/ non functional test before release
- For any reason homepage must be able to handle high resources consumption. We use auto scaling in both way vertical(resources) and horizontal(instances)

2. Durability:
- We have at least 2 cluster for service in production environment just in case (only core component need to be in mirror cluster).
- Using load balancing to distribute traffic, also prevent downtime when incident happen with 1 cluster
- Automatically and manually react with incident: system need to be back to normal state as fast as possible, auto restart service/instances whenever it down nor engineer aware of incident as soon as possible to react with it.

3. Security:
- We monitor site 24/7 with Datadog, every single metric that have meaning for our durable website we will collect and setup alert for anomaly event
- Minimum attack surface: always scanning and patch any potential issue via scanning/patching tools (ex: Snyk for code scanning, ocs inventory for scanning/patching packages/os, etc...)
- Setup policy to prevent both external and internal security risk