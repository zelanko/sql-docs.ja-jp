---
title: sp_refreshsqlmodule (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 07/25/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9ed393edf79c3502bf3e054e23eb459d490ce998
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68075801"
---
# <a name="sprefreshsqlmodule-transact-sql"></a>sp_refreshsqlmodule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  指定された非スキーマ バインド ストアド プロシージャ、ユーザー定義関数、ビュー、DML トリガー、データベース レベルの DDL トリガー、または現在のデータベース内のサーバー レベル DDL トリガーのメタデータを更新します。 、パラメーターのデータ型など、これらのオブジェクトのメタデータを永続的なは、その基になるオブジェクトが変更されたのため古くなることができます。
  
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
`[ @name = ] 'module\_name'` ストアド プロシージャ、ユーザー定義関数、ビュー、DML トリガー、データベース レベルの DDL トリガー、またはサーバー レベル DDL トリガーの名前です。 *モジュール名*共通言語ランタイム (CLR) ストアド プロシージャまたは CLR 関数にすることはできません。 *モジュール名*スキーマ バインドをすることはできません。 *モジュール名*は**nvarchar**、既定値はありません。 *モジュール名*、マルチパート識別子を指定できますが、現在のデータベース内のオブジェクトに参照できるのみです。  
  
`[ , @namespace = ] ' \<class> '` 指定したモジュールのクラスです。 ときに*module_name* 、DDL トリガーは、\<クラス > が必要です。 *\<クラス >* は**nvarchar**(20)。 有効な入力値は次のとおりです。  
  
|||  
|-|-|  
|DATABASE_DDL_TRIGGER||  
|SERVER_DDL_TRIGGER|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 0 以外の値の数 (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_refreshsqlmodule**その定義に影響するモジュールの基になるオブジェクトに変更されたときに実行する必要があります。 それ以外の場合、モジュールがクエリまたは呼び出されたときに、予期しない結果を生成可能性があります。 ビューを更新する、いずれかを使用できます**sp_refreshsqlmodule**または**sp_refreshview**結果は同じにします。  
  
 **sp_refreshsqlmodule**任意のアクセス許可、拡張プロパティ、またはオブジェクトに関連付けられているオプションの設定には影響しません。  
  
 サーバー レベルの DDL トリガーを更新するには、任意のデータベースのコンテキストからこのストアド プロシージャを実行します。  
  
> [!NOTE]  
>  実行すると、オブジェクトに関連付けられている署名は削除**sp_refreshsqlmodule**します。  
  
## <a name="permissions"></a>アクセス許可  
 モジュールに対する ALTER 権限、およびオブジェクトによって参照される CLR ユーザー定義型と XML スキーマ コレクションに対する REFERENCES 権限が必要です。 指定したモジュールがデータベース レベルの DDL トリガーの場合、現在のデータベース内の ALTER ANY DATABASE DDL TRIGGER 権限が必要です。 指定されたモジュールがサーバー レベルの DDL トリガー時に、CONTROL SERVER 権限が必要です。  
  
 さらに、EXECUTE AS 句で定義されているモジュールでは、指定したプリンシパルに対して IMPERSONATE 権限が必要です。 通常、オブジェクトを更新しても、モジュールが EXECUTE AS USER を指定して定義された場合を除いて、オブジェクトの EXECUTE AS のプリンシパルは変更されません。プリンシパルのユーザー名は、モジュールが作成された時点とは異なるユーザーに解決されます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-refreshing-a-user-defined-function"></a>A. ユーザー定義関数を更新  
 次の例では、ユーザー定義関数を更新します。 例では、作成、別名データ型を`mytype`、およびユーザー定義関数では、`to_upper`を使用して`mytype`します。 次に、`mytype`名前に変更されます`myoldtype`、され、新しい`mytype`が作成される、別の定義を持ちます。 `dbo.to_upper`の新しい実装を参照するように関数が更新される`mytype`古いの代わりにします。  
  
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
  
## <a name="see-also"></a>関連項目  
 [sp_refreshview &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-refreshview-transact-sql.md)   
 [データベース エンジン ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)  
  
  
