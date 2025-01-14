---
title: "Step 5: Deploy a Python web app to Azure App Service on Linux using VS Code"
description: Tutorial step 5, deploying the web app code
ms.topic: conceptual
ms.date: 06/06/2020
ms.custom: devx-track-python, seo-python-october2019
---

# 5: Deploy your Python web app to Azure App Service on Linux

[Previous step: configure a custom startup file](tutorial-deploy-app-service-on-linux-04.md)

Use this procedure to deploy your Python app to Azure App Service.

1. In Visual Studio Code, in the Azure Resource explorer, right click on the App Service and select **Deploy to Web App...**.
 
   ![Deploy your web app to App Service in App Service explorer](media/deploy-azure/deploy-web-app-to-app-service-in-app-service-explorer.png)

1. In the prompts that follow, provide the following details:

    - For **Select the folder to deploy**, select your current app folder.
    - If prompted to confirm the deployment, select **Deploy**.
    - If prompted to update your build configuration to run build commands, select **Yes**.
    - If prompted about overwriting the existing deployment, select **Deploy**.
    - If prompted to "Always deploy the workspace", select **Yes**.

1. While the deployment process is underway, you can view progress in the VS Code **Output** window.

    ![Deployment progress in the VS Code output window](media/deploy-azure/view-deployment-progress-in-visual-studio-code-output.png)

1. When deployment is complete after a few minutes (depending on how many dependencies need to be installed), the message below appears. Select the **Browse Website** button to view the running site.

    ![Deployment complete with Browse Website button](media/deploy-azure/web-app-deployment-complete-with-browse-website-button.png)

    An example of the web app deployed is shown below.

    ![The app running successfully on App Service](media/deploy-azure/web-app-running-successfully-on-app-service.png)

1. If you still see the default app, wait a minute or two for the container to restart after the deployment and try again. If you're using a custom startup command and have verified its correctness, then continue to next step.

1. To verify that your files are deployed and check logs, expand the App Service you deployed, and then expand **Files**:

    ![Checking deployment files through the App Service explorer](media/deploy-azure/expand-files-node-to-check-deployment-of-web-app-files.png)

    The file *oryx-manifest.toml* is used by the App Service build system and the file *hostingstart.html* is the default app page.

    The *Logs* folder contains logs that can help in troubleshooting deployment problems. 

> [!div class="nextstepaction"]
> [I deployed my app - continue to step 6 >>>](tutorial-deploy-app-service-on-linux-06.md)

[Having issues? Let us know.](https://aka.ms/FlaskVSCQuickstartHelp)
