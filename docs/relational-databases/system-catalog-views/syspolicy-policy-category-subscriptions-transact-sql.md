---
title: syspolicy_policy_category_subscriptions (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- syspolicy_policy_category_subscriptions_TSQL
- syspolicy_policy_category_subscriptions
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_policy_group_subscriptions view
ms.assetid: b3b3a7d7-0b78-46c0-9755-045f7a5692b9
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3092a2977a35d7ab42cfaafe07611ddd51b9bc5b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="syspolicypolicycategorysubscriptions-transact-sql"></a>syspolicy_policy_category_subscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのポリシー ベースの管理サブスクリプションごとに 1 つの行を表示します。 各行には、対象とポリシー カテゴリのペアがについて説明します。 次の表では、syspolicy_policy_group_subscriptions ビュー内の列について説明します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|policy_category_subscription_id|**int**|このレコードの識別子。|  
|target_type|**sysname**|このサブスクリプションの対象であるデータベース オブジェクトの種類。|  
|target_object|**sysname**|対象オブジェクトの名前。|  
|policy_category_id|**int**|対象に適用されるポリシー カテゴリの ID。|  
  
## <a name="remarks"></a>解説  
 このビューには、ポリシー カテゴリにサブスクライブされる対象が表示されます。  
  
## <a name="permissions"></a>権限  
 msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用して、サーバーを管理します。](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [ポリシーベースの管理ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
