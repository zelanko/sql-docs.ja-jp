---
title: sp_refreshsqlmodule (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_refreshsqlmodule_TSQL
- sp_refreshsqlmodule
dev_langs:
- TSQL
helpviewer_keywords:
- metadata [SQL Server], stored procedures
- metadata [SQL Server], triggers
- metadata [SQL Server], views
- triggers [SQL Server], refreshing metadata
- views [SQL Server], refreshing metadata
- sp_refreshsqlmodule
- metadata [SQL Server], functions
- stored procedures [SQL Server], refreshing metadata
- user-defined functions [SQL Server], refreshing metadata
ms.assetid: f0022a05-50dd-4620-961d-361b1681d375
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 3fb52b0144caea217557cc8abcf7af052ee1569a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sprefreshsqlmodule-transact-sql"></a>sp_refreshsqlmodule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在のデータベースを対象に、指定された非スキーマ バインドのストアド プロシージャ、ユーザー定義関数、ビュー、DML トリガー、データベース レベルの DDL トリガー、またはサーバー レベルの DDL トリガーのメタデータを更新します。 これらのオブジェクトに固有のメタデータ (パラメーターのデータ型など) は、基になるオブジェクトを変更すると、古くなる場合があります。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.sp_refreshsqlmodule [ @name = ] 'module_name'   
    [ , [ @namespace = ] ' <class> ' ]  
  
<class> ::=  
{  
  | DATABASE_DDL_TRIGGER  
  | SERVER_DDL_TRIGGER  
}  
  
```  
  
## <a name="arguments"></a>引数  
 [  **@name=** ] **'***モジュール名***'**  
 ストアド プロシージャ、ユーザー定義関数、ビュー、DML トリガー、データベース レベルの DDL トリガー、またはサーバー レベルの DDL トリガーの名前を指定します。 *モジュール名*共通言語ランタイム (CLR) ストアド プロシージャまたは CLR 関数にすることはできません。 *モジュール名*スキーマ バインドをすることはできません。 *モジュール名*は**nvarchar**、既定値はありません。 *モジュール名*マルチパートの識別子を指定できますが、現在のデータベース内のオブジェクトに参照できるのみです。  
  
 [ **、** @**名前空間**=] **'** \<クラス > **'**  
 指定されたモジュールのクラスです。 ときに*モジュール名*、DDL トリガーは、\<クラス > が必要です。 *\<クラス >* は**nvarchar**(20)。 有効な入力は次のとおりです。  
  
|||  
|-|-|  
|DATABASE_DDL_TRIGGER||  
|SERVER_DDL_TRIGGER|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 0 以外の数値 (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_refreshsqlmodule**その定義に影響するモジュールの基になるオブジェクトが変更されたときに実行する必要があります。 この操作を行わないと、モジュールにクエリを実行したりオブジェクトを呼び出したときに、予期しない結果が生じる可能性があります。 ビューを更新する、いずれかを使用できる**sp_refreshsqlmodule**または**sp_refreshview**同じ結果にします。  
  
 **sp_refreshsqlmodule**任意の権限、拡張プロパティ、またはオブジェクトに関連付けられているオプションの設定には影響しません。  
  
 サーバー レベルの DDL トリガーを更新するには、このストアド プロシージャをデータベースのコンテキストから実行します。  
  
> [!NOTE]  
>  実行すると、オブジェクトに関連付けられている署名は削除**sp_refreshsqlmodule**です。  
  
## <a name="permissions"></a>権限  
 モジュールに対する ALTER 権限、およびオブジェクトによって参照される CLR ユーザー定義型と XML スキーマ コレクションに対する REFERENCES 権限が必要です。 指定されたモジュールがデータベース レベルの DDL トリガーである場合は、現在のデータベースに対する ALTER ANY DATABASE DDL TRIGGER 権限が必要です。 指定されたモジュールがサーバー レベルの DDL トリガーである場合は、CONTROL SERVER 権限が必要です。  
  
 さらに、EXECUTE AS 句で定義されているモジュールでは、指定したプリンシパルに対して IMPERSONATE 権限が必要です。 通常、オブジェクトを更新しても、モジュールが EXECUTE AS USER を指定して定義された場合を除いて、オブジェクトの EXECUTE AS のプリンシパルは変更されません。プリンシパルのユーザー名は、モジュールが作成された時点とは異なるユーザーに解決されます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-refreshing-a-user-defined-function"></a>A. ユーザー定義関数を更新する  
 次の例では、ユーザー定義関数を更新します。 別名データ型の場合は、この例`mytype`、およびユーザー定義関数、`to_upper`を使用して`mytype`です。 その後、`mytype`に名前が変更`myoldtype`、され、新しい`mytype`が作成される別の定義を持ちます。 `dbo.to_upper`の新しい実装を参照するように関数が更新される`mytype`古いの代わりにします。  
  
```  
-- Create an alias type.  
USE AdventureWorks2012;  
GO  
IF EXISTS (SELECT 'mytype' FROM sys.types WHERE name = 'mytype')  
DROP TYPE mytype;  
GO  
  
CREATE TYPE mytype FROM nvarchar(5);  
GO  
  
IF OBJECT_ID ('dbo.to_upper', 'FN') IS NOT NULL  
DROP FUNCTION dbo.to_upper;  
GO  
  
CREATE FUNCTION dbo.to_upper (@a mytype)  
RETURNS mytype  
WITH ENCRYPTION  
AS  
BEGIN  
RETURN upper(@a)  
END;  
GO  
  
SELECT dbo.to_upper('abcde');  
GO  
  
-- Increase the length of the alias type.  
sp_rename 'mytype', 'myoldtype', 'userdatatype';  
GO  
  
CREATE TYPE mytype FROM nvarchar(10);  
GO  
  
-- The function parameter still uses the old type.  
SELECT name, type_name(user_type_id)   
FROM sys.parameters   
WHERE object_id = OBJECT_ID('dbo.to_upper');  
GO  
  
SELECT dbo.to_upper('abcdefgh'); -- Fails because of truncation  
GO  
  
-- Refresh the function to bind to the renamed type.  
EXEC sys.sp_refreshsqlmodule 'dbo.to_upper';  
  
-- The function parameters are now bound to the correct type and the statement works correctly.  
SELECT name, type_name(user_type_id) FROM sys.parameters  
WHERE object_id = OBJECT_ID('dbo.to_upper');  
GO  
  
SELECT dbo.to_upper('abcdefgh');  
GO  
```  
  
### <a name="b-refreshing-a-database-level-ddl-trigger"></a>B. データベース レベルの DDL トリガーを更新する  
 次の例では、データベース レベルの DDL トリガーを更新します。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sys.sp_refreshsqlmodule @name = 'ddlDatabaseTriggerLog' , @namespace = 'DATABASE_DDL_TRIGGER';  
GO  
```  
  
### <a name="c-refreshing-a-server-level-ddl-trigger"></a>C. サーバー レベルの DDL トリガーを更新する  
 次の例では、サーバー レベルの DDL トリガーを更新します。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
  
```  
USE master;  
GO  
EXEC sys.sp_refreshsqlmodule @name = 'ddl_trig_database' , @namespace = 'SERVER_DDL_TRIGGER';  
GO  
  
```  
  
## <a name="see-also"></a>参照  
 [sp_refreshview &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-refreshview-transact-sql.md)   
 [データベース エンジン ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)  
  
  
