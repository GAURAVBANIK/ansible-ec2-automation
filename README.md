🚀 Ansible EC2 Automation

This project demonstrates end-to-end EC2 lifecycle automation using Ansible — from provisioning instances to securely accessing and stopping them using production-grade practices.

📌 What This Project Covers

✅ EC2 provisioning via Ansible

✅ Dynamic AMI handling

✅ Secure SSH access

✅ Inventory configuration

✅ Idempotent infrastructure approach

✅ Production-style EC2 stop using AWS API

🛠️ Tech Stack

Ansible

AWS EC2

boto3

macOS (local control node)

🔄 Workflow Implemented

Provision EC2 instances using Ansible

Configure inventory for remote access

Validate SSH connectivity

Manage instance lifecycle via dedicated playbooks

⚠️ Challenges Faced & Solutions

Invalid AMI error:
Used region-specific valid AMIs instead of hardcoded/expired ones.

Key pair not found:
Ensured EC2 key pair exists in the same AWS region and matched playbook value exactly (case-sensitive).

Permission denied (publickey):
Specified the correct private key in inventory using ansible_ssh_private_key_file.

SSH timeout:
Added inbound rule allowing SSH (port 22) from Anywhere in the security group.

Wrong SSH username:
Used ec2-user for Amazon Linux and ubuntu for Ubuntu instances.

Free tier instance error:
Switched from t2.micro to t3.micro to meet current AWS Free Tier eligibility.

vCPU limit exceeded:
Reduced concurrent instances to stay within the account vCPU quota.

Task skipped unexpectedly:
Corrected when condition based on actual ansible_facts['os_family'].

Connection refused after shutdown:
Understood that OS shutdown kills SSH; adopted AWS API method for production-grade stopping.

Git push refspec error:
Created initial commit and aligned branch name to main before pushing.

🧠 Key Learnings

Infrastructure should be idempotent

Prefer cloud-native automation over manual SSH actions

Always verify region, key pair, and security group alignment

Inventory configuration is critical for Ansible connectivity

📁 Repository Structure
ansible-ec2-automation/
├── create_ec2.yml
├── stop_ec2.yml
├── stop_ec2_production.yml
├── inventory.ini
├── group_vars/
└── vault.pass (ignored)
✍️ Author

Gaurav Banik
