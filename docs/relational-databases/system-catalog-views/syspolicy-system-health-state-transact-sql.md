---
title: syspolicy_system_health_state (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syspolicy_system_health_state_TSQL
- syspolicy_system_health_state
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_system_health_state view
ms.assetid: 00815106-9fe4-481d-a9e1-a256101887f4
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 47701075fd3c650870f2ce81b021fe7c8910b26e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68110901"
---
# <a name="syspolicy_system_health_state-transact-sql"></a>syspolicy_system_health_state (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ポリシーベースの管理ポリシーと対象のクエリ式の組み合わせごとに1つの行を表示します。 サーバーのポリシー正常性をプログラムで確認するには、syspolicy_system_health_state ビューを使用します。 次の表では、syspolicy_system_health_state ビュー内の列について説明します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|health_state_id|**bigint**|ポリシー正常性状態レコードの識別子。|  
|policy_id|**int**|ポリシーの識別子。|  
|last_run_date|**datetime**|ポリシーが最後に実行された日時。|  
|target_query_expression_with_id|**nvarchar (400)**|Id 変数に割り当てられた値を持つターゲット式。ポリシーの評価対象となるターゲットを定義します。|  
|target_query_expression|**nvarchar(max)**|ポリシーの評価対象となるターゲットを定義する対象。|  
|結果|**bit**|ポリシーに関して、このターゲットのヘルス状態:<br /><br /> 0 = 失敗<br /><br /> 1 = 成功|  
  
## <a name="remarks"></a>Remarks  
 syspolicy_system_health_state ビューには、対象のクエリ式の最新の正常性状態が、アクティブ (有効) なポリシーごとに表示されます。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] オブジェクト エクスプローラーと [オブジェクト エクスプローラーの詳細] ページでは、このビューのポリシー正常性が集計され、重大な正常性状態が表示されます。  
  
## <a name="permissions"></a>アクセス許可  
 msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [ポリシーベースの管理を使用してサーバーを管理する](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [ポリシーベースの管理ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
