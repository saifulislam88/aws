### 🔹Can the ALB communicate with EC2 in a private subnet?
 

      Internet
          |
   +--------------+
   | Internet-Facing ALB |
   +--------------+
          |
Public Subnet with IGW (for ALB)
          |
 ┌────────────────────┐
 |  Private Subnet    |
 |  EC2 Web Server(s) |
 └────────────────────┘
          |
    NAT Gateway (for outbound only)


Yes, ALB can route traffic to EC2 instances in private subnets as long as:
- Security group of EC2 allows traffic from ALB
- Network routing allows connectivity within the VPC
