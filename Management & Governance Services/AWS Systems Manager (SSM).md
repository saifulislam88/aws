
## 🛠️ AWS Systems Manager (SSM)

AWS Systems Manager (SSM) is a management service that helps you view, control, and automate operations across your AWS resources securely.

Put simply, SSM lets you:
✅ Manage EC2 instances and other resources remotely  
✅ Run commands without SSH  
✅ Patch and update instances automatically  
✅ Store and retrieve configuration data securely  
✅ Collect logs and inventory

---

### 🌟 Key Capabilities

Here are the main components of SSM you should know:

| Feature            | What it Does                                        |
|--------------------|-----------------------------------------------------|
| **Session Manager** | Connect to EC2 shell without SSH/key pairs          |
| **Run Command**     | Execute scripts or commands on EC2 (e.g., install updates) |
| **Parameter Store** | Store secrets/config values securely               |
| **Patch Manager**   | Automate OS patching and compliance                |
| **Inventory**       | Collect software/hardware info across your fleet   |

---

### 💡 Example Use Case

Let’s say you have:

- EC2 instances in private subnets (no public IP)
- You want to run commands and manage them securely
- No need to set up bastion hosts or SSH keys

You can use SSM to do everything over AWS private network.

---

### 🧪 Example Scenario: Connect to an EC2 instance using SSM Session Manager

✅ **Step 1: Attach IAM Role to EC2**

Create an IAM role with this policy:

\`\`\`
AmazonSSMManagedInstanceCore
\`\`\`

Attach the role to your EC2 instance.

---

✅ **Step 2: Install the SSM Agent**

Amazon Linux 2 and Ubuntu 20+ usually have SSM Agent preinstalled.

If not, install it:

\`\`\`bash
sudo yum install -y amazon-ssm-agent
sudo systemctl enable amazon-ssm-agent
sudo systemctl start amazon-ssm-agent
\`\`\`

---

✅ **Step 3: Use Session Manager**

- Go to **AWS Console > Systems Manager > Session Manager**
- Click **Start Session**
- Select your instance
- Click **Start Session**

✅ **Result:**

You now have a browser-based shell into your instance, without:

- Public IP
- SSH
- Open ports

---

### 📜 Example: Running a Command on EC2

✅ **Run Command Example**

- Go to **Systems Manager > Run Command**
- Click **Run Command**
- Document: `AWS-RunShellScript`
- Targets: Select your instance
- Command:

\`\`\`bash
sudo yum update -y
\`\`\`

- Click **Run**

✅ **Result:**

Your EC2 updates automatically, and you see logs in the console.

---

### 🎯 Why Use SSM?

| Benefit                 | Explanation                                     |
|-------------------------|-------------------------------------------------|
| **No SSH Keys Needed**  | Eliminates managing SSH credentials             |
| **No Public IP Needed** | Increases security by staying private           |
| **Centralized Management** | Manage fleets across regions/accounts        |
| **Automation**          | Schedule patching and commands                  |
| **Auditability**        | Logs all sessions and commands to CloudWatch    |

