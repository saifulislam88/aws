#### Why create an internet-facing ALB in a public subnet while EC2 is in a private subnet?


- The **ALB in the public subnet** handles **internet traffic** through an **Internet Gateway (IGW)**.
- The EC2 instances in the private subnet have **no public IPs** and are **not directly accessible**.
- ALB **forwards requests internally** via **private IPs** to EC2 instances, ensuring high security.
