#### Can the ALB communicate with EC2 in a private subnet *via* the public subnet?

- **No**, ALB **does not use** the public subnet to reach EC2.
- It uses **internal VPC networking**.
- Traffic stays within the **AWS private network**, using **private IPs**.
