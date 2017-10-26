---
title: "Azure の HDInsight クラスターのタスクの作成 |Microsoft ドキュメント"
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
- sql13.dts.designer.afpcreatecltask.f1
- sql14.dts.designer.afpcreatecltask.f1
ms.assetid: a8ec413a-38d3-45df-887e-6f5f4d9f8465
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 71a24dc15253916c32b07e6024e2ab32514c9d39
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="azure-hdinsight-create-cluster-task"></a>Azure HDInsight Create Cluster Task
**Azure HDInsight Create Cluster Task** SSIS パッケージを指定した Azure サブスクリプションとリソース グループ内の Azure HDInsight クラスターを作成するようにします。
  
**Azure HDInsight Create Cluster Task**のコンポーネントである、 [SQL Server Integration Services (SSIS) Feature Pack for Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md)です。
  
> [!NOTE]  
> - 新しい HDInsight クラスターを作成すると、10 がかかる場合があります ~ 20 分です。  
> - 作成して、Azure の HDInsight クラスターの実行に関連するコストがあります。 参照してください[HDInsight の価格](http://azure.microsoft.com/en-us/pricing/details/hdinsight/)詳細についてはします。  
  
**Azure HDInsight Create Cluster Task**を追加するには、SSIS デザイナーにドラッグ アンド ドロップし、ダブルクリックまたは右クリックして、 **[編集]** をクリックします。すると、次の **[Azure HDInsight Create Cluster Task エディター]** ダイアログ ボックスが表示されます。  
  
次の表は、このダイアログ ボックスで、フィールドの説明を提供します。  
  
|||  
|-|-|  
|**フィールド**|**Description**|  
|AzureResourceManagerConnection|既存の Azure リソース マネージャーの接続マネージャーを選択するか、HDInsight クラスターの作成に使用される新しいものを作成します。|  
|AzureStorageConnection|既存の Azure ストレージ接続マネージャーを選ぶか、HDInsight クラスターに関連付けられている Azure ストレージ アカウントを参照する新しい接続マネージャーを作成します。|
|サブスクリプション Id|HDInsight クラスターを作成するサブスクリプションの ID を指定します。|
|リソース グループ|Azure リソース グループでクラスターを作成する HDInsight を指定します。|
|場所|HDInsight クラスターの場所を指定します。 クラスターは、指定された Azure ストレージ アカウントと同じ場所に作成する必要があります。|  
|ClusterName|作成する HDInsight クラスターの名前を指定します。|  
|ClusterSize|クラスターを作成するノードの数を指定します。|  
|BlobContainer|HDInsight クラスターに関連する既定のストレージ コンテナーの名前を指定します。|  
|UserName|HDInsight クラスターに接続するために使用するユーザー名を指定します。|  
|Password|HDInsight クラスターに接続するために使用するパスワードを指定します。|
|SshUserName|SSH を使用して HDInsight クラスターをリモートでアクセスするために使用するユーザー名を指定します。|
|SshPassword|SSH を使用して HDInsight クラスターをリモートでアクセスするためのパスワードを指定します。|
|FailIfExists|クラスターが既に存在する場合に、タスクがエラーになるかどうかを指定します。|  
  
> [!NOTE]  
> HDInsight クラスターと、Azure ストレージ アカウントの場所は、同じである必要があります。

