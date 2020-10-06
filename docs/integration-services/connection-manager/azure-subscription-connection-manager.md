---
description: Azure サブスクリプション接続マネージャー
title: Azure サブスクリプション接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afpsubscrconn.f1
- sql14.dts.designer.afpsubscrconn.f1
ms.assetid: e1225327-c308-4c50-8f44-c411f52ef378
author: chugugrace
ms.author: chugu
ms.openlocfilehash: da836cc7f53f4a4d83aae28ea2a41ec646ca3bd0
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91728073"
---
# <a name="azure-subscription-connection-manager"></a>Azure サブスクリプション接続マネージャー

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  **Azure サブスクリプション接続マネージャー** を使用すると、Azure サブスクリプション ID と管理証明書のプロパティに指定した値を使用して、SSIS パッケージを Azure サブスクリプションに接続できます。  
  
 **Azure サブスクリプション接続マネージャー**は、[SQL Server Integration Services (SSIS) Feature Pack for Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md) のコンポーネントです。
  
1.  上記の **[SSIS 接続マネージャーの追加]** ダイアログ ボックスで **[Azure サブスクリプション]** を選択し、 **[追加]** をクリックします。  次の **[Azure Subscription Connection Manager Editor]** (Azure サブスクリプション接続マネージャー エディター) ダイアログ ボックスが表示されます。  
  
    ![SSIS-AzureSubscriptionConnectionManager](../../integration-services/connection-manager/media/ssis-azuresubscriptionconnectionmanager.png)
  
2.  **[Azure サブスクリプション ID]** には、Azure サブスクリプションを一意に識別する Azure サブスクリプション ID を入力します。  この値は、 [Azure 管理ポータル](https://manage.windowsazure.com) の **[設定]** ページで確認できます。  
  
    ![SSIS-AzureSettings-SubscriptionID](../../integration-services/connection-manager/media/ssis-azuresettings-subscriptionid.png "SSIS-AzureSettings-SubscriptionID")  
  
3.  ドロップダウン リストから **[Management certificate store location (管理証明書ストアの場所)]** と **[Management certificate store name (管理証明書ストアの名前)]** を選択します。  
  
4.  **管理証明書の拇印**を入力するか、**[参照]** をクリックして、選択したストアから証明書を選択します。 証明書は、サブスクリプションの管理証明書としてアップロードする必要があります。 これを行うには、Azure Portal の次のページで **[アップロード]** をクリックします (詳細については、こちらの [MSDN の投稿](/previous-versions/azure/gg551722(v=azure.100))を参照)。  
  
     ![SSIS-AzureSettings-ManagementCertificate](../../integration-services/connection-manager/media/ssis-azuresettings-managementcertificate.png "SSIS-AzureSettings-ManagementCertificate")  
  
5.  **[接続テスト]** をクリックして接続をテストします。  
  
6.  **[OK]** をクリックしてダイアログ ボックスを閉じます。  
  
