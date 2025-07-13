# azure-blob-storage-cli-lab
Hands-on lab demonstrating how to create and manage Azure Blob Storage containers using Azure CLI and IAM role assignments.
# Azure Blob Storage CLI Lab

## 📌 Lab Title
**Creating and Managing Azure Blob Storage Containers via Azure CLI with Role Assignments**

---

## 🧪 Lab Overview

This lab demonstrates how to create an Azure Blob Storage container using the Azure Command-Line Interface (CLI), assign appropriate IAM roles, and troubleshoot container creation issues. The hands-on project combines Azure portal configurations and CLI scripting to provision, secure, and verify Azure Blob resources from a Linux shell.

---

## 🎯 Objectives

- Create a storage account and blob container using Azure CLI
- Assign IAM roles using Azure Portal
- Configure public blob access
- Upload a sample file using CLI
- Troubleshoot common permission and container creation errors

---

## 🛠️ Tools & Technologies

- Azure CLI 2.0+ on Linux
- Azure Portal (IAM Role Assignment)
- Bash Terminal
- GitHub for documentation
- Python environment (warnings from pkg_resources observed)

---

## 📂 Project Structure

| Step | Task |
|------|------|
| 1️⃣ | Logged in to Azure CLI using `az login` |
| 2️⃣ | Attempted to create container in `demostoragexyz` using CLI |
| 3️⃣ | Encountered `ErrorCode: ContainerNotFound` |
| 4️⃣ | Verified role assignments in Azure Portal (IAM) |
| 5️⃣ | Created a sample file using echo (`sample.txt`) |
| 6️⃣ | Re-executed container creation script |
| 7️⃣ | Verified permission & access status |

---

## 🧪 Key Commands Used

```bash
# Create blob container
az storage container create \
  --name mycontainer \
  --account-name demostoragexyz \
  --auth-mode login \
  --public-access blob

# Upload sample file to blob
az storage blob upload \
  --container-name mycontainer \
  --account-name demostoragexyz \
  --name sample.txt \
  --file sample.txt \
  --auth-mode login

# List blob containers
az storage container list \
  --account-name demostoragexyz \
  --auth-mode login \
  --output table

🧱 Challenges Faced
❌ ErrorCode: ContainerNotFound
Occurred while attempting to upload to a container that didn’t exist yet.

⚠️ pkg_resources deprecation warning
Python package warning seen during each CLI execution. Didn’t affect execution but should be noted for future updates.

🔐 Role Assignment Failed (Already Exists)
While assigning "Storage Blob Data Contributor" role via IAM, an error indicated the role already existed—confirming correct assignment despite UI alert.

✅ Solutions & Fixes
Verified the storage account name and container existence via:


az storage container list --account-name demostoragexyz --output table
Ensured IAM role assignment was active through the Azure Portal > Access Control (IAM)

Repeated container creation until a created: true response was received

Used diagnostic logging and request IDs from errors to troubleshoot

📚 Lessons Learned
Always verify role assignments before creating resources via CLI

Azure CLI’s --auth-mode login works well when permissions are properly granted

Using Azure Portal in parallel with CLI gives better insight into IAM and role-related problems

Clear and descriptive naming conventions (e.g., demostoragexyz, mycontainer) help avoid confusion during scripting

📸 Lab Screenshots & Evidence
All screenshots of this lab (CLI outputs, Azure Portal views, errors, fixes) are available at:

👉 GitHub Image Folder: Click here to view screenshots

📍 Take-Home Summary
Creating storage containers with Azure CLI is efficient—but relies heavily on correct role assignment.

Troubleshooting CLI errors requires checking both the command-line output and portal IAM settings.

This lab built foundational confidence in:

Storage configuration

IAM management

CLI automation

📢 Author
Ime Ben
Cloud Security Analyst
🔗 LinkedIn: www.linkedin.com/in/ime-ben-8aa008362
📧 imegcu55@gmail.com


