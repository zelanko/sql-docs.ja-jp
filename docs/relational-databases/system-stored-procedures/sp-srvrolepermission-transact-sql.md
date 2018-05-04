---
title: sp_srvrolepermission (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/20/2017
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
- sp_srvrolepermission_TSQL
- sp_srvrolepermission
dev_langs:
- TSQL
helpviewer_keywords:
- sp_srvrolepermission
ms.assetid: 5709667f-e3e4-48a2-93ec-af5e22a2ac58
caps.latest.revision: 32
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: a9035aab262ca4b32b828ef5c2f1257e1ae4ca58
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spsrvrolepermission-transact-sql"></a>sp_srvrolepermission (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  固定サーバー ロールの権限を表示します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_srvrolepermission [ [ @srvrolename = ] 'role']  
```  
  
## <a name="arguments"></a>引数  
 [  **@srvrolename =** ] **'***ロール***'**  
 権限を返す固定サーバー ロールの名前を指定します。 *ロール*は**sysname**、既定値は NULL です。 ロールを指定しない場合、すべての固定サーバー ロールの権限が返されます。 *ロール*値は次のいずれかを持つことができます。  
  
|値|Description|  
|-----------|-----------------|  
|**sysadmin**|システム管理者。|  
|**securityadmin**|セキュリティ管理者。|  
|**serveradmin**|サーバー管理者。|  
|**setupadmin**|セットアップ管理者。|  
|**processadmin**|プロセス管理者。|  
|**diskadmin**|ディスク管理者。|  
|**dbcreator**|データベース作成者。|  
|**bulkadmin**|BULK INSERT ステートメントを実行できます。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**サーバー ロール**|**sysname**|固定サーバー ロールの名前。|  
|**アクセス許可**|**sysname**|関連付けられた権限**ServerRole**|  
  
## <a name="remarks"></a>解説  
 表示される権限には、固定サーバー ロールのメンバーが実行できる、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントとその他の特別な操作が含まれます。 固定サーバー ロールの一覧を表示するには実行**sp_helpsrvrole**です。  
  
 **Sysadmin**固定サーバー ロールは、その他のすべての固定サーバー ロールのアクセス許可を持っています。  
  
## <a name="permissions"></a>権限  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次のクエリでは、固定サーバー ロール `sysadmin` に関連する権限が返されます。  
  
```  
EXEC sp_srvrolepermission 'sysadmin';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティ ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md)   
 [sp_dropsrvrolemember &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql.md)   
 [sp_helpsrvrole &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsrvrole-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
