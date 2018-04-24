---
title: DATABASEPROPERTYEX (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DATABASEPROPERTYEX
- DATABASEPROPERTYEX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DATABASEPROPERTYEX function
- displaying database properties
- database properties [SQL Server]
ms.assetid: 8a9e0ffb-28b5-4640-95b2-a54e3e5ad941
caps.latest.revision: 84
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 4331e2c3e4b68a3c439ed72a16f0941068b76802
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="databasepropertyex-transact-sql"></a>DATABASEPROPERTYEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の、指定されたデータベース オプションの現在の設定値、または指定されたデータベースのプロパティを返します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
DATABASEPROPERTYEX ( database , property )  
```  
  
## <a name="arguments"></a>引数  
*database*  
指定されたプロパティ情報を返す基になるデータベースの名前を表す式を指定します。 *database* は **nvarchar(128)** です。  
[!INCLUDE[ssSDS](../../includes/sssds-md.md)] では、現在のデータベースの名前を指定する必要があります。 別のデータベース名が指定されている場合は、すべてのプロパティに対して NULL を返します。
  
*property*  
返されるデータベース プロパティの名前を表す式を指定します。 *プロパティ* は **varchar (128)**, 、値は次のいずれかを指定することができます。 戻り値の型は **sql_variant**です。 次の表は、各プロパティ値に対する基本のデータ型です。
  
> [!NOTE]  
>  データベースが起動されていない場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がメタデータから値を取得するのではなく直接データベースにアクセスして取得したプロパティは、NULL を返します。 つまり、データベースで AUTO_CLOSE が ON に設定されているなど、データベースがオフラインの場合に NULL を返します。  
  
|プロパティ|Description|返される値|  
|---|---|---|
|[照合順序]|データベースの既定の照合順序名です。|照合順序名<br /><br /> NULL = データベースを閉じている場合<br /><br /> 基本データ型: **nvarchar(128)**|  
|ComparisonStyle|照合順序の Windows 比較形式です。 ComparisonStyle はビットマップであり、利用可能な形式に対応する次の値を使用して計算されます。<br /><br /> 大文字と小文字を区別しない<br /><br /> アクセントを無視する: 2<br /><br /> ひらがなとカタカナを区別しない: 65536<br /><br /> 全角と半角を区別しない: 131072<br /><br /> <br /><br /> たとえば、既定値 196609 は、大文字と小文字を区別しない、ひらがなとカタカナを区別しない、全角と半角を区別しないという 3 つのオプションを足した値を表しています。|比較スタイルを返します。<br /><br /> バイナリ照合順序ではすべて 0 が返されます。<br /><br /> 基本データ型: * * **int** * *|  
|のエディション|データベースのエディションまたはサービス層です。|**適用対象**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]、[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]。<br /><br /> <br /><br /> General Purpose<br /><br /> Business Critical<br /><br /> [標準]<br /><br /> Standard<br /><br /> Premium<br /><br /> システム (マスター データベース)<br /><br /> NULL = データベースを閉じている場合<br /><br /> 基本データ型: **nvarchar**(64)|  
|IsAnsiNullDefault|データベースは、ISO のルールに従い NULL 値を許可します。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力<br /><br /> 基本データ型: * * **int** * *|  
|IsAnsiNullsEnabled|NULL 値との比較はすべて、不明として評価されます。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力<br /><br /> 基本データ型: * * **int** * *|  
|IsAnsiPaddingEnabled|比較または挿入を行う前に、対象の文字列が同じ長さになるようにパディングを行います。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力<br /><br /> 基本データ型: * * **int** * *|  
|IsAnsiWarningsEnabled|一般的なエラー状態が発生した場合、エラー メッセージまたは警告メッセージを出力します。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力<br /><br /> 基本データ型: * * **int** * *|  
|IsArithmeticAbortEnabled|クエリ実行中にオーバーフローまたは 0 除算エラーが発生したとき、クエリは終了します。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力<br /><br /> 基本データ型: * * **int** * *|  
|IsAutoClose|最後のユーザーが終了すると、データベースは即座にシャットダウンし、リソースを解放します。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力<br /><br /> 基本データ型: * * **int** * *|  
|IsAutoCreateStatistics|クエリのパフォーマンスを向上させるために、クエリ オプティマイザーが必要に応じて 1 列ずつの統計を作成します。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力<br /><br /> 基本データ型: * * **int** * *|  
|IsAutoCreateStatisticsIncremental|可能な場合、自動作成された 1 列ずつの統計は増分統計になります。|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> <br /><br /> 1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力<br /><br /> 基本データ型: * * **int** * *|  
|IsAutoShrink|データベース ファイルを、自動的に行われる定期的な圧縮の対象とします。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力<br /><br /> 基本データ型: * * **int** * *|  
|IsAutoUpdateStatistics|クエリで使用される既存の統計が古くなっている可能性がある場合、クエリ オプティマイザーによって更新されます。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力<br /><br /> 基本データ型: * * **int** * *|
|IsClone|データベースは、スキーマと統計情報であり、単にユーザー データベースのコピーです。|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Service Pack 2<br /><br /> <br /><br /> 1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力<br /><br /> 基本データ型: * * **int** * *| 
|IsCloseCursorsOnCommitEnabled|トランザクションがコミットされたときに開いていたカーソルを閉じます。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力<br /><br /> 基本データ型: * * **int** * *|  
|IsFulltextEnabled|データベースではフルテキストおよびセマンティック インデックス作成を有効にします。|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> <br /><br /> 1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力<br /><br /> 基本データ型: * * **int** * *<br /><br /> **注意:** このプロパティの値には、影響ありません。 ユーザー データベースでは、常にフルテキスト検索が有効になっています。 この列は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の将来のリリースでは削除される予定です。 新規の開発作業ではこの列を使用しないようにし、現在この列を使用しているアプリケーションはできるだけ早く修正してください。|  
|IsInStandBy|データベースは読み取り専用のオンライン状態で、復元ログが許可されています。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力<br /><br /> 基本データ型: * * **int** * *|  
|IsLocalCursorsDefault|カーソル宣言の既定値は LOCAL です。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力<br /><br /> 基本データ型: * * **int** * *|  
|IsMemoryOptimizedElevateToSnapshotEnabled|セッション設定 TRANSACTION ISOLATION LEVEL が低い分離レベル (READ COMMITTED または READ UNCOMMITTED) に設定されている場合は、SNAPSHOT 分離を使用してメモリ最適化テーブルにアクセスします。|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> <br /><br /> 1 = TRUE<br /><br /> 0 = FALSE<br /><br /> 基本データ型: * * **int** * *|  
|IsMergePublished|レプリケーションがインストールされている場合は、データベースのテーブルをマージ レプリケーション用にパブリッシュできます。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力<br /><br /> 基本データ型: * * **int** * *|  
|IsNullConcat|NULL を連結したオペランドは、NULL になります。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力<br /><br /> 基本データ型: * * **int** * *|  
|IsNumericRoundAbortEnabled|式の有効桁数が失われた場合にエラーが生成されます。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力<br /><br /> 基本データ型: * * **int** * *|  
|IsParameterizationForced|データベース SET オプション PARAMETERIZATION が FORCED に設定されています。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力|  
|IsQuotedIdentifiersEnabled|識別子に二重引用符を使用できます。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力<br /><br /> 基本データ型: * * **int** * *|  
|IsPublished|レプリケーションがインストールされている場合は、データベースのテーブルをスナップショット レプリケーションまたはトランザクション レプリケーション用にパブリッシュできます。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力<br /><br /> 基本データ型: * * **int** * *|  
|IsRecursiveTriggersEnabled|トリガーの再帰的な発生が許可されています。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力<br /><br /> 基本データ型: * * **int** * *|  
|IsSubscribed|データベースはパブリケーションにサブスクライブされます。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力<br /><br /> 基本データ型: * * **int** * *|  
|IsSyncWithBackup|データベースは、パブリッシュされたデータベース、またはディストリビューション データベースです。また、トランザクション レプリケーションを中断せずに復元できます。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力<br /><br /> 基本データ型: * * **int** * *|  
|IsTornPageDetectionEnabled|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]は、電源障害やその他のシステムの停止によって発生した不完全な I/O 操作を検出します。|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力<br /><br /> 基本データ型: * * **int** * *|  
|IsXTPSupported|データベースがインメモリ OLTP、つまり、メモリ最適化テーブルとネイティブ コンパイル モジュールの作成と使用をサポートするかどうかを示します。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に固有:<br /><br /> IsXTPSupported は、インメモリ OLTP オブジェクトを作成するために必要な MEMORY_OPTIMIZED_DATA ファイル グループの存在に依存しません。|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]。<br /><br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 以降の [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。<br /><br /> <br /><br /> 1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = 無効な入力、エラー、または該当なし<br /><br /> 基本データ型: * * **int** * *|  
|LCID (LCID)|照合順序の Windows ロケール識別子 (LCID) です。|LCID 値 (10 進数形式)。<br /><br /> 基本データ型: * * **int** * *|  
|MaxSizeInBytes|最大データベース サイズ (バイト単位)。|**適用対象**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]、[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]。<br /><br /> <br /><br /> 1073741824<br /><br /> 5368709120<br /><br /> 10737418240<br /><br /> 21474836480<br /><br /> 32212254720<br /><br /> 42949672960<br /><br /> 53687091200<br /><br /> NULL = データベースを閉じている場合<br /><br /> 基本データ型: * * * * **bigint** 型|  
|復旧|データベースの復旧モデルです。|FULL = 完全復旧モデル<br /><br /> BULK_LOGGED = 一括ログ復旧モデル<br /><br /> SIMPLE = 単純復旧モデル<br /><br /> 基本データ型: **nvarchar(128)**|  
|ServiceObjective|[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] または [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] のデータベースのパフォーマンス レベルについて説明します。|次のいずれかになります。<br /><br /> Null: データベースが開始されていません。<br /><br /> Shared (Web/Business エディション向け)<br /><br /> [標準]<br /><br /> S0<br /><br /> S1<br /><br /> S2<br /><br /> S3<br /><br /> P1<br /><br /> P2<br /><br /> P3<br /><br /> ElasticPool<br /><br /> System (マスター DB 向け)<br /><br /> 基本データ型: **nvarchar(32)**|  
|ServiceObjectiveId|[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] のサービス目標の ID です。|* * **uniqueidentifier** * * をサービス目標を識別します。|  
|SQLSortOrder|以前のバージョンの SQL Server でサポートされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 並べ替え順 ID です。|0 = データベースが Windows 照合順序を使用している場合<br /><br /> >0 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 並べ替え順 ID<br /><br /> NULL = 入力が有効ではないか、データベースを閉じている場合<br /><br /> 基本データ型: * * * * **tinyint**|  
|状態|データベースの状態です。|ONLINE = データベースをクエリに使用できます。<br /><br /> **注意:** データベースが開かれると、まだ復旧されていないときに、オンラインのステータスを取得することがあります。 照合順序プロパティをクエリに、データベースが接続を受け入れるときを特定するには、* * * * **DATABASEPROPERTYEX** です。 データベースは、データベースの照合順序から NULL 以外の値が返されたときに接続を受け入れることができます。 AlwaysOn データベースの場合は、sys.dm_hadr_database_replica_states の database_state または database_state_desc 列のクエリを実行します。<br /><br /> OFFLINE = データベースが明示的にオフラインになりました。<br /><br /> RESTORING = データベースは復元中です。<br /><br /> RECOVERING = データベースは復旧中で、まだクエリに使用できません。<br /><br /> SUSPECT = データベースを復旧できません。<br /><br /> EMERGENCY = データベースは、読み取り専用の緊急モードです。 sysadmin メンバーのみにアクセスが制限されます。<br /><br /> 基本データ型: **nvarchar(128)**|  
|Updateability|データを変更できるかどうかを示します。|READ_ONLY = データを読み取ることはできますが、変更できません。<br /><br /> READ_WRITE = データの読み取りと変更が可能です。<br /><br /> 基本データ型: **nvarchar(128)**|  
|UserAccess|データベースにアクセスできるユーザーを示します。|SINGLE_USER = 一度に 1 人の db_owner、dbcreator、または sysadmin ユーザーのみ<br /><br /> RESTRICTED_USER = db_owner、dbcreator、および sysadmin の各ロールのメンバーのみ<br /><br /> MULTI_USER = すべてのユーザー<br /><br /> 基本データ型: **nvarchar(128)**|  
|[バージョンのオプション]|このデータベースが作成された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コードの内部バージョン番号です。 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|バージョン番号 = データベースを開いている場合<br /><br /> NULL = データベースを閉じている場合<br /><br /> 基本データ型: * * **int** * *|  
  
## <a name="return-types"></a>戻り値の型
**sql_variant**
  
## <a name="exceptions"></a>例外  
エラーが発生した場合、または呼び出し元にオブジェクトの表示権限がない場合は、NULL が返されます。
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、そのユーザーが所有している、または権限を与えられている、セキュリティ保護可能なアイテムのメタデータのみを表示できます。 つまり、オブジェクトに対する権限がユーザーに与えられていない場合、メタデータを生成する組み込み関数 (OBJECT_ID など) が NULL を返す可能性があります。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。
  
## <a name="remarks"></a>Remarks  
DATABASEPROPERTYEX は、プロパティの設定値を一度に 1 つだけ返します。 表示するには複数のプロパティの設定を使用して、 [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) カタログ ビューです。
  
## <a name="examples"></a>使用例  
  
### <a name="a-retrieving-the-status-of-the-autoshrink-database-option"></a>A. AUTO_SHRINK データベース オプションの設定値を取得する  
次の例では、`AdventureWorks` データベースの AUTO_SHRINK データベース オプションの設定値を返します。
  
```sql
SELECT DATABASEPROPERTYEX('AdventureWorks2014', 'IsAutoShrink');  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]この結果セットは、AUTO_SHRINK がオフであることを示しています。
  
```sql
------------------  
0  
```  
  
### <a name="b-retrieving-the-default-collation-for-a-database"></a>B. データベースの既定の照合順序を取得する  
次の例は、`AdventureWorks` データベースの複数の属性を返します。
  
```sql
SELECT   
    DATABASEPROPERTYEX('AdventureWorks2014', 'Collation') AS Collation,  
    DATABASEPROPERTYEX('AdventureWorks2014', 'Edition') AS Edition,  
    DATABASEPROPERTYEX('AdventureWorks2014', 'ServiceObjective') AS ServiceObjective,  
    DATABASEPROPERTYEX('AdventureWorks2014', 'MaxSizeInBytes') AS MaxSizeInBytes  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Collation                     Edition        ServiceObjective  MaxSizeInBytes  
----------------------------  -------------  ----------------  --------------  
SQL_Latin1_General_CP1_CI_AS  DataWarehouse  DW1000            5368709120  
```  
  
## <a name="see-also"></a>参照
[ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
[データベースの状態](../../relational-databases/databases/database-states.md)  
[sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
[sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)  
[SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)
  
  
