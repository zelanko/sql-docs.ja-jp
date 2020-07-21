---
title: sp_update_targetservergroup (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_targetservergroup_TSQL
- sp_update_targetservergroup
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_targetservergroup
ms.assetid: 4ac65ed6-e07e-40e4-a282-13bfd92dfa41
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 16cd7c339a476875ee3f3a7319ddaf57f0d69711
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85891274"
---
# <a name="sp_update_targetservergroup-transact-sql"></a>sp_update_targetservergroup (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  指定した対象サーバーグループの名前を変更します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_update_targetservergroup  
     [@name =] 'current_name' ,  
     [@new_name =] 'new_name'  
```  
  
## <a name="arguments"></a>引数  
`[ @name = ] 'current_name'`対象サーバーグループの名前。 *current_name*は**sysname**であり、既定値はありません。  
  
`[ @new_name = ] 'new_name'`対象サーバーグループの新しい名前を指定します。 *new_name*は**sysname**であり、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="permissions"></a>アクセス許可  
 このストアドプロシージャを実行するには、 **sysadmin**固定サーバーロールがユーザーに付与されている必要があります。  
  
## <a name="remarks"></a>Remarks  
 **sp_update_targetservergroup**は、 **msdb**データベースから実行する必要があります。  
  
## <a name="examples"></a>使用例  
 次の例では、ターゲット サーバー グループ `Servers Processing Customer Orders` の名前を `Local Servers Processing Customer Orders` に変更します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_targetservergroup  
    @name = N'Servers Processing Customer Orders',  
    @new_name = N'Local Servers Processing Customer Orders' ;  
GO  
```  
  
## <a name="see-also"></a>関連項目  
 [sp_add_targetservergroup &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-add-targetservergroup-transact-sql.md)   
 [sp_delete_targetservergroup &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-delete-targetservergroup-transact-sql.md)   
 [sp_help_targetservergroup &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-help-targetservergroup-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
