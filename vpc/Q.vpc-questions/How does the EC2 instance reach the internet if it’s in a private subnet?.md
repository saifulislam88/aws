### 🔹How does the EC2 instance reach the internet if it’s in a private subnet?


The private subnet routes outbound traffic to a **NAT Gateway**, which is placed in a **public subnet** and has an **Elastic IP**. This allows EC2 instances to **initiate outbound connections** (e.g., software updates) without being reachable from the internet.
