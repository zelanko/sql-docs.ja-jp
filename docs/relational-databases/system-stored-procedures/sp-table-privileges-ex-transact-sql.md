---
title: sp_table_privileges_ex (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_table_privileges_ex
- sp_table_privileges_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_table_privileges_ex
ms.assetid: b58d4a07-5c40-4f17-b66e-6d6b17188dda
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d800eed984c6371ed689e9d8ec2748cb6b9886c1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47752756"
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
 データベースの名前は、指定した*table_name*が存在します。 *table_catalog*は**sysname**、既定値は NULL です。  
  
 [  **@fUsePattern =**] **'***fUsePattern***'**  
 文字 '_'、'%'、'['、および ']' をワイルドカード文字として解釈するかどうかを指定します。 有効な値は 0 (パターン一致がオフ) および 1 (パターン一致がオン) です。 *fUsePattern*は**ビット**、既定値は 1 です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|テーブル修飾子の名前。 さまざまな DBMS 製品は、3 つの部分がテーブルの名前付けをサポート (*修飾子 ***.*** 所有者 ***.*** 名前*)。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、この列は、データベース名を表します。 一部の製品で、テーブルのデータベース環境のサーバー名を表します。 このフィールドには NULL を指定できます。|  
|**TABLE_SCHEM**|**sysname**|テーブルの所有者名です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、この列は、テーブルを作成したデータベース ユーザーの名前を表します。 このフィールドは常に値を返します。|  
|**TABLE_NAME**|**sysname**|テーブル名です。 このフィールドは常に値を返します。|  
|**権限の許可者**|**sysname**|このアクセス許可が付与されるデータベース ユーザー名**TABLE_NAME**を表示される**権限付与対象ユーザー**します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、この列が同じでは常に、 **TABLE_OWNER**します。 このフィールドは常に値を返します。 また、GRANTOR 列は、データベース所有者可能性があります (**TABLE_OWNER**) またはデータベース所有者が GRANT ステートメントで WITH GRANT OPTION 句を使用して、アクセス許可を許可するユーザー。|  
|**権限付与対象ユーザー**|**sysname**|このアクセス許可が与えられているデータベース ユーザー名**TABLE_NAME**により**GRANTOR**します。 このフィールドは常に値を返します。|  
|**特権**|**varchar(** 32 **)**|使用可能なテーブル権限の 1 つ。 次に示す値、または実装が定義されるときにデータ ソースによってサポートされるその他の値のいずれかになります。<br /><br /> 選択 =**権限付与対象ユーザー** 1 つまたは複数の列のデータを取得することができます。<br /><br /> 挿入 =**権限付与対象ユーザー**新しい行のデータを 1 つまたは複数の列を提供できます。<br /><br /> 更新 =**権限付与対象ユーザー** 1 つまたは複数の列の既存のデータを変更することができます。<br /><br /> 削除 =**権限付与対象ユーザー**テーブルから行を削除できます。<br /><br /> 参照 =**権限付与対象ユーザー**主キー/外部キーのリレーションシップで外部テーブルで列を参照できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、主キー/外部キーのリレーションシップはテーブル制約を使用して定義されます。<br /><br /> 与えられる操作のスコープ、**権限付与対象ユーザー**特権とは、特定のテーブルで、データ ソースに依存します。 UPDATE 権限が有効にするなど、**権限付与対象ユーザー**を 1 つのデータ ソースではテーブルのすべての列および列のみを更新する、 **GRANTOR**に別のデータ ソースに対する更新権限。|  
|**IS_GRANTABLE**|**varchar (** 3 **)**|示すかどうか、**権限付与対象ユーザー**で許可されている他のユーザーに権限を付与します。 これは、"許可の許可" 権限と呼ばれることがあります。 YES、NO、NULL のいずれかになります。 不明、つまり NULL の場合は、"許可の許可" が適用されないデータ ソースを示します。|  
  
## <a name="remarks"></a>コメント  
 返される結果は並べ**TABLE_QUALIFIER**、 **TABLE_OWNER**、 **TABLE_NAME**、および**特権**します。  
  
## <a name="permissions"></a>アクセス許可  
 スキーマに対する SELECT 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例で始まる名前のテーブルに関する特権情報を返します`Product`で、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]指定したリンク サーバーからデータベース`Seattle1`します。 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はリンク サーバーであることが前提となっています)。  
  
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
  
  
