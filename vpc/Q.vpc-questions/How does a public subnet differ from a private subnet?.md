#### How does a public subnet differ from a private subnet?

- A **public subnet** has a route to the **Internet Gateway (IGW)**.
- A **private subnet** does **not** have such a route and typically uses a **NAT Gateway** for outbound internet access.
- Public subnets can host **internet-facing resources**, private subnets are used for **internal services**.
