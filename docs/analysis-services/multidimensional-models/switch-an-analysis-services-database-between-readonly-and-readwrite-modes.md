---
title: "Analysis Services データベースの ReadOnly モードと ReadWrite モードの切り替え | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ReadOnly プロパティ"
  - "ReadWriteMode コマンド"
  - "操作 [Analysis Services - 多次元データ]"
ms.assetid: 4eff8181-08dd-4fad-b091-d400fc21a020
caps.latest.revision: 16
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 16
---
# Analysis Services データベースの ReadOnly モードと ReadWrite モードの切り替え
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のデータベース管理者は、クエリ専用の複数のサーバー間でクエリ ワークロードを分散する作業の一部として、テーブルまたは多次元のデータベースの読み取り/書き込みモードを変更できます。  
  
 データベース モードを切り替える方法は複数あります。 このドキュメントでは、次の一般的なシナリオについて説明します。  
  
-   の対話的な使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
-   AMO を使用したプログラム  
  
-   XMLA または TMSL を使用したスクリプト  
  
## Management Studio を使用してデータベースの読み取り/書き込みモードを対話的に切り替える  
  
1.  オブジェクト エクスプローラーで、データベースを右クリックし、**[プロパティ]** をクリックします。  
  
     場所を書き留めます。 データベースのストレージの場所が空の場合は、データベース フォルダーがサーバー データ フォルダー内にあることを示しています。  
  
2.  データベースを右クリックし、**[デタッチ]** をクリックします。  
  
3.  デタッチするデータベースにパスワードを割り当て、 **[OK]** をクリックしてデタッチ コマンドを実行します。  
  
4.  オブジェクト エクスプローラーで、**[データベース]** フォルダーを右クリックし、**[アタッチ]** をクリックします。  
  
5.  **[フォルダー]** ボックスに、データベース フォルダーの元の場所を入力します。 または、参照ボタン (**[…]**) を使用して、データベース フォルダーを探すこともできます。  
  
6.  データベースの読み取り/書き込みモードを選択します。  
  
7.  パスワードを入力し、 **[OK]** をクリックしてアタッチ コマンドを実行します。  
  
## プログラムで AMO を使用してデータベースの読み取り/書き込みモードを切り替える  
 C# アプリケーションで、必要なパラメーターを指定して `SwitchReadWrite()` を呼び出します。 コードをコンパイルして実行し、データベースを移動します。  
  
```  
private void SwitchReadWrite(Server server, string dbName, ReadWriteMode dbReadWriteMode)  
{  
    if (server.Databases.ContainsName(dbName))  
    {  
        Database db;  
        string databaseLocation;  
        db = server.Databases[dbName];  
        databaseLocation = db.DbStorageLocation;  
  
              if (databaseLocation == null)  
            {  
                 string dataDir = server.ServerProperties["DataDir"].Value;  
                 string dataDir = server.ServerProperties["DataDir"].Value;  
                 string dataDir = server.ServerProperties["DataDir"].Value;  
  
    String[] possibleFolders = Directory.GetDirectories(dataDir, string.Concat(dbName,"*"), SearchOption.TopDirectoryOnly);  
  
   if (possibleFolders.Length > 1)  
         {  
         List<String> sortedFolders = new List<string>(possibleFolders.Length);  
         sortedFolders.AddRange(possibleFolders);  
         sortedFolders.Sort();  
         databaseLocation = sortedFolders[sortedFolders.Count - 1];  
         }  
         else  
         {  
         databaseLocation = possibleFolders[0];  
          }  
        }  
    db.Detach();  
    server.Attach(databaseLocation, dbReadWriteMode);  
    }  
}  
  
```  
  
## XMLA を使用したスクリプトでデータベースの読み取り/書き込みモードを切り替える  
 次の手順は、互換モードが 1050、1100、または 1103 の多次元データベースと表形式データベースに適用されます。  
  
1.  オブジェクト エクスプローラーで、データベースを右クリックし、**[プロパティ]** をクリックします。  
  
     場所を書き留めます。 データベースのストレージの場所が空の場合は、データベース フォルダーがサーバー データ フォルダー内にあることを示しています。  
  
2.  データベースを右クリックし、**[デタッチ]** をクリックします。  
  
3.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]で、新しい XMLA タブを開きます。  
  
4.  次の XMLA 用のスクリプト テンプレートをコピーします。  
  
    ```  
    <Detach xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
       <Object>  
          <DatabaseID>%dbName%</DatabaseID>  
          <Password>%password%</Password>  
       </Object>  
    </Detach>  
    ```  
  
5.  `%dbName%` をデータベースの名前に置き換え、 `%password%` をパスワードに置き換えます。 テンプレートに含まれている文字 % は削除する必要があります。  
  
6.  XMLA コマンドを実行します。  
  
7.  新しい XMLA タブに、次の XMLA 用のスクリプト テンプレートをコピーします。  
  
    ```  
    <Attach xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
       <Folder>%dbFolder%</Folder>  
       <ReadWriteMode xmlns="http://schemas.microsoft.com/analysisservices/2008/engine/100">%ReadOnlyMode%</ReadWriteMode>  
    </Attach>  
    ```  
  
8.  `%dbFolder%` をデータベース フォルダーの完全な UNC パスに置き換え、`%ReadOnlyMode%` を対応する値 **ReadOnly** または **ReadWrite** に置き換え、`%password%` をパスワードに置き換えます。 テンプレートに含まれている文字 % は削除する必要があります。  
  
9. XMLA コマンドを実行します。  
  
## 参照  
 [<xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Analysis Services の高可用性とスケーラビリティ](../../analysis-services/instances/high-availability-and-scalability-in-analysis-services.md)   
 [Analysis Services データベースのインポートとデタッチ](../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [データベースの格納場所](../../analysis-services/multidimensional-models/database-storage-location.md)   
 [データベースの ReadWriteMode](../../analysis-services/multidimensional-models/database-readwritemodes.md)   
 [Attach 要素](../../analysis-services/xmla/xml-elements-commands/attach-element.md)   
 [Detach 要素](../../analysis-services/xmla/xml-elements-commands/detach-element.md)   
 [ReadWriteMode 要素](../../analysis-services/xmla/xml-elements-properties/readwritemode-element.md)   
 [DbStorageLocation 要素](../../analysis-services/xmla/xml-elements-properties/dbstoragelocation-element.md)  
  
  