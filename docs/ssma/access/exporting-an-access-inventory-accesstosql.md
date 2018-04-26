---
title: エクスポート アクセス インベントリ (AccessToSQL) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-access
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Access databases
- Access databases, exporting metadata
- exporting
- exporting Access metadata
- exporting, Access metadata
- exporting, querying exported metadata
- inventories of Access databases
- querying exported metadata
ms.assetid: 7e1941fb-3d14-4265-aff6-c77a4026d0ed
caps.latest.revision: 18
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4d3968104ed7e9dec525afa3bd3e0cd7b8dcbb96
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="exporting-an-access-inventory-accesstosql"></a>アクセス インベントリ (AccessToSQL) をエクスポートします。
アクセスの複数のデータベースがあり、どれに移行するかわからない場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]プロジェクト内のすべてのアクセス データベースのインベントリをエクスポートすることができます。 確認し、データベースと移行にこれらのデータベース内のオブジェクトを決定するインベントリのメタデータをクエリします。 このインベントリではすぐに、次のように、質問への回答を検索します。  
  
-   最大級のデータベースとは  
  
-   ほとんどのデータベースの所有者はだれですか。  
  
-   のどのデータベースでは、同じテーブルを含めるか。  
  
-   過去 6 か月間のどのデータベースが変更されていないか。  
  
-   対象のデータベースには、秘密情報が含まれていますか。  
  
これらの質問に答えるために使用するクエリの例は、このトピックの最後に提供されます。  
  
## <a name="exported-metadata"></a>エクスポートされるメタデータ  
SSMA は、Access データベース、テーブル、列、インデックス、外部キー、クエリ、レポート、フォーム、マクロ、およびモジュールに関するメタデータをエクスポートします。 これらの項目のカテゴリのそれぞれについてのメタデータは、別のテーブルにエクスポートされます。 これらのテーブルのスキーマは、次を参照してください。[アクセス インベントリ スキーマ](http://msdn.microsoft.com/en-us/fdd3cff2-4d62-4395-8acf-71ea8f17f524)です。  
  
## <a name="exporting-inventory-data"></a>インベントリ データをエクスポートします。  
アクセスのインベントリをエクスポートするに最初に開くまたは SSMA プロジェクトを作成して分析する Access データベースを追加します。 指定したこれらのデータベースに関するメタデータをエクスポートする SSMA プロジェクトにデータベースを追加した後[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースおよびスキーマです。 必要に応じて、SSMA は、メタデータを格納するテーブルを作成します。 SSMA に Access データベースに関するメタデータを追加し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。  
  
> [!NOTE]  
> Access データベースは、複数のファイルに分割することができます: テーブルとフロント エンドを含むデータベースをクエリ、フォーム、レポート、マクロ、モジュール、およびショートカットを含むバック エンド データベース。 分割データベースを移行する場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]SSMA をフロント エンド データベースを追加します。  
  
次の手順は、プロジェクトを作成、データベースをプロジェクトに追加に接続する方法を説明[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、およびインベントリ データをエクスポートします。  
  
**プロジェクトを作成するには**  
  
1.  アクセスするためには、SSMA を開きます。  
  
2.  **[ファイル]** メニューの **[新しいプロジェクト]** を選択します。  
  
    **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
3.  **名前**ボックスで、プロジェクトの名前を入力します。  
  
4.  **場所**ボックス入力するか、プロジェクトのフォルダーを選択します。  
  
5.  **移行先**コンボ ボックスで、移行、およびをクリックするターゲット バージョンを選択**OK**です。  
  
プロジェクトの作成の詳細については、次を参照してください。[を管理するプロジェクトの作成および](http://msdn.microsoft.com/en-us/f2d1f0b0-5394-4adb-b3f3-abd71eb68ca7)です。  
  
**検索し、データベースを追加するには**  
  
1.  **ファイル** メニューのをクリックして**検索データベース**です。  
  
2.  ウィザードで、検索データベースには、ドライブ、ファイル パスまたは UNC パスを検索する文字列を入力します。 またはをクリックして**参照**ドライブやネットワーク フォルダーを選択します。  
  
3.  をクリックして**追加**をリスト ボックスに場所を追加します。  
  
    追加の検索場所を追加する前の 2 つの手順を繰り返します。  
  
4.  必要に応じて、返されるデータベースの一覧を絞り込む検索条件を追加します。  
  
    > [!IMPORTANT]  
    > **ファイル名の全部または一部**テキスト ボックスでは、ワイルドカード文字はサポートされません。  
  
5.  をクリックして**スキャン**です。  
  
    スキャンのページが表示されます。 検出されたデータベースと検索の進行状況が表示されます。 検索を停止する をクリックして**停止**です。  
  
6.  [ファイルの選択] ページで、プロジェクトに追加する各データベースを選択します。  
  
    使用することができます、**すべて選択**と**すべてクリア**をオンまたはオフのすべてのデータベース一覧の上部にあるボタンです。 また、複数の行を選択するのには、CTRL キーを押ししたり、行の範囲を選択するように、SHIFT キーを保持できます。  
  
7.  **[次へ]** をクリックします。  
  
8.  確認してください ページで、をクリックして**完了**です。  
  
詳細については、データベース プロジェクトを追加して、次を参照してください。[の追加と削除の Access データベース ファイル](http://msdn.microsoft.com/en-us/e944c740-4c8a-4bc1-b0ed-be57bc06dced)です。  
  
**SQL Server に接続するには**  
  
1.  **ファイル**メニューの  **SQL Server への接続**です。  
  
2.  接続ダイアログ ボックスで入力するかのインスタンスの名前を選択[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
    -   ローカル コンピューターの既定のインスタンスに接続する場合は、入力**localhost**またはドット (**.**)。  
  
    -   別のコンピューターの既定のインスタンスに接続する場合は、コンピューターの名前を入力します。  
  
    -   名前付きインスタンスに接続する場合は、コンピューター名、バック スラッシュとインスタンス名を入力します。 例: myserver \myinstance です。  
  
3.  **データベース**ボックスで、エクスポートされるメタデータのターゲット データベースの名前を入力します。  
  
4.  場合、インスタンスの[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]既定以外のポートで接続を受け入れる、使用されるポート番号を入力するように構成[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]内の接続、**サーバー ポート**ボックス。 既定のインスタンスの[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]既定のポート番号は 1433 です。 名前付きインスタンスは、SSMA 取得しようとはポート番号を[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Browser サービス。  
  
5.  **認証**ドロップダウン メニューで、接続に使用する認証の種類を選択します。 現在の Windows アカウントを使用するのには、選択**Windows 認証**です。 使用する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ログインで、 **SQL Server 認証**、ユーザー名とパスワードを指定します。  
  
接続の詳細については[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]を参照してください[SQL Server に接続する&#40;AccessToSQL&#41;](../../ssma/access/connecting-to-sql-server-accesstosql.md)です。  
  
**インベントリ情報をエクスポートするには**  
  
1.  メタデータ エクスプ ローラーでのアクセス、**アクセス メタベース**です。  
  
2.  次のチェック ボックスをオン**データベース**です。  
  
    個々 のデータベースまたはデータベース オブジェクトを省略する場合は、展開、**データベース**フォルダー、およびデータベースやデータベース オブジェクトの横にあるチェック ボックスをオフにし、します。  
  
3.  右クリック**データベース**選択**スキーマのエクスポート**です。  
  
4.  **エクスポート用のスキーマの選択**ダイアログ ボックスでは、エクスポートされたメタデータに対するターゲット スキーマを選択し、をクリックして**OK**です。  
  
メタデータをエクスポートするたびに SSMA は、インベントリ データを追加します。 インベントリの既存のデータが更新または削除されません。  
  
## <a name="querying-the-exported-metadata"></a>エクスポートされるメタデータのクエリを実行します。  
Access データベースに関するメタデータをエクスポートした後は、メタデータを照会できます。 次の手順の説明のクエリ エディター ウィンドウを使用する[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]クエリを実行します。  
  
**メタデータのクエリに**  
  
1.  **開始** メニューのをポイント**すべてのプログラム**、 をポイント**Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005**または**Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008**または**Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012**、クリックして**SQL Server Management Studio**です。  
  
2.  **サーバーへの接続**ダイアログ ボックスでは、設定を確認し、をクリックして**接続**です。  
  
3.  Management Studio ツールバーで、をクリックして**新しいクエリ**クエリ エディターを開きます。  
  
4.  クエリ エディター ウィンドウで、クエリを入力します。 いくつかの例は、次のセクションに表示されます。  
  
5.  F5 キーを押してクエリを実行します。  
  
## <a name="query-examples"></a>クエリの例  
次のクエリを実行する前に、USE を実行する必要があります*database_name*エクスポートされたメタデータが含まれているデータベース、クエリが実行されるかどうかを確認するクエリ。 たとえば、MyAccessMetadata をという名前のデータベースにメタデータをエクスポートした場合、次に追加の先頭、[!INCLUDE[tsql](../../includes/tsql_md.md)]コード。  
  
```  
USE MyAccessMetadata;  
GO  
```  
すべての次の例を使用して、 **dbo**スキーマです。 別のスキーマにメタデータをエクスポートする場合は、これらのクエリを実行すると、スキーマを変更することを確認してください。  
  
### <a name="what-tables-and-columns-are-in-these-databases"></a>どのようなテーブルと列は、これらのデータベースでは?  
次のクエリでは、列、テーブル、およびデータベースのメタデータを含むテーブルを結合し、すべてのデータベース、テーブル、および列名で並べ替える列の名前を返します。  
  
```  
SELECT DatabaseName, TableName, ColumnName   
FROM dbo.SSMA_Access_InventoryColumns C  
JOIN dbo.SSMA_Access_InventoryTables T  
ON C.TableId = T.TableId  
JOIN dbo.SSMA_Access_InventoryDatabases D  
ON T.DatabaseId = D.DatabaseId  
ORDER BY ColumnName;  
```  
  
### <a name="what-are-the-largest-databases"></a>最大級のデータベースとは  
次のクエリは、ファイルのサイズ順に並べ替えて、各 Access データベースにデータベース名、ファイルのサイズ、およびテーブルの数を返します。  
  
```  
SELECT DatabaseName, FileSize, TablesCount  
FROM dbo.SSMA_Access_InventoryDatabases  
ORDER BY FileSize DESC;  
```  
  
### <a name="who-is-the-owner-of-most-of-the-databases"></a>ほとんどのデータベースの所有者は誰ですか。  
次のクエリは、データベースの名前と所有者に並べ替えて、各アクセス データベースの所有者を返します。  
  
```  
SELECT DatabaseName, FileOwner  
FROM dbo.SSMA_Access_InventoryDatabases  
ORDER BY FileOwner;  
```  
  
### <a name="which-databases-contain-the-same-tables"></a>のどのデータベースでは、同じテーブルを含めるか。  
次のクエリでは、テーブルの一覧に 2 回以上表示されるすべてのテーブル名を検索するサブクエリを使用し、このテーブルの一覧を使用して、データベース名を取得します。 結果は、データベース名とテーブル名として返されるされ、テーブル名によって並べ替えられます。  
  
```  
SELECT DatabaseName, TableName   
FROM dbo.SSMA_Access_InventoryTables T  
JOIN dbo.SSMA_Access_InventoryDatabases D  
ON D.DatabaseId = T.DatabaseId  
WHERE TableName IN (  
SELECT TableName   
FROM dbo.SSMA_Access_InventoryTables  
GROUP BY TableName   
HAVING count(*)>1  
)  
ORDER BY TableName;  
```  
  
### <a name="which-databases-were-not-modified-in-the-last-six-months"></a>過去 6 か月間には、対象のデータベースは変更されていないか。  
次のクエリは、現在の日付を取得、6 か月前の月の値を取得し、6 か月前よりも大きい値の変更日付を持つデータベースの一覧を返します。  
  
```  
SELECT DatabaseName, DateModified  
FROM dbo.SSMA_Access_InventoryDatabases  
WHERE DATEDIFF(month, DateModified, GETDATE()) > 6  
ORDER BY DateModified;  
```  
  
### <a name="which-databases-contain-private-information"></a>対象のデータベースには、秘密情報が含まれていますか。  
Access データベースには、機密情報や個人情報が含まれます。 これらのデータベースを移動することができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]のセキュリティ機能を活用するためにします。 機密データを含む列が、特定の名前、または特定の文字を含めることがわかっている場合は、その情報が含まれているすべての列を検索するクエリを使用できます。 たとえば、「給与」文字列が含まれるすべての列を見つけることができます。  クエリは、データベース名、テーブル名、および列名を返します。  
  
```  
SELECT DatabaseName, TableName, ColumnName   
FROM dbo.SSMA_Access_InventoryColumns C  
JOIN dbo.SSMA_Access_InventoryTables T  
ON C.TableId = T.TableId  
JOIN dbo.SSMA_Access_InventoryDatabases D  
ON T.DatabaseId = D. DatabaseId  
WHERE ColumnName LIKE '%salary%';  
```  
列の名前がわからない場合は、すべての列を返すクエリを記述できます。 これを行うには、前のクエリから WHERE 句を削除します。  
  
## <a name="see-also"></a>参照  
[Access データベースの移行の準備](http://msdn.microsoft.com/en-us/9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114)  
  
