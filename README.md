
# 🛡 Microsoft Defender for Cloud – Automated Namespace Governance

![Defender for Cloud](https://img.shields.io/badge/Microsoft-Defender%20for%20Cloud-blue.svg)
![Azure Logic Apps](https://img.shields.io/badge/Azure-Logic%20Apps-brightgreen.svg)
![GitHub](https://img.shields.io/github/license/kapetanios55/MicrosoftDefenderForCloud)

## 🚀 Overview
This repository provides **automated governance assignments** for **Microsoft Defender for Cloud** using **Azure Logic Apps**. It helps organizations enforce security policies **at scale** by applying governance rules to namespaces across **subscriptions** or **management groups**.

By deploying the provided **Logic Apps**, you can:
✔ Automate **namespace governance assignments**.  
✔ Enforce **security policies** dynamically.  
✔ Monitor **compliance and ownership** efficiently.  

## 📥 Deployment Options
You can deploy the Logic Apps **at different governance levels** based on your needs:

### **🔹 Management Group-Level Deployment**
This deployment ensures security governance is enforced across **multiple subscriptions**.

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fkapetanios55%2FMicrosoftDefenderForCloud%2Fmain%2FLogicAppTemplateManagementGroup.json)

### **🔹 Subscription-Level Deployment**
This deployment enforces governance policies **on a single Azure subscription**.

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fkapetanios55%2FMicrosoftDefenderForCloud%2Fmain%2FLogicAppTemplateSubscription.json)

## ⚙ How It Works
1️⃣ **Event Trigger:** The Logic App listens for new **namespace assignments**.  
2️⃣ **Policy Check:** It checks compliance using **Microsoft Defender for Cloud**.  
3️⃣ **Governance Assignment:** Assigns ownership based on the **namespace mapping**.  
4️⃣ **Notification & Logging:** Sends notifications to teams and logs actions.  

## 🛠 Customization
You can customize **namespace-to-owner mappings** in two ways:

### **🔧 Before Deployment**
1. Open the **template file** (`LogicAppTemplateManagementGroup.json` or `LogicAppTemplateSubscription.json`).
2. Locate the `parameters` section:
   ```json
   "parameters": {
       "resourceMapping": {
           "defaultValue": {
               "namespace1": "user1@example.com",
               "namespace2": "user2@example.com"
           }
       }
   }







Management Group Logic-App deployment

[![Deploy To Azure](https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/1-CONTRIBUTION-GUIDE/images/deploytoazure.svg?sanitize=true)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FKapetanios55%2FMicrosoftDefenderforCloud%2Fmain%2FLogicAppTemplateManagementGroup.json)

Subscription Logic-App deployment

[![Deploy To Azure](https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/1-CONTRIBUTION-GUIDE/images/deploytoazure.svg?sanitize=true)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FKapetanios55%2FMicrosoftDefenderforCloud%2Fmain%2FLogicAppTemplateSubscription.json)
