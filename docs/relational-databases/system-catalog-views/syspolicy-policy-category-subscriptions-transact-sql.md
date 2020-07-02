---
title: syspolicy_policy_category_subscriptions (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syspolicy_policy_category_subscriptions_TSQL
- syspolicy_policy_category_subscriptions
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_policy_group_subscriptions view
ms.assetid: b3b3a7d7-0b78-46c0-9755-045f7a5692b9
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: f8bd5886c9cb0686b1bef9764f9f9fb12d1548cc
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85786412"
---
# <a name="syspolicy_policy_category_subscriptions-transact-sql"></a>syspolicy_policy_category_subscriptions (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのポリシー ベースの管理サブスクリプションごとに 1 つの行を表示します。 各行には、ターゲットとポリシーカテゴリのペアが記述されています。 次の表では、syspolicy_policy_group_subscriptions ビュー内の列について説明します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|policy_category_subscription_id|**int**|このレコードの識別子。|  
|target_type|**sysname**|このサブスクリプションの対象であるデータベース オブジェクトの種類。|  
|target_object|**sysname**|対象オブジェクトの名前。|  
|policy_category_id|**int**|ターゲットに適用されるポリシーカテゴリの ID。|  
  
## <a name="remarks"></a>Remarks  
 このビューには、ポリシーカテゴリにサブスクライブされているターゲットが表示されます。  
  
## <a name="permissions"></a>アクセス許可  
 msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。  
  
## <a name="see-also"></a>関連項目  
 [ポリシーベースの管理を使用してサーバーを管理する](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [ポリシーベースの管理ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
