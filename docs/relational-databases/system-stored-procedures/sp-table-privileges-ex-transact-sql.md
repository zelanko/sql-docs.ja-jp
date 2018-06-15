---
title: sp_table_privileges_ex (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_table_privileges_ex
- sp_table_privileges_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_table_privileges_ex
ms.assetid: b58d4a07-5c40-4f17-b66e-6d6b17188dda
caps.latest.revision: 33
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: fc97335ccb0e014e130a2f47c70f480dd7c23554
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33260002"
---
# <a name="sptableprivilegesex-transact-sql"></a>sp_table_privileges_ex (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定したリンク サーバーから、指定したテーブルの特権情報を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_table_privileges_ex [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]   
     [ , [ @table_catalog = ] 'table_catalog' ]  
     [ , [@fUsePattern =] 'fUsePattern']  
```  
  
## <a name="arguments"></a>引数  
 [  **@table_server =** ] **'***table_server***'**  
 情報を返すリンク サーバーの名前を指定します。 *table_server*は**sysname**、既定値はありません。  
  
 [  **@table_name =** ] **'***table_name***'**]  
 テーブルの特権情報を提供するテーブルの名前を指定します。 *table_name*は**sysname**、既定値は NULL です。  
  
 [  **@table_schema =** ] **'***、table_schema、***'**  
 テーブル スキーマを指定します。 これは一部の DBMS 環境ではテーブル所有者になります。 *table_schema、* は**sysname**、既定値は NULL です。  
  
 [  **@table_catalog =** ] **'***table_catalog***'**  
 対象となるデータベースの名前を指定した*table_name*が存在します。 *table_catalog*は**sysname**、既定値は NULL です。  
  
 [  **@fUsePattern =**] **'***fUsePattern***'**  
 文字 '_'、'%'、'['、および ']' をワイルドカード文字として解釈するかどうかを指定します。 有効な値は 0 (パターン一致がオフ) および 1 (パターン一致がオン) です。 *fUsePattern*は**ビット**、既定値は 1 です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|テーブル修飾子の名前。 さまざまな DBMS 製品は、3 部構成テーブルの名前付けをサポート (*修飾子 ***.*** 所有者 ***.*** 名前*)。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、この列は、データベースの名前を表します。 一部の製品では、テーブルのデータベース環境のサーバー名を表します。 このフィールドには NULL を指定できます。|  
|**TABLE_SCHEM**|**sysname**|テーブル所有者名です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、この列がテーブルを作成したデータベース ユーザーの名前を表します。 このフィールドは常に値を返します。|  
|**TABLE_NAME**|**sysname**|テーブル名です。 このフィールドは常に値を返します。|  
|**権限の許可者**|**sysname**|これに対する権限が許可されるデータベース ユーザー名**TABLE_NAME**を表示される**権限付与対象ユーザー**です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、この列は常に、同じ、 **TABLE_OWNER**です。 このフィールドは常に値を返します。 GRANTOR 列も、データベース所有者である可能性があります (**TABLE_OWNER**) または、権限をユーザーと、データベース所有者が GRANT ステートメントで WITH GRANT OPTION 句を使用しています。|  
|**権限付与対象ユーザー**|**sysname**|このアクセス許可が与えられているデータベース ユーザー名**TABLE_NAME**によって、表示される**GRANTOR**です。 このフィールドは常に値を返します。|  
|**特権**|**varchar(** 32 **)**|使用可能なテーブル権限の 1 つ。 次に示す値、または実装が定義されるときにデータ ソースによってサポートされるその他の値のいずれかになります。<br /><br /> オン =**権限付与対象ユーザー** 1 つまたは複数の列のデータを取得することができます。<br /><br /> 挿入 =**権限付与対象ユーザー**新しい行のデータを 1 つまたは複数の列を提供できます。<br /><br /> 更新 =**権限付与対象ユーザー** 1 つまたは複数の列の既存のデータを変更できます。<br /><br /> 削除 =**権限付与対象ユーザー**テーブルから行を削除することができます。<br /><br /> 参照 =**権限付与対象ユーザー**主キー/外部キーのリレーションシップで外部テーブルで列を参照できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブルの制約を使用して主キー/外部キーのリレーションシップを定義します。<br /><br /> 与えられる操作のスコープ、**権限付与対象ユーザー**特権とは、特定のテーブルで、データ ソースに依存します。 UPDATE 権限により、たとえば、**権限付与対象ユーザー**を 1 つのデータ ソース上のテーブルのすべての列と列のみを更新する、 **GRANTOR**別のデータ ソースに対する更新権限を持っています。|  
|**IS_GRANTABLE**|**varchar (** 3 **)**|示すかどうか、**権限付与対象ユーザー**は他のユーザーに権限を与える許可。 これは、"許可の許可" 権限と呼ばれることがあります。 YES、NO、NULL のいずれかになります。 不明、つまり NULL の場合は、"許可の許可" が適用されないデータ ソースを示します。|  
  
## <a name="remarks"></a>解説  
 返される結果は並べ**TABLE_QUALIFIER**、 **TABLE_OWNER**、 **TABLE_NAME**、および**特権**です。  
  
## <a name="permissions"></a>権限  
 スキーマに対する SELECT 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例で始まる名前のテーブルに関する特権情報を返します`Product`で、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]指定したリンク サーバーからデータベース`Seattle1`です。 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はリンク サーバーであることが前提となっています)。  
  
```  
EXEC sp_table_privileges_ex @table_server = 'Seattle1',   
   @table_name = 'Product%',   
   @table_schema = 'Production',  
   @table_catalog ='AdventureWorks2012';  
```  
  
## <a name="see-also"></a>参照  
 [sp_column_privileges_ex &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-ex-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [分散クエリ ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)  
  
  
