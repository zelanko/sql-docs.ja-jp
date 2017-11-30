---
title: "sp_update_targetservergroup (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_update_targetservergroup_TSQL
- sp_update_targetservergroup
dev_langs: TSQL
helpviewer_keywords: sp_update_targetservergroup
ms.assetid: 4ac65ed6-e07e-40e4-a282-13bfd92dfa41
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cef648a7eb3b332a41d7b8d69b2b09201e1128cd
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spupdatetargetservergroup-transact-sql"></a>sp_update_targetservergroup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定した対象サーバー グループの名前を変更します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_update_targetservergroup  
     [@name =] 'current_name' ,  
     [@new_name =] 'new_name'  
```  
  
## <a name="arguments"></a>引数  
 [  **@name =**] **'***current_name***'**  
 対象サーバー グループの名前を指定します。 *current_name*は**sysname**、既定値はありません。  
  
 [  **@new_name =**] **'***new_name***'**  
 対象サーバー グループの新しい名前を指定します。 *新しい名前*は**sysname**、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="permissions"></a>Permissions  
 このストアド プロシージャを実行するユーザーに付与する必要があります、 **sysadmin**固定サーバー ロール。  
  
## <a name="remarks"></a>解説  
 **sp_update_targetservergroup**から実行する必要があります、 **msdb**データベース。  
  
## <a name="examples"></a>使用例  
 次の例では、対象サーバー グループ `Servers Processing Customer Orders` の名前を `Local Servers Processing Customer Orders` に変更します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_targetservergroup  
    @name = N'Servers Processing Customer Orders',  
    @new_name = N'Local Servers Processing Customer Orders' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_add_targetservergroup &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-add-targetservergroup-transact-sql.md)   
 [sp_delete_targetservergroup &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-delete-targetservergroup-transact-sql.md)   
 [sp_help_targetservergroup &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-help-targetservergroup-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
