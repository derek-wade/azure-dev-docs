---
title: Quickstart - Deploy your first Azure resource with the AzAPI Terraform provider
description: Learn how to use the AzAPI Terraform provider to manage an Azure Lab Service
keywords: azure devops terraform lab azapi resource
ms.topic: quickstart
ms.date: 04/24/2022
ms.custom: devx-track-terraform
author: grayzu
ms.author: markgray
---

# Quickstart: Deploy your first Azure resource with the AzAPI Terraform provider

Article tested with the following Terraform and Terraform provider versions:

- [Terraform v1.1.8](https://releases.hashicorp.com/terraform/)
- [AzureRM Provider v.3.0.2](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs)
- [AzAPI Provider v.0.1.0](https://registry.terraform.io/providers/azure/azapi/latest/docs)

[!INCLUDE [Terraform abstract](./includes/abstract.md)]

In this article, you learn how to use the [AzAPI Terraform provider](https://registry.terraform.io/providers/azure/azapi/latest/docs) to manage an Azure service that is not currently supported by the [AzureRM provider](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs). The `azapi_resource` will be used to manage an [Azure Lab Services](/azure/lab-services/lab-services-overview) account as well as a lab.

> [!div class="checklist"]

> * Define and configure the AzureRM and AzAPI providers.
> * Use the AzureRM provider to create an Azure resource group
> * Use the AzureRM provider to register the "Microsoft.LabServices" provider in your subscription
> * Use the AzAPI provider to create the Azure Lab Services resources

> [!NOTE]
> The example code in this article is located in the [Azure Terraform GitHub repo](https://github.com/Azure/terraform/tree/master/quickstart/101-azapi-lab-services).

## Prerequisites

[!INCLUDE [open-source-devops-prereqs-azure-subscription.md](../includes/open-source-devops-prereqs-azure-subscription.md)]

[!INCLUDE [configure-terraform.md](includes/configure-terraform.md)]

## Implement the Terraform code

1. Create a directory in which to test the sample Terraform code and make it the current directory.

1. Create a file named `providers.tf` and insert the following code:

    [!code-terraform[master](../../terraform_samples/quickstart/101-azapi-lab-services/providers.tf)]

1. Create a file named `main.tf` and insert the following code:

    [!code-terraform[master](../../terraform_samples/quickstart/101-azapi-lab-services/main.tf)]

1. Create a file named `main-generic.tf` and insert the following code:

    [!code-terraform[master](../../terraform_samples/quickstart/101-azapi-lab-services/main-generic.tf)]

## Initialize Terraform

[!INCLUDE [terraform-init.md](includes/terraform-init.md)]

## Create a Terraform execution plan

[!INCLUDE [terraform-plan.md](includes/terraform-plan.md)]

## Apply a Terraform execution plan

[!INCLUDE [terraform-apply-plan.md](includes/terraform-apply-plan.md)]

## Verify the results

1. In your Azure subscription browse to the `rg-qs101` resource group.
1. A new Lab Services account named `qs101LabAccount` displays as a member of the resource group.

## Clean up resources

[!INCLUDE [terraform-plan-destroy.md](includes/terraform-plan-destroy.md)]

## Troubleshoot Terraform on Azure

[Troubleshoot common problems when using Terraform on Azure](troubleshoot.md)

## Next steps

> [!div class="nextstepaction"]
> [Learn more about using Terraform in Azure](/azure/terraform)
