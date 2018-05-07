---
title: syspolicy_policies (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- syspolicy_policies_TSQL
- syspolicy_policies
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_policies view
ms.assetid: aecf35bb-187e-4f80-870f-48081b88974e
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5c05a24d94ba5b65eff8c3aec2791c9993b99589
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="syspolicypolicies-transact-sql"></a>syspolicy_policies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのポリシー ベースの管理ポリシーごとに 1 つの行を表示します。 syspolicy_policies は、msdb データベースの dbo スキーマに属します。 次の表では、syspolicy_policies ビューの列について説明します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|policy_id|**int**|ポリシーの識別子。|  
|name|**sysname**|ポリシーの名前。|  
|condition_id|**int**|このポリシーによって適用またはテストされる条件の ID。|  
|root_condition_id|**int**|内部使用のみです。|  
|date_created|**datetime**|ポリシーが作成された日時。|  
|execution_mode|**int**|ポリシーの評価モード。 使用可能な値は次のとおりです。<br /><br /> 0 = 要求時<br /><br /> このモードでは、ユーザーが直接指定した場合にポリシーが評価されます。<br /><br /> 1 = 変更時: 回避<br /><br /> この自動モードでは、DDL トリガーを使用してポリシー違反が防止されます。<br /><br /> 2 = 変更時: ログのみ<br /><br /> この自動モードでは、関連する変更が行われたときにイベント通知を使用してポリシーが評価され、ポリシー違反がログに記録されます。<br /><br /> 4 = スケジュールで実行<br /><br /> この自動モードでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブを使用してポリシーが定期的に評価されます。 ポリシー違反はログに記録されます。<br /><br /> 注: 値 3 は、使用可能な値ではありません。|  
|policy_category|**int**|このポリシーが属するポリシー ベースの管理のポリシー カテゴリの ID。 既定のポリシー グループの場合は NULL です。|  
|schedule_uid|**uniqueidentifier**|execution_mode が "スケジュールで実行" の場合にスケジュールの ID が格納されます。それ以外の場合は NULL です。|  
|description|**nvarchar(max)**|ポリシーの説明。 この説明の列は省略可能であり、NULL の場合もあります。|  
|help_text|**nvarchar (4000)**|help_link に属するハイパーリンク テキスト。|  
|help_link|**nvarchar(2083)**|ポリシーの作成者がポリシーに割り当てた追加のヘルプ ハイパーリンク。|  
|object_set_id|**int**|ポリシーが評価するオブジェクト セットの ID。|  
|is_enabled|**bit**|ポリシーが現在有効 (1) か無効 (0) かを示します。|  
|job_id|**uniqueidentifier**|execution_mode が "スケジュールで実行" の場合に、ポリシーを実行する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブの ID が格納されます。|  
|created_by|**sysname**|ポリシーを作成したログイン。|  
|modified_by|**sysname**|ポリシーを最後に変更したログイン。 変更されていない場合は NULL です。|  
|date_modified|**datetime**|ポリシーが作成された日時。 変更されていない場合は NULL です。|  
  
## <a name="remarks"></a>解説  
 ポリシー ベースの管理のトラブルシューティングを行うときは、クエリ、 [syspolicy_conditions](../../relational-databases/system-catalog-views/syspolicy-conditions-transact-sql.md)ビューによってポリシーが有効になっているかどうかを決定します。 このビューには、ポリシーを作成したユーザーや最後に変更したユーザーも表示されます。  
  
## <a name="permissions"></a>権限  
 msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用して、サーバーを管理します。](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [ポリシーベースの管理ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
