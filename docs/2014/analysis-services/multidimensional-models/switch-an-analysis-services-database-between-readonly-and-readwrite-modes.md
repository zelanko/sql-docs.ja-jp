---
title: Analysis Services データベースの ReadOnly モードと ReadWrite モードの切り替え |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ReadOnly property
- ReadWriteMode command
- operations [Analysis Services - multidimensional data]
ms.assetid: 4eff8181-08dd-4fad-b091-d400fc21a020
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 184a674d03e6c8fb6b30d10b91b2a58225894ba2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36071054"
---
# <a name="switch-an-analysis-services-database-between-readonly-and-readwrite-modes"></a>Analysis Services データベースの ReadOnly モードと ReadWrite モードの切り替え
  多くの場合、状況もある場合に、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベース管理者 (dba) が、表形式または多次元データベースの読み取り/書き込みモードを変更します。 こうした状況は、ユーザーが操作しやすくなるように一連の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバー間でデータベースを共有するなどのビジネス上のニーズによって頻繁に発生します。  
  
 データベースのモードは、さまざまな方法で切り替えることができます。 このドキュメントでは、次の一般的なシナリオについて説明します。  
  
-   の対話的な使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
-   AMO を使用したプログラム  
  
-   XMLA を使用したスクリプト  
  
## <a name="procedures"></a>手順  
  
#### <a name="to-switch-the-readwrite-mode-of-a-database-interactively-using-management-studio"></a>Management Studio を使用してデータベースの読み取り/書き込みモードを対話的に切り替えるには  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] の左側または右側のペインで切り替えるデータベースを指定します。  
  
2.  データベースを右クリックし **プロパティ**です。 データベース フォルダーを検索し、場所を確認します。 データベースのストレージの場所が空の場合は、データベース フォルダーがサーバー データ フォルダー内にあることを示しています。  
  
    > [!IMPORTANT]  
    >  データベースがデタッチされるとすぐに、[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] では、データベースの位置を取得できなくなります。  
  
3.  データベースを右クリックし、 **[デタッチ]** をクリックします。  
  
4.  デタッチするデータベースにパスワードを割り当て、 **[OK]** をクリックしてデタッチ コマンドを実行します。  
  
5.  検索、**データベース**の左側または右側のウィンドウでフォルダ[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]です。  
  
6.  右クリックし、**データベース**フォルダーと選択**アタッチしています.**  
  
7.  **[フォルダー]** ボックスに、データベース フォルダーの元の場所を入力します。 または、参照ボタン (**[…]**) を使用して、データベース フォルダーを探すこともできます。  
  
8.  データベースの読み取り/書き込みモードを選択します。  
  
9. 手順 3. で使用されたパスワードを入力し、をクリックして**OK**してアタッチ コマンドを実行します。  
  
#### <a name="to-switch-the-readwrite-mode-to-a-database-programmatically-using-amo"></a>プログラムで AMO を使用してデータベースの読み取り/書き込みモードを切り替えるには  
  
1.  C# アプリケーションで、次のサンプル コードを調整して、指定されたタスクを完了します。  
  
 `private void SwitchReadWrite(Server server, string dbName,`  
  
 `ReadWriteMode dbReadWriteMode)`  
  
 `{`  
  
 `if (server.Databases.ContainsName(dbName))`  
  
 `{`  
  
 `Database db;`  
  
 `string databaseLocation;`  
  
 `db = server.Databases[dbName];`  
  
 `databaseLocation = db.DbStorageLocation;`  
  
 `if (databaseLocation == null)`  
  
 `{`  
  
 `string dataDir = server.ServerProperties["DataDir"].Value;`  
  
 `String[] possibleFolders = Directory.GetDirectories(dataDir, string.Concat(dbName,"*"), SearchOption.TopDirectoryOnly);`  
  
 `if (possibleFolders.Length > 1)`  
  
 `{`  
  
 `List<String> sortedFolders = new List<string>(possibleFolders.Length);`  
  
 `sortedFolders.AddRange(possibleFolders);`  
  
 `sortedFolders.Sort();`  
  
 `databaseLocation = sortedFolders[sortedFolders.Count - 1];`  
  
 `}`  
  
 `else`  
  
 `{`  
  
 `databaseLocation = possibleFolders[0];`  
  
 `}`  
  
 `}`  
  
 `db.Detach();`  
  
 `server.Attach(databaseLocation, dbReadWriteMode);`  
  
 `}`  
  
 `}`  
  
1.  C# アプリケーションで、必要なパラメーターを指定して `SwitchReadWrite()` を呼び出します。  
  
2.  コードをコンパイルして実行し、データベースを移動します。  
  
#### <a name="to-switch-the-readwrite-mode-to-a-database-by-script-using-xmla"></a>XMLA を使用したスクリプトでデータベースの読み取り/書き込みモードを切り替えるには  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] の左側または右側のペインで切り替えるデータベースを指定します。  
  
2.  データベースを右クリックし **プロパティ**です。 データベース フォルダーを検索し、場所を確認します。 データベースのストレージの場所が空の場合は、データベース フォルダーがサーバー データ フォルダー内にあることを示しています。  
  
    > [!IMPORTANT]  
    >  データベースがデタッチされるとすぐに、[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] では、データベースの位置を取得できなくなります。  
  
3.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]で、新しい XMLA タブを開きます。  
  
4.  次の XMLA 用のスクリプト テンプレートをコピーします。  
  
 `<Detach xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">`  
  
 `<Object>`  
  
 `<DatabaseID>%dbName%</DatabaseID>`  
  
 `<Password>%password%</Password>`  
  
 `</Object>`  
  
 `</Detach>`  
  
1.  `%dbName%` をデータベースの名前に置き換え、 `%password%` をパスワードに置き換えます。 テンプレートに含まれている文字 % は削除する必要があります。  
  
2.  XMLA コマンドを実行します。  
  
3.  新しい XMLA タブに、次の XMLA 用のスクリプト テンプレートをコピーします。  
  
 `<Attach xmlns="http://schemas.microsoft.com/analysisservices/2003` `/engine` `">`  
  
 `<Folder>%dbFolder%</Folder>`  
  
 `<ReadWriteMode xmlns="http://schemas.microsoft.com/analysisservices/2008/engine/100">%ReadOnlyMode%</ReadWriteMode>`  
  
 `</Attach>`  
  
1.  `%dbFolder%` をデータベース フォルダーの完全な UNC パスに置き換え、`%ReadOnlyMode%` を対応する値 `ReadOnly` または `ReadWrite` に置き換え、`%password%` をパスワードに置き換えます。 テンプレートに含まれている文字 % は削除する必要があります。  
  
2.  XMLA コマンドを実行します。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.AnalysisServices.Server.Attach%2A>   
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [アタッチし、Analysis Services データベースのデタッチ](attach-and-detach-analysis-services-databases.md)   
 [データベースの格納場所](database-storage-location.md)   
 [データベースの Readwritemode](database-readwritemodes.md)   
 [Attach 要素](../xmla/xml-elements-commands/attach-element.md)   
 [Detach 要素](../xmla/xml-elements-commands/detach-element.md)   
 [ReadWriteMode 要素](../xmla/xml-elements-properties/readwritemode-element.md)   
 [DbStorageLocation 要素](../xmla/xml-elements-properties/dbstoragelocation-element.md)  
  
  