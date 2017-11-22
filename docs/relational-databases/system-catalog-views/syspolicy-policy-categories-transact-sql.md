---
title: "syspolicy_policy_categories (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
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
- syspolicy_policy_categories
- syspolicy_policy_categories_TSQL
dev_langs: TSQL
helpviewer_keywords: syspolicy_policy_groups view
ms.assetid: 65f080c7-771f-4cf6-a7a0-88882c637f8d
caps.latest.revision: "15"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7f75d3b95c0c37fa9acf2a550651f34308d0e782
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="syspolicypolicycategories-transact-sql"></a>syspolicy_policy_categories (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  インスタンスのポリシー ベースの管理のポリシー カテゴリごとに 1 行を表示[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 ポリシー カテゴリを使用して、多数のポリシーがある場合は、ポリシーを編成できます。 次の表では、syspolicy_policy_groups ビュー内の列について説明します。  
 
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|policy_category_id|**int**|ポリシー カテゴリの識別子です。|  
|name|**sysname**|ポリシー カテゴリの名前です。|  
|mandate_database_subscriptions|**bit**|明示的なサブスクリプションがなくてもポリシー カテゴリをインスタンス内のすべてのデータベースに適用するか (1)、明示的なサブスクリプションを使用してポリシー カテゴリをデータベースに適用する必要があるか (0) を示します。|  
  
## <a name="remarks"></a>解説  
 ポリシー ベースの管理ポリシー グループが一覧表示されます。  
  
## <a name="permissions"></a>Permissions  
 msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したサーバーの管理](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [ポリシーベースの管理ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
