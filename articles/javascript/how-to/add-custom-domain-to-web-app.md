---
title: Secure JavaScript website with Azure domain and certificates
description:  Learn how to create a web app on Azure with a custom domain name secured with an TLS/SSL certificate. 
ms.topic: how-to
ms.date: 11/03/2021
ms.custom: devx-track-js
---

# Secure JavaScript websites with custom domains and certificates

Learn how to create a web app on Azure and purchase an Azure Domain name secured with an TLS/SSL certificate. The same process works for both Azure Function apps and Azure App service (web apps). 

If you want to bring your own domain name or SSL certificate, use these resources:

* [Map an existing custom DNS name to Azure App service](/azure/app-service/app-service-web-tutorial-custom-domain?tabs=cname)
* [Add custom SSL certificate to Azure App service](/azure/app-service/configure-ssl-bindings)

## 1. Get an Azure domain for App Service

You can purchase a domain name in the Azure portal, specifically for your Azure Web app, or you can bring your own domain. 

The domain resource is a separate resource from the web app resource. 

1. In the Azure portal, use [this link](https://ms.portal.azure.com/#create/Microsoft.Domain) to begin creating a new domain. 
1. As part of the creation process, create a **new resource group** to contain all the resources for your secured and named web app. 
1. In the **Domain Details**, enter the domain name you want, such as `cats-flying-dogs.com`. You should have a few domain name choices with variations to try. 

    :::image type="content" source="../media/custom-domain/create-new-app-service-domain.png" alt-text="A new creation page opens. Create a new **App Service domain**.":::

1. Continue filling out the creation tabs for the service:

    |Tab name|Select|
    |--|--|
    |Contact information|Personal or corporate information about web site ownership.|
    |Hostname assignment|Keep the default settings.|
    |Advanced|Keep the default settings so your domain name renews next year and your contact information is kept private.|

1. When you are done, select **Review + create** at the bottom of the web site. 

    The domain name is purchased for you and billed to your Azure subscription.

## 2. Create a new web app service

Create a new paid web resource using one of the following links. Do not create the resource using a free pricing tier. Create the resource in the resource group created in the previous section. 

* [Azure App service](https://ms.portal.azure.com/#create/Microsoft.WebSite) (web app)
* [Azure Function](https://ms.portal.azure.com/#create/Microsoft.FunctionApp)

## 3. Configure domain for web app service

# [Create Azure App Service Domain](#tab/configure-new-app-service-domain)

1. In the Azure portal, for your new web app, select the **Custom domains** setting, then select **+ Add custom domain**. 

    :::image type="content" source="../media/custom-domain/azure-portal-app-service-setting-custom-domain-add-custom-domain.png" alt-text="Select the **Custom domains** setting, then select **+ Add custom domain**. " lightbox="../media/custom-domain/azure-portal-app-service-setting-custom-domain-add-custom-domain.png":::

1. In the right panel, enter the new domain name, such as `cats-flying-dogs.com`, then select **Validate**.
1. Select the **Add custom domain** to connect the domain name to the app service's IP address. 

    :::image type="content" source="../media/custom-domain/azure-portal-app-service-setting-custom-domain-validate-custom-domain.png" alt-text="Select the **Add custom domain** to connect the domain name to the app service's IP address.":::

# [Bring your own domain](#tab/configure-existing-external-domain)

1. In the Azure portal, for your new web app, select the **Custom domains** setting, and copy your IP Address. 
1. Select **+ Add custom domain**. 

    :::image type="content" source="../media/custom-domain/azure-portal-app-service-setting-custom-domain-add-custom-domain.png" alt-text="Select the **Custom domains** setting, then select **+ Add custom domain**. " lightbox="../media/custom-domain/azure-portal-app-service-setting-custom-domain-add-custom-domain.png":::


1. In the right panel, enter your domain name, such as `www.dinatests.me`, then select **Validate**.
1. Select the **Hostname record type** to indicate if the domain name includes subdomains.
1. From the Azure portal for your web app, copy the web app domain name, such as `https://web-app-test.azurewebsites.net`, but remove the `https://` when you copy the host name in the next step. 
1. In your domain provider's site, create a new TXT record. Add the Verification ID as a TXT record with your domain provider.

CNAME record and paste the web app domain name into the **Hostname** field.
Copy the **Custom Domain Verification ID** and enter that CNAME record in your domain name provider's site. 

## 4. Create free managed private certificate

1. Select **TSL/SSL Settings** from the **Settings** area. 

    :::image type="content" source="../media/custom-domain/azure-portal-app-service-select-tsl-ssl-settings.png" alt-text="Select **TSL/SSL Settings** from the **Settings** area.":::

1. Select **Private Key Certificates** then select **+ Create App Service Managed Certificate**

    :::image type="content" source="../media/custom-domain/azure-portal-app-service-create-private-managed-certificate-button.png" lightbox="../media/custom-domain/azure-portal-app-service-create-private-managed-certificate-button.png" alt-text="Select **Private Key Certificates** then select **+ Create App Service Managed Certificate**":::

1. Select the new domain name then select **Create**.

    :::image type="content" source="../media/custom-domain/azure-portal-app-service-add-app-service-create-managed-certificate.png" alt-text="Select the new domain name then select **Create**.":::

    This may take a minute or two to complete.

## 5. Add binding between certificate and domain

1. Select the **Custom domains** setting, then select **Add binding** for the new domain name. 

    :::image type="content" source="../media/custom-domain/azure-portal-app-service-setting-custom-domain-add-binding.png" lightbox="../media/custom-domain/azure-portal-app-service-setting-custom-domain-add-binding.png" alt-text="Select the **Custom domains** setting, then select **Add binding** for the new domain name.":::

1. In the right panel, select the new domain, the private certificate, and the TLS/SSL type.

    :::image type="content" source="../media/custom-domain/azure-portal-app-service-setting-custom-domain-add-binding-panel.png" alt-text="In the right panel, select the new domain, the private certificate, and the TLS/SSL type.":::

1. The process completes and the Custom Domain page shows the custom domain name is secure. 

    :::image type="content" source="../media/custom-domain/azure-portal-app-service-setting-custom-domain-add-binding-complete.png" lightbox="../media/custom-domain/azure-portal-app-service-setting-custom-domain-add-binding-complete.png" alt-text="The process completes and the Custom Domain page shows the custom domain name is secure.":::

1. Select the app's **Overview** page and see the URL for your web app uses the new domain name. 

## Learn more about securing your web app service

You can use existing domain names and certificates or you can create new domain names and certificates on your hosting services:

|Azure host service|Custom domain name| Certificates|
|--|--|--|
|[Azure Static Web Apps](/azure/static-web-apps/)|[Use existing custom domain](/azure/static-web-apps/custom-domain)||
|[Azure Functions](/azure/azure-functions/) & [Apps](/azure/app-service)|[Buy custom domain name on Azure](/azure/app-service/manage-custom-dns-buy-domain)</br>[Map existing domain name](/Azure/app-service/app-service-web-tutorial-custom-domain)<br>[Map with Traffic Manager](/azure/app-service/configure-domain-traffic-manager)|[Create free managed certificate](/azure/app-service/configure-ssl-certificate#create-a-free-managed-certificate-preview)</br>[Import existing certificate from Key Vault](/azure/app-service/configure-ssl-certificate#import-a-certificate-from-key-vault)</br>[Upload private certificate](/azure/app-service/configure-ssl-certificate#upload-a-private-certificate)</br>[Upload public certificate](/azure/app-service/configure-ssl-certificate#upload-a-public-certificate)</br>[Configure SSL bindings](/azure/app-service/configure-ssl-bindings)|
|[Container Instances](/azure/container-instances)||[Using sidecar container](/azure/container-instances/container-instances-container-group-ssl)|

## Next steps

* [Deploy a web app](deploy-web-app.md)
