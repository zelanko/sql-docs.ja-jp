---
title: sys.objects (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 05/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.objects_TSQL
- objects
- sys.objects
- objects_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.objects catalog view
- table-valued parameters, sys.objects catalog view
- user-defined table types [SQL Server]
- table types [SQL Server]
ms.assetid: f8d6163a-2474-410c-a794-997639f31b3b
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 47e332d8dfda76bbf2702335b72793c112c15d75
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68102321"
---
# <a name="sysobjects-transact-sql"></a>sys.objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  ネイティブ コンパイルのスカラー ユーザー定義関数を含む、データベース内で作成されるユーザー定義のスキーマ スコープ オブジェクトごとに行が含まれています。  
  
 詳しくは、「[インメモリ OLTP でのユーザー定義のスカラー関数](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md)」をご覧ください。  
  
> [!NOTE]  
>  sys.objects では、スキーマ スコープはないために、DDL トリガー, は表示されません。 すべてのトリガー、DML と DDL の両方にあるは[sys.triggers](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md)します。 sys.triggers には、さまざまな種類のトリガーの名前スコープ ルールの組み合わせがサポートされています。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|NAME|**sysname**|オブジェクト名です。|  
|object_id|**int**|オブジェクト ID 番号。 データベース内で一意です。|  
|principal_id|**int**|スキーマの所有者と異なる場合、個々 の所有者の ID。 既定では、スキーマに含まれるオブジェクトは、スキーマの所有者によって所有されます。 ただし、所有権を変更する ALTER AUTHORIZATION ステートメントを使用して、別の所有者を指定できます。<br /><br /> 別の所有者がない場合は NULL です。<br /><br /> オブジェクトの型が次のいずれかの場合は NULL になります。<br /><br /> C = CHECK 制約<br /><br /> D = DEFAULT (制約またはスタンドアロン)<br /><br /> F = FOREIGN KEY 制約<br /><br /> PK = PRIMARY KEY 制約<br /><br /> R = ルール (旧形式、スタンドアロン)<br /><br /> TA = アセンブリ (CLR 統合) トリガー<br /><br /> TR = SQL トリガー<br /><br /> UQ = UNIQUE 制約<br /><br /> EC エッジの制約を = |  
|schema_id|**int**|オブジェクトに含まれるスキーマの ID。<br /><br /> スキーマ スコープ システム オブジェクトは、常に sys スキーマまたは INFORMATION_SCHEMA スキーマに含まれています。|  
|parent_object_id|**int**|このオブジェクトが所属するオブジェクトの ID。<br /><br /> 0 = 子オブジェクトではありません。|  
|type|**char(2)**|オブジェクトの種類:<br /><br /> AF = 集計関数 (CLR)<br /><br /> C = CHECK 制約<br /><br /> D = DEFAULT (制約またはスタンドアロン)<br /><br /> F = FOREIGN KEY 制約<br /><br /> FN = SQL スカラー関数<br /><br /> FS = アセンブリ (CLR) スカラー関数<br /><br /> FT = アセンブリ (CLR) テーブル値関数<br /><br /> IF = SQL インライン テーブル値関数<br /><br /> IT = 内部テーブル<br /><br /> P = SQL ストアド プロシージャ<br /><br /> PC = アセンブリ (CLR) ストアド プロシージャ<br /><br /> PG = プラン ガイド<br /><br /> PK = PRIMARY KEY 制約<br /><br /> R = ルール (旧形式、スタンドアロン)<br /><br /> RF = レプリケーション フィルター プロシージャ<br /><br /> S = システム ベース テーブル<br /><br /> SN = シノニム<br /><br /> SO = シーケンス オブジェクト<br /><br /> U = テーブル (ユーザー定義)<br /><br /> V = ビュー<br /><br /> EC エッジの制約を = <br /><br /> <br /><br /> **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> <br /><br /> SQ = サービス キュー<br /><br /> TA = アセンブリ (CLR) DML トリガー<br /><br /> TF = SQL テーブル値関数<br /><br /> TR = SQL DML トリガー<br /><br /> TT = テーブル型<br /><br /> UQ = UNIQUE 制約<br /><br /> X = 拡張ストアド プロシージャ<br /><br /> <br /><br /> **適用対象**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]、 [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]します。<br /><br /> <br /><br /> ET 外部テーブルを =|  
|type_desc|**nvarchar(60)**|オブジェクトの種類の説明です。<br /><br /> AGGREGATE_FUNCTION<br /><br /> CHECK_CONSTRAINT<br /><br /> CLR_SCALAR_FUNCTION<br /><br /> CLR_STORED_PROCEDURE<br /><br /> CLR_TABLE_VALUED_FUNCTION<br /><br /> CLR_TRIGGER<br /><br /> DEFAULT_CONSTRAINT<br /><br /> EXTENDED_STORED_PROCEDURE<br /><br /> FOREIGN_KEY_CONSTRAINT<br /><br /> INTERNAL_TABLE<br /><br /> PLAN_GUIDE<br /><br /> PRIMARY_KEY_CONSTRAINT<br /><br /> REPLICATION_FILTER_PROCEDURE<br /><br /> RULE<br /><br /> SEQUENCE_OBJECT<br /><br /> <br /><br /> **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> <br /><br /> SERVICE_QUEUE<br /><br /> SQL_INLINE_TABLE_VALUED_FUNCTION<br /><br /> SQL_SCALAR_FUNCTION<br /><br /> SQL_STORED_PROCEDURE<br /><br /> SQL_TABLE_VALUED_FUNCTION<br /><br /> SQL_TRIGGER<br /><br /> SYNONYM<br /><br /> SYSTEM_TABLE<br /><br /> TABLE_TYPE<br /><br /> UNIQUE_CONSTRAINT<br /><br /> USER_TABLE<br /><br /> VIEW|  
|create_date|**datetime**|オブジェクトが作成された日付です。|  
|modify_date|**datetime**|ALTER ステートメントを使用して、オブジェクトの最終更新日。 オブジェクトがテーブルまたはビューの場合は、テーブルやビューのクラスター化インデックスが作成または変更されると、modify_date も変更されます。|  
|is_ms_shipped|**bit**|オブジェクトが内部 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントによって作成されることを示します。|  
|is_published|**bit**|オブジェクトが発行されます。|  
|is_schema_published|**bit**|オブジェクトのスキーマのみがパブリッシュされることを示します。|  
  
## <a name="remarks"></a>コメント  
 適用することができます、 [OBJECT_ID](../../t-sql/functions/object-id-transact-sql.md)、 [OBJECT_NAME](../../t-sql/functions/object-name-transact-sql.md)、および[OBJECTPROPERTY](../../t-sql/functions/objectproperty-transact-sql.md)sys.objects に表示されるオブジェクトへの () 組み込み関数。  
  
 このビューと呼ばれる、同じスキーマのバージョンがある[sys.system_objects](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md)、システム オブジェクトを表示します。 呼ばれる別のビューがある[sys.all_objects](../../relational-databases/system-catalog-views/sys-all-objects-transact-sql.md)システムとユーザーの両方のオブジェクトを表示します。 すべての 3 つのカタログ ビューには、同じ構造があります。  
  
 このバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、XML インデックスや空間インデックスなどの拡張インデックスは、sys.objects で内部テーブルと見なされます (type = IT および type_desc = INTERNAL_TABLE)。 拡張インデックスの場合。  
  
-   名前は、インデックス テーブルの内部名です。  
  
-   parent_object_id はベース テーブルの object_id です。  
  
-   is_ms_shipped、is_published、is_schema_published の各列は 0 に設定されます。  

**関連する便利なシステム ビュー**  
など、オブジェクトの特定の種類のシステム ビューを使用して、オブジェクトのサブセットを表示できます。  
- [sys.tables](sys-tables-transact-sql.md)  
- [sys.views](sys-views-transact-sql.md)  
- [sys.procedures](sys-procedures-transact-sql.md)  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-all-the-objects-that-have-been-modified-in-the-last-n-days"></a>A. 過去 n 日間に変更されたすべてのオブジェクトを返す  
 次のクエリの `<database_name>` と `<n_days>` を有効な値に置き換えてから、クエリを実行します。  
  
```sql  
USE <database_name>;  
GO  
SELECT name AS object_name   
  ,SCHEMA_NAME(schema_id) AS schema_name  
  ,type_desc  
  ,create_date  
  ,modify_date  
FROM sys.objects  
WHERE modify_date > GETDATE() - <n_days>  
ORDER BY modify_date;  
GO  
```  
  
### <a name="b-returning-the-parameters-for-a-specified-stored-procedure-or-function"></a>B. 指定されたストアド プロシージャまたは関数に対するパラメーターを返す  
 次のクエリを実行する前に置き換える`<database_name>`と`<schema_name.object_name>`を有効な名前。  
  
```sql  
USE <database_name>;  
GO  
SELECT SCHEMA_NAME(schema_id) AS schema_name  
    ,o.name AS object_name  
    ,o.type_desc  
    ,p.parameter_id  
    ,p.name AS parameter_name  
    ,TYPE_NAME(p.user_type_id) AS parameter_type  
    ,p.max_length  
    ,p.precision  
    ,p.scale  
    ,p.is_output  
FROM sys.objects AS o  
INNER JOIN sys.parameters AS p ON o.object_id = p.object_id  
WHERE o.object_id = OBJECT_ID('<schema_name.object_name>')  
ORDER BY schema_name, object_name, p.parameter_id;  
GO  
```  
  
### <a name="c-returning-all-the-user-defined-functions-in-a-database"></a>C. データベース内のすべてのユーザー定義関数を返す  
 次のクエリを実行する前に置き換える`<database_name>`有効なデータベース名を使用します。  
  
```sql  
USE <database_name>;  
GO  
SELECT name AS function_name   
  ,SCHEMA_NAME(schema_id) AS schema_name  
  ,type_desc  
  ,create_date  
  ,modify_date  
FROM sys.objects  
WHERE type_desc LIKE '%FUNCTION%';  
GO  
```  
  
### <a name="d-returning-the-owner-of-each-object-in-a-schema"></a>D. スキーマ内の各オブジェクトの所有者を返す  
 次のクエリの `<database_name>` と `<schema_name>` をすべて有効な名前に置き換えてから、クエリを実行します。  
  
```sql  
USE <database_name>;  
GO  
SELECT 'OBJECT' AS entity_type  
    ,USER_NAME(OBJECTPROPERTY(object_id, 'OwnerId')) AS owner_name  
    ,name   
FROM sys.objects WHERE SCHEMA_NAME(schema_id) = '<schema_name>'  
UNION   
SELECT 'TYPE' AS entity_type  
    ,USER_NAME(TYPEPROPERTY(SCHEMA_NAME(schema_id) + '.' + name, 'OwnerId')) AS owner_name  
    ,name   
FROM sys.types WHERE SCHEMA_NAME(schema_id) = '<schema_name>'   
UNION  
SELECT 'XML SCHEMA COLLECTION' AS entity_type   
    ,COALESCE(USER_NAME(xsc.principal_id),USER_NAME(s.principal_id)) AS owner_name  
    ,xsc.name   
FROM sys.xml_schema_collections AS xsc JOIN sys.schemas AS s  
    ON s.schema_id = xsc.schema_id  
WHERE s.name = '<schema_name>';  
GO  
```  
  
## <a name="see-also"></a>関連項目  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.all_objects &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-objects-transact-sql.md)   
 [sys.system_objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md)   
 [sys.triggers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md)   
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [SQL Server のシステム カタログよく寄せられる質問のクエリを実行します。](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.internal_tables &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-internal-tables-transact-sql.md)  
  
  
