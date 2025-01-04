# E-Commerce-Platform-on-Azure

---

### **Project : E-Commerce Platform on Azure**

#### **Client Requirement:**
- Build a scalable and resilient e-commerce platform.
- Host the platform using Azure App Services.
- Use Azure SQL for database management.
- Ensure data redundancy and recovery options.
- Secure the application using Azure AD and implement role-based access control (RBAC).
- Optimize costs and provide performance monitoring.

---

#### **Solution Overview:**
1. **Frontend and Backend:**  
   Deploy frontend and backend applications on Azure App Services.
2. **Database:**  
   Use Azure SQL with Geo-Replication for high availability.
3. **Storage:**  
   Utilize Blob Storage for static content like images and documents.
4. **Security:**  
   Implement RBAC using Azure Active Directory and enable Multi-Factor Authentication.
5. **Monitoring:**  
   Use Azure Monitor for performance insights.
6. **Load Balancing:**  
   Employ an Azure Load Balancer to distribute traffic across instances.

---

#### **Code Snippet:**
```bash
# Create a Resource Group
az group create --name ECommerceRG --location eastus

# Deploy Azure SQL Database
az sql server create --name ecommerceserver --resource-group ECommerceRG --location eastus \
    --admin-user adminuser --admin-password MyP@ssword123

az sql db create --resource-group ECommerceRG --server ecommerceserver \
    --name ECommerceDB --service-objective S1

# Deploy App Service
az webapp create --name ECommerceApp --resource-group ECommerceRG \
    --plan ECommerceAppPlan --runtime "DOTNET|6.0"

# Enable Azure AD Authentication
az webapp auth update --name ECommerceApp --resource-group ECommerceRG \
    --enabled true --aad-allowed-token-audiences https://ECommerceApp.azurewebsites.net
```

---

#### **Architecture Diagram:**

- Users → Azure Load Balancer → Azure App Services (Web + API)  
- Azure App Services → Azure SQL Database  
- Blob Storage (for images)  
- Azure AD (for authentication)  
- Azure Monitor (for performance)

---
