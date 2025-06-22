
## 🔐 AWS Network Security: NACL vs Security Group (SG)

In AWS, both Network ACLs (NACLs) and Security Groups (SGs) are used to control traffic flow in and out of your resources. However, they differ in scope, behavior, and use cases.

---

### 📌 What is a Security Group (SG)?

Security Group (SG) is a virtual firewall for EC2 instances to control inbound and outbound traffic at the instance level.

#### Key Characteristics:
- **Stateful**: If you allow inbound traffic, the return traffic is automatically allowed.
- **Attached to**: EC2 instances or ENIs (Elastic Network Interfaces).
- **Rules**: Only allow rules are supported (no deny).
- **Default behavior**: Denies all traffic unless explicitly allowed.
- **Granularity**: Can allow specific IPs, ports, and protocols.

#### Example Use Case:
Allow HTTP (port 80) and SSH (port 22) from specific IP ranges to a web server.

---

### 📘 What is a Network ACL (NACL)?

Network ACL (NACL) is a subnet-level firewall that controls traffic in and out of entire subnets within a VPC.

#### Key Characteristics:
- **Stateless**: Both inbound and outbound rules must be explicitly defined.
- **Attached to**: VPC subnets.
- **Rules**: Supports both allow and deny rules.
- **Default behavior**: Default NACL allows all traffic; custom NACL denies all unless specified.
- **Rule evaluation**: Rules are evaluated in order by rule number (lowest to highest).

#### Example Use Case:
Block all traffic from a known malicious IP across the entire subnet.

---

### 🔄 Side-by-Side Comparison: NACL vs Security Group

| Feature               | Security Group (SG)         | Network ACL (NACL)           |
|-----------------------|------------------------------|-------------------------------|
| **Applies To**        | EC2 instances (ENIs)         | Entire subnet                 |
| **Type**              | Stateful                     | Stateless                     |
| **Rule Types**        | Allow only                   | Allow and Deny                |
| **Evaluation**        | All rules are evaluated      | Rules evaluated in order (lowest number first) |
| **Default Behavior**  | Deny all unless allowed      | Default NACL allows all; custom NACL denies all |
| **Logging Support**   | No native logging            | Can log traffic with VPC Flow Logs |
| **Common Use Case**   | Restricting access to specific instances | Blacklisting IPs or controlling subnet traffic |

---


### ✅ Best Practice

- Use **Security Groups** as your **primary defense** at the instance level.
- Use **NACLs** for an **extra layer** of subnet-level control, especially for **deny rules or broader network-level restrictions**.

---

## 🔄 Stateful vs Stateless in AWS Networking

These terms define how a firewall or filter handles traffic sessions and responses:

---

### 🧠 What Does "Stateful" Mean?

**Stateful** means the firewall remembers the state of the connection. Once a connection is allowed in one direction, the return traffic is **automatically allowed**.

#### 🔐 Example (Security Group):
If you allow inbound SSH (port 22) from IP 1.2.3.4, AWS automatically allows the outbound response.

✅ You do not need to create an outbound rule for return traffic.

#### ✅ Benefits:
- Simpler configuration – only define one side of the rule.
- Automatic handling of replies (e.g., TCP handshakes, web responses).
- Better suited for EC2 and application-level access.

---

### 🧠 What Does "Stateless" Mean?

**Stateless** means the firewall does not track traffic sessions. You must explicitly allow **both inbound and outbound** traffic, even for responses.

#### 🔐 Example (NACL):
If you allow inbound HTTP (port 80) traffic from the internet, you must also allow outbound traffic (like port 1024-65535) for the return response.

❌ Otherwise, the reply is blocked.

#### ⚠️ Implications:
- More complex to configure properly.
- Must mirror rules in both directions.
- Suitable for broad subnet-level restrictions or blacklisting.

---


### 🎯 Real-World Example

**Use Case**: A web server running on EC2

| Requirement                          | With Security Group (Stateful) | With NACL (Stateless)                  |
|--------------------------------------|--------------------------------|----------------------------------------|
| Allow inbound HTTP (port 80)         | Allow port 80 inbound          | Allow port 80 inbound                  |
| Allow return traffic to user         | ✅ Auto-allowed                 | ❌ Must allow ephemeral ports outbound |
| Allow outbound DNS query (port 53)   | Allow port 53 outbound         | Allow port 53 outbound and inbound reply port |

---

### 📝 Summary

| Term       | Means...                        | In AWS…                     | Best For...                       |
|------------|----------------------------------|-----------------------------|-----------------------------------|
| **Stateful** | Tracks traffic session state     | Security Groups             | App-level access, EC2 protection  |
| **Stateless**| Doesn't track sessions          | Network ACLs                | Subnet-level filters, IP blocking |


