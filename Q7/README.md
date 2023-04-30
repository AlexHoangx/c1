# Q7: Describe an incident response that you had to own and deliver post mortem. What was the root cause?

For the first time I used Kubernetes, based on the business I need to work on-premise system. We used VSphere as the core Virtualization to manage resources across physical infrastructure. In that time we had over 250 out of 300 instances working 24/7 to serve customers. When we moved from traditional way to manage our microservices (directly install each services to instances, install agent on each instance to monitor) to orchestration platform (Kubernetes).  My life as an engineer was never better when using K8s manage services/resources but the horrible thing come up just in 1 year after that. 

### How the bad thing happen ?
That was the company's summer vacation. We enjoined the weather, food, vibe on our trip, then the notification come up on our Slack in the middle of fun directing us from fun to hell zone.
1. The log said half of our microservices were unreachable to the internet
2. We couldn't use kubectl to check what happened with our clusters
3. Kubelet kept failed even thousands of time to reset. The log on system at that time very obfuscating and hard to detect root issue


### How I solved it 
1. I remembered that I read the documentation of K8s before. It said the K8s didn't have automation method to renew certificate if we built from scratch. But in that time I just finished installing it so I just mention to our leader about that and we were too busy to mind about it after installing.
2. I checked log of the kubeadm, got the main reason come from here:
```
[authentication.go:64] Unable to authenticate the request due to an error: 
[x509: certificate has expired or is not yet valid, x509: certificate has expired or is not yet valid
```
3. So because of our certificate expired, K8s worker was unable to initialize TLS connection to the control plane. That led to tons of our microservices couldn't resolve domain name through CoreDNS.   
4. Because we not using 3rd party to manage K8s, that's so 
5. After that issue, we wrote some small script on the master node to regularly check Certificate of the cluster. It will automatically remind us if the expired date come in the next 3 month, 1 month and massive notification spam if the Certificate still not renew in less than the last 1 week.