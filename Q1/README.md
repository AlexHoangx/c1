
# Q1: Please share your github link and example projects that demonstrate your expertise

## Security Platform Provisioner
This project aims at automatically building a lab for security practice in simple way using on-premise system. This project is written by python, using SDK and Network framework to connect with each endpoint.

As we know GNS3 is a Networking Virtualization platform provide us environment to bring up a network same as in practice. 

*Noted I haven't evolved any kind of IaC tools or Configure Management tools yet because they didn't support well for platforms I used at this time* 
<br/>

### Diagram
![High level](img/Crawling_system.svg)

<br/>

### Structure of the project:
```
├── src
│   ├── controller
│   │   ├── **/*.css
│   ├── views
│   ├── model
│   ├── index.js
├── public
│   ├── css
│   │   ├── **/*.css
│   ├── images
│   ├── js
│   ├── index.html
├── dist (or build)
├── node_modules
├── package.json
├── package-lock.json 
└── .gitignore
```
<br/>

### TechStacks
GNS3, QEMU, Python, Nodejs, NginX