---
title: "DBCC CHECKFILEGROUP (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CHECKFILEGROUP_TSQL
- DBCC_CHECKFILEGROUP_TSQL
- DBCC CHECKFILEGROUP
- CHECKFILEGROUP
dev_langs:
- TSQL
helpviewer_keywords:
- DBCC CHECKFILEGROUP statement
- database objects [SQL Server], checking
- allocation checks
- integrity [SQL Server], database objects
- filegroups [SQL Server], consistency checks
- table integrity checks [SQL Server]
- checking database objects
ms.assetid: 8c70bf34-7570-4eb6-877a-e35064a1380a
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fc36aa0cfddcceefda1aefc6f4e7dc040f9a4b5f
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="dbcc-checkfilegroup-transact-sql"></a>DBCC CHECKFILEGROUP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]割り当てとすべてのテーブルと、現在のデータベースの指定したファイル グループのインデックス付きビューの構造的整合性をチェックします。
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
  
DBCC CHECKFILEGROUP   
[  
    [ ( { filegroup_name | filegroup_id | 0 }   
        [ , NOINDEX ]   
  ) ]  
    [ WITH   
        {   
            [ ALL_ERRORMSGS | NO_INFOMSGS ]   
            [ , TABLOCK ]   
            [ , ESTIMATEONLY ]  
            [ , PHYSICAL_ONLY ]    
            [ , MAXDOP  = number_of_processors ]  
        }   
    ]  
]  
```  
  
## <a name="arguments"></a>引数  
 *filegroup_name*  
 現在のデータベースで、テーブルの割り当てと構造的整合性をチェックするファイル グループの名前を指定します。 指定しない場合、または 0 を指定した場合、既定はプライマリ ファイル グループとなります。 ファイル グループ名は、規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)です。  
 *filegroup_name* FILESTREAM ファイル グループをすることはできません。  
  
 *filegroup_id*  
 現在のデータベースで、テーブルの割り当てと構造的整合性をチェックするファイル グループの ID 番号を指定します。  
  
 NOINDEX  
 ユーザー テーブルの非クラスター化インデックスの集中チェックを実行しないように指定します。 これにより、全体の実行時間が短縮されます。 DBCC CHECKFILEGROUP は、常にすべてのシステム テーブルのインデックスをチェックするため、NOINDEX はシステム テーブルには影響を与えません。  
  
 ALL_ERRORMSGS  
 オブジェクトごとにエラーを無制限に表示します。 既定では、すべてのエラー メッセージが表示されます。 そのため、このオプションを指定しても省略しても影響はありません。  
  
 NO_INFOMSGS  
 すべての情報メッセージを表示しないようにします。  
  
 TABLOCK  
 DBCC CHECKFILEGROUP が、内部データベースのスナップショットを使用するのではなく、ロックを取得します。  
  
 ESTIMATE ONLY  
 必要な他のオプションをすべて指定した状態で、DBCC CHECKFILEGROUP の実行時に必要となる tempdb 領域の予測サイズを表示します。  
  
 PHYSICAL_ONLY  
 チェック内容を、ページ、レコード ヘッダー、および B-Tree の物理構造の整合性に限定します。 ファイル グループの物理的一貫性に関する低オーバーヘッド チェックを提供するように設計されているため、このチェックではデータが損傷する可能性のある破損ページおよび一般的なハードウェア障害も検出できます。 完全な DBCC CHECKFILEGROUP を実行すると、以前のバージョンよりはるかに時間がかかることがあります。 原因は次のとおりです。  
 -   論理チェックの対象範囲が広がった。  
 -   チェック対象の、基になる構造の一部が複雑になった。  
 -   新機能を含めるために多数の新しいチェックが導入された。  
 したがって、大規模なファイル グループでは、PHYSICAL_ONLY オプションを使用すると DBCC CHECKFILEGROUP の実行時間が大幅に短縮されることがあるため、実稼働システムで頻繁に使用する場合はこのオプションを使用することをお勧めします。 ただし、完全な DBCC CHECKFILEGROUP を定期的に実行することもお勧めします。 実行する頻度は、それぞれの業務環境や運用環境に固有の要因によって異なります。 PHYSICAL_ONLY を指定した場合は常に NO_INFOMSGS も暗黙的に指定されるため、修復オプションを同時指定することはできません。  
  
> [!NOTE]  
>  PHYSICAL_ONLY を指定すると、DBCC CHECKFILEGROUP で FILESTREAM データのチェックがすべてスキップされるようになります。  
  
 MAXDOP  
 **適用されます**:[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を通じて 2014 SP2[現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)します。  
  
 上書き、**並列処理の次数の最大**構成オプションの**sp_configure**ステートメントです。 MAXDOP では、sp_configure で構成されている値を超えることができます。 MAXDOP では、リソース ガバナーで構成されている値を超えると、データベース エンジンは、ALTER WORKLOAD GROUP (TRANSACT-SQL)」に記載のリソース ガバナーの MAXDOP 値を使用します。 MAXDOP クエリ ヒントを使用している場合は、max degree of parallelism 構成オプションで使用されるすべての意味ルールを適用できます。 詳細については、「 [max degree of parallelism サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)」を参照してください。  
  
> [!CAUTION]  
>  MAXDOP が 0 に設定されている場合、サーバーでは最大限の並列処理が実行されます。  
  
## <a name="remarks"></a>解説  
DBCC CHECKFILEGROUP と DBCC CHECKDB はほぼ同じ DBCC コマンドです。 主な相違点は、DBCC CHECKFILEGROUP の対象が、指定された単一のファイル グループと必要なテーブルのみに限定されることです。
DBCC CHECKFILEGROUP は、次のコマンドを実行します。
-   [DBCC CHECKALLOC](../../t-sql/database-console-commands/dbcc-checkalloc-transact-sql.md)ファイル グループのです。  
-   [DBCC CHECKTABLE](../../t-sql/database-console-commands/dbcc-checktable-transact-sql.md)のすべてのテーブルおよびインデックス付きビューのファイル グループにします。  
  
DBCC CHECKALLOC または DBCC CHECKTABLE を DBCC CHECKFILEGROUP と分けて実行する必要はありません。
  
## <a name="internal-database-snapshot"></a>内部データベース スナップショット  
DBCC CHECKFILEGROUP は、内部データベースのスナップショットを使用して、これらのチェックを実行するために必要なトランザクションの一貫性を実現します。 詳細については、次を参照してください[データベース スナップショット &#40; のスパース ファイルのサイズを表示。TRANSACT-SQL と #41 です。](../../relational-databases/databases/view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md) 「DBCC 内部データベース スナップショットの使用」」、および[DBCC &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/database-console-commands/dbcc-transact-sql.md).
スナップショットを作成できない場合や TABLOCK オプションが指定されている場合、DBCC CHECKFILEGROUP はロックを取得して必要な一貫性を実現します。 この場合、割り当てのチェックを行うための排他データベース ロックと、テーブルのチェックを行うための共有テーブル ロックが必要です。 TABLOCK の作用によって負荷の高いデータベースでも DBCC CHECKFILEGROUP の実行速度が速くなりますが、DBCC CHECKFILEGROUP の実行中、データベースでの同時実行性は低下します。
  
> [!NOTE]  
>  tempdb に対して DBCC CHECKFILEGROUP を実行しても、割り当てのチェックは行われず、共有テーブル ロックを取得してテーブルのチェックを行う必要があります。 これは、パフォーマンス上の理由から、データベースのスナップショットが tempdb では利用できないためです。 つまり、必要なトランザクションの一貫性を実現できないためです。  
  
## <a name="checking-objects-in-parallel"></a>オブジェクトの並列チェック  
既定では、DBCC CHECKFILEGROUP はオブジェクトの並列チェックを実行します。 並列処理の次数は、クエリ プロセッサによって自動的に決定されます。 並列処理の次数の最大値は、並列クエリと同様に構成します。 使用して DBCC チェックに利用できるプロセッサの最大数を制限するには、 [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)です。 詳細については、「 [max degree of parallelism サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)」を参照してください。
並列チェックはトレース フラグ 2528 を使用して無効にできます。 詳細については、「[トレース フラグ &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)」を参照してください。
  
## <a name="nonclustered-indexes-on-separate-filegroups"></a>異なるファイル グループの非クラスター化インデックス  
指定したファイル グループ内の非クラスター化インデックスが、別のファイル グループ内のテーブルに関連付けられている場合、ベース テーブルが検証できないので、インデックスはチェックされません。
指定したファイル グループ内のテーブルに対応する非クラスター化インデックスが、別のファイル グループ内にある場合、その非クラスター化インデックスは次の理由によりチェックされません。
-   ベース テーブル構造は非クラスター化インデックスの構造に依存しません。 ベース テーブルを検証するために、非クラスター化インデックスをスキャンする必要はありません。  
-   DBCC CHECKFILEGROUP コマンドでは、指定したファイル グループのみでオブジェクトが検証されます。  
クラスター化インデックスおよびテーブルは異なるファイル グループに配置されないため、上記の注意事項は、非クラスター化インデックスにのみ適用されます。
  
## <a name="partitioned-tables-on-separate-filegroups"></a>異なるファイル グループのパーティション テーブル  
パーティション テーブルが複数のファイル グループに分散している場合、DBCC CHECKFILEGROUP によってチェックされるのは指定したファイル グループに存在しているパーティション行セットのみで、他のファイル グループの行セットは無視されます。 チェックされなかったパーティションは、情報メッセージ 2594 に示されます。 指定したファイル グループにない非クラスター化インデックスはチェックされません。
  
## <a name="understanding-dbcc-error-messages"></a>DBCC エラー メッセージについて  
メッセージが書き込まれます DBCC CHECKFILEGROUP コマンドの終了後、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラー ログ。 DBCC コマンドが正常に実行された場合、メッセージでは正常完了とコマンド実行時間が示されます。 エラーのため、チェックを完了する前に、DBCC コマンドが停止すると、メッセージは、コマンドが終了した、状態の値とコマンド実行時間の量を示します。 次の表は、メッセージに含まれる可能性がある状態値の一覧と説明です。
  
|状態|Description|  
|-----------|-----------------|  
|0|エラー番号 8930 が発生しました。 メタデータの破損が原因で DBCC コマンドが終了しました。|  
|1|エラー番号 8967 が発生しました。 内部 DBCC エラーがあります。|  
|2|緊急モードのデータベース修復中にエラーが発生しました。|  
|3|メタデータの破損が原因で DBCC コマンドが終了しました。|  
|4|アサートまたはアクセス違反が検出されました。|  
|5|不明なエラーが発生し、DBCC コマンドが終了しました。|  
  
## <a name="error-reporting"></a>[エラー報告]  
ミニ ダンプ ファイル (SQLDUMP*nnnn*.txt) で作成された、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DBCC CHECKFILEGROUP は、破損エラーを検出するたびに、ログ ディレクトリ。 インスタンスの機能の使用状況データ収集およびエラー レポート機能が有効な場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に、ファイルが自動的に転送[!INCLUDE[msCoName](../../includes/msconame-md.md)]です。 収集されたデータは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機能向上のために使用されます。
このダンプ ファイルには、DBCC CHECKFILEGROUP コマンドの結果と追加の診断出力が含まれます。 また、制限付きの随意アクセス制御リスト (DACL) が割り当てられます。 アクセスが制限されて、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サービス アカウントとのメンバー、 **sysadmin**ロール。 既定では、 **sysadmin**ロールには、Windows の builtin \administrators グループとローカル管理者のグループのすべてのメンバーが含まれています。 データ収集プロセスが失敗しても、DBCC コマンドは失敗しません。
  
## <a name="resolving-errors"></a>エラーの解決  
DBCC CHECKFILEGROUP によってエラーが報告される場合は、データベース バックアップからデータベースを復元することをお勧めします。 DBCC CHECKFILEGROUP に修復オプションを指定することはできません。
バックアップが存在しない場合、指定した修復オプションで DBCC CHECKDB を実行することによって、報告されたエラーを修正します。 使用する修復オプションは、報告されたエラーの一覧の最後に指定されています。 REPAIR_ALLOW_DATA_LOSS オプションを使用してエラーを修正する場合は、一部のページ (データ) が削除されることがあります。
  
## <a name="result-sets"></a>結果セット  
DBCC CHECKFILEGROUP は次の結果セットを返します (値は異なることがあります)。
-   ESTIMATEONLY または NO_INFOMSGS が指定されている場合は除きます。  
-   データベースが指定されていない場合は、オプション (NOINDEX を除く) が指定されているかどうかに関係なく、現在のデータベースが対象になります。  
  
```sql
DBCC results for 'master'.  
DBCC results for 'sys.sysrowsetcolumns'.  
There are 630 rows in 7 pages for object 'sys.sysrowsetcolumns'.  
DBCC results for 'sys.sysrowsets'.  
There are 97 rows in 1 pages for object 'sys.sysrowsets'.  
DBCC results for 'sysallocunits'.  
There are 195 rows in 3 pages for object 'sysallocunits'.  
  
There are 2340 rows in 16 pages for object 'spt_values'.  
DBCC results for 'MSreplication_options'.  
There are 2 rows in 1 pages for object 'MSreplication_options'.  
CHECKFILEGROUP found 0 allocation errors and 0 consistency errors in database 'master'.  
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
NO_INFOMSGS が指定されている場合、DBCC CHECKFILEGROUP は次の結果セットを返します。
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
 ESTIMATEONLY が指定されている場合、DBCC CHECKFILEGROUP は次の結果セットを返します (値は異なることがあります)。  

```sql
Estimated TEMPDB space needed for CHECKALLOC (KB)
-------------------------------------------------   
15  
  
(1 row(s) affected)  
  
Estimated TEMPDB space needed for CHECKTABLES (KB)   
--------------------------------------------------   
207  
  
(1 row(s) affected)  
  
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>権限  
**sysadmin** 固定サーバー ロールまたは **db_owner** 固定データベース ロールのメンバーシップが必要です。
  
## <a name="examples"></a>使用例  
### <a name="a-checking-the-primary-filegroup-in-the-a-database"></a>A. データベース内の PRIMARY ファイル グループをチェックする  
次の例では、現在のデータベースのプライマリ ファイル グループをチェックします。
  
```sql  
  
DBCC CHECKFILEGROUP;  
GO  
```  
  
### <a name="b-checking-the-adventureworks-primary-filegroup-without-nonclustered-indexes"></a>B. 非クラスター化インデックスを除く AdventureWorks データベースの PRIMARY ファイル グループをチェックする  
次の例のチェック、`AdventureWorks2012`データベース プライマリ ファイル グループ (非クラスター化インデックスを除く) を指定して、プライマリ ファイル グループの識別番号を指定することによって`NOINDEX`です。
  
```sql  
USE AdventureWorks2012;  
GO  
DBCC CHECKFILEGROUP (1, NOINDEX);  
GO  
```  
  
### <a name="c-checking-the-primary-filegroup-with-options"></a>C. オプションを指定してプライマリ ファイル グループをチェックする  
次の例では、`master` データベースのプライマリ ファイル グループをチェックします。このとき、オプション `ESTIMATEONLY` を指定します。
  
```sql  
USE master;  
GO  
DBCC CHECKFILEGROUP (1)  
WITH ESTIMATEONLY;  
```  
  
## <a name="see-also"></a>参照  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[FILEGROUP_ID &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/filegroup-id-transact-sql.md)  
[sp_helpfile を実行 &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helpfile-transact-sql.md)  
[sp_helpfilegroup &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helpfilegroup-transact-sql.md)  
[sys.sysfilegroups &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-compatibility-views/sys-sysfilegroups-transact-sql.md)  
[DBCC CHECKDB &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)  
[DBCC CHECKALLOC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkalloc-transact-sql.md)  
[DBCC CHECKTABLE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checktable-transact-sql.md)
  
  
