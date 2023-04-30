# Q3: Please describe a system you deployed in production that had performance issue and how you diagnosed and optimized the performance

I've installed Graylog cluster to catch log from our microservices. First everything was fine but one day the log timestamp on dashboard later that the timestamp of the real log. We want to our graylog can be able to have latest log as real time system so that 5min log timestamp delay is unacceptable for us. Graylog is a good fit for debugging microservice in production in that time especially for on-premise system:

![Diagram](img/q3-1.png)

Debugging follow these step:
1. Check resources: As usual ElasticSearch cluster hunger for Ram as usual for better performance. I wrote a mini script to index sample data directly to ElasticSearch without go through Graylog or Load Balancer. The index still immediately show up when I query => This is not the main issue
2. The MongoDB only use for storing meta information and configuration data and doesn’t need many resources => Not the root cause too
3. Check from the Load Balancer, HA Proxy log not have any suspects log. Resources not consume too much in node and the dashboard look good => Not the issue
4. Now to the Graylog, same for 3 components above. Resources not hung too much, but weird stuff show up when I try to push sample logs: 2 nodes get it very fast and log pump up right after that on Graylog dashboard, except for the last node. It take 5mins after that to appear on the board => This node is the main reason
5. How to check it ? Log as usual don't have any things matter, compared configuration file this node to 2 other nothing different. Resources not matter too so I started check the network, Iperf to test bandwidth between Load Balancer with both big packet and small packet still good. So what happen here? I realized the time on the VM is late than global time 5 min, so when we access the dashboard through the Load Balancer, it's bind to this delay node as the main node and not routing to another node. After setup the HA proxy to routing between 3 node graylog and fix the time issue, the log not delay anymore.

I realized that sometime the issue not just come from some casual reason as usual like resources, misconfig or network. It may come to some unexpected aspect that we barely aware about it like environment, so we need to have an open mindset to debug issue.