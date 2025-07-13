### 🔹What security group settings are required for the ALB and EC2?

**ALB Security Group:**
- **Inbound:** HTTP/HTTPS from 0.0.0.0/0  
- **Outbound:** All traffic

**EC2 Security Group:**
- **Inbound:** HTTP/HTTPS or application port only from ALB SG  
- **Outbound:** All traffic or restricted as needed
