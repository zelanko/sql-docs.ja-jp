---
title: sp_resync_targetserver (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_resync_targetserver
- sp_resync_targetserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_resync_targetserver
ms.assetid: 40e44df7-d3e3-44ee-b149-08aba629a21f
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8d91ef10c7f1e98c4ad65d014f90fc42b0317ec5
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="spresynctargetserver-transact-sql"></a>sp_resync_targetserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定された対象サーバー内のマルチサーバー ジョブをすべて再同期化します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_resync_targetserver  
     [ @server_name = ] 'server'  
```  
  
## <a name="arguments"></a>引数  
 [ **@server_name =**] **'***server***'**  
 再同期化するサーバーの名前を指定します。 *server* のデータ型は **sysname**で、既定値はありません。 場合**すべて**が指定されているすべての対象サーバーが再同期化します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 結果を報告**sp_post_msx_operation**アクション。  
  
## <a name="remarks"></a>解説  
 **sp_resync_targetserver**については、対象サーバーの現在のセットを削除し、ダウンロードする対象サーバーの新しいセットが通知されます。 新しいセットは、すべてのマルチサーバー ジョブを削除する命令が 1 つと、サーバーで対象になっている各ジョブのエージェントで構成されます。  
  
## <a name="permissions"></a>権限  
 このプロシージャの実行権限は、既定では **sysadmin** 固定サーバー ロールのメンバーに与えられています。  
  
## <a name="examples"></a>使用例  
 次の例では、対象サーバー `SEATTLE1` を再同期化します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_resync_targetserver  
    N'SEATTLE1' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_help_downloadlist &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-downloadlist-transact-sql.md)   
 [sp_post_msx_operation &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
