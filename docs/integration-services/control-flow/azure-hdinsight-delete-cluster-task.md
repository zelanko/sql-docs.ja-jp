---
title: Azure HDInsight クラスターの削除タスク | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afpdelcltask.f1
- sql14.dts.designer.afpdelcltask.f1
ms.assetid: e298776e-d18a-4393-a8e6-65ee3d555749
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 87bbb8455169ae0c50475781b3b9e25e9967fd93
ms.sourcegitcommit: 4b775a3ce453b757c7435cc2a4c9b35d0c5a8a9e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/31/2020
ms.locfileid: "87472553"
---
# <a name="azure-hdinsight-delete-cluster-task"></a>Azure HDInsight クラスターの削除タスク

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


**Azure HDInsight クラスターの削除タスク**を使用すると、指定された Azure サブスクリプションとリソース グループの Azure HDInsight クラスターを SSIS パッケージで削除できます。
  
**Azure HDInsight クラスターの削除タスク**は、[SQL Server Integration Services (SSIS) Feature Pack for Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md) のコンポーネントです。
  
> [!NOTE]
> HDInsight クラスターの削除には 10 分から 20 分かかる場合があります。  
  
**Azure HDInsight クラスターの削除タスク**を追加するには、SSIS デザイナーにドラッグ アンド ドロップし、ダブルクリックまたは右クリックして、 **[編集]** をクリックすると、次の **[Azure HDInsight クラスターの削除タスク エディター]** ダイアログ ボックスが表示されます。  
  
次の表で、ダイアログ ボックスの各フィールドについて説明します。  
  
|フィールド|説明|  
|-|-|  
|AzureResourceManagerConnection|既存の Azure Resource Manager 接続マネージャーを選択するか、HDInsight クラスターを削除するために使用する新しいものを作成します。|
|SubscriptionId|HDInsight クラスターが存在するサブスクリプションの ID を指定します。|
|ResourceGroup|HDInsight クラスターが存在する Azure リソース グループを指定します。|
|ClusterName|削除するクラスターの名前を指定します。|  
|FailIfNotExists|クラスターが存在しない場合に、タスクがエラーになるかどうかを指定します。|
