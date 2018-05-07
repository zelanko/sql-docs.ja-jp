---
title: sp_tables (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_tables
- sp_tables_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_tables
ms.assetid: 787a2fa5-87a1-49bd-938b-6043c245f46b
caps.latest.revision: 43
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: b0a4e8b4ae1b78da17beb1a5289a90782979ad3c
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sptables-transact-sql"></a>sp_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在の環境でクエリされるオブジェクトの一覧が返されます。 これは、シノニム オブジェクトを除く、ユーザー テーブルまたはビューを表します。  
  
> [!NOTE]  
>  シノニムのベース オブジェクトの名前を確認するのには、クエリ、 [sys.synonyms](../../relational-databases/system-catalog-views/sys-synonyms-transact-sql.md)カタログ ビューです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
sp_tables [ [ @table_name = ] 'name' ]   
     [ , [ @table_owner = ] 'owner' ]   
     [ , [ @table_qualifier = ] 'qualifier' ]   
     [ , [ @table_type = ] "type" ]   
     [ , [@fUsePattern = ] 'fUsePattern'];  
```  
  
## <a name="arguments"></a>引数  
 [ **@table_name=** ] **'***name***'**  
 カタログ情報を返すために使用するテーブルを指定します。 *名前*は**nvarchar (384)**、既定値は NULL です。 ワイルドカードによるパターン照合がサポートされています。  
  
 [  **@table_owner=** ] **'***所有者***'**  
 カタログ情報を返すために使用するテーブルのテーブル所有者です。 *所有者*は**nvarchar (384)**、既定値は NULL です。 ワイルドカードによるパターン照合がサポートされています。 所有者を指定しない場合は、基になる DBMS の既定のテーブル可視性ルールが適用されます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、現在のユーザーには、指定した名前を持つテーブルを所有している、そのテーブルの列が返されます。 所有者を指定せず、かつ、指定した名前のテーブルを現在のユーザーが所有していない場合は、このプロシージャは、データベース所有者が所有する、指定された名前のテーブルを探します。 そのテーブルが存在する場合、そのテーブルの列が返されます。  
  
 [  **@table_qualifier=** ] **'***修飾子***'**  
 テーブル識別子の名前です。 *修飾子*は**sysname**、既定値は NULL です。 さまざまな DBMS 製品は、3 部構成テーブルの名前付けをサポート (*修飾子 ***.*** 所有者 ***.*** 名前*)。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、この列は、データベースの名前を表します。 一部の製品では、テーブルのデータベース環境のサーバー名を表します。  
  
 [ **、** [  **@table_type=** ] **"'***型***'**、 **'** 型 **'"** ]  
 指定したテーブル型のすべてのテーブルに関する情報を持つ、コンマで区切られた値の一覧です。 これらを含める**テーブル**、 **SYSTEMTABLE**、および**ビュー**です。 *型*は**varchar (100)**、既定値は NULL です。  
  
> [!NOTE]  
>  テーブル型はそれぞれ単一引用符で囲み、パラメーター全体を二重引用符で囲む必要があります。 テーブル型は必ず大文字です。 SET QUOTED_IDENTIFIER がオンになっている場合は、単一引用符をそれぞれ 2 つずつ付け、パラメーター全体を単一引用符で囲む必要があります。  
  
 [  **@fUsePattern =** ] **'***fUsePattern***'**  
 アンダースコア (_)、パーセント (%)、および角かっこ ([ または ]) の各文字がワイルドカードとして解釈されるかどうかを決定します。 有効な値は 0 (パターン一致がオフ) および 1 (パターン一致がオン) です。 *fUsePattern*は**ビット**、既定値は 1 です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_QUALIFIER**|**sysname**|テーブル修飾子の名前。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、この列は、データベースの名前を表します。 このフィールドには NULL を指定できます。|  
|**TABLE_OWNER**|**sysname**|テーブル所有者名です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、この列がテーブルを作成したデータベース ユーザーの名前を表します。 このフィールドは常に値を返します。|  
|**TABLE_NAME**|**sysname**|テーブル名です。 このフィールドは常に値を返します。|  
|**TABLE_TYPE**|**varchar (32)**|テーブル、システム テーブル、またはビューです。|  
|**「解説」**|**varchar(254)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] この列の値を返しません。|  
  
## <a name="remarks"></a>解説  
 相互運用可能性を最大にするため、ゲートウェイのクライアントは、SQL-92 標準の SQL パターン照合 (% と _ ワイルドカード文字) のみを想定してください。  
  
 特定のテーブルに対する、現在のユーザーの読み取りおよび書き込みアクセス権についての特権情報は必ずしも確認されません。 したがって、アクセスは保証されません。 この結果セットには、テーブルとビューだけでなく、それらの型をサポートする DBMS 製品へのゲートウェイのシノニムや別名も含まれます。 場合、サーバー属性**ACCESSIBLE_TABLES**が Y の結果セットの**sp_server_info**、現在のユーザーがアクセスできるテーブルのみが返されます。  
  
 **sp_tables**は等価**SQLTables** ODBC にします。 返される結果は並べ**TABLE_TYPE**、 **TABLE_QUALIFIER**、 **TABLE_OWNER**、および**TABLE_NAME**です。  
  
## <a name="permissions"></a>権限  
 スキーマに対する SELECT 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-a-list-of-objects-that-can-be-queried-in-the-current-environment"></a>A. 現在の環境でクエリされるオブジェクトの一覧を返す  
 次の例では、現在の環境でクエリされるオブジェクトの一覧が返されます。  
  
```  
EXEC sp_tables ;  
```  
  
### <a name="b-returning-information-about-the-tables-in-a-specified-schema"></a>B. 指定したスキーマ内のテーブルに関する情報を返す  
 次の例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベース内の `Person` スキーマに属するテーブルに関する情報が返されます。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_tables   
   @table_name = '%',  
   @table_owner = 'Person',  
   @table_qualifier = 'AdventureWorks2012';  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-returning-a-list-of-objects-that-can-be-queried-in-the-current-environment"></a>C. 現在の環境でクエリされるオブジェクトの一覧を返す  
 次の例では、現在の環境でクエリされるオブジェクトの一覧が返されます。  
  
```  
EXEC sp_tables ;  
```  
  
### <a name="d-returning-information-about-the-tables-in-a-specified-schema"></a>D. 指定したスキーマ内のテーブルに関する情報を返す  
 次の例は、内のディメンション テーブルに関する情報を返します、`AdventureWorksPDW201`データベース。  
  
```  
-- Uses AdventureWorks  
  
EXEC sp_tables   
   @table_name = 'Dim%',  
   @table_owner = 'dbo',  
   @table_qualifier = 'AdventureWorksPDW2012';  
```  
  
## <a name="see-also"></a>参照  
 [sys.synonyms &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-synonyms-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

