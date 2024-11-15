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
- [⚙️ Step 3: Deploy the Azure File Sync Service](#deploy-the-azure-file-sync-service)
- [⚙️Step 4: Azure File Sync Service Configuration](#⚙step-4-azure-file-sync-service-configuration)
- [📝 Step 5: Server Registration](#step-5-server-registration)
- [🔄 Step 5: Server Endpoint Configuration](#step-5-server-endpoint-configuration)
- [✅Step 6 : Verify Files on the Azure File Share](#verify-files-on-the-azure-file-share)
- [🔍 Troubleshooting](#troubleshooting)

## 🔧 Prerequisites

- Windows Server 2012 R2 or newer
- Azure subscription with contributor access and a storage account setup (Optional for the storage account, you can quickly create it.)
- Internet connectivity
- Modern web browser (Edge, Chrome, or Firefox)
- Server admin credentials

## 🖥️ Step 1: Create File Share in Windows Server

1. **Open Server Manager** 🚀
- Click Start > **`Server Manager`**
- Or type **`Server Manager`** in the Start menu

2. **Navigate to File Services** 📂
- Click **`File and Storage Services`**
- Select **`Shares`**
- Right-Click on the empty space.
- Select **`New Share...`**
  
![image](https://github.com/user-attachments/assets/0b3c7210-194a-477a-a2f8-e1691236e623)


3. **Share Configuration** ⚙️
- Select **`SMB Share - Quick`**

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
- In the storage account, go to **`File shares`** and click on **`+ Add file share`**.


![image](https://github.com/user-attachments/assets/f3c253d1-dc74-4805-b480-002c2215a70b)


- Name your file share and then click on **`Review + Create`**.


![image](https://github.com/user-attachments/assets/9143c7fa-2cc2-491d-bda2-837119a841f5)

- Click on **`Create`** to create your file share

![image](https://github.com/user-attachments/assets/6ef60c8a-b3b1-4071-aca0-7e18f0f2b3ed)

- Our Azure file share has been created and now we are ready to go for next step.

![image](https://github.com/user-attachments/assets/7d2c51b5-c3bd-4f28-85d5-80179ef99bc2)


## ⚙️ Step 3:  Deploy the Azure File Sync Service


-In the Azure portal, type on the search bar **`Azure File Sync`** and then seclect it.

![image](https://github.com/user-attachments/assets/63fc5ce8-57be-44cd-a359-32b6a65f2eca)


- In the new tab, that is going to open, provide all the informations (azure file sync name, subscription , resource name and location same as your storage) on the **`Basics tab`** and then click on **`Review + Create`**.


![image](https://github.com/user-attachments/assets/e4b9581a-9d27-41bb-bde3-b62dd9ddec60)


-Now, click on **`Create`**  to deploy your file sync service.


![image](https://github.com/user-attachments/assets/e2c9b6b7-b169-48c6-ad5f-cf9434c1d2ca)


## ⚙️Step 4: Azure File Sync Service Configuration

- Navigate to your newly created **`Azure File Sync`** in the Azure portal.
- Expand **`Sync`**, click on **`Sync Groups`** and then click on **`+ Add a sysnc group`**.


![image](https://github.com/user-attachments/assets/37591d8b-6b6d-4dbd-835b-5a6d8fcf315e)


- In the new tab that is goinng to open, provide all the details informations (sync group name, your subscription, your storage account and youe Azure file share) and then click on **`Create`** to deploy the group.


![image](https://github.com/user-attachments/assets/8e43bc61-2630-47c0-a3d3-d08197455a85)


-Your azure sync group has been created, let's move on to the next step.


![image](https://github.com/user-attachments/assets/211e04f4-a235-4e64-b31f-471ff1c8ac2e)


## 📝 Step 5: Server Registration : Configure Azure File Sync on the Windows Server

- In the Azure sync service, click on**`Registered servers`**  and then download the Azure File Sync agent from the Azure portal by clicking on **`Azure file sync agent`**.


![image](https://github.com/user-attachments/assets/a3aa3a81-362b-4e8b-ac25-b7709e2b6e22)


- Choose your prefered language and then clcik on **`Download`**


![image](https://github.com/user-attachments/assets/49b16bd0-05ff-4f19-82bf-69aebe118ef2)


- Choose your windows server version, for me it is **`Windows server 2022`** and then click on **`Dowload`**


![image](https://github.com/user-attachments/assets/cbb743b2-f945-4e98-b753-ae3b1b37d2c3)

- After downloding the agent, install it by just following the wizard, it's very simple.

![image](https://github.com/user-attachments/assets/a4147da0-17f3-4ad3-a5cd-67e5452ced7a)

- Now a new wizard will open to register yor serrver, choose **`AzureCloud`** or different based on the cloud type you're using, you can see that on the proposition. Then click on **`Sign in`** to start the registration.


![image](https://github.com/user-attachments/assets/2207e7ac-f875-4a70-a431-420110c4c2be)

- Provide your Azure account credentials (email and password or Azure account) and then click on **`Sign in`**.


![image](https://github.com/user-attachments/assets/86b7c5ae-3f44-444d-b540-56991f308ee4)

- Now provide all the detail informations **`(Subscription, Resource group and storage sync service)`** on the new panel that is going to open. Make sure you choose acccording to your previous configuration in case you multiple subscriptions, resource groups or storage sync services. Then click on **`Register`**


![image](https://github.com/user-attachments/assets/b2a8f763-225c-4fba-b6af-daff05165078)

  
- Now we are done with the server registration as you can see.


![image](https://github.com/user-attachments/assets/5076770a-bca5-4d72-a663-a928626be894)

 - Now if you go back to the Azure portal in your storage sync service under **`Sync>Registered servers`** you should see your registered servers

![image](https://github.com/user-attachments/assets/06ac9140-8406-4c77-866f-f3c15b453d75)


## 🔄 Step 5: Server Endpoint Configuration

- Open the Azure portal and go to the **`Storage Sync Service`**.
- Select the **`Sync Group`** you want to add the endpoint to.

![image](https://github.com/user-attachments/assets/6176444c-2fe5-4012-ac13-7e9aa7ab9ad6)

- Under **`Server endpoints`**, click on **`+ Add server endpoint`**.  The **`Add server endpoint`** blade will open.
- Enter the required details:
  . **`Registered Server`**: Choose your registered server.
  . **`Path`**: Specify the path on your on-premises server where you want to sync files.
- Click on **`Create`** to create the server endpoint.


![image](https://github.com/user-attachments/assets/0e167edd-c308-4317-978d-1b23502c8767)


- Your server endpoint has been successfully created and running smoothly.


![image](https://github.com/user-attachments/assets/7a20d407-881f-4832-956e-9b69f731d62f)


## ✅Step 6 : Verification in Azure and on-premise server

### Verify Files on the Azure File Share 

- Navigating Back to Your File Share
- Navigate to **`Storage Accounts`** in the Azure portal, search for your storage account and select it.
- Access **`File Shares`** : In the storage account menu, click on **`Storage browser> File shares`**.
- Select your File Share: Find the file share you previously created and click on it.
- View Files: You will now see all the files and folders stored in your on-premise shared path. Check that the files and folders you expect to be synced are present and up to date.


![image](https://github.com/user-attachments/assets/4a8ac1a3-bec2-4eee-901e-177964027562)

### Verify Files on the On-Premises Server

- Open **`File Explorer`** on your on-premises server.
- Navigate to the folder configured for Azure File Sync.
- Check that the files in this folder match those in your Azure file share.
  

![image](https://github.com/user-attachments/assets/f961f43e-c8a4-4148-b26d-5784628a73b5)

## 🔍 Troubleshooting
In the Internet Explorer Enhanced Security Configuration dialog box, set the options to **Off** for both **Administrators** and **Users**.

![image](https://github.com/user-attachments/assets/549fe31b-af69-4c40-b456-4579b057ff89)

----
## Conclusion 

🚀 You're Now Part of the Azure Cloud Journey!
Your hybrid cloud storage solution is ready to serve your organization's needs. As you continue your Azure journey, remember that this setup can be expanded and optimized to meet your growing requirements.

🎉 Congratulations! You've Set Up Azure File Sync!
