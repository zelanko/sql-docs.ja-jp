---
title: Analysis Services データベースを ReadOnly モードと ReadWrite モードの間で切り替えます。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- ReadOnly property
- ReadWriteMode command
- operations [Analysis Services - multidimensional data]
ms.assetid: 4eff8181-08dd-4fad-b091-d400fc21a020
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2a1496bee303e94720a354002e63cefcf479df85
ms.sourcegitcommit: 04ba0ed3d860db038078609d6e348b0650739f55
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468917"
---
# <a name="switch-an-analysis-services-database-between-readonly-and-readwrite-modes"></a>Analysis Services データベースの ReadOnly モードと ReadWrite モードの切り替え
  多くの場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース管理者 (dba) がテーブルまたは多次元データベースの読み取り/書き込みモードを変更する必要があります。 こうした状況は、ユーザーが操作しやすくなるように一連の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバー間でデータベースを共有するなどのビジネス上のニーズによって頻繁に発生します。  
  
 データベースモードは、さまざまな方法で切り替えることができます。 このドキュメントでは、次の一般的なシナリオについて説明します。  
  
-   の対話的な使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
-   AMO を使用したプログラム  
  
-   XMLA を使用したスクリプト  
  
## <a name="procedures"></a>プロシージャ  
  
#### <a name="to-switch-the-readwrite-mode-of-a-database-interactively-using-management-studio"></a>Management Studio を使用してデータベースの読み取り/書き込みモードを対話的に切り替えるには  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] の左側または右側のペインで切り替えるデータベースを指定します。  
  
2.  データベースを右クリックし、[**プロパティ**] を選択します。 データベース フォルダーを検索し、場所を確認します。 データベースのストレージの場所が空の場合は、データベース フォルダーがサーバー データ フォルダー内にあることを示しています。  
  
    > [!IMPORTANT]  
    >  データベースがデタッチされるとすぐに、[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] では、データベースの位置を取得できなくなります。  
  
3.  データベースを右クリックし、[**デタッチ**] を選択します。  
  
4.  デタッチするデータベースにパスワードを割り当て、 **[OK]** をクリックしてデタッチ コマンドを実行します。  
  
5.  の左側または右側のペインで、[**データベース**] フォルダーを探し [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ます。  
  
6.  [**データベース**] フォルダーを右クリックし、[**アタッチ**] を選択します。  
  
7.  **[フォルダー]** ボックスに、データベース フォルダーの元の場所を入力します。 または、参照ボタン ([.**..**]) を使用してデータベースフォルダーを検索することもできます。  
  
8.  データベースの読み取り/書き込みモードを選択します。  
  
9. 手順 3. で使用したパスワードを入力し、[ **OK** ] をクリックして attach コマンドを実行します。  
  
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
  
2.  データベースを右クリックし、[**プロパティ**] を選択します。 データベース フォルダーを検索し、場所を確認します。 データベースのストレージの場所が空の場合は、データベース フォルダーがサーバー データ フォルダー内にあることを示しています。  
  
    > [!IMPORTANT]  
    >  データベースがデタッチされるとすぐに、[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] では、データベースの位置を取得できなくなります。  
  
3.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]で、新しい XMLA タブを開きます。  
  
4.  次の XMLA 用のスクリプト テンプレートをコピーします。  
  
 `<Detach xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">`  
  
 `<Object>`  
  
 `<DatabaseID>%dbName%</DatabaseID>`  
  
 `<Password>%password%</Password>`  
  
 `</Object>`  
  
 `</Detach>`  
  
1.  `%dbName%` をデータベースの名前に置き換え、 `%password%` をパスワードに置き換えます。 テンプレートに含まれている文字 % は削除する必要があります。  
  
2.  XMLA コマンドを実行します。  
  
3.  新しい XMLA タブに、次の XMLA 用のスクリプト テンプレートをコピーします。  
  
 `<Attach xmlns="https://schemas.microsoft.com/analysisservices/2003` `/engine` `">`  
  
 `<Folder>%dbFolder%</Folder>`  
  
 `<ReadWriteMode xmlns="https://schemas.microsoft.com/analysisservices/2008/engine/100">%ReadOnlyMode%</ReadWriteMode>`  
  
 `</Attach>`  
  
1.  `%dbFolder%` をデータベース フォルダーの完全な UNC パスに置き換え、`%ReadOnlyMode%` を対応する値 `ReadOnly` または `ReadWrite` に置き換え、`%password%` をパスワードに置き換えます。 テンプレートに含まれている文字 % は削除する必要があります。  
  
2.  XMLA コマンドを実行します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.AnalysisServices.Server.Attach%2A>   
 [Microsoft.analysisservices.sharepoint.integration.dll * のようになります。](/dotnet/api/microsoft.analysisservices.core.database.detach)   
 [Analysis Services データベースのアタッチとデタッチ](attach-and-detach-analysis-services-databases.md)   
 [データベースのストレージの場所](database-storage-location.md)   
 [データベース ReadWriteModes](database-readwritemodes.md)   
 [Attach 要素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element)   
 [Detach 要素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element)   
 [ReadWriteMode 要素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/readwritemode-element)   
 [DbStorageLocation 要素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/dbstoragelocation-element)  
  
  
