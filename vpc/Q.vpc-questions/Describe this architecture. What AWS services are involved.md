### 🔹Describe this architecture. What AWS services are involved?


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



This architecture uses an **Internet-Facing Application Load Balancer (ALB)** placed in a **public subnet** (with an Internet Gateway) to expose a web application running on **EC2 instances located in a private subnet**. Outbound internet access from EC2s is enabled through a **NAT Gateway** in the public subnet.
