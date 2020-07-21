---
title: Azure Storage 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpstorageconn.f1
- sql11.dts.designer.afpstorageconn.f1
ms.assetid: 68bd1d04-d20f-4357-a34e-7c9c76457062
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 47580d8d1d961df9fbcbed0bd7164f1c54792b86
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85434329"
---
# <a name="azure-storage-connection-manager"></a>Azure Storage 接続マネージャー
  Azure Storage 接続マネージャーは、SSIS パッケージがストレージ アカウント名プロパティとアカウント キー プロパティに指定された値を使用して Azure Storage アカウントに接続することを可能にします。  
  
1.  **[SSIS 接続マネージャーの追加]** ダイアログ ボックスで **[AzureStorage]**(AzureStorage) を選択し、 **[追加]** をクリックします。  
  
2.  Azure Storage 接続マネージャー エディター ダイアログ ボックスで、インターネット経由で Azure Storage サービスに接続する場合は **[Use Azure account]** (Azure アカウントを使用する) を選択し、Azure Storage エミュレーターによってホストされているローカル サービスに接続する場合は **[Use local developer account]** (ローカル開発者アカウントを使用する) を選択します。  
  
3.  **[Use Azure account]** (Azure アカウントを使用する) オプションを選択した場合は、次の操作を行います。  
  
    1.  **[Storage account name]** (ストレージ アカウント名) フィールドと **[Account key]** (アカウント キー) フィールドに値を指定します。 これらの値は、SSIS パッケージ内で機微なデータとして保存されます。  
  
    2.  Azure Storage サービスへの接続に HTTP ではなく HTTPS を使用する場合は、 **[Use HTTPS]** (HTTPS を使用する) を選択します。  
  
4.  **[OK]** をクリックしてダイアログ ボックスを閉じます。  
  
5.  作成した接続マネージャーのプロパティは、 **[プロパティ]** ウィンドウに表示されます。  
  
  
