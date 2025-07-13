####🔹Why is the ALB placed in a public subnet and EC2 in a private subnet?


The ALB must be in a **public subnet with IGW** so it can accept traffic from the internet. The EC2s are kept in **private subnets** to prevent direct public access, which enhances security. The ALB forwards traffic to EC2 securely via **target groups**.
