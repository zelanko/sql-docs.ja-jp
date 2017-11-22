---
title: "Sybase ASE データベース オブジェクト (SybaseToSQL) を変換する |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords: Converting Database Objects
ms.assetid: 509cb65d-2f54-427a-83d7-37919cc4e3e3
caps.latest.revision: "8"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c26c897ef9b4ffe1a05a47ab722770681a3737a8
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="converting-sybase-ase-database-objects-sybasetosql"></a>Sybase ASE データベース オブジェクト (SybaseToSQL) を変換します。
Sybase Adaptive Server Enterprise (ASE) に接続すると後に、接続[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Sybase Adaptive Server Enterprise (ASE) 使用するデータベース オブジェクトに変換するには SQL Azure、およびプロジェクトの設定とデータのマッピング オプション、または[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure データベースのオブジェクト。  
  
## <a name="the-conversion-process"></a>変換プロセス  
データベース オブジェクトを変換する ASE からオブジェクト定義を受け取り、同様に変換[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure オブジェクト、および SSMA メタデータにこの情報を読み込みます。 インスタンスに、情報は読み込まれません[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 使用して、オブジェクトとそのプロパティを表示することができますし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure メタデータ エクスプ ローラー。  
  
変換中には、SSMA は、出力ウィンドウに出力メッセージとエラー一覧 ウィンドウにエラー メッセージを出力します。 ASE データベースまたは必要な変換の結果を得るため、変換プロセスを変更するのにかどうかを確認するのにには、出力とエラー情報を使用します。  
  
## <a name="setting-conversion-options"></a>変換オプションの設定  
オブジェクトを変換する前に、プロジェクトの変換オプションを確認、**プロジェクト設定** ダイアログ ボックス。 このダイアログ ボックスを使用すると、SSMA で、関数およびグローバル変数がどのように変換されるかを設定できます。 詳細については、次を参照してください。[プロジェクトの設定 &#40;です。変換&#41;&#40;です。SybaseToSQL &#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md).  
  
## <a name="converting-ase-database-objects"></a>ASE データベース オブジェクトを変換します。  
ASE データベース オブジェクトに変換するには、最初に、変換するオブジェクトを選択し、SSMA が変換を実行します。 変換中に出力メッセージを表示する、**ビュー**メニューの **出力**です。  
  
**ASE オブジェクトを SQL Server または SQL Azure の構文に変換するには**  
  
1.  Sybase メタデータ エクスプ ローラーで、ASE サーバーを展開し、展開**データベース**です。  
  
2.  変換するオブジェクトを選択します。  
  
    -   すべてのデータベースを変換するには、チェック ボックスを横に選択**データベース**です。  
  
    -   変換するか、データベースを省略、オンまたはデータベース名の横にあるチェック ボックスをオフにします。  
  
    -   変換または個別のスキーマを省略、データベースを展開し、**スキーマ**を選択するか、スキーマの横にあるチェック ボックスをオフにします。  
  
    -   変換またはオブジェクトのカテゴリの省略は、スキーマを展開し、選択するか、カテゴリの横にあるチェック ボックスをオフにします。  
  
    -   変換または個々 のオブジェクトを省略、カテゴリ フォルダーを展開し、選択するか、オブジェクトの横にあるチェック ボックスをオフにします。  
  
3.  選択したすべてのオブジェクトを変換するを右クリックして**データベース**選択**スキーマの変換**です。  
  
    オブジェクトまたはその親フォルダーを右クリックしを選択して、個々 のオブジェクトまたはオブジェクトのカテゴリを変換することができますも**変換スキーマ**です。  
  
> [!NOTE]  
> いくつかの Sybase システム関数は完全に一致しない動作では、同等の SQL Server システム関数です。 Sybase ASE 動作をエミュレートするためには、SSMA は、's2ss' と呼ばれるスキーマで変換後の SQL Server データベースにユーザー定義関数を生成します。 これらのエミュレートされた関数とはいくつかの SQL Server のシステム関数が、プロジェクトの設定によって置き換えられます。 SSMA では、次のユーザー定義関数を作成します。  
  
||||  
|-|-|-|  
|**char_length_nvarchar**|**index_colorder**|**ssma_datepart**|  
|**char_length_varchar**|**inttohex**|**substring_nvarchar**|  
|**charindex_nvarchar**|**ssma_datediff**|**substring_varbinary**|  
|**charindex_varchar**|**hextoint**|**substring_varchar**|  
|**ulowsurr**|**to_unichar**|**ssma_current_time**|  
|**uhighsurr**|||  
  
## <a name="objects-not-supported-in-sql-azure"></a>SQL Azure でサポートされていないオブジェクト  
通常の SQL Server への変換時 Sybase の次の T-SQL キーワードを SSMA によって使用されますが、SQL Azure の T-SQL 構文では、これらのキーワードはサポートされていません。  
  
||||  
|-|-|-|  
|CHECKPOINT|CREATE/ALTER/DROP DEFAULT|CREATE/DROP RULE|  
|DBCC TRACEOFF|DBCC TRACEON|すべての付与、取り消し、拒否|  
|KILL|READTEXT|SELECT INTO|  
|SET OFFSETS|SETUSER|SHUTDOWN|  
|WRITETEXT|||  
  
## <a name="viewing-conversion-problems"></a>変換の問題を表示します。  
一部の ASE オブジェクトに変換できません可能性があります。 集計変換レポートを表示して、変換の成功率を指定できます。  
  
**概要レポートを表示するには**  
  
1.  Sybase メタデータ エクスプ ローラーで、次のように選択します。**データベース**です。  
  
2.  右側のペインで、**レポート**タブです。  
  
    このレポートには、評価または変換されているすべてのデータベース オブジェクトの評価の概要レポートが表示されます。 個々 のオブジェクトの概要レポートを表示することもできます。  
  
    -   個々 のデータベースのレポートを表示するには、Sybase メタデータ エクスプ ローラーで、データベースを選択します。  
  
    -   個々 のデータベース オブジェクトのレポートを表示するには、Sybase メタデータ エクスプ ローラーで、オブジェクトを選択します。 変換の問題のあるオブジェクトでは、赤いエラー アイコンがあります。  
  
オブジェクトの変換に失敗した場合に、変換エラーが発生した構文を表示することができます。  
  
**個々 の変換の問題を表示するには**  
  
1.  Sybase メタデータ エクスプ ローラーで、**データベース**です。  
  
2.  赤いエラー アイコンが表示されるデータベースを展開します。  
  
3.  展開、**スキーマ**フォルダーで、赤いエラー アイコンが表示されるスキーマを展開します。  
  
4.  スキーマの下に赤いエラー アイコンを持つフォルダーを展開します。  
  
5.  赤いエラー アイコンがあるオブジェクトを選択します。  
  
6.  右側のウィンドウでをクリックして、**レポート**タブです。  
  
7.  上部にある、**レポート**タブは、ドロップダウン リスト。 一覧に表示される場合**統計**、選択を変更するに**ソース**です。  
  
    SSMA は、ソース コードとコードのすぐ上のいくつかのボタンに表示されます。  
  
8.  クリックして、**次の問題**ボタンをクリックします。 これは、右向き矢印の付いた赤いエラー アイコンです。  
  
    ASE の SSMA では、現在のオブジェクト内で見つかった最初の問題のあるソース コードを強調表示されます。  
  
変換できなかった項目ごとのオブジェクトで実行するかを決定する必要があります。  
  
-   プロシージャやトリガーのソース コードを編集することができます、 **SQL**タブです。  
  
-   ASE オブジェクトを削除するか、問題のあるコードの修正を変更することができます。 SSMA に、更新されたコードを読み込むするには、メタデータを更新する必要があります。 詳細については、次を参照してください[Sybase ASE &#40; に接続する。SybaseToSQL &#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md).  
  
-   オブジェクトは、移行から除外できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure メタデータ エクスプ ローラーと Sybase メタデータ エクスプ ローラーにオブジェクトを読み込む前に、アイテムの横のチェック ボックスをオフに[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure と ASE からデータを移行します。  
  
## <a name="next-step"></a>次の手順  
移行プロセスの次の手順が、 [SQL Server に変換されたデータベース オブジェクトの読み込み/SQL Azure (SybaseToSQL)](http://msdn.microsoft.com/en-us/4c59256f-99a8-4351-9559-a455813dbd06)です。  
  
## <a name="see-also"></a>参照  
[SQL Server - Azure SQL DB &#40; への Sybase ASE データベースの移行SybaseToSQL &#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
