---
title: "Azure HDInsight Create Cluster Task | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "02/28/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.afpcreatecltask.f1"
  - "sql14.dts.designer.afpcreatecltask.f1"
ms.assetid: a8ec413a-38d3-45df-887e-6f5f4d9f8465
caps.latest.revision: 11
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# Azure HDInsight Create Cluster Task
  **Azure HDInsight Create Cluster Task** を使用すると、指定された Azure サブスクリプションの Azure HDInsight クラスターを SSIS パッケージで作成できます。  
  
 **Azure HDInsight Create Cluster Task** は、SQL Server 2016. 用の SQL Server Integration Services (SSIS) Feature Pack for Azure のコンポーネントです。 Feature Pack は [こちら](http://go.microsoft.com/fwlink/?LinkID=626967)からダウンロードしてください。  
  
> [!NOTE]  
>  -   通常、新しい HDInsight クラスターを作成するには 10 分かかります。  
> -   Azure HDInsight クラスターの作成と実行には、料金がかかります。 詳細については、「[HDInsight の価格](http://azure.microsoft.com/en-us/pricing/details/hdinsight/)」を参照してください。  
  
 **Azure HDInsight Create Cluster Task** を追加するには、SSIS デザイナーにドラッグ アンド ドロップし、ダブルクリックまたは右クリックして、**[編集]** をクリックします。すると、次の **[Azure HDInsight Create Cluster Task エディター]** ダイアログ ボックスが表示されます。  
  
 次の表で、このダイアログ ボックスの各フィールドについて説明します。  
  
|||  
|-|-|  
|**フィールド**|**Description**|  
|AzureSubscriptionConnection|既存の Azure サブスクリプション接続マネージャーを選ぶか、HDInsight クラスターをホストする Azure サブスクリプションを参照する新しい接続マネージャーを作成します。|  
|AzureStorageConnection|既存の Azure ストレージ接続マネージャーを選ぶか、HDInsight クラスターに関連付けられている Azure ストレージ アカウントを参照する新しい接続マネージャーを作成します。|  
|場所|HDInsight クラスターの場所を指定します。 クラスターは、Azure Storage と同じ場所に作成する必要があります。|  
|ClusterName|作成する HDInsight クラスターの名前を指定します。|  
|ClusterSize|クラスターに含めるノードの数を指定します。|  
|BlobContainer|HDInsight クラスターに関連付けられる既定のストレージ コンテナーの名前を指定します。|  
|UserName|クラスターにアクセスできるユーザーの名前を指定します。|  
|Password|そのユーザーのパスワードを指定します。|  
|FailIfExists|クラスターが既に存在する場合に、タスクがエラーになるかどうかを指定します。|  
  
> [!NOTE]  
>  HDInsight クラスターの場所と Azure Storage の場所は同じである必要があります。  
  
  