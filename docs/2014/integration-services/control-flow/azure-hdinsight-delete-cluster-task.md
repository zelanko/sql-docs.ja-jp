---
title: Azure HDInsight クラスターの削除タスク | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpdelcltask.f1
- sql11.dts.designer.afpdelcltask.f1
ms.assetid: e298776e-d18a-4393-a8e6-65ee3d555749
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 513faad27977b3a4aef9b1e4907c85cd3a2905be
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52767174"
---
# <a name="azure-hdinsight-delete-cluster-task"></a>Azure HDInsight クラスターの削除タスク
**Azure HDInsight クラスターの削除タスク**を使用すると、指定された Azure サブスクリプションとリソース グループの Azure HDInsight クラスターを SSIS パッケージで削除できます。
  
> [!NOTE]
> HDInsight クラスターの削除には 10 分から 20 分かかる場合があります。  
  
**Azure HDInsight クラスターの削除タスク**を追加するには、SSIS デザイナーにドラッグ アンド ドロップし、ダブルクリックまたは右クリックして、 **[編集]** をクリックすると、次の **[Azure HDInsight クラスターの削除タスク エディター]** ダイアログ ボックスが表示されます。  
  
次の表で、ダイアログ ボックスの各フィールドについて説明します。  
  
|||  
|-|-|  
|**フィールド**|**[説明]**|  
|AzureResourceManagerConnection|既存の Azure Resource Manager 接続マネージャーを選択するか、HDInsight クラスターを削除するために使用する新しいものを作成します。|
|SubscriptionId|HDInsight クラスターが存在するサブスクリプションの ID を指定します。|
|ResourceGroup|HDInsight クラスターが存在する Azure リソース グループを指定します。|
|ClusterName|削除するクラスターの名前を指定します。|  
|FailIfNotExists|クラスターが存在しない場合に、タスクがエラーになるかどうかを指定します。|
