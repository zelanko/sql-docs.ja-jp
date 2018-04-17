---
title: sp_add_maintenance_plan_db (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_add_maintenance_plan_db_TSQL
- sp_add_maintenance_plan_db
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_maintenance_plan_db
ms.assetid: 76f4fefa-5b99-4deb-beed-e198987a45a9
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2b2057ddd82b34d3762c45159ad7e151b369b413
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="spaddmaintenanceplandb-transact-sql"></a>sp_add_maintenance_plan_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベースとメンテナンス プランを関連付けます。  
  
> [!NOTE]  
>  このストアド プロシージャは、データベース メンテナンス プランと共に使用できます。 ただし、この機能は、このストアド プロシージャを使用しないメンテナンス プランでも実行できます。 このプロシージャは、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からアップグレードしたプログラムでデータベース メンテナンス プランを管理する場合に使用します。  
  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_add_maintenance_plan_db [ @plan_id = ] 'plan_id' ,   
     [ @db_name = ] 'database_name'  
```  
  
## <a name="arguments"></a>引数  
 [  **@plan_id =**] **'***plan_id***'**  
 メンテナンス プランのプラン ID を指定します。 *plan_id*は**uniqueidentifier**、有効な ID を指定する必要があります  
  
 [ **@db_name =**] **'***database_name***'**  
 メンテナンス プランに追加するデータベースの名前を指定します。 データベースが存在しない場合は、データベースをプランに追加する前にデータベースを作成する必要があります。 *database_name* は **sysname** です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_add_maintenance_plan_db**から実行する必要があります、 **msdb**データベース。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_add_maintenance_plan_db**です。  
  
## <a name="examples"></a>使用例  
 この例では追加、 **AdventureWorks2012**データベースで作成したメンテナンス プランを**sp_add_maintenance_plan**です。  
  
```  
EXECUTE   sp_add_maintenance_plan_db N'FAD6F2AB-3571-11D3-9D4A-00C04FB925FC',N'AdventureWorks2012';  
```  
  
## <a name="see-also"></a>参照  
 [メンテナンス プラン](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [データベース メンテナンス プラン ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-maintenance-plan-stored-procedures-transact-sql.md)  
  
  
