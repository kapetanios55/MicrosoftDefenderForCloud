
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

3. Modify the namespace-to-owner mappings.
4. Deploy using the Deploy to Azure button.

### **⚡ After Deployment (via Azure UI)**
If you need to update the namespace-to-owner mapping after the Logic App is deployed, follow these steps:

1. Open the **deployed Logic App** in **Azure Portal**.
2. Navigate to **Parameters** under the Logic App settings.
3. Locate the **resourceMapping** parameter and update the values as needed.
4. Click **Save** to apply the changes.

---

## 🔐 Assigning Permissions to the Logic App
For the Logic App to successfully execute governance assignments, its **Managed Identity** must have the appropriate **Security Admin** and **Reader** permissions.

### **🔹 Using PowerShell**
```powershell
//Management Group
az role assignment create --assignee "<ManageIdentityID>" --role "Security Admin" --scope "/providers/Microsoft.Management/managementGroups/<MGID>"
az role assignment create --assignee "<ManagedIdentityID>" --role "Reader" --scope "/providers/Microsoft.Management/managementGroups/<MGID>"

//Subscription
az role assignment create --assignee "<ManagedIdentityID>" --role "Security Admin" --scope "/subscriptions/<SubscriptionID>"
az role assignment create --assignee "<ManagedIdentityID>" --role "Reader" --scope "/subscriptions/<SubscriptionID>"
```
### **Applying on Multiple subscriptions**
If you want your logic app to run on multiple subscriptions you can do that by changing the HTTP compoment API call body:
```json
{
  "subscriptions": [
    "<subscription1ID>",
    "<subscription2ID>"
  ],
  "query": "<query>"
}

Make sure to assign the needed permissions on all subscriptions refferenced in the HTTP component