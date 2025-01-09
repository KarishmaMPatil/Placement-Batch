# Scenario-Based Interview Questions

### Kubernetes and AWS Integration
1. **EKS and Secrets Manager**: Suppose you have an application deployed inside EKS, and your application needs some secrets to run. These secrets are stored in the Secrets Manager service in AWS. How will you provision this so that your application can access those secrets and configurations?

2. **Highly Available Database in Kubernetes**: Suppose you have a database that needs to be deployed on Kubernetes, and it needs to be highly available. How would you achieve that?

3. **Database on Specific Node in Kubernetes**: Suppose you have a situation where your database needs to run on a specific node in Kubernetes and be highly available. How would you achieve that?

### Terraform
4. **Terraform Local**: What is Terraform local?

5. **Managing Multiple Environments with Terraform**: Suppose you have a situation where you have three environments: prod, staging, and dev. All of these environments have similar services; the only difference is the specifications of these services. For example, development has lower-spec machines compared to production. How would you manage this kind of infrastructure using Terraform, and how would you manage the state file?

6. **Domain Structure in Route 53**: Suppose you have a system with an apex domain abc.com and multiple environments such as dev.abc.com and prod.abc.com. Additionally, there are multiple subdomains for each environment, such as api.dev.abc.com. How would you structure this kind of system in Route 53?

### Kubernetes Load Balancing
7. **Load Balancer vs. NodePort**: Where would you use a Load Balancer and a NodePort in a Kubernetes cluster?

### AWS Concepts
8. **AMI Creation**: Why can't you create an AMI from stopped instances?

### Jenkins
9. **Shared Directory**: What is a shared directory in Jenkins?

10. **Parameters in Jenkins**: What are parameters in Jenkins?
