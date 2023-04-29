# Q5: Have you created a reusable module that was packaged in npm or pip like package repository? What was the reusable module and how was it used by your org or open source community?

## NPM/PIP for packaged tools
---
### I've already built a CLI tool based on TypeScript. It's about helping developer reduce their time configuring kubernetes to switching between multiple clusters. We have several clusters across AWS and GCP so every time developer wants to use `kubectl` command they would take time to re-config parameter/config file point to new clusters again. We packed our source using npm so when new Developer join our team, they just need to own an account to access our npm organization repository and install whole tool with single command `npm -g install <@org_name/tool_name>` 
<br/>

## NPM/PIP for packaged tools
---
### We also built the core CI/CD, Infrastructure provisioning around Jenkins and Terraform. We create an dynamic library using Groovy for Jenkins so we can standardize our pipeline by coding. That's much easier to manage and reduce re-creating new Jenkins manifest file for the same stuff(), we only have to import, reuse those function and Jenkinfile which are used as an entrypoint, same as the platform we optimize and manage them by using IaC tools (Terraform, Pulumi) to structuralize them in the OOP as much as possible.