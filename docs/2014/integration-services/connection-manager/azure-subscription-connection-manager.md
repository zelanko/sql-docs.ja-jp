---
title: Azure サブスクリプション接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.afpsubscrconn.f1
- sql11.dts.designer.afpsubscrconn.f1
ms.assetid: e1225327-c308-4c50-8f44-c411f52ef378
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 878f8fc674659d91a732549fcd68da134cdf5fc4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178501"
---
# <a name="azure-subscription-connection-manager"></a>Azure サブスクリプション接続マネージャー
  Azure HDInsight 接続マネージャーを使用してプロパティを指定する値を使用して、Azure サブスクリプションに接続する SSIS パッケージ: Azure サブスクリプション ID と管理証明書。  
  
1.  上記の **[SSIS 接続マネージャーの追加]** ダイアログ ボックスで **[Azure サブスクリプション]** を選択し、 **[追加]** をクリックします。  次の **[Azure Subscription Connection Manager Editor]** (Azure サブスクリプション接続マネージャー エディター) ダイアログ ボックスが表示されます。  
  
     ![SSIS AzureSubscriptionManager](../media/ssis-azuresubscriptionmanager.png "SSIS AzureSubscriptionManager")  
  
2.  **[Azure サブスクリプション ID]** には、Azure サブスクリプションを一意に識別する Azure サブスクリプション ID を入力します。  この値は、 [Azure 管理ポータル](https://manage.windowsazure.com) の **[設定]** ページで確認できます。  
  
     ![SSIS-AzureSettings-SubscriptionID](../media/ssis-azuresettings-subscriptionid.png "SSIS-AzureSettings-SubscriptionID")  
  
3.  ドロップダウン リストから **[Management certificate store location (管理証明書ストアの場所)]** と **[Management certificate store name (管理証明書ストアの名前)]** を選択します。  
  
4.  **[Management certificate thumbprint (管理証明書のサムプリント)]** を入力するか、または **[参照…]** をクリックして、選択したストアから証明書を選択します。 証明書は、サブスクリプションの管理証明書としてアップロードする必要があります。 これを行うには、Azure ポータルの次のページで **[アップロード]** をクリックします (詳細については、こちらの [MSDN の投稿](https://msdn.microsoft.com/library/azure/gg551722.aspx) を参照)。  
  
     ![SSIS-AzureSettings-ManagementCertificate](../media/ssis-azuresettings-managementcertificate.png "SSIS-AzureSettings-ManagementCertificate")  
  
5.  **[接続テスト]** をクリックして接続をテストします。  
  
6.  **[OK]** をクリックしてダイアログ ボックスを閉じます。  
  
  