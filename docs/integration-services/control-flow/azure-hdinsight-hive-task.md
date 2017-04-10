---
title: "Azure HDInsight Pig Task | Microsoft Docs"
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
  - "sql13.dts.designer.afphivetask.f1"
  - "sql14.dts.designer.afphivetask.f1"
ms.assetid: e1896c73-128a-4128-9814-3e01f7dfe19b
caps.latest.revision: 13
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 10
---
# Azure HDInsight Pig Task
  Azure HDInsight クラスターで Hive スクリプトを実行するには、 **Azure HDInsight Hive Task** を使用します。
     
**Azure HDInsight Hive Task** を追加するには、SSIS デザイナーにドラッグ アンド ドロップし、ダブルクリックまたは右クリックして、**[編集]** をクリックします。**[Azure HDInsight Hive Task エディター]** ダイアログ ボックスが表示されます。  
  
 **Azure HDInsight Hive Task** は、SQL Server 2016 用の SQL Server Integration Services (SSIS) Feature Pack for Azure のコンポーネントです。 Feature Pack は [こちら](http://go.microsoft.com/fwlink/?LinkID=626967)からダウンロードしてください。  
  
 次の一覧で、このダイアログ ボックスのフィールドについて説明します。  
  
1.  **[AzureSubscriptionConnection]** フィールドで、既存の Azure サブスクリプション接続マネージャーを選択するか、HDInsight クラスターをホストする Azure サブスクリプションを参照する新しい接続マネージャーを作成します。  
  
2.  **[HDInsightClusterName]** フィールドで、Hive スクリプトを実行する HDInsight クラスターの名前を選択します。  
  
3.  **[LocalLogFolder]** フィールドで、**[...] (省略記号)** をクリックし、HDInsight クラスターから Hive 処理のログをダウンロードするフォルダーを選択します。  
  
4.  Hive スクリプトを指定するには、次の 2 つの方法があります。  
  
    1.  **インライン スクリプト**: **[スクリプト]** フィールドの横の **[...] (省略記号)** をクリックし、**[スクリプトの入力]** ダイアログ ボックスにインライン スクリプトを入力します。  
  
    2.  **スクリプト ファイル**: BLOB の場所にスクリプト ファイルをアップロードし、その **[BlobName]**に値を指定します。 HDInsight クラスターの既定のストレージまたはコンテナーに BLOB がない場合は、 **[ExternalStorageAccountName]** と **[ExternalBlobContainer]** に値を指定する必要があります。 外部 BLOB の場合は、"パブリックにアクセス可能" として構成されていることを確認します。  
  
     スクリプトを両方の方法で指定した場合は、スクリプト ファイルが使用され、インライン スクリプトは無視されます。  
  
  