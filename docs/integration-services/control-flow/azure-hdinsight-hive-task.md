---
title: "Azure HDInsight Hive タスク |Microsoft ドキュメント"
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
- sql13.dts.designer.afphivetask.f1
- sql14.dts.designer.afphivetask.f1
ms.assetid: e1896c73-128a-4128-9814-3e01f7dfe19b
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f9e67e91b5cd38482ab1151d5942c9c55c04136c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="azure-hdinsight-hive-task"></a>Azure HDInsight Pig Task
Azure HDInsight クラスターで Hive スクリプトを実行するには、 **Azure HDInsight Hive Task** を使用します。
     
**Azure HDInsight Hive Task**を追加するには、SSIS デザイナーにドラッグ アンド ドロップし、ダブルクリックまたは右クリックして、 **[編集]** をクリックします。 **[Azure HDInsight Hive Task エディター]** ダイアログ ボックスが表示されます。  
  
**Azure HDInsight Hive Task**のコンポーネントである、 [SQL Server Integration Services (SSIS) Feature Pack for Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md)です。
  
 次の一覧で、このダイアログ ボックスのフィールドについて説明します。  
  
1.  **HDInsightConnection**フィールドで、既存の Azure HDInsight 接続マネージャーを選択するか、新しいスクリプトの実行に使用する Azure の HDInsight クラスターを表す 1 つ作成します。
  
2.  **AzureStorageConnection**フィールドで、既存の Azure Storage 接続マネージャーを選択するか、新しいクラスターに関連付けられている Azure ストレージ アカウントを参照する 1 つ作成します。 これは、スクリプトの実行の出力とエラー ログをダウンロードする場合に必要です。
 
3.  **BlobContainer**フィールドに、クラスターに関連付けられているストレージ コンテナー名を指定します。 これは、スクリプトの実行の出力とエラー ログをダウンロードする場合に必要です。
  
4.  **LocalLogFolder**フィールドに、スクリプトの実行の出力とエラー ログをダウンロードするフォルダーを指定します。 これは、スクリプトの実行の出力とエラー ログをダウンロードする場合に必要です。   
  
5.  これにを実行する Hive スクリプトを指定する 2 つの方法があります。
  
    1.  **インライン スクリプト**: 指定、**スクリプト**」と入力してのフィールドと、インラインで実行するスクリプト、**スクリプトの入力** ダイアログ ボックス。
  
    2.  **スクリプト ファイル**: Azure Blob ストレージにスクリプト ファイルをアップロードし、指定、 **BlobName**フィールドです。 既定のストレージ アカウントまたは HDInsight クラスターに関連付けられたコンテナーに、blob がない場合、 **[externalstorageaccountname]**と**ExternalBlobContainer**フィールドを指定する必要があります。 外部の blob をご確認ください構成されていることとパブリックにアクセスできます。  
  
     両方が指定されている場合は、スクリプト ファイルを使用してインライン スクリプトは無視されます。

