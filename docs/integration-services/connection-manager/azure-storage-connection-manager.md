---
title: "Azure Storage 接続マネージャー | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: connection-manager
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.afpstorageconn.f1
- sql14.dts.designer.afpstorageconn.f1
ms.assetid: 68bd1d04-d20f-4357-a34e-7c9c76457062
caps.latest.revision: "13"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cc320994dba6dc2b6f2207d5a6aad9e9c193d515
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="azure-storage-connection-manager"></a>Azure Storage 接続マネージャー
  **Azure Storage 接続マネージャー** は、SSIS パッケージがストレージ アカウント名プロパティとアカウント キー プロパティに指定された値を使用して Azure Storage アカウントに接続することを可能にします。  
   
 **Azure Storage 接続マネージャー**は、[SQL Server Integration Services (SSIS) Feature Pack for Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md) のコンポーネントです。 
  
1.  **[SSIS 接続マネージャーの追加]** ダイアログ ボックスで **[AzureStorage]**(AzureStorage) を選択し、 **[追加]**をクリックします。  
  
2.  Azure Storage 接続マネージャー エディター ダイアログ ボックスで、インターネット経由で Azure Storage サービスに接続する場合は **[Use Azure account]** (Azure アカウントを使用する) を選択し、Azure Storage エミュレーターによってホストされているローカル サービスに接続する場合は **[Use local developer account]** (ローカル開発者アカウントを使用する) を選択します。  
  
3.  **[Use Azure account]** (Azure アカウントを使用する) オプションを選択した場合は、次の操作を行います。  
  
    1.  **[Storage account name]** (ストレージ アカウント名) フィールドと **[Account key]** (アカウント キー) フィールドに値を指定します。 これらの値は、SSIS パッケージ内で機微なデータとして保存されます。  
  
    2.  Azure Storage サービスへの接続に HTTP ではなく HTTPS を使用する場合は、 **[Use HTTPS]** (HTTPS を使用する) を選択します。  
  
4.  **[OK]** をクリックして、ダイアログ ボックスを閉じます。  
  
5.  作成した接続マネージャーのプロパティは、 **[プロパティ]** ウィンドウに表示されます。  
  
  
