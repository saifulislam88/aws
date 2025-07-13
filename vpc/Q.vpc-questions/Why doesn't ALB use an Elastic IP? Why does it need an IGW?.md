#### Why doesn't ALB use an Elastic IP? Why does it need an IGW?


- **ALBs do not support Elastic IPs (EIPs)**.
- Instead, they use **AWS-managed dynamic public IPs**, exposed via DNS.
- To be reachable from the internet, ALB must reside in **public subnets with a route to an Internet Gateway (IGW)**.
- The IGW handles **ingress and egress traffic** between internet and public IPs.
