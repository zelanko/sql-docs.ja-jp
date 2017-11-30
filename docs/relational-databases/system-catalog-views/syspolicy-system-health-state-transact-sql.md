---
title: "syspolicy_system_health_state (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- syspolicy_system_health_state_TSQL
- syspolicy_system_health_state
dev_langs: TSQL
helpviewer_keywords: syspolicy_system_health_state view
ms.assetid: 00815106-9fe4-481d-a9e1-a256101887f4
caps.latest.revision: "22"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 63928630f941e92fbbf7a7e0e3c4a48939d1a8db
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="syspolicysystemhealthstate-transact-sql"></a>syspolicy_system_health_state (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ポリシー ベースの管理ポリシーと対象のクエリ式の組み合わせごとに 1 つの行を表示します。 サーバーのポリシー正常性をプログラムで確認するには、syspolicy_system_health_state ビューを使用します。 次の表では、syspolicy_system_health_state ビュー内の列について説明します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|health_state_id|**bigint**|ポリシー正常性状態レコードの識別子。|  
|policy_id|**int**|ポリシーの識別子。|  
|last_run_date|**datetime**|ポリシーが最後に実行された日時。|  
|target_query_expression_with_id|**nvarchar (400)**|ID 変数に値が割り当てられた、ポリシーが評価される対象を定義する対象の式。|  
|target_query_expression|**nvarchar(max)**|ポリシーが評価される対象を定義する式。|  
|result|**bit**|ポリシーに対するこの対象の正常性状態:<br /><br /> 0 = 失敗<br /><br /> 1 = 成功|  
  
## <a name="remarks"></a>解説  
 syspolicy_system_health_state ビューには、対象のクエリ式の最新の正常性状態が、アクティブ (有効) なポリシーごとに表示されます。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] オブジェクト エクスプローラーと [オブジェクト エクスプローラーの詳細] ページでは、このビューのポリシー正常性が集計され、重大な正常性状態が表示されます。  
  
## <a name="permissions"></a>Permissions  
 msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したサーバーの管理](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [ポリシーベースの管理ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
