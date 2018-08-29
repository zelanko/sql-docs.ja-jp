---
title: データベース メンテナンス プラン ストアド プロシージャ (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- database maintenance plans [SQL Server]
- system stored procedures [SQL Server], database maintenance plans
- maintenance plans [SQL Server], stored procedures
ms.assetid: f5f658e3-417e-4286-9213-5738266f3b28
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 96fd66726f900130bd9fe4e6300a660a0d2d6302
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43027106"
---
# <a name="database-maintenance-plan-stored-procedures-transact-sql"></a>データベース メンテナンス プランのストアド プロシージャ (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、次のシステムはストアド プロシージャを設定するメンテナンス タスクに使用されます。 これらのストアド プロシージャは、データベース メンテナンス プランと共に使用できます。 ただし、この機能は、これらのストアド プロシージャを使用しないメンテナンス プランでも実行できます。 これらのプロシージャは、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からアップグレードしたプログラムでデータベース メンテナンス プランを管理する場合に使用します。  
  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
|||  
|-|-|  
|[sp_add_maintenance_plan](../../relational-databases/system-stored-procedures/sp-add-maintenance-plan-transact-sql.md)|[sp_delete_maintenance_plan_db](../../relational-databases/system-stored-procedures/sp-delete-maintenance-plan-db-transact-sql.md)|  
|[sp_add_maintenance_plan_db](../../relational-databases/system-stored-procedures/sp-add-maintenance-plan-db-transact-sql.md)|[sp_delete_maintenance_plan_job](../../relational-databases/system-stored-procedures/sp-delete-maintenance-plan-job-transact-sql.md)|  
|[sp_add_maintenance_plan_job](../../relational-databases/system-stored-procedures/sp-add-maintenance-plan-job-transact-sql.md)|[sp_help_maintenance_plan](../../relational-databases/system-stored-procedures/sp-help-maintenance-plan-transact-sql.md)|  
|[sp_delete_maintenance_plan](../../relational-databases/system-stored-procedures/sp-delete-maintenance-plan-transact-sql.md)||  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [メンテナンス プラン](../../relational-databases/maintenance-plans/maintenance-plans.md)  
  
  
