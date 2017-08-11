---
title: "Azure Storage Connection Manager |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.afpstorageconn.f1
- sql14.dts.designer.afpstorageconn.f1
ms.assetid: 68bd1d04-d20f-4357-a34e-7c9c76457062
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 848b0f0e3e639d31fa739e8d744fc4b80839a5fd
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="azure-storage-connection-manager"></a>Azure Storage 接続マネージャー
  **Azure Storage 接続マネージャー** は、SSIS パッケージがストレージ アカウント名プロパティとアカウント キー プロパティに指定された値を使用して Azure Storage アカウントに接続することを可能にします。  
   
 **Azure Storage 接続マネージャー**のコンポーネントである、 [SQL Server Integration Services (SSIS) Feature Pack for Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md)です。 
  
1.  **[SSIS 接続マネージャーの追加]** ダイアログ ボックスで **[AzureStorage]**(AzureStorage) を選択し、 **[追加]**をクリックします。  
  
2.  Azure Storage 接続マネージャー エディター ダイアログ ボックスで、インターネット経由で Azure Storage サービスに接続する場合は **[Use Azure account]** (Azure アカウントを使用する) を選択し、Azure Storage エミュレーターによってホストされているローカル サービスに接続する場合は **[Use local developer account]** (ローカル開発者アカウントを使用する) を選択します。  
  
3.  **[Use Azure account]** (Azure アカウントを使用する) オプションを選択した場合は、次の操作を行います。  
  
    1.  **[Storage account name]** (ストレージ アカウント名) フィールドと **[Account key]** (アカウント キー) フィールドに値を指定します。 これらの値は、SSIS パッケージ内で機微なデータとして保存されます。  
  
    2.  Azure Storage サービスへの接続に HTTP ではなく HTTPS を使用する場合は、 **[Use HTTPS]** (HTTPS を使用する) を選択します。  
  
4.  **[OK]** をクリックして、ダイアログ ボックスを閉じます。  
  
5.  作成した接続マネージャーのプロパティは、 **[プロパティ]** ウィンドウに表示されます。  
  
  

