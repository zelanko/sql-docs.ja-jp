---
title: Integration Services (SSIS) 用の Azure Feature Pack | Microsoft Docs
ms.custom: ''
ms.date: 07/09/2018
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL13.SSIS.AZURE.F1
- SQL14.SSIS.AZURE.F1
ms.assetid: 31de555f-ae62-4f2f-a6a6-77fea1fa8189
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: bc49dc5bd2375d52d3f8a849578bd5ac9ef74430
ms.sourcegitcommit: dcd29cd2d358bef95652db71f180d2a31ed5886b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2018
ms.locfileid: "37934864"
---
# <a name="azure-feature-pack-for-integration-services-ssis"></a>Integration Services (SSIS) 用の Azure Feature Pack
SQL Server Integration Services (SSIS) Feature Pack for Azure は、このページにリストされている SSIS のコンポーネントを提供して、Azure サービスへの接続、Azure とオンプレミスのデータ ソース間でのデータ転送、および Azure に格納されたデータの処理を行うための拡張機能です。

[![SSIS Feature Pack for Azure のダウンロード](../analysis-services/media/download.png)](https://www.microsoft.com/download/details.aspx?id=54798) **ダウンロード**

- SQL Server 2017 の場合 - [Microsoft SQL Server 2017 Integration Services Feature Pack for Azure](https://www.microsoft.com/download/details.aspx?id=54798)
- SQL Server 2016 の場合 - [Microsoft SQL Server 2016 Integration Services Feature Pack for Azure](https://www.microsoft.com/download/details.aspx?id=49492)
- SQL Server 2014 の場合 - [Microsoft SQL Server 2014 Integration Services Feature Pack for Azure](https://www.microsoft.com/download/details.aspx?id=47366)
- SQL Server 2012 の場合 - [Microsoft SQL Server 2012 Integration Services Feature Pack for Azure](https://www.microsoft.com/download/details.aspx?id=47367)

ダウンロード ページには、前提条件に関する情報も含まれます。 必ず SQL Server をインストールしてから Azure Feature Pack をサーバーにインストールします。そうしないと、サーバー上の SSIS カタログ データベース (SSISDB) にパッケージを展開するときに Feature Pack 内のコンポーネントを利用できない場合があります。

## <a name="components-in-the-feature-pack"></a>Feature Pack のコンポーネント
-   接続マネージャー

    -   [Azure Data Lake Analytics 接続マネージャー](connection-manager/azure-data-lake-analytics-connection-manager.md)

    -   [Azure Data Lake Store 接続マネージャー](../integration-services/connection-manager/azure-data-lake-store-connection-manager.md)
    
    -   [Azure HDInsight 接続マネージャー](../integration-services/connection-manager/azure-hdinsight-connection-manager.md)

    -   [Azure Resource Manager の接続マネージャー](../integration-services/connection-manager/azure-resource-manager-connection-manager.md)
    
    -   [Azure Storage 接続マネージャー](../integration-services/connection-manager/azure-storage-connection-manager.md)

    -   [Azure サブスクリプション接続マネージャー](../integration-services/connection-manager/azure-subscription-connection-manager.md)
    
-   処理手順

    -   [Azure BLOB のダウンロード タスク](../integration-services/control-flow/azure-blob-download-task.md)

    -   [Azure BLOB のアップロード タスク](../integration-services/control-flow/azure-blob-upload-task.md)

    -   [Azure Data Lake Analytics タスク](control-flow/azure-data-lake-analytics-task.md)

    -   [Azure Data Lake Store ファイル システム タスク](../integration-services/control-flow/azure-data-lake-store-file-system-task.md)

    -   [Azure HDInsight クラスターの作成タスク](../integration-services/control-flow/azure-hdinsight-create-cluster-task.md)

    -   [Azure HDInsight クラスターの削除タスク](../integration-services/control-flow/azure-hdinsight-delete-cluster-task.md)
    
    -   [Azure HDInsight Hive タスク](../integration-services/control-flow/azure-hdinsight-hive-task.md)

    -   [Azure HDInsight Pig タスク](../integration-services/control-flow/azure-hdinsight-pig-task.md)

    -   [Azure SQL DW のアップロード タスク](../integration-services/control-flow/azure-sql-dw-upload-task.md)

-   データ フロー コンポーネント

    -   [Azure BLOB Source](../integration-services/data-flow/azure-blob-source.md)

    -   [Azure Blob Destination](../integration-services/data-flow/azure-blob-destination.md)
    
    -   [Azure Data Lake Store Source](../integration-services/data-flow/azure-data-lake-store-source.md)
    
    -   [Azure Data Lake Store Destination](../integration-services/data-flow/azure-data-lake-store-destination.md)

-   Azure Blob と Azure Data Lake Store のファイル列挙子。 「[Foreach ループ コンテナー](http://msdn.microsoft.com/library/95a19dde-61ca-4d9b-aa3d-131fa4264296)」を参照してください。

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
  
