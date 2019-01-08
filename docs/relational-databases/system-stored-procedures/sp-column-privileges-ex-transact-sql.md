---
title: sp_column_privileges_ex (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_column_privileges_ex
- sp_column_privileges_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_column_privileges_ex
ms.assetid: 98cb6e58-4007-40fc-b048-449fb2e7e6be
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b79fbbd504f7294835e92401a2210e6acac3c440
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52514021"
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
 [  **@table_server =** ] **'**_table_server_**'**  
 情報を返すリンク サーバーの名前を指定します。 *table_server*は**sysname**、既定値はありません。  
  
 [  **@table_name =** ] **'**_table_name_**'**  
 指定した列が含まれるテーブルの名前を指定します。 *table_name*は**sysname**、既定値は NULL です。  
  
 [  **@table_schema =** ] **'**_、table_schema、_**'**  
 テーブル スキーマを指定します。 *table_schema、* は**sysname**、既定値は NULL です。  
  
 [  **@table_catalog =** ] **'**_table_catalog_**'**  
 データベースの名前は、指定した*table_name*が存在します。 *table_catalog*は**sysname**、既定値は NULL です。  
  
 [  **@column_name =** ] **'**_column_name_**'**  
 特権情報を提供する列の名前を指定します。 *column_name*は**sysname**、既定値は null です (すべて共通)。  
  
## <a name="result-sets"></a>結果セット  
 次の表は結果セットの列を示しています。 返される結果は並べ**TABLE_QUALIFIER**、 **TABLE_OWNER**、 **TABLE_NAME**、 **COLUMN_NAME**、および**特権**します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|テーブル修飾子の名前。 さまざまな DBMS 製品は、3 つの部分がテーブルの名前付けをサポート (_修飾子_**.**_所有者_**.**_名前_)。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、この列はデータベース名を表します。 一部の製品で、テーブルのデータベース環境のサーバー名を表します。 このフィールドには NULL を指定できます。|  
|**TABLE_SCHEM**|**sysname**|テーブルの所有者名です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、この列はテーブルを作成したデータベース ユーザーの名前を表します。 このフィールドは常に値を返します。|  
|**TABLE_NAME**|**sysname**|テーブル名です。 このフィールドは常に値を返します。|  
|**COLUMN_NAME**|**sysname**|各列の列名、 **TABLE_NAME**が返されます。 このフィールドは常に値を返します。|  
|**権限の許可者**|**sysname**|このアクセス許可が付与されるデータベース ユーザー名**COLUMN_NAME**を表示される**権限付与対象ユーザー**します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、この列が同じでは常に、 **TABLE_OWNER**します。 このフィールドは常に値を返します。<br /><br /> **GRANTOR**列は、データベース所有者を指定できます (**TABLE_OWNER**) または他のユーザーに、データベース所有者が GRANT ステートメントで WITH GRANT OPTION 句を使用して、アクセス許可を許可します。|  
|**権限付与対象ユーザー**|**sysname**|このアクセス許可が与えられているデータベース ユーザー名**COLUMN_NAME**により**GRANTOR**します。 このフィールドは常に値を返します。|  
|**特権**|**varchar(** 32 **)**|有効な列権限。 列権限は、次に挙げる値 (または実装が定義されるときにデータ ソースによってサポートされるその他の値) のいずれかになります。<br /><br /> 選択 =**権限付与対象ユーザー**列のデータを取得できます。<br /><br /> 挿入 =**権限付与対象ユーザー**新しい行が挿入されたときに、この列のデータを提供できます (によって、**権限付与対象ユーザー**) テーブルにします。<br /><br /> 更新 =**権限付与対象ユーザー**列内の既存のデータを変更することができます。<br /><br /> 参照 =**権限付与対象ユーザー**主キー/外部キーのリレーションシップで外部テーブルで列を参照できます。 主キー/外部キーの関係は、テーブル制約によって定義されます。|  
|**IS_GRANTABLE**|**varchar (** 3 **)**|示すかどうか、**権限付与対象ユーザー**で許可されている他のユーザー (「許可の許可」とも呼ばれます) にアクセス許可を付与します。 YES、NO、NULL のいずれかになります。 不明な値 (つまり NULL) は、"許可の許可" 権限が適用されないデータ ソースを示します。|  
  
## <a name="permissions"></a>アクセス許可  
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
  
  
