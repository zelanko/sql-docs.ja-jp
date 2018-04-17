---
title: sp_syspolicy_purge_health_state (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_syspolicy_purge_health_state_TSQL
- sp_syspolicy_purge_health_state
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_purge_health_state
ms.assetid: 4ba4aa91-4c19-41c7-b70d-5fd9d0e89a5e
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4d05668b8775c98e6b374545579a0043bb50df95
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="spsyspolicypurgehealthstate-transact-sql"></a>sp_syspolicy_purge_health_state (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  ポリシー ベースの管理のポリシー正常性状態を削除します。 ポリシー正常性状態とは、オブジェクト エクプローラ内の視覚インジケーター (赤い "X" の付いたスクロール記号) であり、ポリシーの評価に失敗したノードを確認するために使用できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_syspolicy_purge_health_state [ @target_tree_root_with_id = ] 'target_tree_root_with_id'  
```  
  
## <a name="arguments"></a>引数  
 [ **@target_tree_root_with_id =** ] **'***target_tree_root_with_id***'**  
 正常性状態をクリアするオブジェクト エクスプローラー内のノードを表します。 *target_tree_root_with_id* is **nvarchar(400)**, with a default of NULL.  
  
 msdb.dbo.syspolicy_system_health_state システム ビューの target_query_expression_with_id 列から値を指定できます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 msdb システム データベースのコンテキストで sp_syspolicy_purge_health_state を実行する必要があります。  
  
 パラメーターを指定せずにこのストアド プロシージャを実行すると、オブジェクト エクスプローラー内のすべてのノードのシステム正常性状態が削除されます。  
  
## <a name="permissions"></a>権限  
 PolicyAdministratorRole 固定データベース ロールのメンバーシップが必要です。  
  
> [!IMPORTANT]  
>  資格情報が昇格される可能性について: PolicyAdministratorRole ロールに割り当てられているユーザーは、サーバー トリガーを作成して、[!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスの動作に影響する可能性があるポリシーの実行をスケジュールできます。 たとえば、PolicyAdministratorRole ロールに割り当てられているユーザーは、ほとんどのオブジェクトが[!INCLUDE[ssDE](../../includes/ssde-md.md)]で作成されないようにすることができるポリシーを作成できます。 構成を制御について信頼できるユーザーにのみこの昇格される可能性の資格情報、ため PolicyAdministratorRole ロールを許可してください、[!INCLUDE[ssDE](../../includes/ssde-md.md)]です。  
  
## <a name="examples"></a>使用例  
 次の例では、オブジェクト エクスプローラー内の特定のノードの正常性状態を削除します。  
  
```  
EXEC msdb.dbo.sp_syspolicy_purge_health_state @target_tree_root_with_id = 'Server/Database[@ID=7]';  
  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)  
  
  
