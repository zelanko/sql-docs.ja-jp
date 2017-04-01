---
title: "Azure サブスクリプション接続マネージャー | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.afpsubscrconn.f1"
  - "sql14.dts.designer.afpsubscrconn.f1"
ms.assetid: e1225327-c308-4c50-8f44-c411f52ef378
caps.latest.revision: 11
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 10
---
# Azure サブスクリプション接続マネージャー
  **Azure サブスクリプション接続マネージャー**を使用すると、Azure サブスクリプション ID と管理証明書のプロパティに指定した値を使用して、SSIS パッケージを Azure サブスクリプションに接続できます。  
  
 **Azure サブスクリプション接続マネージャー**は、SQL Server 2016 用の SQL Server Integration Services (SSIS) Feature Pack for Azure のコンポーネントです。 Feature Pack は [こちら](http://go.microsoft.com/fwlink/?LinkID=626967)からダウンロードしてください。  
  
1.  上記の **[SSIS 接続マネージャーの追加]** ダイアログ ボックスで **[Azure サブスクリプション]**を選択し、 **[追加]**をクリックします。  次の **[Azure Subscription Connection Manager Editor]** (Azure サブスクリプション接続マネージャー エディター) ダイアログ ボックスが表示されます。  
  
    ![SSIS-AzureSubscriptionConnectionManager](../../integration-services/connection-manager/media/ssis-azuresubscriptionconnectionmanager.png)
  
2.  **[Azure サブスクリプション ID]**には、Azure サブスクリプションを一意に識別する Azure サブスクリプション ID を入力します。  この値は、 [Azure 管理ポータル](https://manage.windowsazure.com) の **[設定]** ページで確認できます。  
  
    ![SSIS-AzureSettings-SubscriptionID](../../integration-services/connection-manager/media/ssis-azuresettings-subscriptionid.png "SSIS-AzureSettings-SubscriptionID")  
  
3.  ドロップダウン リストから **[Management certificate store location (管理証明書ストアの場所)]** と **[Management certificate store name (管理証明書ストアの名前)]** を選択します。  
  
4.  **[Management certificate thumbprint (管理証明書のサムプリント)]** を入力するか、または **[参照…]** をクリックして、選択したストアから証明書を選択します。 証明書は、サブスクリプションの管理証明書としてアップロードする必要があります。 これを行うには、Azure ポータルの次のページで **[アップロード]** をクリックします (詳細については、こちらの [MSDN の投稿](https://msdn.microsoft.com/library/azure/gg551722.aspx)を参照)。  
  
     ![SSIS-AzureSettings-ManagementCertificate](../../integration-services/connection-manager/media/ssis-azuresettings-managementcertificate.png "SSIS-AzureSettings-ManagementCertificate")  
  
5.  **[接続テスト]** をクリックして接続をテストします。  
  
6.  **[OK]** をクリックして、ダイアログ ボックスを閉じます。  
  
  