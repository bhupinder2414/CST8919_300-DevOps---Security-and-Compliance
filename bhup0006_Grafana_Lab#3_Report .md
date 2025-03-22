**DevOps -- Security and Compliance CST 8919**

**Student Name: Bhupinder Singh** **(bhup0006)**

## Lab Report: Grafana Installation and Authentication Using Managed Identity

**1. Objective**

This lab aimed to install and configure Grafana on an Ubuntu virtual
machine (VM) in Azure. The primary goal was to authenticate Grafana with
Azure Monitor using a Managed Identity instead of a Service Principal.
Additionally, a dashboard was created to visualize server performance
metrics.

**2. Prerequisites**

\- Azure subscription with permissions to create and manage resources.  
- Ubuntu Server (18.04 or later) deployed on Azure.  
- SSH access to the VM.  
- Basic Linux command-line knowledge.

**3. Steps Taken**

**Step 1: Creating the Ubuntu VM**

1.  Created a VM with Standard B2s v2 SKU:

    ![1](images\A1.png)

    ![1](images\A2.png)

    4\. Enabled Managed Identity for the VM:  

    ![1](images\A3.png)

**Step 2: Installing Grafana**

1.  **Connected to the VM via SSH:**  
    ssh azureuser@20.80.89.137  

    ![1](images\A.png)

    **2. Updated and installed necessary dependencies:**  
    sudo apt-get update && sudo apt-get upgrade -y  
    sudo apt-get install -y apt-transport-https
    software-properties-common wget  

    ![1](images\B.png)

    ![1](images\C.png)

    3\. Installed Grafana and started the service.

**Step 3: Configuring Network Access**

1.  **Verified Grafana service status:**  
    sudo systemctl status grafana-server  
    ![1](images\D.png)

2.  **Allowed traffic on port 3000:**  
    sudo ufw allow 3000/tcp

    ![1](images\B1.png)

    ![1](images\E.png)

**Step 4: Configuring Managed Identity Authentication**

1.  Assigned roles to the VM's Managed
    Identity.
    ![1](images\F.png)

    ![1](images\G.png)

    2\. Modified Grafana\'s configuration file
    (\`/etc/grafana/grafana.ini\`).

    ![1](images\H.png)
    
    ![1](images\I.png)

    3\. Restarted Grafana service.

### 

**Step 5: Connecting Grafana to Azure Monitor**

Accessed Grafana via \`http://20.80.89.137:3000\`.

![1](images\J.png)

2\. Logged in and configured the Azure Monitor data source using Managed
Identity.

![1](images\K.png)

![1](images\L.png)

**Step 6: Creating a Dashboard**

1.  Created a new dashboard and added performance metrics panels.  
    2. Customized and saved the dashboard.

<!-- -->

4.  **Issues Encountered and Resolutions**

|                                             |                                                                                                                                    |
|---------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------|
| **Issue**                                   | **Resolution**                                                                                                                     |
| **Quota limitation for Standard B2s v2 VM** | Submitted a support request to increase the quota.                                                                                 |
| **Azure Monitor authentication failing**    | Encountered persistent authentication failures despite ensuring Managed Identity was assigned and roles were correctly configured. |

**5. Conclusion**

This lab successfully demonstrated the installation of Grafana on an
Ubuntu VM and authentication using Managed Identity. By replacing
Service Principal authentication with Managed Identity, we improved
security and reduced the need for credential management. The final
Grafana dashboard provided real-time insights into the server\'s
performance metrics.
