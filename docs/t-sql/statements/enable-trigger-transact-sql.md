---
title: "ENABLE TRIGGER (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ENABLE TRIGGER
- ENABLE_TSQL
- ENABLE_TRIGGER_TSQL
- ENABLE
dev_langs:
- TSQL
helpviewer_keywords:
- DDL triggers, enabling
- triggers [SQL Server], enabling
- DML triggers, enabling
- ENABLE TRIGGER statement
ms.assetid: 6e21f0ad-68d0-432f-9c7c-a119dd2d3fc9
caps.latest.revision: 39
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fb2fba080ea3c51e5c29456b2166eeea6274f8a3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="enable-trigger-transact-sql"></a>ENABLE TRIGGER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  DML トリガー、DDL トリガー、またはログオン トリガーを有効化します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
ENABLE TRIGGER { [ schema_name . ] trigger_name [ ,...n ] | ALL }  
ON { object_name | DATABASE | ALL SERVER } [ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *schema_name*  
 トリガーが属するスキーマの名前を指定します。 *schema_name* DDL トリガーまたはログオン トリガーを指定することはできません。  
  
 *trigger_name*  
 有効化するトリガーの名前です。  
  
 ALL  
 ON 句のスコープで定義されたすべてのトリガーを有効化することを示します。  
  
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
 トリガーを有効化しても、トリガーが再作成されるわけではありません。 無効化されたトリガーは、引き続き現在のデータベースのオブジェクトとして残りますが、起動されることはありません。 トリガーを有効化すると、そのトリガーがプログラムされている [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントが実行されたときに起動されます。 使用してトリガーが無効になっている[DISABLE TRIGGER](../../t-sql/statements/disable-trigger-transact-sql.md)です。 テーブルに定義された DML トリガーを指定できますも無効にするかを使用して有効になっている[ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md)です。  
  
## <a name="permissions"></a>Permissions  
 DML トリガーを有効化するには、少なくとも、そのトリガーが作成されたテーブルまたはビューに対する ALTER 権限が必要です。  
  
 サーバー スコープ (ON ALL SERVER) 付きの DDL トリガーまたはログオン トリガーを有効化するには、サーバーでの CONTROL SERVER 権限が必要です。 DDL トリガーをデータベース スコープ (ON DATABASE) で有効化するには、少なくとも、現在のデータベースでの ALTER ANY DATABASE DDL TRIGGER 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-enabling-a-dml-trigger-on-a-table"></a>A. テーブル上の DML トリガーを有効化する  
 次の例には、トリガーが無効になります。`uAddress`テーブル上に作成された`Address`、AdventureWorks データベースされ有効になります。  
  
```  
DISABLE TRIGGER Person.uAddress ON Person.Address;  
GO  
ENABLE Trigger Person.uAddress ON Person.Address;  
GO  
```  
  
### <a name="b-enabling-a-ddl-trigger"></a>B. DDL トリガーを有効化する  
 次の例では、DDL トリガー`safety`とデータベースのスコープ、無効にし、それを有効にします。  
  
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
ENABLE TRIGGER safety ON DATABASE;  
GO  
```  
  
### <a name="c-enabling-all-triggers-that-were-defined-with-the-same-scope"></a>C. 同じスコープで定義されたすべてのトリガーを有効化する  
 次の例では、サーバー スコープで作成されたすべての DDL トリガーを有効化します。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```  
ENABLE Trigger ALL ON ALL SERVER;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [DISABLE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/disable-trigger-transact-sql.md)   
 [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [DROP TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-trigger-transact-sql.md)   
 [sys.triggers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md)  
  
  

