---
title: sys.sql_expression_dependencies (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sql_expression_dependencies
- sql_expression_dependencies_TSQL
- sql_expression_dependencies
- sys.sql_expression_dependencies_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sql_expression_dependencies catalog view
ms.assetid: 78a218e4-bf99-4a6a-acbf-ff82425a5946
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e4ef878879fb5c2896c45aedbf2a86f83557804c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47826187"
---
# <a name="syssqlexpressiondependencies-transact-sql"></a>sys.sql_expression_dependencies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  ユーザー定義エンティティに対する名前による依存関係ごとに 1 つの行を現在のデータベースに格納します。 これにより、ネイティブ コンパイル、スカラー ユーザー定義関数、およびその他の間の依存関係が含まれます。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]モジュール。 1 つのエンティティが呼び出されたときに、2 つのエンティティ間の依存関係が作成された、*エンティティを参照*と呼ばれる別のエンティティの永続化された SQL 式で名前が、*エンティティを参照する*します。 たとえば、ビューの定義内でテーブルが参照されている場合、参照元エンティティであるビューは、参照先エンティティであるテーブルに依存します。 テーブルが削除された場合、ビューは使用できなくなります。  
  
 詳しくは、「[インメモリ OLTP でのユーザー定義のスカラー関数](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md)」をご覧ください。  
  
 このカタログ ビューを使用すると、次のエンティティについて依存関係情報をレポートできます。  
  
-   スキーマ バインド エンティティ。  
  
-   非スキーマ バインド エンティティ。  
  
-   複数のデータベースやサーバーにまたがるエンティティ。 エンティティ名はレポートされますが、エンティティ ID は解決されません。  
  
-   スキーマ バインド エンティティの列レベルの依存関係。 非スキーマ バインド オブジェクトの列レベルの依存関係を使用して返される[sys.dm_sql_referenced_entities](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md)します。  
  
-   サーバーレベルの DDL トリガー (master データベースのコンテキスト内)。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|referencing_id|**int**|参照元エンティティの ID。 NULL 値は許可されません。|  
|referencing_minor_id|**int**|参照元エンティティが列の場合は列 ID。それ以外の場合は 0。 NULL 値は許可されません。|  
|referencing_class|**tinyint**|参照元エンティティのクラス。<br /><br /> 1 = オブジェクトまたは列<br /><br /> 12 = データベース DDL トリガー<br /><br /> 13 = サーバー DDL トリガー<br /><br /> NULL 値は許可されません。|  
|referencing_class_desc|**nvarchar(60)**|参照元エンティティのクラスの説明。<br /><br /> OBJECT_OR_COLUMN<br /><br /> DATABASE_DDL_TRIGGER<br /><br /> SERVER_DDL_TRIGGER<br /><br /> NULL 値は許可されません。|  
|is_schema_bound_reference|**bit**|1 = 参照先エンティティはスキーマ バインドです。<br /><br /> 0 = 参照先エンティティは非スキーマ バインドです。<br /><br /> NULL 値は許可されません。|  
|referenced_class|**tinyint**|参照先エンティティのクラス。<br /><br /> 1 = オブジェクトまたは列<br /><br /> 6 = 型<br /><br /> 10 = XML スキーマ コレクション<br /><br /> 21 = パーティション関数<br /><br /> NULL 値は許可されません。|  
|referenced_class_desc|**nvarchar(60)**|参照先エンティティのクラスの説明。<br /><br /> OBJECT_OR_COLUMN<br /><br /> TYPE<br /><br /> XML_SCHEMA_COLLECTION<br /><br /> PARTITION_FUNCTION<br /><br /> NULL 値は許可されません。|  
|referenced_server_name|**sysname**|参照先エンティティのサーバー名。<br /><br /> 有効な 4 部構成の名前を指定することによって作成されたサーバー間依存関係については、この列に値が格納されます。 マルチパート名については、次を参照してください。 [TRANSACT-SQL 構文表記規則&#40;TRANSACT-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)します。<br /><br /> 4 部構成の名前を指定せずにエンティティが参照される非スキーマ バインド エンティティの場合は NULL。<br /><br /> のみ定義できます 2 つの部分を使用して、同じデータベースである必要がありますのでスキーマ バインド エンティティの場合は NULL (*schema.object*) の名前。|  
|referenced_database_name|**sysname**|参照先エンティティのデータベース名。<br /><br /> 有効な 3 部構成または 4 部構成の名前を指定することによって作成された複数データベースまたは複数サーバーにまたがる参照については、この列に値が格納されます。<br /><br /> 1 部構成または 2 部構成の名前を使って指定された非スキーマ バインド参照の場合は NULL。<br /><br /> のみ定義できます 2 つの部分を使用して、同じデータベースである必要がありますのでスキーマ バインド エンティティの場合は NULL (*schema.object*) の名前。|  
|referenced_schema_name|**sysname**|参照先エンティティが属しているスキーマ。<br /><br /> スキーマ名を指定せずにエンティティが参照される非スキーマ バインド参照の場合は NULL。<br /><br /> スキーマ バインド エンティティは 2 つの部分で構成される名前を使用して定義および参照する必要があるので、スキーマ バインド参照の場合、NULL にすることはできません。|  
|referenced_entity_name|**sysname**|参照先エンティティの名前。 NULL 値は許可されません。|  
|referenced_id|**int**|参照先エンティティの ID。 この列の値は、スキーマ バインド参照の NULL はことはありません。 この列の値は、サーバー間およびデータベース間の参照を NULL では常にします。<br /><br /> データベース内の参照で ID を判別できない場合は、NULL。 非スキーマ バインド参照では、次の場合に ID を解決できません。<br /><br /> 参照先エンティティがデータベースに存在しない。<br /><br /> 参照先エンティティのスキーマが呼び出し元に依存し、実行時に解決される。 この場合、is_caller_dependent は 1 に設定されます。|  
|referenced_minor_id|**int**|参照元エンティティが列の場合は参照される列の ID。それ以外の場合は 0。 NULL 値は許可されません。<br /><br /> 参照元エンティティの中で列が名前で指定されていた場合、または SELECT * ステートメントの中で親エンティティが使用されていた場合、参照先エンティティは列になります。|  
|is_caller_dependent|**bit**|参照先エンティティのスキーマ バインドが実行時に行われるため、エンティティ ID の解決が呼び出し元のスキーマに依存することを示します。 これが該当するのは、参照先エンティティがストアド プロシージャ、拡張ストアド プロシージャ、または、EXECUTE ステートメント内で呼び出される非スキーマ バインド ユーザー定義関数である場合です。<br /><br /> 1 = 参照先エンティティが呼び出し元に依存し、実行時に解決します。 この場合、referenced_id は NULL です。<br /><br /> 0 = 参照先エンティティの ID は呼び出し元に依存しません。<br /><br /> スキーマ バインド参照のほか、スキーマ名を明示的に指定するデータベース間参照やサーバー間参照の場合は常に 0 になります。 たとえば、`EXEC MyDatabase.MySchema.MyProc` 形式のエンティティ参照は呼び出し元に依存しません。 ただしの形式での参照を`EXEC MyDatabase..MyProc`は呼び出し元が依存します。|  
|is_ambiguous|**bit**|参照があいまいであり、実行時、ユーザー定義関数、ユーザー定義型 (UDT)、または型の列への xquery 参照に解決できることを示します**xml**します。<br /><br /> たとえば、あるステートメント`SELECT Sales.GetOrder() FROM Sales.MySales`ストアド プロシージャで定義されます。 `Sales.GetOrder()` が `Sales` スキーマ内のユーザー定義関数なのか、`Sales` という名前のメソッドを持つ UDT 型の `GetOrder()` という名前の列なのかは、ストアド プロシージャが実行されるまで不明です。<br /><br /> 1 = 参照はあいまいです。<br /><br /> 0 = 参照は明確です。つまり、ビューを呼び出したときに、エンティティを正しくバインドできます。<br /><br /> スキーマの 0 は、常に参照をバインドします。|  
  
## <a name="remarks"></a>コメント  
 次の表に、依存関係情報が作成および管理されるエンティティの種類を示します。 ルール、既定値、一時テーブル、一時ストアド プロシージャ、またはシステム オブジェクトについては、依存関係情報は作成も管理もされません。  
  
|エンティティの種類|参照元エンティティ|参照先エンティティ|  
|-----------------|------------------------|-----------------------|  
|テーブル|可*|はい|  
|表示|はい|はい|  
|フィルター選択されたインデックス|可**|いいえ|  
|フィルター選択された統計|可**|いいえ|  
|[!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャ***|はい|はい|  
|CLR ストアド プロシージャ (CLR stored procedure)|いいえ|はい|  
|[!INCLUDE[tsql](../../includes/tsql-md.md)] ユーザー定義関数|はい|はい|  
|CLR ユーザー定義関数|いいえ|はい|  
|CLR トリガー (DML および DDL)|いいえ|いいえ|  
|[!INCLUDE[tsql](../../includes/tsql-md.md)] DML トリガー|はい|いいえ|  
|[!INCLUDE[tsql](../../includes/tsql-md.md)] データベース レベルの DDL トリガー|はい|いいえ|  
|[!INCLUDE[tsql](../../includes/tsql-md.md)] サーバー レベルの DDL トリガー|はい|いいえ|  
|拡張ストアド プロシージャ|いいえ|はい|  
|キュー|いいえ|はい|  
|シノニム|いいえ|はい|  
|型 (別名および CLR ユーザー定義型)|いいえ|はい|  
|XML スキーマ コレクション|いいえ|はい|  
|パーティション関数|いいえ|はい|  
  
 \* テーブルは、参照する場合にのみ、参照元エンティティとして追跡を[!INCLUDE[tsql](../../includes/tsql-md.md)]モジュール、ユーザー定義型、または計算列、CHECK 制約、または既定の制約の定義の XML スキーマ コレクションです。  
  
 ** フィルター述語で使用する各列は、参照元エンティティとして追跡されます。  
  
 *** 1 より大きな整数値を持つ番号付きストアド プロシージャは、参照元エンティティとしても、参照先エンティティとしても追跡されません。  
  
## <a name="permissions"></a>アクセス許可  
 データベースに対する VIEW DEFINITION 権限およびデータベースの sys.sql_expression_dependencies に対する SELECT 権限が必要です。 既定では、SELECT 権限は db_owner 固定データベース ロールのメンバーだけに与えられます。 SELECT 権限と VIEW DEFINITION 権限が別のユーザーに与えられている場合、権限が許可されているユーザーはデータベース内のすべての依存関係を表示できます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-entities-that-are-referenced-by-another-entity"></a>A. 別のエンティティによって参照されるエンティティを取得する  
 次の例では、ビュー `Production.vProductAndDescription` 内で参照されているテーブルおよび列を取得します。 ビューが依存に返されるエンティティ (テーブルおよび列)、`referenced_entity_name`と`referenced_column_name`列。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT OBJECT_NAME(referencing_id) AS referencing_entity_name,   
    o.type_desc AS referencing_desciption,   
    COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
    referencing_class_desc,  
    referenced_server_name, referenced_database_name, referenced_schema_name,  
    referenced_entity_name,   
    COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,  
    is_caller_dependent, is_ambiguous  
FROM sys.sql_expression_dependencies AS sed  
INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
WHERE referencing_id = OBJECT_ID(N'Production.vProductAndDescription');  
GO  
  
```  
  
### <a name="b-returning-entities-that-reference-another-entity"></a>B. 別のエンティティを参照するエンティティを取得する  
 次の例では、テーブル `Production.Product` を参照するエンティティを取得します。 `referencing_entity_name` 列に返されるエンティティは、`Product` テーブルに依存します。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT OBJECT_SCHEMA_NAME ( referencing_id ) AS referencing_schema_name,  
    OBJECT_NAME(referencing_id) AS referencing_entity_name,   
    o.type_desc AS referencing_desciption,   
    COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
    referencing_class_desc, referenced_class_desc,  
    referenced_server_name, referenced_database_name, referenced_schema_name,  
    referenced_entity_name,   
    COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,  
    is_caller_dependent, is_ambiguous  
FROM sys.sql_expression_dependencies AS sed  
INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
WHERE referenced_id = OBJECT_ID(N'Production.Product');  
GO  
  
```  
  
### <a name="c-returning-cross-database-dependencies"></a>C. データベース間の依存関係を取得する  
 次の例では、データベース間の依存関係をすべて取得します。 例では、まずデータベースを作成する`db1`と 2 つのストアド プロシージャ、データベース内のテーブルを参照する`db2`と`db3`します。 次に、`sys.sql_expression_dependencies` テーブルに対してクエリを実行して、プロシージャとテーブルの間のデータベース間依存関係をレポートします。 参照先エンティティ `referenced_schema_name` の `t3` 列に NULL が返されることに注意してください。これは、プロシージャの定義の中でそのエンティティにスキーマ名が指定されていないためです。  
  
```  
CREATE DATABASE db1;  
GO  
USE db1;  
GO  
CREATE PROCEDURE p1 AS SELECT * FROM db2.s1.t1;  
GO  
CREATE PROCEDURE p2 AS  
    UPDATE db3..t3  
    SET c1 = c1 + 1;  
GO  
SELECT OBJECT_NAME (referencing_id),referenced_database_name,   
    referenced_schema_name, referenced_entity_name  
FROM sys.sql_expression_dependencies  
WHERE referenced_database_name IS NOT NULL;  
GO  
USE master;  
GO  
DROP DATABASE db1;  
GO  
  
```  
  
## <a name="see-also"></a>参照  
 [sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md)   
 [sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md)  
  
  
