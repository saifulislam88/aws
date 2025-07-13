### 🔹What route table entries should exist for the private subnet for ec2 internet

The private subnet's route table should have:

| Destination | Target          |
|-------------|------------------|
| 0.0.0.0/0   | NAT Gateway ID   |

This ensures that outbound internet-bound traffic goes through the NAT Gateway.
