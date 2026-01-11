# AWS Auto Scaling with Application Load Balancer

### 📌 Overview

AWS Auto Scaling automatically adjusts the number of EC2 instances based on demand.
This project demonstrates how to create an Auto Scaling Group (ASG) using an AMI, a Launch Template, and an Application Load Balancer (ALB) to ensure high availability and fault tolerance.

---

### 🧠 Definition

- AWS Auto Scaling helps maintain application availability by automatically launching or terminating EC2 instances according to defined scaling policies, health checks, and capacity settings.

### 🖼 Step 1: Create an Amazon Machine Image (AMI)
- Go to EC2 → Instances
- Select your configured web server instance
- Click Actions → Image and templates → Create image
- Image name: mywebserver-image
- Click Create image
---

### 🔍 Verify AMI Creation
- Go to EC2 → AMIs
- Confirm that mywebserver-image is available
---

### ⚙️ Step 2: Create Auto Scaling Group
- Create Auto Scaling Group
- Go to EC2 → Auto Scaling Groups
- Click Create Auto Scaling group
- Name: mywebserver-asg
---

### 📄 Step 3: Create Launch Template
- Click Create launch template
- Launch template name: mywebserver-template
- Description: Launch template for web server with load balancing
- AMI: Select My AMIs → mywebserver-image
- Key Pair: Select existing key pair
### Network Settings:
- Select Security Group
- Ensure HTTP (Port 80) is enabled (mandatory)
- Click Create launch template
---

### 🔗 Step 4: Configure Auto Scaling Group
- Select launch template: mywebserver-template
- Version: 1
- Click Next
- Select desired Availability Zones
- Click Next
---

### ⚖️ Step 5: Attach Load Balancer
- Enable Attach to an existing load balancer
- Select the target group (e.g., webserver-lb-tg)
- Enable Amazon EBS health checks
- Click Next
---

### 📈 Step 6: Configure Scaling Policies
- Desired capacity: 2
- Minimum capacity: 1
- Maximum capacity: 2
- Enable Target tracking scaling policy

### Metric type:
- Application Load Balancer request count per target
- Select target group: webserver-lb-tg
- Click Next
- Skip to review
- Click Create Auto Scaling group
---

## ✅ Verification Steps
### 1️⃣ Verify via Load Balancer
- Go to EC2 → Load Balancers
- Open Resource map
- Confirm multiple targets are registered
- Copy the Load Balancer DNS name
- Paste it into a browser to verify traffic distribution
---

### 2️⃣ Verify via Auto Scaling Group
- Go to Auto Scaling Groups
- Select mywebserver-asg
- Under Instance management, verify:
- Instances are running
- Health status is Healthy
---

### 3️⃣ Test Auto Scaling Behavior
- Go to EC2 → Instances
- Stop or terminate one EC2 instance
- Refresh the Auto Scaling Group
- A new instance will be automatically launched to maintain desired capacity
 ### ✅ This confirms Auto Scaling is working correctly.
---
  ## 👨‍💻 Author

**Kumlesh Kurre**
💼 IT Support & Network Engineer

⭐ If you find this guide helpful, don’t forget to star ⭐ the GitHub repository!

**Purpose:** AWS Learning & Practice 🚀
