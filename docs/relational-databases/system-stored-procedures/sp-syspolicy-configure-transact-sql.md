---
title: sp_syspolicy_configure (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_configure
- sp_syspolicy_configure_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_configure
ms.assetid: 70c10922-9345-4190-ba69-808a43f760da
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c51d30c8453cd5a9c2a92a3eb2ad22016c461b8f
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33255936"
---
# <a name="spsyspolicyconfigure-transact-sql"></a>sp_syspolicy_configure (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ポリシー ベースの管理を有効にするかどうかなど、ポリシー ベースの管理の設定を構成します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_syspolicy_configure [ @name = ] 'name'  
    , [ @value = ] value  
```  
  
## <a name="arguments"></a>引数  
 [ **@name =** ] **'***name***'**  
 構成する設定の名前を指定します。 *名前*は**sysname**が必要であり、NULL または空の文字列にすることはできません。  
  
 *名前*値は次のいずれかを指定できます。  
  
-   'Enabled' : ポリシー ベースの管理を有効にするかどうかを指定します。  
  
-   'HistoryRetentionInDays' : ポリシー評価履歴を保持する日数を指定します。 0 に設定した場合、履歴は自動的には削除されません。  
  
-   'LogOnSuccess' : ポリシー ベースの管理のログに成功したポリシー評価を記録するかどうかを指定します。  
  
 [ **@value =** ] *value*  
 指定された値に関連付けられている値は、*名前*です。 *値*は**sql_variant**が必要とします。  
  
-   'Enabled' を指定する場合*名前*値は次のいずれかを使用することができます。  
  
    -   0 = ポリシー ベースの管理を無効にします。  
  
    -   1 = ポリシー ベースの管理を有効にします。  
  
-   'HistoryRententionInDays' を指定する場合*名前*整数値としての日数を指定します。  
  
-   'LogOnSuccess' を指定した場合*名前*値は次のいずれかを使用することができます。  
  
    -   0 = 失敗したポリシー評価のみをログに記録します。  
  
    -   1 = 成功したポリシー評価と失敗したポリシー評価の両方をログに記録します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 msdb システム データベースのコンテキストで sp_syspolicy_configure を実行する必要があります。  
  
 これらの設定の現在の値を表示するには、msdb.dbo.syspolicy_configuration システム ビューに対してクエリを実行します。  
  
## <a name="permissions"></a>権限  
 PolicyAdministratorRole 固定データベース ロールのメンバーシップが必要です。  
  
> [!IMPORTANT]  
>  資格情報が昇格される可能性について: PolicyAdministratorRole ロールに割り当てられているユーザーは、サーバー トリガーを作成して、[!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスの動作に影響する可能性があるポリシーの実行をスケジュールできます。 たとえば、PolicyAdministratorRole ロールに割り当てられているユーザーは、ほとんどのオブジェクトが[!INCLUDE[ssDE](../../includes/ssde-md.md)]で作成されないようにすることができるポリシーを作成できます。 構成を制御について信頼できるユーザーにのみこの昇格される可能性の資格情報、ため PolicyAdministratorRole ロールを許可してください、[!INCLUDE[ssDE](../../includes/ssde-md.md)]です。  
  
## <a name="examples"></a>使用例  
 次の例では、ポリシー ベースの管理を有効にします。  
  
```  
EXEC msdb.dbo.sp_syspolicy_configure @name = N'Enabled'  
, @value = 1;  
  
GO  
```  
  
 次の例では、ポリシーの履歴の保有期間を 14 日に設定します。  
  
```  
EXEC msdb.dbo.sp_syspolicy_configure @name = N'HistoryRetentionInDays'  
, @value = 14;  
  
GO  
```  
  
 次の例では、成功したポリシー評価と失敗したポリシー評価の両方をログに記録するようにポリシー ベースの管理を構成します。  
  
```  
EXEC msdb.dbo.sp_syspolicy_configure @name = N'LogOnSuccess'  
, @value = 1;  
  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_set_config_enabled &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-set-config-enabled-transact-sql.md)   
 [sp_syspolicy_set_config_history_retention &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-set-config-history-retention-transact-sql.md)   
 [sp_syspolicy_set_log_on_success &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-set-log-on-success-transact-sql.md)  
  
  
