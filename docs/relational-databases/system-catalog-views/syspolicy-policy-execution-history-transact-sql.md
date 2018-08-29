---
title: syspolicy_policy_execution_history (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- syspolicy_policy_execution_history_TSQL
- syspolicy_policy_execution_history
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_policy_execution_history view
ms.assetid: b13c44a7-6d49-4d50-abe1-e657fc52bb05
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 7db5a20395ec6e0e41d70d6b2dbb04dee991a0c1
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43021396"
---
# <a name="syspolicypolicyexecutionhistory-transact-sql"></a>syspolicy_policy_execution_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ポリシーが実行された時間、各実行の結果、およびエラーの詳細 (発生した場合) を表示します。 次の表では、syspolicy_policy_execution_history ビュー内の列について説明します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|history_id|**bigint**|このレコードの識別子。 各レコードは、1 つのポリシーを示し、そのポリシーが開始された 1 回分を表します。|  
|policy_id|**int**|ポリシーの識別子。|  
|start_date|**datetime**|このポリシーの実行が試行された日時。|  
|end_date|**datetime**|このポリシーの実行が終了した時刻。|  
|result|**bit**|ポリシーの成功または失敗。 0 = 失敗、1 = 成功。|  
|exception_message|**nvarchar(max)**|例外が発生した場合に、その例外によって生成されたメッセージ。|  
|exception|**nvarchar(max)**|例外が発生した場合、その説明。|  
  
## <a name="remarks"></a>コメント  
 [Syspolicy_policy_execution_history_details](../../relational-databases/system-catalog-views/syspolicy-policy-execution-history-details-transact-sql.md)ビューには、ポリシーおよびテストされた条件式のターゲットについての関連する詳細が含まれています。  
  
## <a name="permissions"></a>アクセス許可  
 msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したサーバーの管理](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [ポリシーベースの管理ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
