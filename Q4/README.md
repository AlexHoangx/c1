# Q4: Please describe a system that you had to develop to real paying users and what were some technical challenges you had to solve?

### With experience serving thousand of user at same time in sale season, there's always hard time to calculate between minimum cost of scale, durability of our system. It takes too much cost to spend on scaling solution without knowing where the weakest point in our system could lead us to not have a efficiency system.
<br/>

### But here is few step for the preparation for the customers best experience (at minimum delay) when they use our site:
1. Measure/tracking/alert everything as possible with monitoring system
2. Auto-scaling is a must in our design.
3. LoadBalancing and 
4. Cache to reduce workload
5. Bench our system and extend resources higher than it's limited 20% as a contingency measure

<br/>

### Also this is few step I always look for when troubleshoot issue for fastest recover with incident:
1. Delineate an area for investigation, smallest scope by how it's affected and the 