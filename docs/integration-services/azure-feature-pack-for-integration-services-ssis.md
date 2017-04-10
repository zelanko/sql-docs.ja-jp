---
title: "Integration Services (SSIS) 用の Azure Feature Pack | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SQL13.SSIS.AZURE.F1"
  - "SQL14.SSIS.AZURE.F1"
ms.assetid: 31de555f-ae62-4f2f-a6a6-77fea1fa8189
caps.latest.revision: 19
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 15
---
# Integration Services (SSIS) 用の Azure Feature Pack
  SQL Server Integration Services (SSIS) Feature Pack for Azure for SQL Server 2016 は、SSIS の次のコンポーネントを提供して、Azure への接続、Azure とオンプレミスのデータ ソース間でのデータ転送、Azure に格納されたデータの処理を行うための拡張機能です。

[![SSIS Feature Pack for Azure のダウンロード](../analysis-services/media/download.png)](http://go.microsoft.com/fwlink/?LinkID=626967) **[SSIS Feature Pack for Azure for SQL Server 2016 のダウンロード](http://go.microsoft.com/fwlink/?LinkID=626967)**


-   接続マネージャー

    -   [Azure Storage 接続マネージャー](../integration-services/connection-manager/azure-storage-connection-manager.md)

    -   [Azure サブスクリプション接続マネージャー](../integration-services/connection-manager/azure-subscription-connection-manager.md)
    
    -   [Azure Data Lake Store 接続マネージャー](../integration-services/connection-manager/azure-data-lake-store-connection-manager.md)

-   処理手順

    -   [Azure BLOB のアップロード タスク](../integration-services/control-flow/azure-blob-upload-task.md)

    -   [Azure BLOB のダウンロード タスク](../integration-services/control-flow/azure-blob-download-task.md)

    -   [Azure HDInsight Hive タスク](../integration-services/control-flow/azure-hdinsight-hive-task.md)

    -   [Azure HDInsight Pig タスク](../integration-services/control-flow/azure-hdinsight-pig-task.md)

    -   [Azure HDInsight クラスターの作成タスク](../integration-services/control-flow/azure-hdinsight-create-cluster-task.md)

    -   [Azure HDInsight クラスターの削除タスク](../integration-services/control-flow/azure-hdinsight-delete-cluster-task.md)
    
    -   [Azure SQL DW のアップロード タスク](../integration-services/control-flow/azure-sql-dw-upload-task.md)

-   データ フロー コンポーネント

    -   [Azure BLOB Source](../integration-services/data-flow/azure-blob-source.md)

    -   [Azure Blob Destination](../integration-services/data-flow/azure-blob-destination.md)
    
    -   [Azure Data Lake Store Source](../integration-services/data-flow/azure-data-lake-store-source.md)
    
    -   [Azure Data Lake Store Destination](../integration-services/data-flow/azure-data-lake-store-destination.md)

-   Azure Blob 列挙子。 [列挙子 = Foreach Azure Blob 列挙子](../../../Topic/Foreach%20Loop%20Editor%20\(Collection%20Page\).md#ForeachAzureBlob)

## <a name="download-the-feature-pack"></a>Feature Pack のダウンロード
 SQL Server Integration Services (SSIS) Feature Pack for Azure for SQL Server 2016 は、 [ここ](http://go.microsoft.com/fwlink/?LinkID=626967)からダウンロードします。

## <a name="prerequisites"></a>前提条件
 この機能パックをインストールする前に、次の前提条件をインストールする必要があります。

-   SQL Server Integration Services

-   .NET Framework 4.5

## <a name="scenario-processing-big-data"></a>シナリオ: ビッグ データの処理
 Azure コネクタを使用して、次のビッグ データの処理を完了します。

1.  Azure Blob Upload Task を使用して、入力データを Azure Blob ストレージにアップロードします。

2.  Azure HDInsight Create Cluster Task を使用して、Azure HDInsight のクラスターを作成します。 独自のクラスターを使用する場合は、この手順は省略できます。

3.  Azure HDInsight Hive Task か Azure HDInsight Pig Task を使用して、Azure HDInsight クラスターで Pig または Hive ジョブを呼び出します。

4.  手順 2 でオンデマンドの HDInsight クラスターを作成した場合は、使用後の HDInsight クラスターを Azure HDInsight Delete Cluster Task で削除します。

5.  Azure HDInsight Blob Download Task を使用して、Azure Blob ストレージから Pig/Hive の出力データをダウンロードします。

![SSIS-AzureConnector-BigDataScenario](../integration-services/media/ssis-azureconnector-bigdatascenario.png)
 
## <a name="scenario-managing-data-in-the-cloud"></a>シナリオ: クラウド内のデータ管理
 SSIS パッケージ内の Azure Blob Destination を使用して、出力データを Azure Blob ストレージに書き込みむか、または Azure Blob Source を使用して、Azure Blob ストレージからデータを読み取ります。

![SSIS-AzureConnector-CloudArchive-1](../integration-services/media/ssis-azureconnector-cloudarchive-1.png)
 
 ![SSIS-AzureConnector-CloudArchive-2](../integration-services/media/ssis-azureconnector-cloudarchive-2.png)

 Azure Blob 列挙子とともに Foreach ループ コンテナーを使用して、複数の BLOB ファイルのデータを処理します。

![SSIS-AzureConnector-CloudArchive-3](../integration-services/media/ssis-azureconnector-cloudarchive-3.png)
  