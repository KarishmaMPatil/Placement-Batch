# 🧠 DevOps Scenario-Based & Technical Interview Questions

---

## ### Scenario-Based Questions

### 1. Suppose you have an application deployed inside EKS, and your application needs some secrets to run. These secrets are stored in the Secrets Manager service in AWS. How will you provision this so that your application can access those secrets and configurations?

### 2. Suppose you have a database that needs to be deployed on Kubernetes, and it needs to be highly available. How would you achieve that?

### 3. Suppose you have a situation where your database needs to run on a specific node in Kubernetes and be highly available. How would you achieve that?

### 4. What is Terraform local?

### 5. Suppose you have a situation where you have three environments: prod, staging, and dev. All of these environments have similar services; the only difference is the specifications of these services. How would you manage this kind of infrastructure using Terraform, and how would you manage the state file?

### 6. Suppose you have a system with an apex domain abc.com and multiple environments such as dev.abc.com and prod.abc.com. Additionally, there are multiple subdomains for each environment, such as api.dev.abc.com. How would you structure this kind of system in Route 53?

### 7. Where would you use a Load Balancer and a NodePort in a Kubernetes cluster?

### 8. Why can't you create an AMI from stopped instances?

### 9. What is a shared directory in Jenkins?

### 10. What are parameters in Jenkins?

### 11. What is a data type in Jenkins?

### 12. How can I upload my plugin into Jenkins?

### 13. What is the difference between GitHub webhook and Poll SCM in Jenkins?

### 14. In Python, what is the difference between mutable and immutable objects?

### 15. What is the subprocess module?

### 16. What is boto3?

### 17. How many ways are there to create a Lambda function?

### 18. Display the unique numbers in the list `[1, 2, 3, 2, 5, 6, 5, 4, 1, 3]`.

### 19. What kind of backups does Velero store?

### 20. What is a rollout restart?

### 21. What is the difference between `kubectl get events` and `kubectl describe pod`?

### 22. What is the difference between a liveness probe and a readiness probe?

### 23. What does `terraform local-exec` do?

### 24. What is the `null_resource` in Terraform?

### 25. What are addons in Terraform?

### 26. When a Terraform file becomes corrupted, how can you restore it?

### 27. In two environments, production and development, I have the same set of files. However, in the production environment, I don't want to create a database, but in the development environment, I want both an EC2 instance and an RDS instance. How can I ensure this using Terraform?

### 28. What is `count` in Terraform?

### 29. For example, let's consider an EKS cluster and a node group. When running `terraform apply`, the process fails with an error stating that the EKS cluster is not active. How can this issue be resolved?

### 30. What is `terraform graph`?

### 31. What is `terraform state list` command?

### 32. What is the purpose of the `terraform mv` command?

### 33. What does the `terraform rm` command do?

### 34. How would you configure Jenkins to grant specific access permissions to different teams?

### 35. What is the master-slave architecture in Jenkins, and how does it work?

### 36. In Jenkins, do you install plugins on the master node or the slave node?

### 37. How do you manage secrets stored in AWS SSM Service for the CI process in Jenkins?

### 38. What is a shared library in Jenkins?

### 39. What will be there in a slave?

### 40. You are doing CI, but this CI process requires some secrets. How can you manage secrets in Jenkins?

### 41. What if some secrets are stored in AWS SSM service?

### 42. How do you typically create a Jenkins pipeline?

### 43. How can you deploy a Jenkins pipeline?

### 44. How can you achieve parallel stages in Jenkins?

### 45. Let's say you want to integrate some Jenkins APIs with Kubernetes events. How can you achieve this?

### 46. How do you reduce the Docker image size?

### 47. Which command lists all processes running inside your VM?

### 48. What is the difference between spot instances and reserved instances? Which is more cost-effective?

### 49. Let's say there are two regions, Mumbai and Singapore. There is one AMI present in the Singapore region, and you want to use that AMI in the Mumbai region, but the AMI is encrypted using a CMK. How can you do this?

### 50. What is the difference between a public subnet and a private subnet?

### 51. What is the difference between a Network ACL (NACL) and a Security Group (SG)?

### 52. What is the difference between stateless and stateful?

### 53. What is a customer gateway?

### 54. What is the difference between CloudWatch Alarms and EventBridge?

### 55. There is an EC2 instance with a process running on it. You want to trigger an alarm if that process goes down. How can you set this up?

### 56. You want to create an S3 replication policy. What are the prerequisites for it?

### 57. What is the purpose of GitLab?

### 58. How do you integrate auto-trigger builds?

### 59. Which trigger do you set up for webhooks, and what URL do you mention in GitHub?

### 60. You have a Jenkins pipeline that should auto-trigger on a repository push. How would you set it up?

### 61. You have two Jenkins jobs listening to different repositories. If you push to repo A, which job will trigger?

### 62. How do you ensure high availability of Jenkins, and what happens if the master goes down?

### 63. Is there any Jenkins backup that happens daily?

### 64. What is Git as?

### 65. How is SonarQube integrated with Jenkins?

### 66. Every time you build your application, do you reinstall dependencies like Java each time?

### 67. Explain a multistage Dockerfile.

### 68. What is a layer in Dockerfiles?

### 69. What is an image manifest file?

### 70. What are CIDR ranges?

### 71. How do you decide on the CIDR ranges?

### 72. I want 510 usable hosts, so I used a /23 CIDR and created one subnet. What about the rest of the IPs?

### 73. What kind of data is hosted in S3? Is it updated frequently or infrequently?

### 74. Can you explain the process of hosting content on an S3 bucket?

### 75. I don't want to use CloudFront for direct access to content. What are the alternatives?

### 76. What is caching in CloudFront, and what is cache invalidation?

### 77. What is a CRD in Kubernetes?

---

## ### Linux & Shell Scripting

### 78. How do you set environment variables?

### 79. What is the `PATH` variable?

### 80. How do you make environment variables persistent?

### 81. What is the difference between `export` and `set`?

### 82. How do you view all environment variables?

### 83. What is cron in Linux?

### 84. How do you schedule a cron job?

### 85. What is the format of crontab?

### 86. How do you list current cron jobs?

### 87. What is the `at` command used for?

### 88. Where are system logs stored?

### 89. What is `syslog`?

### 90. How do you monitor log files in real-time?

### 91. What is log rotation?

### 92. How do you search logs for specific patterns?

### 93. How do you install packages using `apt`?

### 94. What is `yum` used for?

### 95. How do you update all packages?

### 96. What's the difference between `apt` and `apt-get`?

### 97. How do you remove packages?

### 98. What is a shell script?

### 99. How do you make a script executable?

### 100. What is the shebang line?

### 101. How do you pass arguments to a script?

### 102. What are conditional statements in bash?

### 103. How do you mount and unmount filesystems?

### 104. What is `/etc/fstab`?

### 105. How do you check filesystem disk space?

### 106. What is `fsck` used for?

### 107. How do you create and manage users?

### 108. How do you troubleshoot high CPU usage?

### 109. What is `iostat` used for?

### 110. How do you monitor network traffic?

### 111. What is `vmstat`?

### 112. How do you analyze memory usage?

### 113. How do you secure SSH connections?

### 114. What is `sudo` and how does it work?

### 115. How do you configure firewall rules?

### 116. What is SELinux?

### 117. How do you check for rootkits?

### 118. How do you configure static IP addresses?

### 119. What is `iptables`?

### 120. How do you set up port forwarding?

### 121. What is network bonding?

### 122. How do you troubleshoot DNS issues?

### 123. What is the difference between containers and VMs?

### 124. How do you install Docker on Linux?

### 125. What are Linux namespaces?

### 126. How do you manage Linux containers?

### 127. What is `systemd`, and how does it work?
