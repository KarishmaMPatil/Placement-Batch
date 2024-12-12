# Amazon EC2 Interview Questions 

## 1. What is an EC2 instance type, and how do you choose the right one for your application?
**Answer:**
- EC2 instance types determine the compute, memory, and storage capacity available. You select an instance type based on your application's requirements. For example:
  - Choose `t2.micro` for lightweight web servers.
  - Opt for `c5.large` for compute-intensive tasks like data analysis.
  - Use `r5.xlarge` for memory-heavy databases.

---

## 2. What is an EC2 instance family, and when would you use one family over another?
**Answer:**
- Instance families group instance types based on similar use cases:
  - **General Purpose (e.g., T, M families):** Balanced compute, memory, and storage for web apps or development.
  - **Compute Optimized (e.g., C families):** High-performance compute for data processing or ML workloads.
  - **Memory Optimized (e.g., R, X families):** For in-memory databases or real-time analytics.

---

## 3. Describe the typical steps involved in launching an EC2 instance.
**Answer:**
1. Log in to the AWS Management Console.
2. Go to the EC2 Dashboard and click on "Launch Instance."
3. Choose an Amazon Machine Image (AMI).
4. Select an instance type.
5. Configure instance details like network and auto-scaling.
6. Add storage (e.g., EBS volumes).
7. Tag the instance for easier identification.
8. Configure security groups for inbound/outbound rules.
9. Launch the instance and download the key pair for SSH access.

---

## 4. What is an EC2 user data script, and how can it be used during instance launch?
**Answer:**
- User data scripts are shell commands or scripts provided during instance launch. They are executed on the instance’s first boot to automate configurations like installing software or initializing services.

**Example:** Installing Apache:
```bash
#!/bin/bash
yum install -y httpd
systemctl start httpd
systemctl enable httpd
```

---

## 5. Explain the purpose of EC2 instance metadata and how you can access it from within an instance.
**Answer:**
- Instance metadata provides details about the running instance, such as instance ID, public IP, or security groups.
- Access it via the command:
  ```bash
  curl http://169.254.169.254/latest/meta-data/
  ```
  
---

## 6. How can you create custom AMIs, and why might you want to do so?
**Answer:**
- A custom AMI is created by configuring an instance, stopping it, and selecting "Create Image" from the console. Custom AMIs save pre-installed software and configurations for repeatable deployments.

---

## 7. What are security groups, and how do they control inbound and outbound traffic to EC2 instances?
**Answer:**
- Security groups act as virtual firewalls:
  - Inbound rules control incoming traffic.
  - Outbound rules control outgoing traffic.

**Example:**
- Allow SSH: Port 22, Source `0.0.0.0/0`.
- Allow HTTP: Port 80, Source `0.0.0.0/0`.

---

## 8. Explain the use of Network Access Control Lists (NACLs) and how they differ from security groups.
**Answer:**
- NACLs operate at the subnet level and can allow or deny traffic explicitly.
- Security groups operate at the instance level and only allow traffic.

**Example:** Use NACLs for broad network traffic rules and security groups for fine-grained instance-level controls.

---

## 9. How do you enable and configure AWS Web Application Firewall (WAF) in front of an EC2-based web application?
**Answer:**
- Set up AWS WAF to protect against common web exploits:
  1. Create a WebACL in WAF.
  2. Define rules for SQL injection or XSS filtering.
  3. Associate the WebACL with an Application Load Balancer in front of EC2 instances.

---

## 10. What is Auto Scaling, and how can it be used to ensure high availability and scalability of EC2 instances?
**Answer:**
- Auto Scaling adjusts the number of EC2 instances based on load:
  - **Scaling Out:** Add instances during high traffic.
  - **Scaling In:** Remove instances during low traffic.

---

## 11. Explain the purpose of Amazon Elastic Load Balancing (ELB) and its integration with EC2 instances.
**Answer:**
- ELB distributes incoming traffic across multiple EC2 instances to improve fault tolerance.
- Types:
  - **Application Load Balancer:** HTTP/HTTPS-based routing.
  - **Network Load Balancer:** High-performance TCP/UDP routing.

---

## 12. How to resolve boot-related issues like kernel panic in EC2 instances?
**Answer:**
1. Detach the root volume.
2. Attach it to another instance.
3. Inspect or fix corrupted files (e.g., `fstab`).
4. Reattach the volume and reboot.

---

## 13. What are the different types of EBS volumes available, and when would you use each type?
**Answer:**
1. **gp2/gp3:** General-purpose SSD for most workloads.
2. **io1/io2:** High-performance SSD for databases.
3. **st1:** HDD for streaming workloads.
4. **sc1:** Cold HDD for infrequent access.

---

## 14. What is an EBS snapshot, and why is it important for data durability and disaster recovery?
**Answer:**
- Snapshots are incremental backups of EBS volumes stored in S3.
- Use them for quick recovery or creating new volumes in another region.

---

## 15. What are some best practices for using Placement Groups in AWS?
**Answer:**
- Use **Cluster Placement Groups** for low-latency applications like HPC.
- Use **Spread Placement Groups** to isolate instances for fault tolerance.
- Use **Partition Placement Groups** for large distributed systems.

---

## 16. How can you monitor the performance and health of EBS volumes, and what AWS services or tools can assist in this process?
**Answer:**
- Use Amazon CloudWatch for:
  - Metrics like IOPS, latency, throughput.
  - Setting alarms for unusual activity.

---

This README.md file contains simplified conversational answers tailored for interview preparation.
