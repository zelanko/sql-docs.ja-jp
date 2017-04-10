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
  - "sql13.dts.designer.afppigtask.f1"
  - "sql14.dts.designer.afppigtask.f1"
ms.assetid: 26f34f64-f344-486e-9190-acf71aef29a8
caps.latest.revision: 12
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 9
---
# Azure HDInsight Pig Task
  Azure HDInsight クラスターで Pig スクリプトを実行するには、 **Azure HDInsight Pig Task** を使用します。 
    
**Azure HDInsight Pig Task** を追加するには、SSIS デザイナーにドラッグ アンド ドロップし、ダブルクリックまたは右クリックして、**[編集]** をクリックします。すると、次の **[Azure HDInsight Pig Task Editor]** (Azure HDInsight Pig Task エディター) ダイアログ ボックスが表示されます。  
  
 **Azure HDInsight Pig Task** は、SQL Server 2016 用の SQL Server Integration Services (SSIS) Feature Pack for Azure のコンポーネントです。 Feature Pack は [こちら](http://go.microsoft.com/fwlink/?LinkID=626967)からダウンロードしてください。  
  
1.  **[AzureSubscriptionConnection]** フィールドで、既存の Azure サブスクリプション接続マネージャーを選択するか、HDInsight クラスターをホストする Azure サブスクリプションを参照する新しい接続マネージャーを作成します。  
  
2.  **[HDInsightClusterName]** (HDInsightClusterName) に、Pig スクリプトを実行する HDInsight クラスターの名前を入力します。  
  
3.  **[LocalLogFolder]** (LocalLogFolder) で、**[...] (省略記号)** をクリックし、HDInsight クラスターから Pig 処理のログをダウンロードするフォルダーを選択します。  
  
4.  Pig スクリプトを指定するには、次の 2 つの方法があります。  
  
    1.  **インライン スクリプト**: **[スクリプト]** フィールドの横の **[...] (省略記号)** をクリックし、**[スクリプトの入力]** ダイアログ ボックスにインライン スクリプトを入力します。  
  
    2.  **スクリプト ファイル**: BLOB の場所にスクリプト ファイルをアップロードし、その **[BlobName]**に値を指定します。 HDInsight クラスターの既定のストレージまたはコンテナーに BLOB がない場合は、 **[ExternalStorageAccountName]** と **[ExternalBlobContainer]** に値を指定する必要があります。 外部 BLOB の場合は、"パブリックにアクセス可能" として構成されていることを確認します。  
  
     スクリプトを両方の方法で指定した場合は、スクリプト ファイルが使用され、インライン スクリプトは無視されます。  
  
  