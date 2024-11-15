# azure-file-sync-guide
Step-by-step guide for implementing Azure File Sync with on-premises file shares using Azure Portal

# Azure File Sync Setup Guide - Portal Edition 🔄

[![Azure](https://img.shields.io/badge/Azure-0089D6?style=flat-square&logo=microsoft-azure&logoColor=white)](https://azure.microsoft.com/)
[![Windows Server](https://img.shields.io/badge/Windows%20Server-0078D6?style=flat-square&logo=windows&logoColor=white)](https://www.microsoft.com/windows-server)


> A step-by-step guide for setting up Azure File Sync using the Azure Portal interface. Perfect for administrators who prefer GUI-based configuration.

#  🏗 Architecture Overview

```plaintext
┌─────────────────┐     ┌──────────────────┐     ┌────────────────┐
│  On-Premises    │     │   Azure File     │     │    Azure       │
│  File Server    ├────►│     Sync         ├────►│  File Share    │
└─────────────────┘     └──────────────────┘     └────────────────┘
```

## 📑 Table of Contents

- [🔧 Prerequisites](#prerequisites)
- [🖥️ Step 1: Create File Share in Windows Server](#step-1-create-file-share-in-windows-server)
- [☁️ Step 2: Create an Azure File Share](#step-2-create-an-azure-file-share)
- [⚙️ Step 3: Azure File Sync Service Configuration](#step-3-azure-file-sync-service-configuration)
- [📝 Step 4: Server Registration](#step-4-server-registration)
- [🔄 Step 5: Sync Configuration](#step-5-sync-configuration)
- [📊 Monitoring and Management](#monitoring-and-management)
- [🔍 Troubleshooting](#troubleshooting)
- [📚 Additional Resources](#additional-resources)
- [🤝 Contributing](#contributing)
- [📄 License](#license)

## 🔧 Prerequisites

- Windows Server 2012 R2 or newer
- Azure subscription with contributor access and a storage account setup (optional)
- Internet connectivity
- Modern web browser (Edge, Chrome, or Firefox)
- Server admin credentials

## 🖥️ Step 1: Create File Share in Windows Server

1. **Open Server Manager** 🚀
   - Click Start > **Server Manager**
   - Or type **Server Manager** in the Start menu

2. **Navigate to File Services** 📂
   - Click **File and Storage Services**
   - Select "**Shares**
   - Right-Click on the empty space.
   - Select **New Share...**
  
![image](https://github.com/user-attachments/assets/0b3c7210-194a-477a-a2f8-e1691236e623)


3. **Share Configuration** ⚙️
   - Select **SMB Share - Quick**

![image](https://github.com/user-attachments/assets/5bd7878e-dd45-4cff-8049-3a76cfad2ab1)

   - Choose share location
   - Name your share

     
![image](https://github.com/user-attachments/assets/3a8a7f70-17de-4e3a-9303-0afa05175443)

     
   - Configure permissions


![image](https://github.com/user-attachments/assets/bb576a2e-2d61-43b3-bc2c-71a078d76e66)

   - Complete the wizard
   - File share has been created

![image](https://github.com/user-attachments/assets/1e111799-6f84-4380-8269-705cbc041235)


## ☁️ Step 2: Create an Azure File Share

  - Sign in to the Azure portal and navigate to the Storage accounts section.
  - Create a new storage account or use an existing one.
  - In the storage account, go to **File shares** and click on **+ Add File share**.


![image](https://github.com/user-attachments/assets/f3c253d1-dc74-4805-b480-002c2215a70b)


 - Name your file share and then click on **Review + Create**.


![image](https://github.com/user-attachments/assets/9143c7fa-2cc2-491d-bda2-837119a841f5)

- Click on **Create** to create your file share

![image](https://github.com/user-attachments/assets/6ef60c8a-b3b1-4071-aca0-7e18f0f2b3ed)


## 🙏 Acknowledgments

- Microsoft Azure Documentation Team
- Azure Storage Team
- Community Contributors
