---
title: sp_delete_maintenance_plan_db (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_maintenance_plan_db_TSQL
- sp_delete_maintenance_plan_db
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_maintenance_plan_db
- maintenance plans [SQL Server], deleting
- removing maintenance plan
- disassociating maintenance plan
ms.assetid: d1e8afb5-12ee-492b-a770-ba708ed7c8a4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2935ecccb9ce0421396d552787d38b0b80fb3c45
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85772233"
---
# <a name="sp_delete_maintenance_plan_db-transact-sql"></a>sp_delete_maintenance_plan_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  指定されたデータベースから、指定されたメンテナンス プランの関連付けを解除します。  
  
> [!NOTE]  
>  このストアドプロシージャは、データベースメンテナンスプランで使用されます。 この機能は、このストアドプロシージャを使用しないメンテナンスプランに置き換えられました。 このプロシージャは、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からアップグレードしたプログラムでデータベース メンテナンス プランを管理する場合に使用します。  
  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_delete_maintenance_plan_db [ @plan_id = ] 'plan_id' ,   
     [ @db_name = ] 'database_name'   
```  
  
## <a name="arguments"></a>引数  
`[ @plan_id = ] 'plan\_id'`メンテナンスプランの ID を指定します。 *plan_id*は**uniqueidentifier**です。  
  
`[ @db_name = ] 'database\_name'`メンテナンスプランから削除するデータベース名を指定します。 *database_name* は **sysname** です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_delete_maintenance_plan_db**は、 **msdb**データベースから実行する必要があります。  
  
 **Sp_delete_maintenance_plan_db**ストアドプロシージャは、メンテナンスプランと指定されたデータベースとの間の関連付けを削除します。データベースを削除したり、破棄したりすることはありません。  
  
 **Sp_delete_maintenance_plan_db** 、メンテナンスプランから最後のデータベースを削除すると、ストアドプロシージャによってメンテナンスプランも削除されます。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_delete_maintenance_plan_db**を実行できるのは、 **sysadmin**固定サーバーロールのメンバーだけです。  
  
## <a name="examples"></a>使用例  
 以前に**sp_add_maintenance_plan_db**を使用して追加した、 **AdventureWorks2012**データベースのメンテナンスプランを削除します。  
  
```  
EXECUTE   sp_delete_maintenance_plan_db N'FAD6F2AB-3571-11D3-9D4A-00C04FB925FC', N'AdventureWorks2012';  
```  
  
## <a name="see-also"></a>関連項目  
 [メンテナンス プラン](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [データベースメンテナンスプランのストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/database-maintenance-plan-stored-procedures-transact-sql.md)  
  
  
