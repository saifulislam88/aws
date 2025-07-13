### 🔹What are the failure points and how can you make it highly available?

```sh

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

```

- **NAT Gateway:** Use **multiple NAT Gateways** in different AZs.
- **ALB:** Ensure it spans **multiple public subnets (AZs)**.
- **EC2:** Use **Auto Scaling Groups** with instances across AZs.
