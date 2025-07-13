### 🔹What are the failure points and how can you make it highly available?


- **NAT Gateway:** Use **multiple NAT Gateways** in different AZs.
- **ALB:** Ensure it spans **multiple public subnets (AZs)**.
- **EC2:** Use **Auto Scaling Groups** with instances across AZs.
