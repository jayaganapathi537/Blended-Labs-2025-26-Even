# Lab 6 – Scale and Load Balance Your Architecture

## Title

Scale and Load Balance Your Architecture
#### Author : JAYAGANAPATHI S 
#### Reg no : 212224040133
#### Date : 19.03.2026

---

## Objective

The objective of this lab is to understand how to design a scalable and highly available architecture on AWS using Auto Scaling and Elastic Load Balancing. This experiment focuses on distributing incoming traffic across multiple EC2 instances, automatically scaling resources based on demand, and validating fault tolerance.

---

## Prerequisites

* Basic knowledge of Amazon EC2 and VPC
* Completion of previous labs (IAM, EC2, EBS, Database Server)
* AWS Academy Lab access
* Stable internet connection

---

## Tools Used

* AWS Management Console
* Amazon EC2
* Elastic Load Balancer (ELB / ALB)
* Auto Scaling Groups (ASG)
* Amazon CloudWatch

---

## Tasks Performed

### Task 1: Review Existing Architecture

Students review the existing EC2-based application architecture created in previous experiments.

### Task 2: Create a Launch Template

Students create a launch template that defines the EC2 instance configuration including AMI, instance type, security group, and user data.

### Task 3: Create an Auto Scaling Group

Students create an Auto Scaling Group using the launch template and configure minimum, maximum, and desired instance capacity.

### Task 4: Configure an Application Load Balancer

Students create an Application Load Balancer and configure target groups for routing traffic to EC2 instances.

### Task 5: Register Auto Scaling Group with Load Balancer

Students attach the Auto Scaling Group to the target group of the load balancer.

### Task 6: Configure Scaling Policies

Students configure scaling policies based on CPU utilization using Amazon CloudWatch alarms.

### Task 7: Test Load Balancing and Scaling

Students test the setup by generating traffic and observing automatic scaling and load distribution.

---

## Workflow

1. Launch the AWS lab environment and open the AWS Management Console.

2. Navigate to **Amazon EC2**, select **Web Server 1**, and create an **Amazon Machine Image (AMI)** named `WebServerAMI`.

3. Go to **Target Groups** and create a new target group named `LabGroup`, selecting **Instances** as the target type and choosing **Lab VPC**.

4. Create an **Application Load Balancer** named `LabELB`, select **Lab VPC**, and configure **Public Subnet 1** and **Public Subnet 2**.

5. Attach the **Web Security Group** and configure the **HTTP:80 listener** to forward traffic to the `LabGroup` target group.

6. Navigate to **Launch Templates** and create a launch template named `LabConfig` using the `WebServerAMI`, instance type `t2.micro`, key pair `vockey`, and **Web Security Group**.

7. Enable **Detailed Monitoring** through **Amazon CloudWatch** in the advanced settings of the launch template.

8. Create an **Auto Scaling Group** named `Lab Auto Scaling Group` using the launch template and select **Private Subnet 1** and **Private Subnet 2**.

9. Configure scaling settings:
   - Desired capacity: `2`
   - Minimum capacity: `2`
   - Maximum capacity: `6`
   - Scaling policy: Target tracking with **Average CPU Utilization = 60%**.

10. Verify the setup by accessing the application using the **Load Balancer DNS name**, perform a **Load Test**, monitor alarms in **CloudWatch**, observe new instances launched by **Auto Scaling**, and finally **terminate Web Server 1**.
---

## Output Screenshots 

<img width="1440" height="900" alt="Screenshot 2026-03-19 at 8 24 29 PM" src="https://github.com/user-attachments/assets/4ee43bb8-5ec0-4fb3-82c4-b97f3d96a0fb" />
<img width="1440" height="900" alt="Screenshot 2026-03-19 at 8 34 00 PM" src="https://github.com/user-attachments/assets/4dadf13f-409e-43f5-bc8b-fcc05b92552f" />
<img width="1440" height="900" alt="Screenshot 2026-03-19 at 8 47 52 PM" src="https://github.com/user-attachments/assets/5caeb973-d3ef-488b-ba6b-4254472f7a70" />
<img width="1440" height="900" alt="Screenshot 2026-03-19 at 8 51 21 PM" src="https://github.com/user-attachments/assets/5013161e-6830-4c48-88a3-8624b3337406" />
<img width="1440" height="900" alt="Screenshot 2026-03-19 at 8 53 32 PM" src="https://github.com/user-attachments/assets/7864e231-1cd4-47d9-8a16-f87e6fd4225d" />



---


## Result

This experiment demonstrated how to build a scalable and fault-tolerant cloud architecture using Auto Scaling Groups and Elastic Load Balancing. The system automatically adjusted resources based on workload and ensured continuous service availability by distributing traffic across multiple instances.
