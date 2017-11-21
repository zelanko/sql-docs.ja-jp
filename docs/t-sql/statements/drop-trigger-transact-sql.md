---
title: "DROP TRIGGER (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/12/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP TRIGGER
- DROP_TRIGGER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- renaming triggers
- triggers [SQL Server], removing
- DDL triggers, removing
- DROP TRIGGER statement
- deleting triggers
- dropping triggers
- removing triggers
- DML triggers, removing
ms.assetid: 092d0d71-9f1e-4e38-a1c4-2487adfa5b4e
caps.latest.revision: 53
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e3ca35b2b33a60d0af5dd31467f1381402f8f99b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="drop-trigger-transact-sql"></a>DROP TRIGGER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  1 つ以上の DML トリガーまたは DDL トリガーを現在のデータベースから削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Trigger on an INSERT, UPDATE, or DELETE statement to a table or view (DML Trigger)  
  
DROP TRIGGER [ IF EXISTS ] [schema_name.]trigger_name [ ,...n ] [ ; ]  
  
-- Trigger on a CREATE, ALTER, DROP, GRANT, DENY, REVOKE or UPDATE statement (DDL Trigger)  
  
DROP TRIGGER [ IF EXISTS ] trigger_name [ ,...n ]   
ON { DATABASE | ALL SERVER }   
[ ; ]  
  
-- Trigger on a LOGON event (Logon Trigger)  
  
DROP TRIGGER [ IF EXISTS ] trigger_name [ ,...n ]   
ON ALL SERVER  
```  

  
## <a name="arguments"></a>引数  
 *場合に存在します。*  
 **適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)、 [!INCLUDE[sssds](../../includes/sssds-md.md)])。  
  
 条件付きでは既に存在する場合にのみ、トリガーを削除します。  
  
 *schema_name*  
 DML トリガーが属しているスキーマの名前を指定します。 DML トリガーのスコープは、そのトリガーが作成されたテーブルまたはビューのスキーマです。 *schema_name* DDL トリガーまたはログオン トリガーを指定することはできません。  
  
 *trigger_name*  
 削除するトリガーの名前を指定します。 現在作成されているトリガーの一覧を表示する[sys.server_assembly_modules](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md)または[sys.server_triggers](../../relational-databases/system-catalog-views/sys-server-triggers-transact-sql.md)です。  
  
 DATABASE  
 DDL トリガーのスコープが現在のデータベースに適用されることを示します。 トリガーを作成または変更したときに DATABASE を指定した場合は、同じく DATABASE を指定する必要があります。  
  
 ALL SERVER  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 DDL トリガーのスコープが現在のサーバーに適用されることを示します。 トリガーを作成または変更したときに ALL SERVER を指定した場合は、同じく ALL SERVER を指定する必要があります。 ALL SERVER はログオン トリガーにも適用されます。  
  
> [!NOTE]  
>  このオプションは、包含データベースでは使用できません。  
  
## <a name="remarks"></a>解説  
 DML トリガーを削除するには、DML トリガー自体またはトリガー テーブルを削除します。 テーブルを削除した場合、関係付けられているすべてのトリガーも削除されます。  
  
 トリガーに関する情報を削除トリガーを削除すると、 **sys.objects**、 **sys.triggers**と**sys.sql_modules**カタログ ビューです。  
  
 すべてのトリガーが同一の ON 句で作成されている場合のみ、DROP TRIGGER ステートメントごとに複数の DDL トリガーを削除できます。  
  
 トリガーの名前を変更するには、DROP TRIGGER と CREATE TRIGGER を使用します。 トリガーの定義を変更するには、ALTER TRIGGER を使用します。  
  
 特定のトリガーの依存関係の確認の詳細については、次を参照してください。 [sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)、 [sys.dm_sql_referenced_entities と #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md)、および[sys.dm_sql_referencing_entities および #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md).  
  
 トリガーのテキストを表示する方法の詳細については、次を参照してください。 [sp_helptext & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md)と[sys.sql_modules & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md).  
  
 既存のトリガーの一覧を表示する方法の詳細については、次を参照してください。 [sys.triggers & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md)と[sys.server_triggers & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-server-triggers-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 削除 DML トリガーでは、テーブルまたはトリガーが定義されているビューに対する ALTER 権限が必要です。  
  
 サーバー スコープ (ON ALL SERVER) で定義されている DDL トリガー、またはログオン トリガーを削除するには、サーバーでの CONTROL SERVER 権限が必要です。 データベース スコープ (ON DATABASE) で定義されている DDL トリガーを削除するには、現在のデータベースでの ALTER ANY DATABASE DDL TRIGGER 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-dropping-a-dml-trigger"></a>A. DML トリガーを削除する  
 次の例では削除、`employee_insupd`トリガーには、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。 (以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]トリガー IF EXISTS の DROP 構文を使用することができます)。  
  
```  
IF OBJECT_ID ('employee_insupd', 'TR') IS NOT NULL  
   DROP TRIGGER employee_insupd;  
```  
  
### <a name="b-dropping-a-ddl-trigger"></a>B. DDL トリガーを削除する  
 次の例は、DDL トリガーを削除`safety`です。  
  
> [!IMPORTANT]  
>  DDL トリガーはスキーマ スコープではないと、そのためには表示されませんので、 **sys.objects**カタログ ビューをデータベースに存在するかどうかをクエリに、OBJECT_ID 関数は使用できません。 スキーマ スコープでないオブジェクトをクエリするには、適切なカタログ ビューを使用する必要があります。 DDL トリガーは、使用**sys.triggers**です。  
  
```  
DROP TRIGGER safety  
ON DATABASE;  
```  
  
## <a name="see-also"></a>参照  
 [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [ENABLE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/enable-trigger-transact-sql.md)   
 [DISABLE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/disable-trigger-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [DML トリガーに関する情報の取得](../../relational-databases/triggers/get-information-about-dml-triggers.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sp_helptrigger &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptrigger-transact-sql.md)   
 [sys.triggers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md)   
 [sys.trigger_events &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trigger-events-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.assembly_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-assembly-modules-transact-sql.md)   
 [sys.server_triggers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-triggers-transact-sql.md)   
 [sys.server_trigger_events &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql.md)   
 [sys.server_sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql.md)   
 [sys.server_assembly_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql.md)  
  
  

