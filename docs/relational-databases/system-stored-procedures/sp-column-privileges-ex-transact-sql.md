---
title: sp_column_privileges_ex (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_column_privileges_ex
- sp_column_privileges_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_column_privileges_ex
ms.assetid: 98cb6e58-4007-40fc-b048-449fb2e7e6be
caps.latest.revision: 34
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 36e3f3c95614fda36c12309c1252b76cdc2da208
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="spcolumnprivilegesex-transact-sql"></a>sp_column_privileges_ex (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたリンク サーバー上の指定されたテーブルの列の特権を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_column_privileges_ex [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]   
     [ , [ @table_catalog = ] 'table_catalog' ]   
     [ , [ @column_name = ] 'column_name' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@table_server =** ] **'***table_server***'**  
 情報を返すリンク サーバーの名前を指定します。 *table_server*は**sysname**、既定値はありません。  
  
 [  **@table_name =** ] **'***table_name***'**  
 指定した列が含まれるテーブルの名前を指定します。 *table_name*は**sysname**、既定値は NULL です。  
  
 [  **@table_schema =** ] **'***、table_schema、***'**  
 テーブル スキーマを指定します。 *table_schema、*は**sysname**、既定値は NULL です。  
  
 [  **@table_catalog =** ] **'***table_catalog***'**  
 対象となるデータベースの名前を指定した*table_name*が存在します。 *table_catalog*は**sysname**、既定値は NULL です。  
  
 [  **@column_name =** ] **'***column_name***'**  
 特権情報を提供する列の名前を指定します。 *column_name*は**sysname**で、既定値は NULL です (すべて共通)。  
  
## <a name="result-sets"></a>結果セット  
 次の表は結果セットの列を示しています。 返される結果は並べ**TABLE_QUALIFIER**、 **TABLE_OWNER**、 **TABLE_NAME**、 **COLUMN_NAME**、および**特権**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|テーブル修飾子の名前。 さまざまな DBMS 製品は、3 部構成テーブルの名前付けをサポート (*修飾子 ***.*** 所有者 ***.*** 名前*)。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、この列は、データベースの名前を表します。 一部の製品では、テーブルのデータベース環境のサーバー名を表します。 このフィールドには NULL を指定できます。|  
|**TABLE_SCHEM**|**sysname**|テーブル所有者名です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、この列がテーブルを作成したデータベース ユーザーの名前を表します。 このフィールドは常に値を返します。|  
|**TABLE_NAME**|**sysname**|テーブル名です。 このフィールドは常に値を返します。|  
|**COLUMN_NAME**|**sysname**|各列の列名、 **TABLE_NAME**が返されます。 このフィールドは常に値を返します。|  
|**権限の許可者**|**sysname**|この権限が許可されるデータベース ユーザー名**COLUMN_NAME**を表示される**権限付与対象ユーザー**です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、この列は常に、同じ、 **TABLE_OWNER**です。 このフィールドは常に値を返します。<br /><br /> **GRANTOR**列は、データベース所有者を指定できます (**TABLE_OWNER**) または他のユーザー データベースの所有者が権限を許可、GRANT ステートメントで WITH GRANT OPTION 句を使用します。|  
|**権限付与対象ユーザー**|**sysname**|このアクセス許可が与えられているデータベース ユーザー名**COLUMN_NAME**によって、表示される**GRANTOR**です。 このフィールドは常に値を返します。|  
|**特権**|**varchar(** 32 **)**|有効な列権限。 列権限は、次に挙げる値 (または実装が定義されるときにデータ ソースによってサポートされるその他の値) のいずれかになります。<br /><br /> オン =**権限付与対象ユーザー**列のデータを取得できます。<br /><br /> 挿入 =**権限付与対象ユーザー**新しい行が挿入されると、この列のデータを提供できます (によって、**権限付与対象ユーザー**) テーブルにします。<br /><br /> 更新 =**権限付与対象ユーザー**列内の既存のデータを変更できます。<br /><br /> 参照 =**権限付与対象ユーザー**主キー/外部キーのリレーションシップで外部テーブルで列を参照できます。 主キー/外部キーの関係は、テーブル制約によって定義されます。|  
|**IS_GRANTABLE**|**varchar (** 3 **)**|示すかどうか、**権限付与対象ユーザー**を許可 (「許可の許可」権限とも呼ばれます) の他のユーザーに権限を付与します。 YES、NO、NULL のいずれかになります。 不明な値 (つまり NULL) は、"許可の許可" 権限が適用されないデータ ソースを示します。|  
  
## <a name="permissions"></a>権限  
 スキーマに対する SELECT 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、`HumanResources.Department` リンク サーバーにある [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースの `Seattle1` テーブルの列特権情報を返します。  
  
```  
EXEC sp_column_privileges_ex @table_server = 'Seattle1',   
   @table_name = 'Department',   
   @table_schema = 'HumanResources',  
   @table_catalog ='AdventureWorks2012';  
```  
  
## <a name="see-also"></a>参照  
 [sp_table_privileges_ex &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-ex-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
