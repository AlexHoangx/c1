# Q7: Describe an incident response that you had to own and deliver post mortem. What was the root cause?

For the first time use Kubernetes, base on the business I need to work on-premise system. We use VSphere as the core Virtualization to manage resources across physical infrastructure, in that time we have over 250 instances working 24/7 to serve customer out of 300 instances. When we moving from traditional way manage our microservices(directly install each services to instances, install agent on each instance to monitor) to orchestration platform(Kubernetes). My life as an engineer in that time never few better when using K8s manage services/resources but the horrible thing come up just in 1 year after that. 

### How the bad thing happen ?
That was summer vacation for whole company. We enjoined the weather, food, vibe on our trip, then the notification come up on our Slack in the middle of fun direct us from fun to hell zone.
1. The log said half of our microservices unreachable to the internet
2. We can't use kubectl to check what happened with our cluster
3. Kubelet keep failed even thousand of time to reset. The log on system at that time very obfuscating and hard to detect root issue


### How I solved it 
1. I remembered that's I read the documentation of K8s before that said the K8s not have automation method to renew certificate if we build from scratch. But in that time I just finished install it so I just mention to our leader about that and we too busy to mind about it when just finished install.
2. I checked log of the kubeadm, gotcha the main reason come from here:
```
[authentication.go:64] Unable to authenticate the request due to an error: 
[x509: certificate has expired or is not yet valid, x509: certificate has expired or is not yet valid
```
3. So because of our certificate expired, K8s worker unable to initial TLS connection to the control plane. That lead to tons of our microservice cannot resolve domain name through CoreDNS.   
4. Because we not using 3rd party to manage K8s, that's so 
5. After that issue, we wrote some small script on the master node to regularly check Certificate of the cluster. It will automatically remind us if the expired date come in the next 3 month, 1 month and massive notification spam if the Certificate still not renew in less than the last 1 week.