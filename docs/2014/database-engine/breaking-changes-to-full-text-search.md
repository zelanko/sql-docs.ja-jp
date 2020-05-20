---
title: フルテキスト検索の重大な変更 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], breaking changes
- full-text catalogs [SQL Server], breaking changes
- breaking changes [full-text search]
- full-text indexes [SQL Server], breaking changes
ms.assetid: c55a6748-e5d9-4fdb-9a1f-714475a419c5
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 9a223060768c35b2daf00837153e59218ff1c50e
ms.sourcegitcommit: 4b5919e3ae5e252f8d6422e8e6fddac1319075a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/09/2020
ms.locfileid: "83001022"
---
# <a name="breaking-changes-to-full-text-search"></a>フルテキスト検索の重大な変更
  このトピックでは、フルテキスト検索の重要な変更について説明します。 これらの変更によって、以前のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に基づくアプリケーション、スクリプト、または機能が使用できなくなる場合があります。 この問題は、アップグレードするときに発生することがあります。 詳細については、「 [Use Upgrade Advisor to Prepare for Upgrades](../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)」を参照してください。  
  
## <a name="breaking-changes-in-full-text-search-in-sssql14"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] におけるフルテキスト検索の重大な変更  
 今後、情報が追加されていきます。  
  
## <a name="breaking-changes-in-full-text-search-in-sssql11"></a>[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] におけるフルテキスト検索の重大な変更  
  
### <a name="collation-changed-for-name-column-in-sysfulltext_languages"></a>sys.fulltext_languages の名前列で変更された照合順序  
 [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql) カタログ ビューの言語の **name** 列の照合順序は、Resource データベースの固定の照合順序から、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスに対して選択した既定の照合順序に変更されました。 この変更により、[sys.syslanguages &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql) ビューを **sys.fulltext_languages** と結合して、**name** 列の値を比較できるようになりました。 たとえば、既定のフルテキスト言語が既定のデータベース言語とは異なっているすべてのデータベースをクエリできます。  
  
## <a name="breaking-changes-in-full-text-search-in-sql-server-2008"></a>SQL Server 2008 におけるフルテキスト検索の重大な変更  
 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] と [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 以降のバージョン間のフルテキスト検索に、次の重大な変更が適用されています。  
  
|特徴|シナリオ|SQL Server 2005|SQL Server 2008 以降のバージョン|  
|-------------|--------------|---------------------|----------------------------------------|  
|ユーザー定義型 (Udt) を使用した[CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)|フルテキスト キーが [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーザー定義型である (たとえば、`MyType = char(1)`)。|ユーザー定義型に割り当てられた型のキーが返されます。<br /><br /> この例では、 **char (1)** です。|ユーザー定義型のキーが返されます。 この例では、 **MyType**になります。|  
|*top_n_by_rank*パラメーター (CONTAINSTABLE ステートメントと[FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメント)|パラメーターとして0を使用してクエリを*top_n_by_rank*します。|ゼロより大きな値を使用するよう通知するエラー メッセージが表示されて処理が失敗します。|処理が成功し、ゼロ行を返します。|  
|CONTAINSTABLE と**ItemCount**|MSSearch に変更を適用する前に、ベース テーブルから行を削除する。|CONTAINSTABLE からゴースト レコードが返されます。 **ItemCount**は変更されません。|CONTAINSTABLE からゴースト レコードが返されません。|  
|**ItemCount**|テーブルに null のドキュメントまたは null 型の列が含まれている。|インデックス付きドキュメントに加えて、null または null 型のドキュメントは、 **ItemCount**値でカウントされます。|**ItemCount**値でカウントされるのは、インデックス付きドキュメントだけです。|  
|カタログ**ItemCount**|NULL 拡張機能を持つ BLOB 列。|**ItemCount**のカタログにカウントされます。|カタログの**ItemCount**にはカウントされません。|  
|**UniqueKeyCount**|カタログで一意のキー数を照会する (たとえば、それぞれに word1、word2、word3 の 3 つの単語を含んだ 2 つのテーブル (table1 と table2) など)。|**UniqueKeyCount** = 9。 この値は次のようにして得られます。<br /><br /> table1 = 3<br /><br /> table1 のフルテキスト インデックスの EOF = 1<br /><br /> table2 = 3<br /><br /> table2 のフルテキスト インデックスの EOF = 1<br /><br /> フルテキスト カタログ = 1|各テーブルについて、 **UniqueKeyCount**は個別のキーワードの数 + 1 (0xff) です。  これは、> 1 ドキュメント内の同じ単語を新しい一意キーとして処理しません。<br /><br /> カタログの場合、 **UniqueKeyCount**は、カタログ内の各テーブルの**UniqueKeyCount**の合計です。 別々のテーブルにある同一の単語は、一意のキーとして扱われます。 この場合の一意のキー数は 8 です。|  
|**事前計算 rank**サーバーレベルオプション|FREETEXTTABLE クエリのパフォーマンス最適化。|このオプションを1に設定すると、 *top_n_by_rank*で指定された FREETEXTTABLE クエリは、フルテキストカタログに格納されている事前計算済み rank データを使用します。|サポートされません。|  
|キー列を更新するときに[sp_fulltext_pendingchanges](/sql/relational-databases/system-stored-procedures/sp-fulltext-pendingchanges-transact-sql)|2 行のテーブルの 1 行でフルテキスト キー列を更新し、sp_fulltext_pendingchanges を実行する。|両方の行が表示されます。|1 行だけが表示されます。|  
|インライン関数|フルテキスト演算子が指定されたインライン関数。|エラー メッセージが返されます。|関連する行が返されます。|  
|[sp_fulltext_database](/sql/relational-databases/system-stored-procedures/sp-fulltext-database-transact-sql)|sp_fulltext_database を使用してフルテキスト検索を有効または無効にする。|フルテキスト クエリには結果が返されません。 データベースでフルテキストが無効になっている場合は、フルテキスト操作を実行できません。|データベースでフルテキストが無効になっていても、フルテキスト クエリに結果が返され、フルテキスト操作も実行できます。|  
|ロケール固有のストップ ワード|ベルギーフランス語やカナダフランス語など、親言語のロケール固有のバリアントをクエリします。|ロケール固有のバリアント内のクエリは、その親言語のコンポーネント (ワードブレーカー、ステミング機能、およびストップワード) によって処理されます。 たとえば、フランス語 (ベルギー) の解析にはフランス語 (フランス) のコンポーネントが使用されます。|ロケール識別子 (LCID) ごとにストップ ワードを明示的に追加する必要があります。 たとえば、ベルギー、カナダ、フランスの LCID を指定する必要があります。|  
|類義語辞典のステミング処理|類義語辞典と変化形 (ステミング) を使用する。|類義語辞典は、その展開後に自動的にステミングされます。|展開でステミング形式が必要な場合は、ステミング形式を明示的に追加する必要があります。|  
|フルテキスト カタログのパスとファイル グループ|フルテキスト カタログを使用する。|フルテキスト カタログは、それぞれに物理パスを持ち、ファイル グループに属します。 これらは、データベース ファイルとして扱われます。|フルテキスト カタログは仮想オブジェクトであり、ファイル グループには属しません。 フルテキスト カタログは、フルテキスト インデックスのグループを指す論理的概念です。<br /><br /> 注: [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] [!INCLUDE[tsql](../includes/tsql-md.md)] フルテキストカタログを指定する DDL ステートメントは正常に動作します。|  
|[sys.fulltext_catalogs](/sql/relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql)|このカタログ ビューの path、data_space_id、および file_id を使用する。|これらの列から特定の値が返されます。|これらの列から NULL が返されます。これは、フルテキスト カタログがファイル システムに配置されなくなったためです。|  
|[sys.sysfulltextcatalogs](/sql/relational-databases/system-compatibility-views/sys-sysfulltextcatalogs-transact-sql)|この非推奨システム テーブルの path 列を使用する。|フルテキスト カタログのファイル システム パスが返されます。|NULL が返されます。これは、フルテキスト カタログがファイル システムに配置されなくなったためです。|  
|[sp_help_fulltext_catalogs](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-transact-sql)<br /><br /> [sp_help_fulltext_catalogs_cursor](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-cursor-transact-sql)|これらの非推奨ストアド プロシージャの PATH 列を使用する。|フルテキスト カタログのファイル システム パスが返されます。|NULL が返されます。これは、フルテキスト カタログがファイル システムに配置されなくなったためです。|  
|[sp_help_fulltext_catalog_components](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-catalog-components-transact-sql)|このストアド プロシージャの sp_help_fulltext_catalog_components を使用する。|現在のデータベースにあるすべてのフルテキスト カタログに使用されている、すべてのコンポーネント (フィルター、ワード ブレーカー、プロトコル ハンドラー) の一覧を返します。|空の行が返されます。|  
|[DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql)|**IsFullTextEnabled**プロパティを使用します。|**IsFullTextEnabled**設定は、指定されたデータベースでフルテキスト検索が有効になっているかどうかを示します。|この列の値は無効です。 ユーザー データベースでは、常にフルテキスト検索が有効になっています。|  
  
## <a name="see-also"></a>参照  
 [フルテキスト検索の動作の変更](../relational-databases/search/full-text-search.md)   
 [フルテキスト検索](../relational-databases/search/full-text-search.md)  
  
  
