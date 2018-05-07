---
title: dbo.syssessions (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dbo.syssessions_TSQL
- dbo.syssessions
- syssessions_TSQL
- syssessions
dev_langs:
- TSQL
helpviewer_keywords:
- syssessions system table
ms.assetid: 187819b6-c7f4-4a26-b74c-0a89e96695cf
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 222e9601e7f683419304f3530aaedeb79c5a776e
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="dbosyssessions-transact-sql"></a>dbo.syssessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  毎回[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントの開始と、新しいセッションを作成します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスが予期せず再開または停止すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントではジョブの状態を保持するためセッションが使用されます。 行ごと、 **syssessions**テーブルには、1 つのセッションの情報が含まれています。 使用して、 **sysjobactivity**各セッションの最後にジョブの状態を表示するテーブル。  
  
 次の表は、 **msdb**データベース。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント セッションの ID。|  
|**agent_start_date**|**datetime**|セッションに対して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスが開始された日時。|  
  
## <a name="remarks"></a>解説  
 メンバーであるユーザーのみの**sysadmin**固定サーバー ロールがこのテーブルにアクセスできます。  
  
## <a name="see-also"></a>参照  
 [dbo.sysjobactivity &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/dbo-sysjobactivity-transact-sql.md)  
  
  
