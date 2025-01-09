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

### 11. What is a data type in Jenkins?
---
### 12. How can I upload my plugin into Jenkins?
---
### 13. What is the difference between GitHub webhook and Poll SCM in Jenkins?
---
### 14. In Python, what is the difference between mutable and immutable objects?
---
### 15. What is the subprocess module?
---
### 16. What is Boto3?
---
### 17. How many ways are there to create a Lambda function?
---
### 18. Display the unique numbers in the list `[1, 2, 3, 2, 5, 6, 5, 4, 1, 3]`
---
### 19. What kind of backups does Velero store?
---
### 20. What is a rollout restart?
---
### 21. What is the difference between `kubectl get events` and `kubectl describe pod`?
---
### 22. What is the difference between a liveness probe and a readiness probe?
---
### 23. What does "terraform local-exec" do?
---
### 24. What is the null_resource in Terraform?
---
### 25. What are addons in Terraform?
---
### 26. "When a Terraform file becomes corrupted, how can you restore it?"
---
### 27. "In two environments, production and development, I have the same set of files. However, in the production environment, I don't want to create a database, but in the development environment, I want both an EC2 instance and an RDS instance. How can I ensure that only the EC2 instance is created in the development environment while both the EC2 instance and RDS instance are created in the production environment?"
---
### 28. What is count in Terraform?
---
### 29. "For example, let's consider an EKS cluster and a node group. In Terraform, there are separate configurations for creating the EKS cluster and the node group. When running `terraform apply`, the process fails with an error stating that the EKS cluster is not active. How can this issue be resolved?"
---
### 30. What is terraform graph?