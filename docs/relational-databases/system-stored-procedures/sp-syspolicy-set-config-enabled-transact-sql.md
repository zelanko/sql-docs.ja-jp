---
title: sp_syspolicy_set_config_enabled (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_set_config_enabled
- sp_syspolicy_set_config_enabled_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_set_config_enabled
ms.assetid: ddace1cc-ff23-4b61-8efb-8ded3df438bb
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: e6b2b64e5a29d6c0f8a072f79714f86fc45bc973
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68035481"
---
# <a name="sp_syspolicy_set_config_enabled-transact-sql"></a>sp_syspolicy_set_config_enabled (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ポリシーベースの管理を有効または無効にします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_syspolicy_set_config_enabled [ @value = ] value  
```  
  
## <a name="arguments"></a>引数  
`[ @value = ] value`ポリシーベースの管理を有効にするかどうかを指定します。 *値*は**sqlvariant**で、次のいずれかの値を指定できます。  
  
-   0 (または 'false') = 無効  
  
-   1 (または ' true ') = 有効  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>Remarks  
 sp_syspolicy_set_config_enabled は msdb システム データベースのコンテキストで実行する必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 PolicyAdministratorRole 固定データベース ロールのメンバーシップが必要です。  
  
> [!IMPORTANT]  
>  資格情報が昇格される可能性について: PolicyAdministratorRole ロールに割り当てられているユーザーは、サーバー トリガーを作成して、[!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスの動作に影響する可能性があるポリシーの実行をスケジュールできます。 たとえば、PolicyAdministratorRole ロールに割り当てられているユーザーは、ほとんどのオブジェクトが[!INCLUDE[ssDE](../../includes/ssde-md.md)]で作成されないようにすることができるポリシーを作成できます。 このような資格情報が昇格される可能性があるため、Policy管理者ロールロールは、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]の構成の制御によって信頼されているユーザーのみに付与する必要があります。  
  
## <a name="examples"></a>使用例  
 次の例では、ポリシーベースの管理を有効にします。  
  
```  
EXEC msdb.dbo.sp_syspolicy_set_config_enabled @value = 1;  
  
GO   
```  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;のポリシーベースの管理ストアドプロシージャ](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_configure &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-configure-transact-sql.md)  
  
  
