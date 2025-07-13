### 🔹How does the ALB know where to send traffic?


The ALB uses a **Target Group** to route traffic to registered **EC2 instances**. **Health checks** determine the instance status, and routing happens based on **configured listener rules** (like path-based or host-based).
