
## ❓ Question
**You have a Jenkins EC2 instance running in the default VPC (`172.31.0.0/16`) and an EKS cluster deployed in a custom VPC (`10.0.0.0/16`), both in the same AWS region. How would you enable communication between them?**

---

### ✅
By default, VPCs in AWS are isolated — even within the same region — so direct communication is not possible.

### Recommended Solution: **VPC Peering**
- Create a **VPC Peering Connection**.
- Add **route table entries** in both VPCs.
- Update **security groups** to allow traffic between the CIDR blocks (e.g., 8080 for Jenkins, 443 for EKS API).

This enables secure, private communication.

---

### 🛑 Alternative Options

### 🌐 Public Access to EKS
- Works only for accessing the **EKS control plane** (not internal services).
- Requires `cluster_endpoint_public_access = true`.

### 🌉 Transit Gateway or Shared Services VPC
- Suitable for large/complex environments.
- Overkill and costly for simple Jenkins-to-EKS setups.

---

### ✅ Final Recommendation

> Use **VPC Peering** for secure, simple communication. For long-term simplicity, consider migrating Jenkins into the same VPC as EKS.


