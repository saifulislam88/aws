### 🔹Can the ALB communicate with EC2 in a private subnet?
 
Yes, ALB can route traffic to EC2 instances in private subnets as long as:
- Security group of EC2 allows traffic from ALB
- Network routing allows connectivity within the VPC
