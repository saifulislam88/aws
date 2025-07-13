#### What is the role of the Internet Gateway (IGW) in ALB architecture?

- Enables **internet access** to and from AWS resources in **public subnets**.
- ALBs use the IGW to **accept incoming requests** from the internet.
- Without an IGW, **ALB cannot be internet-facing**, even if it's in a subnet.
