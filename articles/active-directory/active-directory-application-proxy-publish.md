<properties
	pageTitle="Publish apps with Azure AD Application Proxy | Microsoft Azure"
	description="Publish on-premises applications to the cloud with Azure AD Application Proxy."
	services="active-directory"
	documentationCenter=""
	authors="kgremban"
	manager="stevenpo"
	editor=""/>

<tags
	ms.service="active-directory"
	ms.workload="identity"
	ms.tgt_pltfrm="na"
	ms.devlang="na"
	ms.topic="get-started-article"
	ms.date="06/01/2016"
	ms.author="kgremban"/>


# Publish applications using Azure AD Application Proxy


After you enable Microsoft Azure Active Directory (AD) Application Proxy, you can publish on-premises applications so that remote users can access them outside the private network.

This article walks you through the steps to publish applications that are running on your local network and provide secure remote access from outside your network. If you haven't set up Application Proxy or installed any Connectors, follow the steps in [Enable Application Proxy in the Azure portal](active-directory-application-proxy-enable.md) before continuing here.

If this is your first time using Azure AD Application Proxy, we recommend you test the Connector by publishing a website from your private network before publishing applications.

> [AZURE.NOTE] Application Proxy is a feature that is available only if you upgraded to the Premium or Basic edition of Azure Active Directory. For more information, see [Azure Active Directory editions](active-directory-editions.md).

## Publish an app using the wizard

1. Sign in as an administrator in the [Azure classic portal](https://manage.windowsazure.com/).
2. Go to Active Directory and select the directory where you enabled Application Proxy.

	![Active Directory - icon](./media/active-directory-application-proxy-publish/ad_icon.png)

3. Click the **Applications** tab, and then click the **Add** button at the bottom of the screen

	![Add application](./media/active-directory-application-proxy-publish/aad_appproxy_selectdirectory.png)

4. Select **Publish an application that will be accessible from outside your network**.

	![Publish an application that will be accessible from outside your network](./media/active-directory-application-proxy-publish/aad_appproxy_addapp.png)

5. Provide the following information about your application:

	- **Name**: The user-friendly name for your application. It must be unique within your directory.
	- **Internal URL**: The address that the Application Proxy Connector uses to access the application from inside your private network. You can provide a specific path on the backend server to publish, while the rest of the server is unpublished. In this way you can publish different sites on the same server, and give each one its own name and access rules.
	- **Preauthentication Method**: The way Application Proxy will verify users before giving them access to your application. Choose one of the options from the drop-down menu.

		- Azure Active Directory: Application Proxy will redirect users to sign in with Azure AD, which authenticates their permissions for the directory and application.
		- Passthrough: Users don't have to authenticate to access the application.

	![Application properties](./media/active-directory-application-proxy-publish/aad_appproxy_appproperties.png)  

6. To finish the wizard, click the check mark at the bottom of the screen. The application is now defined in Azure AD.


## Assign users and groups to the application

In order for your users to access your published application, you need to assign them either individually or in groups. For apps that require preauthentication, this grants permissions to use the app. For apps that don't require preauthentication, users don't need permissions but still need to be assigned to the app so that it will appear in their application list.

1. After finishing the Add App wizard, you see the Quick Start page for your application. To manage who has access to the app, select **Users and groups**.

	![Application Proxy quick start assign users - screenshot](./media/active-directory-application-proxy-publish/aad_appproxy_usersgroups.png)

2. Search for specific groups in your directory, or show all your users. Click the check mark to display the results.

  	![Search for groups or users - screenshot](./media/active-directory-application-proxy-publish/aad_appproxy_search.png)

2. Select each user or group you want to assign to this app and click **Assign**. You will be asked to confirm this action.

> [AZURE.NOTE] For Integrated Windows Authentication apps, you can assign only users and groups that are synced from your on-premises Active Directory. Users who sign in with a Microsoft account and guests cannot be assigned for apps published with Azure Active Directory Application Proxy. Make sure your users sign in with credentials that are part of the same domain as the app you are publishing.


## Advanced configuration

You can modify published apps or set up advanced options on the Configure page. On this page, you can customize your app by changing the name or uploading a logo. You can also manage access rules like the preauthentication method or multi-factor authentication.

![Advanced configuration](./media/active-directory-application-proxy-publish/aad_appproxy_configure.png)


After you publish applications using Azure Active Directory Application Proxy, they appear in the Applications list in Azure AD, and you can manage them there.

If you disable Application Proxy services after you have published applications, the applications are not deleted, but will no longer be accessible from outside your private network.

To view an application and make sure it is accessible, double-click the name of the application. If the Application Proxy service is disabled and the application is not available, a warning message appears at the top of the screen.

To delete an application, select an application in the list and then click **Delete**.

## Next steps

- [Publish applications using your own domain name](active-directory-application-proxy-custom-domains.md)
- [Enable single-sign on](active-directory-application-proxy-sso-using-kcd.md)
- [Enable conditional access](active-directory-application-proxy-conditional-access.md)
- [Working with claims aware applications](active-directory-application-proxy-claims-aware-apps.md)

For the latest news and updates, check out the [Application Proxy blog](http://blogs.technet.com/b/applicationproxyblog/)
