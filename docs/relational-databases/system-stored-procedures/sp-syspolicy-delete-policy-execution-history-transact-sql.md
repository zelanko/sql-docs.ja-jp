---
title: sp_syspolicy_delete_policy_execution_history (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_delete_policy_execution_history
- sp_syspolicy_delete_policy_execution_history_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_delete_policy_execution_history
ms.assetid: fe651af9-267e-45ec-b4e7-4b0698fb1be3
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d4e7f496124727389993c1e249b80aeaa7414b5f
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33262735"
---
# <a name="spsyspolicydeletepolicyexecutionhistory-transact-sql"></a>sp_syspolicy_delete_policy_execution_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ポリシー ベースの管理のポリシーの実行履歴を削除します。 このストアド プロシージャを使用して、特定のポリシーまたはすべてのポリシーの実行履歴、および特定の日付までの実行履歴を削除できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_syspolicy_delete_policy_execution_history [ @policy_id = ] policy_id ]  
    [ , [ @oldest_date = ] 'oldest_date' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@policy_id=** ] *policy_id*  
 実行履歴を削除するポリシーの識別子を指定します。 *policy_id*は**int**が必要とします。 NULL を指定できます。  
  
 [ **@oldest_date=** ] **'***oldest_date***'**  
 ポリシーの実行履歴を保持する最も古い日付を指定します。 この日付よりも前の実行履歴は削除されます。 *oldest_date*は**datetime**が必要とします。 NULL を指定できます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 sp_syspolicy_delete_policy_execution_history は msdb システム データベースのコンテキストで実行する必要があります。  
  
 値を取得する*policy_id*、し、実行履歴の日付を表示するには、次のクエリを使用することができます。  
  
```  
SELECT a.name AS N'policy_name', b.policy_id, b.start_date, b.end_date  
FROM msdb.dbo.syspolicy_policies AS a   
INNER JOIN msdb.dbo.syspolicy_policy_execution_history AS b  
ON a.policy_id = b.policy_id  
```  
  
 次の動作は、1 つまたは両方の値に NULL を指定した場合に適用されます。  
  
-   すべてのポリシー実行履歴を削除するには、両方に NULL を指定*policy_id*および*oldest_date*です。  
  
-   特定のポリシーのすべてのポリシー実行履歴を削除する識別子を指定して、ポリシーの*policy_id*、として NULL を指定して*oldest_date*です。  
  
-   特定の日付までのすべてのポリシーのポリシー実行履歴を削除するには、NULL を指定*policy_id*、日付を指定し、 *oldest_date*です。  
  
 ポリシーの実行履歴をアーカイブするには、オブジェクト エクスプローラーでポリシー履歴ログを開いて、実行履歴をファイルにエクスポートします。 ポリシー履歴ログにアクセスするには、展開**管理**を右クリックして**ポリシーの管理**、クリックして**履歴を表示する**です。  
  
## <a name="permissions"></a>権限  
 PolicyAdministratorRole 固定データベース ロールのメンバーシップが必要です。  
  
> [!IMPORTANT]  
>  資格情報が昇格される可能性について: PolicyAdministratorRole ロールに割り当てられているユーザーは、サーバー トリガーを作成して、[!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスの動作に影響する可能性があるポリシーの実行をスケジュールできます。 たとえば、PolicyAdministratorRole ロールに割り当てられているユーザーは、ほとんどのオブジェクトが[!INCLUDE[ssDE](../../includes/ssde-md.md)]で作成されないようにすることができるポリシーを作成できます。 構成を制御について信頼できるユーザーにのみこの昇格される可能性の資格情報、ため PolicyAdministratorRole ロールを許可してください、[!INCLUDE[ssDE](../../includes/ssde-md.md)]です。  
  
## <a name="examples"></a>使用例  
 次の例では、ID が 7 のポリシーについて特定の日付より前のポリシーの実行履歴を削除します。  
  
```  
EXEC msdb.dbo.sp_syspolicy_delete_policy_execution_history @policy_id = 7  
, @oldest_date = '2009-02-16 16:00:00.000';  
  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_set_config_history_retention &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-set-config-history-retention-transact-sql.md)   
 [sp_syspolicy_purge_history &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-purge-history-transact-sql.md)  
  
  
