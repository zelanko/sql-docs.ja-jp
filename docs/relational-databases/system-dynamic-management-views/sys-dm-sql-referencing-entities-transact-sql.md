---
title: sys.dm_sql_referencing_entities (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_sql_referencing_entities
- dm_sql_referencing_entities_TSQL
- sys.dm_sql_referencing_entities_TSQL
- dm_sql_referencing_entities
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_sql_referencing_entities dynamic management function
ms.assetid: c16f8f0a-483f-4feb-842e-da90426045ae
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: cf695b5524787d33694c775bd88744db4c5bd5c5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmsqlreferencingentities-transact-sql"></a>sys.dm_sql_referencing_entities (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在のデータベース内で、他のユーザー定義エンティティを名前で参照する各エンティティについて、対応する 1 行を返します。 1 つのエンティティが呼び出されたときに、2 つのエンティティ間の依存関係が作成された、*エンティティを参照*と呼ばれる別のエンティティの保存されている SQL 式で名前によって表示される、*エンティティを参照している*です。 たとえば、参照先エンティティとしてユーザー定義型 (UDT) を指定した場合、定義の中でその型を名前で参照する各ユーザー定義エンティティが返されます。 この関数は、指定したエンティティを参照していたとしても、他のデータベース内のエンティティは返しません。 この関数は、サーバー レベルの DDL トリガーを参照元エンティティとして返す master データベースのコンテキストで実行する必要があります。  
  
 この動的管理関数に参照先エンティティを指定すると、現在のデータベース内で、そのエンティティを参照する次の種類のエンティティをレポートできます。  
  
-   スキーマ バインドまたは非スキーマ バインド エンティティ  
  
-   データベース レベル DDL トリガー  
  
-   サーバー レベル DDL トリガー  
  
**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])、[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
sys.dm_sql_referencing_entities (  
    ' schema_name.referenced_entity_name ' , ' <referenced_class> ' )  
  
<referenced_class> ::=  
{  
    OBJECT  
  | TYPE  
  | XML_SCHEMA_COLLECTION  
  | PARTITION_FUNCTION  
}  
```  
  
## <a name="arguments"></a>引数  
 *schema_name.referenced*_*entity_name*  
 参照先エンティティの名前を指定します。  
  
 *schema_name*参照先のクラスが PARTITION_FUNCTION である場合を除くが必要です。  
  
 *schema_name.referenced_entity_name*は**nvarchar (517)** です。  
  
 *< Referenced_class >* :: = {オブジェクト |型 |XML_SCHEMA_COLLECTION |PARTITION_FUNCTION}  
 参照先エンティティのクラスを指定します。 クラスは 1 つのステートメントに 1 つだけ指定できます。  
  
 *< referenced_class >* は**nvarchar**(60)。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|referencing_schema_name|**sysname**|参照元エンティティが属しているスキーマ。 NULL 値が許可されます。<br /><br /> データベース レベルおよびサーバー レベルの DDL トリガーの場合は NULL です。|  
|referencing_entity_name|**sysname**|参照元エンティティの名前。 NULL 値は許可されません。|  
|referencing_id|**int**|参照元エンティティの ID。 NULL 値は許可されません。|  
|referencing_class|**tinyint**|参照元エンティティのクラス。 NULL 値は許可されません。<br /><br /> 1 = オブジェクト<br /><br /> 12 = データベース レベル DDL トリガー<br /><br /> 13 = サーバー レベル DDL トリガー|  
|referencing_class_desc|**nvarchar(60)**|参照元エンティティのクラスの説明です。<br /><br /> OBJECT<br /><br /> DATABASE_DDL_TRIGGER<br /><br /> SERVER_DDL_TRIGGER|  
|is_caller_dependent|**bit**|参照先エンティティが呼び出し元のスキーマに依存するため、参照先エンティティ ID の解決は実行時に行われることを示します。<br /><br /> この値が 1 の場合、参照元エンティティがエンティティを参照している可能性はあるものの、参照先エンティティ ID の解決は呼び出し元に依存するため特定できないことを示します。 これが該当するのは、EXECUTE ステートメント内で呼び出されるストアド プロシージャ、拡張ストアド プロシージャ、または、ユーザー定義関数に対する非スキーマ バインド参照だけです。<br /><br /> この値が 0 の場合、参照先エンティティは呼び出し元に依存しません。|  
  
## <a name="exceptions"></a>例外  
 次のいずれかの条件に該当した場合は、空の結果セットが返されます。  
  
-   システム オブジェクトが指定されている。  
  
-   指定されたエンティティが現在のデータベースに存在しない。  
  
-   指定されたエンティティがいずれのエンティティも参照しない。  
  
-   無効なパラメーターが渡される。  
  
 指定された参照先エンティティが番号付きストアド プロシージャの場合は、エラーが返されます。  
  
## <a name="remarks"></a>解説  
 次の表に、依存関係情報が作成および管理されるエンティティの種類を示します。 ルール、既定値、一時テーブル、一時ストアド プロシージャ、またはシステム オブジェクトについては、依存関係情報は作成も管理もされません。  
  
|エンティティの種類|参照元エンティティ|参照先エンティティ|  
|-----------------|------------------------|-----------------------|  
|Table|可*|はい|  
|表示|はい|はい|  
|[!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャ**|はい|はい|  
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
  
 \* テーブルは、参照している場合にのみ、参照元エンティティとして追跡、[!INCLUDE[tsql](../../includes/tsql-md.md)]モジュール、ユーザー定義型、または計算列、CHECK 制約、または既定の制約の定義の XML スキーマ コレクションです。  
  
 ** 1 より大きな整数値を持つ番号付きストアド プロシージャは、参照元エンティティとしても、参照先エンティティとしても追跡されません。  
  
## <a name="permissions"></a>権限  
  
### <a name="includesskatmaiincludessskatmai-mdmd--includesssql11includessssql11-mdmd"></a>[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] – [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   参照されるオブジェクトに対する CONTROL 権限が必要です。 参照先エンティティがパーティション関数である場合、データベースに対する CONTROL 権限が必要です。  
  
-   Sys.dm_sql_referencing_entities に対する SELECT 権限が必要です。 既定では、SELECT 権限が public に与えられます。  
  
### <a name="includesssql14includessssql14-mdmd---includesscurrentincludessscurrent-mdmd"></a>[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] - [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
-   参照されるオブジェクトに対する権限は必要ありません。 ユーザーが一部の参照元エンティティだけの VIEW DEFINITION を持っている場合は、結果の一部を返すことができます。  
  
-   参照元エンティティがオブジェクトの場合は、オブジェクトに対する VIEW DEFINITION が必要です。  
  
-   参照元エンティティがデータベース レベルの DDL トリガーである場合は、データベースに対する VIEW DEFINITION が必要です。  
  
-   参照元エンティティがサーバー レベルの DDL トリガーである場合は、サーバーに対する VIEW ANY DEFINITION が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-the-entities-that-refer-to-a-given-entity"></a>A. 特定のエンティティを参照するエンティティを取得する  
 次の例では、現在のデータベース内で、指定したテーブルを参照するエンティティを取得します。  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT referencing_schema_name, referencing_entity_name, referencing_id, referencing_class_desc, is_caller_dependent  
FROM sys.dm_sql_referencing_entities ('Production.Product', 'OBJECT');  
GO  
```  
  
### <a name="b-returning-the-entities-that-refer-to-a-given-type"></a>B. 指定された型を参照するエンティティを取得する  
 次の例は、別名型を参照するエンティティを返します`dbo.Flag`です。 結果セットには、この型を使用する 2 つのストアド プロシージャが示されます。 `dbo.Flag`型は、いくつかの列の定義では使用も、`HumanResources.Employee`テーブルですただし、、の型が計算列、CHECK 制約、またはテーブルの既定の制約の定義ではない行は返されません、 `HumanResources.Employee`。テーブル。  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT referencing_schema_name, referencing_entity_name, referencing_id, referencing_class_desc, is_caller_dependent  
FROM sys.dm_sql_referencing_entities ('dbo.Flag', 'TYPE');  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 referencing_schema_name referencing_entity_name   referencing_id referencing_class_desc is_caller_dependent  
 ----------------------- -------------------------  ------------- ---------------------- -------------------  
 HumanResources          uspUpdateEmployeeHireInfo  1803153469    OBJECT_OR_COLUMN       0  
 HumanResources          uspUpdateEmployeeLogin     1819153526    OBJECT_OR_COLUMN       0  
 (2 row(s) affected)`  
 ``` 
 
## <a name="see-also"></a>参照  
 [sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md)   
 [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)  
  
  
