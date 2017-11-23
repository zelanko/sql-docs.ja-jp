---
title: "DISABLE TRIGGER (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DISABLE_TSQL
- DISABLE
- DISABLE TRIGGER
- DISABLE_TRIGGER_TSQL
dev_langs: TSQL
helpviewer_keywords:
- DML triggers, disabling
- DDL triggers, disabling
- DISABLE TRIGGER statement
- triggers [SQL Server], disabling
- disabling triggers
ms.assetid: e6529f06-e442-437e-a7bf-41790bc092c5
caps.latest.revision: "45"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 69398e740c4ae5ca49c93b1f70d7c02a0d3fbf42
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="disable-trigger-transact-sql"></a>DISABLE TRIGGER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  トリガーを無効にします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
DISABLE TRIGGER { [ schema_name . ] trigger_name [ ,...n ] | ALL }  
ON { object_name | DATABASE | ALL SERVER } [ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *schema_name*  
 トリガーが属するスキーマの名前を指定します。 *schema_name* DDL トリガーまたはログオン トリガーを指定することはできません。  
  
 *trigger_name*  
 無効にするトリガーの名前を指定します。  
  
 ALL  
 ON 句の有効範囲で定義されたすべてのトリガーを無効にすることを示します。  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]マージ レプリケーション用にパブリッシュされたデータベースでトリガーを作成します。 パブリッシュされたデータベースで ALL を指定すると、これらのトリガーが無効になり、レプリケーションが中断されます。 現在のデータベースがマージ レプリケーション用にパブリッシュされていないことを確認してから、ALL を指定してください。  
  
 *object_name*  
 テーブルまたはビューを DML トリガーの名前を指定*trigger_name*が作成を実行します。  
  
 DATABASE  
 DDL トリガーすることを示します*trigger_name*が作成またはデータベース スコープで実行するように変更します。  
  
 ALL SERVER  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 DDL トリガーすることを示します*trigger_name*が作成または、サーバー スコープで実行するように変更します。 ALL SERVER はログオン トリガーにも適用されます。  
  
> [!NOTE]  
>  このオプションは、包含データベースでは使用できません。  
  
## <a name="remarks"></a>解説  
 既定では、トリガーは作成されたときに有効になります。 トリガーを無効にしてもトリガーは削除されず、 オブジェクトとして現在のデータベースに残りますが、 ただし、トリガーは起動しません任意[!INCLUDE[tsql](../../includes/tsql-md.md)]プログラムされたステートメントを実行します。 使用してトリガーが再度有効にできる[ENABLE TRIGGER](../../t-sql/statements/enable-trigger-transact-sql.md)です。 テーブルに定義された DML トリガーを指定できますも無効にするかを使用して有効になっている[ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md)です。  
  
 使用してトリガーを変更する、 **ALTER TRIGGER**ステートメント、トリガーを有効にします。  
  
## <a name="permissions"></a>Permissions  
 DML トリガーを無効にするには、少なくともトリガーが作成されたテーブルまたはビューに対する ALTER 権限が必要です。  
  
 サーバー スコープ (ON ALL SERVER) 付きの DDL トリガーまたはログオン トリガーを無効化するには、サーバーでの CONTROL SERVER 権限が必要です。 データベース スコープ (ON DATABASE) の DDL トリガーを無効にするには、現在のデータベースに対する ALTER ANY DATABASE DDL TRIGGER 権限が必要です。  
  
## <a name="examples"></a>使用例  
次の例は、AdventureWorks2012 データベースに記述されます。
  
### <a name="a-disabling-a-dml-trigger-on-a-table"></a>A. テーブルの DML トリガーを無効にする  
 次の例では、テーブル `uAddress` に作成されたトリガー `Address` を無効にします。  
  
```  
DISABLE TRIGGER Person.uAddress ON Person.Address;  
GO  
```  
  
### <a name="b-disabling-a-ddl-trigger"></a>B. DDL トリガーを無効にする  
 次の例では、データベース スコープの DDL トリガー `safety` を作成し、無効にします。  
  
```  
CREATE TRIGGER safety   
ON DATABASE   
FOR DROP_TABLE, ALTER_TABLE   
AS   
   PRINT 'You must disable Trigger "safety" to drop or alter tables!'   
   ROLLBACK;  
GO  
DISABLE TRIGGER safety ON DATABASE;  
GO  
```  
  
### <a name="c-disabling-all-triggers-that-were-defined-with-the-same-scope"></a>C. 同じスコープに定義されたすべてのトリガーを無効にする  
 次の例では、サーバー スコープで作成されたすべての DDL トリガーを無効化します。  
  
```  
DISABLE Trigger ALL ON ALL SERVER;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ENABLE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/enable-trigger-transact-sql.md)   
 [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [DROP TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-trigger-transact-sql.md)   
 [sys.triggers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md)  
  
  
