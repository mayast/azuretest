<properties
	pageTitle="Use Mobile Services to upload images to blob storage (Windows Phone) | Microsoft Azure"
	description="Learn how to use Mobile Services to upload images to Azure Blob Storage."
	documentationCenter="windows"
	authors="ggailey777"
	services="mobile-services,storage"
	manager="dwrede"
	editor=""/>

<tags
	ms.service="mobile-services"
	ms.workload="mobile"
	ms.tgt_pltfrm="mobile-windows-phone"
	ms.devlang="dotnet"
	ms.topic="article"
	ms.date="06/16/2015"
	ms.author="glenga"/>

# Upload images to Azure Storage by using Mobile Services

[AZURE.INCLUDE [mobile-services-selector-upload-data-blob-storage](../../includes/mobile-services-selector-upload-data-blob-storage.md)]

##Overview
This topic shows you how to use Azure Mobile Services to enable your Windows Phone 8 or Windows Phone 8.1 Silverlight app to upload and store user-generated images in Azure Storage. Mobile Services uses a SQL Database to store data. However, binary large object (BLOB) data is more efficiently stored in Azure Blob storage service. 

You cannot securely distribute with the client app the credentials required to securely upload data to the Blob Storage service. Instead, you must store these credentials your mobile service and use them to generate a Shared Access Signature (SAS) that is used to upload a new image. The SAS, a credential with a short expiration&mdash;in this case 5 minutes, is returned securely by Mobile Services to the client app. The app then uses this temporary credential to upload the image. In this example, downloads from the Blob service are public.

In this tutorial, you add functionality to the [GetStartedWithData sample app project](mobile-services-dotnet-backend-windows-phone-get-started-data.md) to take pictures and upload the images to Azure by using an SAS generated by Mobile Services.

##Prerequisites

This tutorial requires the following:

+ Microsoft Visual Studio 2013, or a later version
+ [Windows Phone SDK 8.0] or higher
+ Nuget Package Manager installed for Microsoft Visual Studio.
+ [Azure Storage account][How To Create a Storage Account]
+ Complete the tutorial [Add Mobile Services to an existing app](mobile-services-dotnet-backend-windows-phone-get-started-data.md)  

>[AZURE.NOTE]This tutorial only support Windows Phone 8 and Windows Phone 8.1 Silverlight apps. It does not support Windows Phone Store 8.1 or universal Windows 8.1 apps.

[AZURE.INCLUDE [mobile-services-dotnet-backend-configure-blob-storage](../../includes/mobile-services-dotnet-backend-configure-blob-storage.md)]

##<a name="install-storage-client"></a>Install the Storage client for Windows Store apps

To be able to use an SAS to upload images from your app to Blob storage, you must first add the NuGet package that installs Storage client library for Windows Store apps.

1. In **Solution Explorer** in Visual Studio, right-click the client app project and select **Manage NuGet Packages**.

2. In the left pane, select the **Online** category, select **Include Prerelease**, search for **WindowsAzure.Storage-Preview**, click **Install** on the **Azure Storage** package, then accept the license agreements.

  	![][2]

  	This adds the client library for Azure storage services to the project.

[AZURE.INCLUDE [mobile-services-windows-phone-upload-to-blob-storage](../../includes/mobile-services-windows-phone-upload-to-blob-storage.md)]

<!-- Anchors. -->
[Install the Storage Client library]: #install-storage-client
[Update the client app to capture images]: #add-select-images
[Install the storage client in the mobile service project]: #storage-client-server
[Update the TodoItem definition in the data model]: #update-data-model
[Update the table controller to generate an SAS]: #update-scripts
[Upload images to test the app]: #test
[Next Steps]:#next-steps

<!-- Images. -->
[2]: ./media/mobile-services-dotnet-backend-windows-phone-upload-data-blob-storage/mobile-add-storage-nuget-package-dotnet.png

<!-- URLs. -->
[Send email from Mobile Services with SendGrid]: store-sendgrid-mobile-services-send-email-scripts.md
[Schedule backend jobs in Mobile Services]: mobile-services-dotnet-backend-schedule-recurring-tasks.md
[Get started with Mobile Services]: ../mobile-services-windows-phone-get-started.md

[Azure Management Portal]: https://manage.windowsazure.com/
[How To Create a Storage Account]: ../storage-create-storage-account.md
[Azure Storage Client library for Store apps]: http://go.microsoft.com/fwlink/p/?LinkId=276866
[Mobile Services .NET How-to Conceptual Reference]: mobile-services-windows-dotnet-how-to-use-client-library.md
[Windows Phone SDK 8.0]: http://www.microsoft.com/download/details.aspx?id=35471