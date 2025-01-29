### Scenario-Based Interview Questions

**1. Suppose you have an application deployed inside EKS, and your application needs some secrets to run. These secrets are stored in the Secrets Manager service in AWS. How will you provision this so that your application can access those secrets and configurations?**

Enable IAM Roles for Service Accounts (IRSA): This allows fine-grained permissions for Kubernetes pods.

Create an IAM Role: Attach a policy that grants access to Secrets Manager.

Associate the IAM Role with a Kubernetes Service Account: Modify the pod spec to use this service account.

Use AWS SDK or Secrets Manager CSI Driver: Fetch secrets using the AWS SDK or mount secrets directly as files in the pod.

**2. Suppose you have a database that needs to be deployed on Kubernetes, and it needs to be highly available. How would you achieve that?**

To ensure high availability:

Use a StatefulSet for database deployment.

Deploy a PersistentVolumeClaim (PVC) for each replica.

Configure multi-zone Persistent Volumes for resilience.

**3. Suppose you have a situation where your database needs to run on a specific node in Kubernetes and be highly available. How would you achieve that?**

Use nodeSelector or node affinity to schedule the pod on a specific node.

Apply Pod Anti-Affinity to distribute replicas across multiple nodes.

Use Taints and Tolerations to ensure only database workloads run on that node.

**4. What is Terraform local?**
local in Terraform is used to define reusable variables within a module.

Example:
locals {
  env_name = "production"
}
output "environment" {
  value = local.env_name
}

**5. Suppose you have a situation where you have three environments: prod, staging, and dev. All of these environments have similar services; the only difference is the specifications of these services. For example, development has lower-spec machines compared to production. How would you manage this kind of infrastructure using Terraform, and how would you manage the state file?**

Use Terraform Workspaces to manage different environments.

Maintain separate state files for each environment.

Store state files in S3 with DynamoDB locking for safety.

Use Terraform Modules to reuse infrastructure definitions.

Leverage Environment Variables and Input Variables for customization.

**6. Suppose you have a system with an apex domain abc.com and multiple environments such as dev.abc.com and prod.abc.com. Additionally, there are multiple subdomains for each environment, such as api.dev.abc.com. How would you structure this kind of system in Route 53?**

Use a single hosted zone for example.com.

Create subdomains for environments: dev.example.com, staging.example.com, prod.example.com.

Use Alias Records or CNAMEs to point to load balancers or services.

**7. Where would you use a Load Balancer and a NodePort in a Kubernetes cluster?**

LoadBalancer: When exposing services externally (e.g., ALB, NLB in AWS).

NodePort: When exposing services internally or for development.

**8. Why can't you create an AMI from stopped instances?**

If you attempt to create an AMI from a running instance, there is a risk of data inconsistency due to ongoing operations that might not be fully committed to the disk at the time of the snapshot

**9. What is a shared directory in Jenkins?**

A directory accessible by multiple Jenkins jobs, often /var/jenkins_home

**10. What are parameters in Jenkins?**

In Jenkins, parameters are used to allow users to input values before or during the execution of a Jenkins job (or pipeline).

These values can customize the job's behavior,such as determining which code branch to build,providing configuration values,or setting environment-specific parameters.

Parameters are especially useful in automated build or deployment pipelines to introduce flexibility and user interaction.

String Parameter:

A simple text field where the user can input any string value.
Useful for passing variables such as version numbers, branch names, or environment names.

Example:

Name: Branch
Default Value: main

Boolean Parameter:

A checkbox that allows the user to choose between true or false.
Often used to toggle options or features on or off.

Example:

Name: Deploy to Production
Default Value: false

Choice Parameter:

A dropdown menu where the user can select from a predefined list of options.
Useful for choosing among several predefined configurations, environments, or versions.

Example:

Name: Environment

Choices:
Development
Staging
Production

**11. What is a data type in Jenkins?**

In Jenkins, a data type typically refers to the kind of value a variable or parameter can hold or process.

It essentially defines the type of data being used in Jenkins pipelines, jobs, or other configurations.

String: A sequence of characters. Strings are commonly used for text-based values, such as file names or parameters.

Example: param = "example_value"

Integer: Whole numbers without any decimal point.

Example: numRetries = 5

Boolean: Represents a true or false value.

Example: isDeployable = true

List or Array: A collection of values. Jenkins pipelines support lists/arrays, especially when handling multiple items.

Example: branches = ["master", "develop", "feature-xyz"]

**12. How can I upload my plugin into Jenkins?**

**13. What is the difference between GitHub webhook and Poll SCM in Jenkins?**

**14. In Python, what is the difference between mutable and immutable objects?**

**15. What is the subprocess module?**

**16. What is boto3?**

**17. How many ways are there to create a Lambda function?**

**18. Display the unique numbers in the list [1, 2, 3, 2, 5, 6, 5, 4, 1, 3].**

**19. What kind of backups does Velero store?**

**20. What is a rollout restart?**

**21. What is the difference between kubectl get events and kubectl describe pod?**

**22. What is the difference between a liveness probe and a readiness probe?**

**23. What does "terraform local-exec" do?**

**24. What is the null_resource in Terraform?**

**25. What are addons in Terraform?**

**26. When a Terraform file becomes corrupted, how can you restore it?**

**27. In two environments, production and development, I have the same set of files. However, in the production environment, I don't want to create a database, but in the development environment, I want both an EC2 instance and an RDS instance. How can I ensure that only the EC2 instance is created in the development environment while both the EC2 instance and RDS instance are created in the production environment?**

**28. What is count in Terraform?**

**29. For example, let's consider an EKS cluster and a node group. In Terraform, there are separate configurations for creating the EKS cluster and the node group. When running terraform apply, the process fails with an error stating that the EKS cluster is not active. How can this issue be resolved?**

**30. What is terraform graph?**

**31. What is terraform state list command?**

**32. What is the purpose of the terraform mv command?**

**33. What does the terraform rm command do?**

**34. How would you configure Jenkins to grant specific access permissions to different teams? For instance, if you have multiple folders (a, b, c) and you want to allow Team B to access and perform actions only in folder B, how would you achieve this?**

**35. What is the master-slave architecture in Jenkins, and how does it work?**

**36. In Jenkins, do you install plugins on the master node or the slave node?**

**37. How do you manage secrets stored in AWS SSM Service for the CI process in Jenkins?**

**38. What is a shared library in Jenkins?**

**39. What will be there in a slave?**

**40. You are doing CI, but this CI process requires some secrets. How can you manage secrets in Jenkins?**

**41. What if some secrets are stored in AWS SSM service?**

**42. How do you typically create a Jenkins pipeline?**

**43. How can you deploy a Jenkins pipeline?**

**44. How can you achieve parallel stages in Jenkins?**

**45. Let's say you want to integrate some Jenkins APIs. For example, you have a Jenkins pipeline, and there is a Kubernetes pod. You want to trigger an API or a Jenkins pipeline using Jenkins API based on an event inside your Kubernetes, such as an XYZ event. How can you achieve this?**

**46. How do you reduce the Docker image size?**

**47. For example, you just want to know what processes are running inside your VM. The top command shows only the top processes, but you want a list of all processes. Which command would you use?**

**48. What is the difference between spot instances and reserved instances? Which is more cost-effective?**

**49. Let's say there are two regions, Mumbai and Singapore. There is one AMI present in the Singapore region, and you want to use that AMI in the Mumbai region, but the AMI is encrypted using a CMK. How can you do this?**

**50. What is the difference between a public subnet and a private subnet?**

**51. What is the difference between a Network ACL (NACL) and a security group (SG)?**

**52. What is the difference between stateless and stateful?**

**53. What is a customer gateway?**

**54. What is the difference between CloudWatch Alarms and EventBridge?**

**55. For example, let's say there is an EC2 instance with a process running on it. You want to trigger an alarm if that process goes down. How can you set this up?**

**56. You want to create an S3 replication policy. What are the prerequisites for it?**

**57. What is the purpose of GitLab?**

**58. How do you integrate auto-trigger builds?**

**59. Which trigger do you set up for webhooks, and what URL do you mention in GitHub?**

**60. Can you elaborate on this process: You have a Jenkins pipeline that you want to auto-trigger on a certain repository when a push occurs on that repository.**

**61. I have a Jenkins job and have set up two Jenkins jobs that listen to different repositories. Now, you are setting only the GitHub with the Jenkins URL. If you push to repo A, which job will trigger? Both or only one?**

**62. How do you ensure high availability of Jenkins, and what happens if the master goes down?**

**63. Is there any Jenkins backup that happens daily?**

**64. What is GIT as?**

**65. How is SonarQube integrated with Jenkins?**

**66. Every time you build your application, do you go ahead and install Java, deploying it 10 times a day?**

**67. Explain a multistage Dockerfile.**

**68. What is a layer in Dockerfiles?**

**69. What is an image manifest file?**

**70. What are CIDR ranges?**

**71. How do you decide on the CIDR ranges?**

**72. I want 510 usable hosts, so I used a /23 CIDR and created one subnet. What about the rest of the IPs?**

**73. What kind of data is hosted in S3? Is it updated frequently or infrequently?**

**74. Can you explain the process of hosting content on an S3 bucket?**

**75. I don't want to use CloudFront for direct access to content. What are the alternatives?**

**76. What is caching in CloudFront, and what is cache invalidation?**

**77. What is a CRD in Kubernetes?**
