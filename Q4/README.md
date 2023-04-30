# Q4: Please describe a system that you had to develop to real paying users and what were some technical challenges you had to solve?

With experience serving thousand of users at the same time in sale season, there's always hard time to calculate between minimum cost of scale, durability of our system. It takes too much cost to spend on scaling solution without knowing where the weakest point in our system could lead us to not having an  efficient system.
<br/>

### But here is few steps to prepare for the customers best experience (limit risks and achieve outstanding performance) when they use our site:
1. Measure/tracking/alert everything as possible with monitoring system
2. Auto-scaling is a must in our design
3. Load Balancing to distribute incoming traffic
4. Cache to reduce workload pressure on our Database
5. Bench our system and extend resources higher than it's limited 20% as a contingency measure
6. Setup disaster recovery, fault tolerance and high availability design

<br/>

By following all above steps, we have achieved our system can handle nearly thousand request per second due to the black friday:
- We placed CDN at high income traffic region
- Internal cache using Redis to reduce load to our database
- Auto scale for high load service, we set Horizontal Pod Autoscaler to our microservice so it is more flexible to handle job
- We increased resources to 20% on each instances serve for our core product(DB, cache, ...)
- Our monitoring system with SRE team are ready to any incident could happen just in time