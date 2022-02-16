---
title: "ALM Accelerator for Power Platform advanced maker experience | MicrosoftDocs"
description: "The ALM Accelerator for Power Platform advanced maker experience will help you follow ALM patterns and practices. It enables you to source control your solutions and move them from your development environment to test and production environments using DevOps"
author: alvarezskinner
manager: devkeydet

ms.component: pa-admin
ms.topic: conceptual
ms.date: 10/14/2021
ms.subservice: guidance
ms.author: mapichle
ms.reviewer: jimholtz
search.audienceType: 
  - admin
search.app: 
  - D365CE
  - PowerApps
  - Powerplatform
---
# ALM Accelerator for Power Platform advanced maker experience (preview)

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

> [!NOTE]
> ALM Accelerator for Power Platform (AA4PP) is currently in public preview. Go to [Issues currently tagged as vnext](https://github.com/microsoft/coe-starter-kit/issues?q=is%3Aopen+is%3Aissue+label%3Aalm-accelerator+label%3Avnext) for the roadmap to be completed prior to general availability. While the tool is in public preview, there will be breaking changes and frequent updates to address feedback from preview members. Additionally, the public preview is reliant on the experimental [Power Apps Source File Pack and Unpack Utility](https://github.com/microsoft/PowerApps-Language-Tooling) that is being developed separately from AA4PP.

## Demo: ALM Accelerator advanced maker experience

Watch how to use the ALM Accelerator for Power Platform solution.
[Demo Videos](https://github.com/microsoft/coe-starter-kit/blob/main/CenterofExcellenceALMAccelerator/WALKTHROUGHS.md)

## Walk-through: ALM Accelerator advanced maker experience

> [!IMPORTANT]
> The following user experience has been configured using the ALM Accelerator for Power Platform Administration app that is installed with the ALM accelerator solution. For more information on how to use the administration app and configure and share experiences, see [Creating user settings and profiles](setup-almacceleratorpowerplatform-deployment-profiles.md)

1. Once you have installed and configured the app, start it from your environment under **Apps** by selecting **ALM Accelerator for Power Platform**.

1. When you're prompted to create connections and grant consent, create the necessary connections or accept the consent dialog.

1. If you're prompted to create an HTTP with Azure Active Directory (AD) connection, enter 'https://graph.microsoft.com' for both the **Base Resource URL** and **Azure AD Resource URI**.

1. Select **Create** for each connection when prompted.

1. The first time you open the app a dialog opens and you are asked to select an **Environment**. Next time you open the app, it will remember which environment you were working on.

1. Once the environment is selected, the main screen displays a list of all the unmanaged solutions in the environment. Depending on the *user deployment settings* your user has assigned, you'll be able to see the following options for each solution:

   - **Commit Solution**: Commits all the changes you have done within the solution in your version control system. Additionally, the commit will create your deployment pipelines in Azure DevOps as part of the commit process.
   - **Deploy Solution**: Allows you to move the changes across environment.
   - **Choose a Profile**: Allows you to configure what organization, project, repository, target branch, and environments your solution can be deployed to.
   - **Delete Solution**: Deletes the solution allowing you to reimport if necessary from source control again with the latest changes.
   - **Import Solution**: Imports an unmanaged solution into your maker environment from source control.
   - **Request History**: (right arrow icon): Provides a list of requests (commits and deployments) requested and completed for that solution.

   ![Solution List](media/almacceleratorpowerplatform-components/aa4pp-main-screen.png "Solution List")

1. You can now create a new solution from the make.powerapps.com or import an unmanaged solution from an existing DevOps project to begin making changes to it. To import a solution, select **Import Solution**, and then select a **Profile, Solution Source, Solution Folder**, and **Configuration**.

   - **Profile**: the configured profiles your user has access to, this profile points to an organization and project in DevOps.

   - **Solution Source**: is based on the branches in DevOps for the project you selected in the configuration.

   - **Solution Folder**: is a list of folders in the selected branch that contain a **SolutionPackage folder** from a previous export.

   - **Configuration** (Optional): is a directory under the config directory in the **Solution Folder** that contains deployment settings and configuration data. For more information about configuration settings, go to the [Deployment Configuration Guide](setup-almacceleratorpowerplatform-deployment-config.md).

    > [!NOTE]
    > You're either pulling the latest changes from the solution branch or you'll want to pull another makers branch into your own environment. The configuration allows you to ensure that all of the necessary post solution import configuration and data exists in your environment.

   ![Import Solution from branch in DevOps](media/almacceleratorpowerplatform-components/aa4pp-solution-import.png "Import Solution from branch in DevOps")

1. Once you have created or imported your solution, you are going to **Choose a Profile** for the solution so you can associate the solution to a specific organization, project, repository, target branch, and environments where you'll be able to deploy the solution.

   - Select **Choose a Profile** for your solution in the solution list.
   - In the Solution Profile dialog, select a **Profile** and then select **Save**.

    > [!NOTE]
    > Depending on whether you are an admin or not, you'll be able to create new deployment profiles from here. If you are a maker, an administrator from your organization might have made some profiles available for you to choose from. If the profile you want isn't available, contact your administrator to request a new profile.

1. Once you have a profile associated, you can begin to configure your solution for deployment. Select the **Configure Deployment Settings** link under the name of the solution. On the configuration deployment page, the following items appear:

   - **Deployment Environment List** (for example, validation, test, and production)

     - The environments listed are the ones configured in the deployment steps in the deployment profiles created by the administrator.

   - **Connection References**

      :::image type="content" source="media/almacceleratorpowerplatform-components/aa4pp-deployment-settings-connection-references.png" alt-text="Connection Reference configuration":::

      - This screen lists all of the connection references in your solution and allows users to create connections in their downstream environments to hook up the connection references in the target environment.
      - To create a new connection, select **+**.
      - After creating a new connection, select **Refresh** in the top right to get the latest list of connections.
      - To select an existing connection in the target environment, select a connection from the dropdown list.
      - To locate the connection in the target environment, select the name or the status of the connection.

   - **Environment Variables**

      :::image type="content" source="media/almacceleratorpowerplatform-components/aa4pp-deployment-settings-environment-vars.png" alt-text="Environment Variables configuration":::

      - This screen lists all of the environment variables in your solution and allows users to set the value of the environment variables in the downstream environment.
      - For standard environment variables, such as string, number, or JSON, enter the value in the text box to the right of the environment variable name.
      - For data source environment variables, use the dropdown lists to select the appropriate data source to use in the downstream environment.

   - **App Sharing**

      :::image type="content" source="media/almacceleratorpowerplatform-components/aa4pp-deployment-settings-app-sharing.png" alt-text="App Sharing Configuration":::

      - This screen lists all of the apps in your solution and allows users to share the apps in the downstream environment with an Azure Active Directory (AD) Group.
      - Use  the dropdown list to select the **Azure AAD group** with which you'd like to share the app.
      - To view the group details, select the details icon. This button opens a new browser tab with a link to the Azure AD Group in the Azure portal.
      - To set the permissions, select the permissions dropdown list and set the permissions to either **Can View**, **Can Edit**, or **Can View and Share**.

   - **Component Ownership**

      :::image type="content" source="media/almacceleratorpowerplatform-components/aa4pp-deployment-settings-comp-ownership.png" alt-text="Component Ownership configuration":::

      - This screen lists all of the flows in your solution. Users can configure the owner of the flow in the downstream environment by selecting a Dataverse user.
      - Use the dropdown list to select a Dataverse user to own the flow in the downstream environment.
      - To view the flow, select the name of the flow to open a new tab with the flow definition.

1. Once you've configured your solution, you can push your changes to Git using the **Commit Solution** command for your solution. Depending on the permissions you are given, there's a toggle to **Show Advanced** options. **Show Advanced** allows you to choose an existing branch or to create a new one with a specific naming convention. When not given permission to these options, the app creates a new branch based on your user name and deployment profile data.

   > [!NOTE]
   > Be sure to publish any app changes before initiating the push.

1. Select **Commit Solution**.

 1. In the Commit Solution dialog, select an existing branch, or create a new branch based on an existing branch and enter a comment. Use the hashtag notation for example `#123` to link the changes to a specific work item in DevOps and then select **Prepare Solution**.
 
   - After configuring and confirming your solution configuration as described in the previous step, select **Commit Solution** in the **Commit Solution** dialog.
   - When the push begins, a waiting indicator appears. When the push is successful, a checkbox appears, otherwise a red x is displayed. To see the progress of your push, select the progress indicator, which takes you to the running pipeline in DevOps.
   - Repeat the pushes as you iterate on your solution.

   > [!NOTE]
   > Using the progress icons links to visualize what is happening in the pipelines in DevOps can be disabled for makers.

1. Once you have finished the changes in your solution and you are ready to deploy them across other environments using the **Deploy Solution** button.

    > [!NOTE]
    > Be sure to publish any App changes before initiating the push.

    Depending on the permissions, the **Advanced Settings** toggle is displayed.

    - With the **Advanced Settings** toggle off, choose the environment you want to deploy to and use the **Deploy Solution** button.

    - Using the **Advanced Settings** specify the **Source** and **Target** branch and enter a **Title** and **Comment** for your pull request and then select **Deploy Solution**.

1. Once you deploy the solution, the next steps depend on the approval type of the deployment step.

     - **Pull Request**: A pull request is created for your changes, the remaining steps to merge and release to test occur in DevOps. Depending on the branch policies and triggers configured for your target branch, a DevOps user can approve or reject your pull request based on their findings in the submitted changes. The status of the pull request appears in the app.

     - **Environment**: The pipeline to deploy the solution to the target environment will be triggered, the remaining approval steps will occur in DevOps.

1. To initiate a solution upgrade in the target environment, you can tag a pull request with the **solution-upgrade** tag.

1. Approving the pull request or the pipeline execution (depending on the approval type selected for the step/environment) starts the deployment of your solution to the selected environment. If you get the approval for either your pull request or pipeline execution, the progress indicator states the deployment has started. You can select the right chevron icon to visualize the request history.

      ![Request History for a solution](media/almacceleratorpowerplatform-components/aa4pp-request-history.png "Request History for a solution")

1. For production, you can either go into **Advanced settings** for the deployment and choose the main branch used to trigger the deployment to production, or create the pull request directly in DevOps.
   [!INCLUDE[footer-include](../../includes/footer-banner.md)]