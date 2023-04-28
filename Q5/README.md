# Q5: Have you created a reusable module that was packaged in npm or pip like package repository? What was the reusable module and how was it used by your org or open source community?

## NPM/PIP for packaged tools
---
### I already built a CLI tool based on TypeScript. It's about to help developer reduce their time to config kubernetes to switching between multiple cluster. We have several cluster across AWS and GCP so every time developer want to use `kubectl` command they would take time to re-config parameter/config file point to new cluster again. We packed our source using npm so when new Developer join our team they just need to have an account to access our npm organization repository and install whole tool with single command `npm -g install <@org_name/tool_name>` 
<br/>

## NPM/PIP for packaged tools
---
### We also built the core CI/CD, Infrastructure provisioning around Jenkins and Terraform. We create an dynamic library using Groovy for Jenkins so we can standardization our pipeline in the code way. That's much easier to manage and reduce re-create new Jenkins manifest file for the same stuff(), we just need to import, reuse those function and Jenkinfile only use as an entrypoint. Same as the platform we optimize and manage them by using IaC tools (Terraform, Pulumi) to structuralize them in the OOP as much as possible.