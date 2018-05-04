---
title: sp_add_maintenance_plan_job (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
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
- sp_add_maintenance_plan_job_TSQL
- sp_add_maintenance_plan_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_maintenance_plan_job
ms.assetid: 7205855c-964f-4f55-bf75-39a55f6fe7bd
caps.latest.revision: 32
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9030783c4fd6648a99f3cbbbcd8b265f6bc85206
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spaddmaintenanceplanjob-transact-sql"></a>sp_add_maintenance_plan_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  メンテナンス プランを既存のジョブに関連付けます。  
  
> [!NOTE]  
>  このストアド プロシージャは、データベース メンテナンス プランと共に使用できます。 ただし、この機能は、このストアド プロシージャを使用しないメンテナンス プランでも実行できます。 このプロシージャは、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からアップグレードしたプログラムでデータベース メンテナンス プランを管理する場合に使用します。  
  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_add_maintenance_plan_job [ @plan_id = ] 'plan_id' , [ @job_id = ] 'job_id'  
```  
  
## <a name="arguments"></a>引数  
 [  **@plan_id =**] **'***plan_id***'**  
 メンテナンス プランの ID を指定します。 *plan_id*は**uniqueidentifier**、有効な ID を指定する必要があります  
  
 [ **@job_id =**] **'***job_id***'**  
 メンテナンス プランと関連付けられるジョブの ID を指定します。 *job_id*は**uniqueidentifier**、有効な ID を指定する必要があります ジョブまたはジョブを作成するには、実行**sp_add_job**、または SQL Server Management Studio を使用します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_add_maintenance_plan_job**から実行する必要があります、 **msdb**データベース。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_add_maintenance_plan_job**です。  
  
## <a name="examples"></a>使用例  
 この例を使用して作成したメンテナンス プランにジョブ"B8FCECB1-E22C-11D2-AA64-00C04F688EAE"を追加する**sp_add_maintenance_plan_job**です。  
  
```  
EXECUTE   sp_add_maintenance_plan_job N'FAD6F2AB-3571-11D3-9D4A-00C04FB925FC', N'B8FCECB1-E22C-11D2-AA64-00C04F688EAE';  
```  
  
## <a name="see-also"></a>参照  
 [メンテナンス プラン](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [データベース メンテナンス プラン ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-maintenance-plan-stored-procedures-transact-sql.md)  
  
  
