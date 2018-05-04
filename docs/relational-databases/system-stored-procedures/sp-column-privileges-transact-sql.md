---
title: sp_column_privileges (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_column_privileges_TSQL
- sp_column_privileges
dev_langs:
- TSQL
helpviewer_keywords:
- sp_column_privileges
ms.assetid: a3784301-2517-4b1d-bbd9-47404483fad0
caps.latest.revision: 36
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 41f6cc18687e6491295e2843632e0bd6badbc95a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spcolumnprivileges-transact-sql"></a>sp_column_privileges (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在の環境で、1 つのテーブルに関する列の権限情報を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_column_privileges [ @table_name = ] 'table_name'   
     [ , [ @table_owner = ] 'table_owner' ]   
     [ , [ @table_qualifier = ] 'table_qualifier' ]   
     [ , [ @column_name = ] 'column' ]  
```  
  
## <a name="arguments"></a>引数  
 [ @table_name=] '*table_name*'  
 カタログ情報を返すために使用するテーブルを指定します。 *table_name*は**sysname**、既定値はありません。 ワイルドカードによるパターン照合はサポートされていません。  
  
 [ @table_owner=] '*table_owner*'  
 カタログ情報を返すために使用するテーブルの所有者を指定します。 *table_owner*は**sysname**、既定値は NULL です。 ワイルドカードによるパターン照合はサポートされていません。 場合*table_owner*が指定されていない、基になるデータベース管理システム (DBMS) の既定のテーブル可視性規則が適用されます。  
  
 指定した名前のテーブルを現在のユーザーが所有している場合は、そのテーブルの列が返されます。 場合*table_owner*が指定されていない、現在のユーザーが、指定したテーブルを所有していないと*table_name*、sp_column privileges の指定したテーブルが検索*table_name*データベース所有者が所有します。 存在する場合は、そのテーブルの列が返されます。  
  
 [ @table_qualifier=] '*table_qualifier*'  
 テーブル識別子の名前です。 *table_qualifier*は*sysname*、既定値は NULL です。 さまざまな DBMS 製品は、3 部構成テーブルの名前付けをサポート (*修飾子 ***.*** 所有者 ***.*** 名前*)。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、この列は、データベースの名前を表します。 一部の製品では、テーブルのデータベース環境のサーバー名を表します。  
  
 [ @column_name=] '*列*'  
 カタログ情報を 1 列だけ取得する場合に使用する 1 つの列を指定します。 *列*は**nvarchar (** 384 **)**、既定値は NULL です。 場合*列*が指定されていないすべての列が返されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、*列*sys.columns テーブルに示されている列の名前を表します。 *列*基になる DBMS のワイルドカード パターンを使用したワイルドカード文字を含めることができます。 相互運用性を最大にするため、ゲートウェイのクライアントでは、ISO 標準のパターン (% と _ のワイルドカード文字) のみを使用してください。  
  
## <a name="result-sets"></a>結果セット  
 sp_column_privileges は odbc SQLColumnPrivileges に相当します。 返される結果は、TABLE_QUALIFIER、TABLE_OWNER、TABLE_NAME、COLUMN_NAME、PRIVILEGE の順序に従って並べ替えられます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|TABLE_QUALIFIER|**sysname**|テーブル修飾子の名前。 このフィールドには NULL を指定できます。|  
|TABLE_OWNER|**sysname**|テーブル所有者名です。 このフィールドは常に値を返します。|  
|TABLE_NAME|**sysname**|テーブル名です。 このフィールドは常に値を返します。|  
|COLUMN_NAME|**sysname**|返される TABLE_NAME の各列の名前。 このフィールドは常に値を返します。|  
|GRANTOR|**sysname**|COLUMN_NAME に対する権限を、表示される GRANTEE に与えたデータベース ユーザーの名前。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、この列は常に TABLE_OWNER と同じです。 このフィールドは常に値を返します。<br /><br /> GRANTOR 列の値は、データベース所有者 (TABLE_OWNER) か、GRANT ステートメントで WITH GRANT OPTION 句を使用して、データベース所有者が権限を許可したユーザーになります。|  
|GRANTEE|**sysname**|COLUMN_NAME に対する権限を、表示される GRANTOR によって与えられたデータベース ユーザーの名前。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、この列には常に、sysusers テーブルに記録されているデータベース ユーザーが格納されます。 このフィールドは常に値を返します。|  
|PRIVILEGE|**varchar(** 32 **)**|有効な列権限。 列権限は、次に挙げる値 (または実装が定義されるときにデータ ソースによってサポートされるその他の値) のいずれかになります。<br /><br /> SELECT。GRANTEE は、列からデータを取得できます。<br /><br /> INSERT。GRANTEE は、テーブルに新しい行を挿入したときにこの列のデータを設定できます。<br /><br /> UPDATE。GRANTEE は、列内の既存のデータを修正できます。<br /><br /> REFERENCES。GRANTEE は、主キー/外部キーのリレーションシップで外部テーブル内の列を参照できます。 主キー/外部キーのリレーションシップは、テーブル制約を使って定義できます。|  
|IS_GRANTABLE|**varchar (** 3 **)**|(「許可の許可」権限とも呼ばれます) の他のユーザーに権限を与える、権限付与対象ユーザーが許可されているかどうかを示します。 YES、NO、NULL のいずれかになります。 不明な値または NULL の場合は、"許可の許可" が適用されないデータ ソースであることを示します。|  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、権限は GRANT ステートメントで与え、REVOKE ステートメントで取り消します。  
  
## <a name="permissions"></a>権限  
 スキーマに対する SELECT 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、特定の列の列権限情報を返します。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_column_privileges @table_name = 'Employee'   
    ,@table_owner = 'HumanResources'  
    ,@table_qualifier = 'AdventureWorks2012'  
    ,@column_name = 'SalariedFlag';  
```  
  
## <a name="see-also"></a>参照  
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [REVOKE &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
