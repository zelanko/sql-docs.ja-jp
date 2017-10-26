---
title: "Azure HDInsight Delete Cluster Task |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 02/28/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.afpdelcltask.f1
- sql14.dts.designer.afpdelcltask.f1
ms.assetid: e298776e-d18a-4393-a8e6-65ee3d555749
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f98b69e8bd3b2e78f6dd20a19ca17a83a834c3b3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="azure-hdinsight-delete-cluster-task"></a>Azure HDInsight クラスターの削除タスク
**Azure HDInsight クラスターの削除タスク**SSIS パッケージを指定された Azure サブスクリプションとリソース グループ内の Azure の HDInsight クラスターを削除するようにします。
  
**Azure HDInsight クラスターの削除タスク**のコンポーネントである、 [SQL Server Integration Services (SSIS) Feature Pack for Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md)です。
  
> [!NOTE]
> HDInsight クラスターを削除すると、10 がかかる場合があります ~ 20 分です。  
  
**Azure HDInsight クラスターの削除タスク**を追加するには、SSIS デザイナーにドラッグ アンド ドロップし、ダブルクリックまたは右クリックして、 **[編集]** をクリックすると、次の **[Azure HDInsight クラスターの削除タスク エディター]** ダイアログ ボックスが表示されます。  
  
次の表は、ダイアログ ボックスのフィールドの説明を提供します。  
  
|||  
|-|-|  
|**フィールド**|**Description**|  
|AzureResourceManagerConnection|既存の Azure リソース マネージャーの接続マネージャーを選択するか、HDInsight クラスターを削除するために使用する新しいものを作成します。|
|サブスクリプション Id|HDInsight クラスターが、サブスクリプションの ID を指定します。|
|リソース グループ|HDInsight クラスターを Azure リソース グループを指定します。|
|ClusterName|削除するクラスターの名前を指定します。|  
|FailIfNotExists|クラスターが存在しない場合に、タスクがエラーになるかどうかを指定します。|

